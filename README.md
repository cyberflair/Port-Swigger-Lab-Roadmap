# Port-Swigger-Lab-Roadmap
List of Vulnerabilities and Lab Tracker
🛡️ Vulnerability List & Lab Tracker
1️⃣ SQL Injection (18 Labs) 💥
What? Injecting malicious SQL queries to manipulate databases. Impact: Can lead to full database compromise, data leaks, or even remote code execution.

📋 Lab List
Difficulty	Title	Status	Writeup
Apprentice	🧱 🧱 SQL injection vulnerability in WHERE clause allowing retrieval of hidden data	✅ Pwned	📝
Apprentice	🔓 SQL injection vulnerability allowing login bypass	✅ Pwned	📝
Practitioner	🗄️ SQL injection attack, querying the database type and version on Oracle	✅ Pwned	📝
Practitioner	🗄️ SQL injection attack, querying the database type and version on MySQL and Microsoft	✅ Pwned	📝
Practitioner	📁 SQL injection attack, listing the database contents on non-Oracle databases	✅ Pwned	📝
Practitioner	📁 SQL injection attack, listing the database contents on Oracle	✅ Pwned	📝
Practitioner	🔍 SQL injection UNION attack, determining the number of columns returned by the query	✅ Pwned	📝
Practitioner	🔍 SQL injection UNION attack, finding a column containing text	✅ Pwned	📝
Practitioner	🕵️ SQL injection UNION attack, retrieving data from other tables	✅ Pwned	📝
Practitioner	🧩 SQL injection UNION attack, retrieving multiple values in a single column	✅ Pwned	📝
Practitioner	👀 Blind SQL injection with conditional responses	✅ Pwned	📝
Practitioner	❌ Blind SQL injection with conditional errors	✅ Pwned	📝
Practitioner	📢 Visible error-based SQL injection	✅ Pwned	📝
Practitioner	⏳ Blind SQL injection with time delays	✅ Pwned	📝
Practitioner	🕒 Blind SQL injection with time delays and information retrieval	✅ Pwned	📝
Practitioner	🌐 Blind SQL injection with out-of-band interaction	✅ Pwned	📝
Practitioner	📦 Blind SQL injection with out-of-band data exfiltration	✅ Pwned	📝
Practitioner	🧼 SQL injection with filter bypass via XML encoding	✅ Pwned	📝
2️⃣ Cross-site Scripting (XSS) (30 Labs) 💬
What? Injecting malicious scripts into trusted websites. Impact: Session hijacking, phishing, defacement, or redirecting users.

📋 Lab List
Difficulty	Title	Status	Writeup
Apprentice	🧱 Reflected XSS into HTML context with nothing encoded	⬜ Not Pwned	
Apprentice	🧱 Stored XSS into HTML context with nothing encoded	⬜ Not Pwned	
Apprentice	🧩 DOM XSS in document.write sink using source location.search	⬜ Not Pwned	
Apprentice	🧩 DOM XSS in innerHTML sink using source location.search	⬜ Not Pwned	
Apprentice	🧩 DOM XSS in jQuery anchor href attribute sink using location.search source	⬜ Not Pwned	
Apprentice	🧩 DOM XSS in jQuery selector sink using a hashchange event	⬜ Not Pwned	
Apprentice	🧱 Reflected XSS into attribute with angle brackets HTML-encoded	⬜ Not Pwned	
Apprentice	🧱 Stored XSS into anchor href attribute with double quotes HTML-encoded	⬜ Not Pwned	
Apprentice	🧱 Reflected XSS into a JavaScript string with angle brackets HTML encoded	⬜ Not Pwned	
Practitioner	🧩 DOM XSS in document.write sink using source location.search inside a select element	⬜ Not Pwned	
Practitioner	🧩 DOM XSS in AngularJS expression with angle brackets and double quotes HTML-encoded	⬜ Not Pwned	
Practitioner	🧱 Reflected DOM XSS	⬜ Not Pwned	
Practitioner	🧱 Stored DOM XSS	⬜ Not Pwned	
Practitioner	🛑 Reflected XSS into HTML context with most tags and attributes blocked	⬜ Not Pwned	
Practitioner	🛑 Reflected XSS into HTML context with all tags blocked except custom ones	⬜ Not Pwned	
Practitioner	🖼️ Reflected XSS with some SVG markup allowed	⬜ Not Pwned	
Practitioner	🔗 Reflected XSS in canonical link tag	⬜ Not Pwned	
Practitioner	🧱 Reflected XSS into a JavaScript string with single quote and backslash escaped	⬜ Not Pwned	
Practitioner	🧱 Reflected XSS into a JavaScript string with angle brackets and double quotes HTML-encoded and single quotes escaped	⬜ Not Pwned	
Practitioner	🧱 Stored XSS into onclick event with angle brackets and double quotes HTML-encoded and single quotes and backslash escaped	⬜ Not Pwned	
Practitioner	🧱 Reflected XSS into a template literal with angle brackets, single, double quotes, backslash and backticks Unicode-escaped	⬜ Not Pwned	
Practitioner	🍪 Exploiting cross-site scripting to steal cookies	⬜ Not Pwned	
Practitioner	🔐 Exploiting cross-site scripting to capture passwords	⬜ Not Pwned	
Practitioner	🛡️ Exploiting XSS to bypass CSRF defenses	⬜ Not Pwned	
Expert	🧰 Reflected XSS with AngularJS sandbox escape without strings	⬜ Not Pwned	
Expert	🧰 Reflected XSS with AngularJS sandbox escape and CSP	⬜ Not Pwned	
Expert	🛑 Reflected XSS with event handlers and href attributes blocked	⬜ Not Pwned	
Expert	🔗 Reflected XSS in a JavaScript URL with some characters blocked	⬜ Not Pwned	
Expert	📉 Reflected XSS protected by very strict CSP, with dangling markup attack	⬜ Not Pwned	
Expert	🧨 Reflected XSS protected by CSP, with CSP bypass	⬜ Not Pwned	
3️⃣ Cross-site Request Forgery (CSRF) (12 Labs) 🔁
What? Forcing a user to perform unwanted actions on a web application where they're authenticated. Impact: Unauthorized fund transfers, account modifications, or privilege escalation.

📋 Lab List
Difficulty	Title	Status	Writeup
Apprentice	🧱 CSRF vulnerability with no defenses	⬜ Not Pwned	
Practitioner	🔁 CSRF where token validation depends on request method	⬜ Not Pwned	
Practitioner	🔁 CSRF where token validation depends on token being present	⬜ Not Pwned	
Practitioner	🔁 CSRF where token is not tied to user session	⬜ Not Pwned	
Practitioner	🔁 CSRF where token is tied to non-session cookie	⬜ Not Pwned	
Practitioner	🔁 CSRF where token is duplicated in cookie	⬜ Not Pwned	
Practitioner	🔄 SameSite Lax bypass via method override	⬜ Not Pwned	
Practitioner	🔄 SameSite Strict bypass via client-side redirect	⬜ Not Pwned	
Practitioner	🔄 SameSite Strict bypass via sibling domain	⬜ Not Pwned	
Practitioner	🔄 SameSite Lax bypass via cookie refresh	⬜ Not Pwned	
Practitioner	📡 CSRF where Referer validation depends on header being present	⬜ Not Pwned	
Practitioner	📡 CSRF with broken Referer validation	⬜ Not Pwned	
4️⃣ Clickjacking (5 Labs) 👁️
What? Tricking a user into clicking something different than intended. Impact: Can be used to steal credentials, enable XSS, or perform actions unknowingly.

📋 Lab List
Difficulty	Title	Status	Writeup
Apprentice	👁️ Basic clickjacking with CSRF token protection	⬜ Not Pwned	
Apprentice	🖼️ Clickjacking with form input data prefilled from a URL parameter	⬜ Not Pwned	
Apprentice	🛡️ Clickjacking with a frame buster script	⬜ Not Pwned	
Practitioner	💥 Exploiting clickjacking vulnerability to trigger DOM-based XSS	⬜ Not Pwned	
Practitioner	🔄 Multistep clickjacking	⬜ Not Pwned	
5️⃣ DOM-based vulnerabilities (7 Labs) 🧩
What? Client-side bugs that can be exploited without server-side changes. Impact: XSS, redirections, cookie manipulation, and more.

📋 Lab List
Difficulty	Title	Status	Writeup
Practitioner	🧩 DOM XSS using web messages	⬜ Not Pwned	
Practitioner	🧩 DOM XSS using web messages and a JavaScript URL	⬜ Not Pwned	
Practitioner	🧩 DOM XSS using web messages and JSON.parse	⬜ Not Pwned	
Practitioner	🧲 DOM-based open redirection	⬜ Not Pwned	
Practitioner	🍪 DOM-based cookie manipulation	⬜ Not Pwned	
Expert	🧠 Exploiting DOM clobbering to enable XSS	⬜ Not Pwned	
Expert	🧠 Clobbering DOM attributes to bypass HTML filters	⬜ Not Pwned	
6️⃣ Cross-origin Resource Sharing (CORS) (3 Labs) 🌍
What? Misconfigured CORS policies can allow unauthorized access to sensitive APIs. Impact: Data leakage, session hijacking, and API abuse.

📋 Lab List
Difficulty	Title	Status	Writeup
Apprentice	🌍 CORS vulnerability with basic origin reflection	⬜ Not Pwned	
Apprentice	🌍 CORS vulnerability with trusted null origin	⬜ Not Pwned	
Practitioner	🌍 CORS vulnerability with trusted insecure protocols	⬜ Not Pwned	
7️⃣ XML External Entity (XXE) Injection (9 Labs) 🧬
What? Exploiting poorly configured XML processors to read files or interact with internal systems.
Impact: File disclosure, SSRF, and system enumeration.

📋 Lab List
Difficulty	Title	Status	Writeup
Apprentice	📁 Exploiting XXE using external entities to retrieve files	⬜ Not Pwned	
Apprentice	🔄 Exploiting XXE to perform SSRF attacks	⬜ Not Pwned	
Practitioner	🌐 Blind XXE with out-of-band interaction	⬜ Not Pwned	
Practitioner	🌐 Blind XXE with out-of-band interaction via XML parameter entities	⬜ Not Pwned	
Practitioner	📦 Exploiting blind XXE to exfiltrate data using a malicious external DTD	⬜ Not Pwned	
Practitioner	📢 Exploiting blind XXE to retrieve data via error messages	⬜ Not Pwned	
Practitioner	📁 Exploiting XInclude to retrieve files	⬜ Not Pwned	
Practitioner	📁 Exploiting XXE via image file upload	⬜ Not Pwned	
Expert	📦 Exploiting XXE to retrieve data by repurposing a local DTD	⬜ Not Pwned	
8️⃣ Server-side Request Forgery (SSRF) (7 Labs) 🔄
What? Inducing the server to make requests to arbitrary systems.
Impact: Internal network scanning, service interaction, and data leakage.

📋 Lab List
Difficulty	Title	Status	Writeup
Apprentice	🌐 Basic SSRF against the local server	⬜ Not Pwned	
Apprentice	🌐 Basic SSRF against another back-end system	⬜ Not Pwned	
Practitioner	🌐 Blind SSRF with out-of-band detection	⬜ Not Pwned	
Practitioner	🛑 SSRF with blacklist-based input filter	⬜ Not Pwned	
Practitioner	🔁 SSRF with filter bypass via open redirection vulnerability	⬜ Not Pwned	
Expert	🐚 Blind SSRF with Shellshock exploitation	⬜ Not Pwned	
Expert	🟢 SSRF with whitelist-based input filter	⬜ Not Pwned	
9️⃣ HTTP Request Smuggling (21 Labs) 🚚
What? Exploiting discrepancies between how HTTP requests are parsed by front-end and back-end servers.
Impact: Bypassing security controls, cache poisoning, XSS, and session fixation.

📋 Lab List
Difficulty	Title	Status	Writeup
Practitioner	🧪 HTTP request smuggling, confirming a CL.TE vulnerability via differential responses	⬜ Not Pwned	
Practitioner	🧪 HTTP request smuggling, confirming a TE.CL vulnerability via differential responses	⬜ Not Pwned	
Practitioner	🔁 Exploiting HTTP request smuggling to bypass front-end security controls, CL.TE vulnerability	⬜ Not Pwned	
Practitioner	🔁 Exploiting HTTP request smuggling to bypass front-end security controls, TE.CL vulnerability	⬜ Not Pwned	
Practitioner	🧪 Exploiting HTTP request smuggling to reveal front-end request rewriting	⬜ Not Pwned	
Practitioner	🧪 Exploiting HTTP request smuggling to capture other users' requests	⬜ Not Pwned	
Practitioner	💬 Exploiting HTTP request smuggling to deliver reflected XSS	⬜ Not Pwned	
Practitioner	🧪 Response queue poisoning via H2.TE request smuggling	⬜ Not Pwned	
Practitioner	🧪 H2.CL request smuggling	⬜ Not Pwned	
Practitioner	🧪 HTTP/2 request smuggling via CRLF injection	⬜ Not Pwned	
Practitioner	🧪 HTTP/2 request splitting via CRLF injection	⬜ Not Pwned	
Practitioner	🧪 CL.0 request smuggling	⬜ Not Pwned	
Practitioner	🧪 HTTP request smuggling, basic CL.TE vulnerability	⬜ Not Pwned	
Practitioner	🧪 HTTP request smuggling, basic TE.CL vulnerability	⬜ Not Pwned	
Practitioner	🧪 HTTP request smuggling, obfuscating the TE header	⬜ Not Pwned	
Expert	🧪 Exploiting HTTP request smuggling to perform web cache poisoning	⬜ Not Pwned	
Expert	🧪 Exploiting HTTP request smuggling to perform web cache deception	⬜ Not Pwned	
Expert	🔁 Bypassing access controls via HTTP/2 request tunnelling	⬜ Not Pwned	
Expert	🧪 Web cache poisoning via HTTP/2 request tunnelling	⬜ Not Pwned	
Expert	🧪 Client-side desync	⬜ Not Pwned	
Expert	🧪 Server-side pause-based request smuggling	⬜ Not Pwned	
🔟 OS Command Injection (5 Labs) 💥
What? Injecting arbitrary operating system commands via vulnerable web inputs.
Impact: Full remote code execution on the server — potentially leading to full system compromise.

📋 Lab List
Difficulty	Title	Status	Writeup
Apprentice	💣 OS command injection, simple case	⬜ Not Pwned	
Practitioner	⏳ Blind OS command injection with time delays	⬜ Not Pwned	
Practitioner	📤 Blind OS command injection with output redirection	⬜ Not Pwned	
Practitioner	🌐 Blind OS command injection with out-of-band interaction	⬜ Not Pwned	
Practitioner	📦 Blind OS command injection with out-of-band data exfiltration	⬜ Not Pwned	
1️⃣1️⃣ Server-side Template Injection (7 Labs) 🧠
What? Exploiting template engines that allow user input to be parsed as code.
Impact: Can lead to remote code execution or sensitive data leakage depending on the template engine.

📋 Lab List
Difficulty	Title	Status	Writeup
Practitioner	🧪 Basic server-side template injection	⬜ Not Pwned	
Practitioner	🧪 Server-side template injection (code context)	⬜ Not Pwned	
Practitioner	📚 Server-side template injection using documentation	⬜ Not Pwned	
Practitioner	🛠️ Server-side template injection in an unknown language with a documented exploit	⬜ Not Pwned	
Practitioner	📡 Server-side template injection with information disclosure via user-supplied objects	⬜ Not Pwned	
Expert	🔍 Server-side template injection in a sandboxed environment	⬜ Not Pwned	
Expert	🧩 Server-side template injection with a custom exploit	⬜ Not Pwned	
1️⃣2️⃣ Path Traversal (6 Labs) 📁
What? Manipulating file paths to access unauthorized files or directories.
Impact: Allows attackers to read or execute sensitive files like /etc/passwd.

📋 Lab List
Difficulty	Title	Status	Writeup
Apprentice	📂 File path traversal, simple case	⬜ Not Pwned	
Practitioner	🚫 File path traversal, traversal sequences blocked with absolute path bypass	⬜ Not Pwned	
Practitioner	🧹 File path traversal, traversal sequences stripped non-recursively	⬜ Not Pwned	
Practitioner	🔁 File path traversal, traversal sequences stripped with superfluous URL-decode	⬜ Not Pwned	
Practitioner	🔍 File path traversal, validation of start of path	⬜ Not Pwned	
Practitioner	🧪 File path traversal, validation of file extension with null byte bypass	⬜ Not Pwned	
1️⃣3️⃣ Access Control Vulnerabilities (13 Labs) 🔐
What? Flaws in how users are authorized to access certain resources.
Impact: Unauthorized access to admin functions, user accounts, or sensitive data.

📋 Lab List
Difficulty	Title	Status	Writeup
Apprentice	🚪 Unprotected admin functionality	⬜ Not Pwned	
Apprentice	🔒 Unprotected admin functionality with unpredictable URL	⬜ Not Pwned	
Apprentice	🧑‍💼 User role controlled by request parameter	⬜ Not Pwned	
Apprentice	🧾 User role can be modified in user profile	⬜ Not Pwned	
Apprentice	🆔 User ID controlled by request parameter	⬜ Not Pwned	
Apprentice	🔒 User ID controlled by request parameter, with unpredictable user IDs	⬜ Not Pwned	
Apprentice	📤 User ID controlled by request parameter with data leakage in redirect	⬜ Not Pwned	
Apprentice	📤 User ID controlled by request parameter with password disclosure	⬜ Not Pwned	
Apprentice	🔗 Insecure direct object references	⬜ Not Pwned	
Practitioner	🔄 URL-based access control can be circumvented	⬜ Not Pwned	
Practitioner	🧱 Method-based access control can be circumvented	⬜ Not Pwned	
Practitioner	🔄 Multi-step process with no access control on one step	⬜ Not Pwned	
Practitioner	📡 Referer-based access control	⬜ Not Pwned	
1️⃣4️⃣ Authentication (14 Labs) 🔐
What? Mechanisms used to verify user identity. Flaws can allow attackers to bypass or brute-force authentication.
Impact: Account takeover, privilege escalation, and unauthorized access.

📋 Lab List
Difficulty	Title	Status	Writeup
Apprentice	👤 Username enumeration via different responses	⬜ Not Pwned	
Apprentice	🔐 2FA simple bypass	⬜ Not Pwned	
Apprentice	🔄 Password reset broken logic	⬜ Not Pwned	
Practitioner	👀 Username enumeration via subtly different responses	⬜ Not Pwned	
Practitioner	🕒 Username enumeration via response timing	⬜ Not Pwned	
Practitioner	🛑 Broken brute-force protection, IP block	⬜ Not Pwned	
Practitioner	🔒 Username enumeration via account lock	⬜ Not Pwned	
Practitioner	🎯 2FA broken logic	⬜ Not Pwned	
Practitioner	🔁 Brute-forcing a stay-logged-in cookie	⬜ Not Pwned	
Practitioner	🍪 Offline password cracking	⬜ Not Pwned	
Practitioner	🌐 Password reset poisoning via middleware	⬜ Not Pwned	
Practitioner	🔐 Password brute-force via password change	⬜ Not Pwned	
Expert	🚫 Broken brute-force protection, multiple credentials per request	⬜ Not Pwned	
Expert	🔁 2FA bypass using a brute-force attack	⬜ Not Pwned	
1️⃣5️⃣ WebSockets (3 Labs) 🪟
What? Bidirectional communication channels between client and server. Vulnerabilities often stem from insecure implementations.
Impact: Session hijacking, cross-site WebSocket hijacking, or message manipulation.

📋 Lab List
Difficulty	Title	Status	Writeup
Apprentice	📡 Manipulating WebSocket messages to exploit vulnerabilities	⬜ Not Pwned	
Practitioner	🔄 Cross-site WebSocket hijacking	⬜ Not Pwned	
Practitioner	🧪 Manipulating the WebSocket handshake to exploit vulnerabilities	⬜ Not Pwned	
1️⃣6️⃣ Web Cache Poisoning (13 Labs) 🧫
What? Exploiting caching mechanisms to serve malicious content to users.
Impact: Delivering XSS payloads, phishing pages, or malware through trusted caches.

📋 Lab List
Difficulty	Title	Status	Writeup
Practitioner	🧴 Web cache poisoning with an unkeyed header	⬜ Not Pwned	
Practitioner	🍪 Web cache poisoning with an unkeyed cookie	⬜ Not Pwned	
Practitioner	🧪 Web cache poisoning with multiple headers	⬜ Not Pwned	
Practitioner	📦 Targeted web cache poisoning using an unknown header	⬜ Not Pwned	
Practitioner	🔗 Web cache poisoning via an unkeyed query string	⬜ Not Pwned	
Practitioner	📂 Web cache poisoning via an unkeyed query parameter	⬜ Not Pwned	
Practitioner	🧱 Parameter cloaking	⬜ Not Pwned	
Practitioner	📦 Web cache poisoning via a fat GET request	⬜ Not Pwned	
Practitioner	🧭 URL normalization	⬜ Not Pwned	
Expert	🧲 Web cache poisoning to exploit a DOM vulnerability via a cache with strict cacheability criteria	⬜ Not Pwned	
Expert	🔗 Combining web cache poisoning vulnerabilities	⬜ Not Pwned	
Expert	🧨 Cache key injection	⬜ Not Pwned	
Expert	🧊 Internal cache poisoning	⬜ Not Pwned	
1️⃣7️⃣ Insecure Deserialization (10 Labs) 📦
What? Exploiting unsafe deserialization of untrusted data, leading to RCE or session tampering.
Impact: Remote code execution, privilege escalation, or object manipulation.

📋 Lab List
Difficulty	Title	Status	Writeup
Apprentice	🧱 Modifying serialized objects	⬜ Not Pwned	
Practitioner	🧩 Modifying serialized data types	⬜ Not Pwned	
Practitioner	🔁 Using application functionality to exploit insecure deserialization	⬜ Not Pwned	
Practitioner	🐘 Arbitrary object injection in PHP	⬜ Not Pwned	
Practitioner	🧰 Exploiting Java deserialization with Apache Commons	⬜ Not Pwned	
Practitioner	📦 Exploiting PHP deserialization with a pre-built gadget chain	⬜ Not Pwned	
Practitioner	🐍 Exploiting Ruby deserialization using a documented gadget chain	⬜ Not Pwned	
Expert	🧠 Developing a custom gadget chain for Java deserialization	⬜ Not Pwned	
Expert	🧠 Developing a custom gadget chain for PHP deserialization	⬜ Not Pwned	
Expert	📦 Using PHAR deserialization to deploy a custom gadget chain	⬜ Not Pwned	
1️⃣8️⃣ Information Disclosure (5 Labs) 📦
What? Accidental exposure of sensitive information like error messages, debug pages, or source code.
Impact: Can expose internal logic, credentials, or vulnerabilities to attackers.

📋 Lab List
Difficulty	Title	Status	Writeup
Apprentice	🔍 Information disclosure in error messages	⬜ Not Pwned	
Apprentice	🛠️ Information disclosure on debug page	⬜ Not Pwned	
Apprentice	📁 Source code disclosure via backup files	⬜ Not Pwned	
Apprentice	🔐 Authentication bypass via information disclosure	⬜ Not Pwned	
Practitioner	📚 Information disclosure in version control history	⬜ Not Pwned	
1️⃣9️⃣ Business Logic Vulnerabilities (11 Labs) 🎯
What? Logical flaws in how the application enforces business rules. Often overlooked by traditional scanners.
Impact: Financial fraud, privilege escalation, unauthorized access.

📋 Lab List
Difficulty	Title	Status	Writeup
Apprentice	🤖 Excessive trust in client-side controls	⬜ Not Pwned	
Apprentice	🧱 High-level logic vulnerability	⬜ Not Pwned	
Apprentice	🔀 Inconsistent security controls	⬜ Not Pwned	
Apprentice	🧨 Flawed enforcement of business rules	⬜ Not Pwned	
Practitioner	🧩 Low-level logic flaw	⬜ Not Pwned	
Practitioner	🔄 Inconsistent handling of exceptional input	⬜ Not Pwned	
Practitioner	🌐 Weak isolation on dual-use endpoint	⬜ Not Pwned	
Practitioner	🧭 Insufficient workflow validation	⬜ Not Pwned	
Practitioner	🔑 Authentication bypass via flawed state machine	⬜ Not Pwned	
Practitioner	💰 Infinite money logic flaw	⬜ Not Pwned	
Expert	🚫 Bypassing access controls using email address parsing discrepancies	⬜ Not Pwned	
2️⃣0️⃣ HTTP Host Header Attacks (7 Labs) 📡
What? Exploiting misconfigured server behavior based on the Host header.
Impact: Password reset poisoning, SSRF, cache poisoning, or backend interaction.

📋 Lab List
Difficulty	Title	Status	Writeup
Apprentice	🔒 Basic password reset poisoning	⬜ Not Pwned	
Apprentice	🧲 Host header authentication bypass	⬜ Not Pwned	
Practitioner	🧫 Web cache poisoning via ambiguous requests	⬜ Not Pwned	
Practitioner	🌐 Routing-based SSRF	⬜ Not Pwned	
Practitioner	🧪 SSRF via flawed request parsing	⬜ Not Pwned	
Practitioner	🔄 Host validation bypass via connection state attack	⬜ Not Pwned	
Expert	🧨 Password reset poisoning via dangling markup	⬜ Not Pwned	
2️⃣1️⃣ OAuth Authentication (6 Labs) 🔁
What? Misconfigurations in OAuth implementations that can allow token theft or account takeover.
Impact: Unauthorized access to user accounts or services.

📋 Lab List
Difficulty	Title	Status	Writeup
Apprentice	🔐 Authentication bypass via OAuth implicit flow	⬜ Not Pwned	
Practitioner	🌐 SSRF via OpenID dynamic client registration	⬜ Not Pwned	
Practitioner	🔗 Forced OAuth profile linking	⬜ Not Pwned	
Practitioner	🔁 OAuth account hijacking via redirect_uri	⬜ Not Pwned	
Practitioner	📦 Stealing OAuth access tokens via an open redirect	⬜ Not Pwned	
Expert	🕵️ Stealing OAuth access tokens via a proxy page	⬜ Not Pwned	
2️⃣2️⃣ File Upload Vulnerabilities (7 Labs) 📁
What? Exploiting insecure file upload functionality to execute malicious files or gain remote code execution.
Impact: Full server compromise, data exfiltration, or persistent backdoor access.

📋 Lab List
Difficulty	Title	Status	Writeup
Apprentice	🧨 Remote code execution via web shell upload	⬜ Not Pwned	
Apprentice	🔐 Web shell upload via Content-Type restriction bypass	⬜ Not Pwned	
Practitioner	🛤️ Web shell upload via path traversal	⬜ Not Pwned	
Practitioner	🧯 Web shell upload via extension blacklist bypass	⬜ Not Pwned	
Practitioner	🧪 Web shell upload via obfuscated file extension	⬜ Not Pwned	
Practitioner	💥 Remote code execution via polyglot web shell upload	⬜ Not Pwned	
Expert	🏃‍♂️ Web shell upload via race condition	⬜ Not Pwned	
2️⃣3️⃣ JWT Attacks (8 Labs) 🔐
What? Exploiting weaknesses in JSON Web Token (JWT) implementations.
Impact: Session hijacking, privilege escalation, or unauthorized access to protected endpoints.

📋 Lab List
Difficulty	Title	Status	Writeup
Apprentice	🧱 JWT authentication bypass via unverified signature	⬜ Not Pwned	
Apprentice	🛡️ JWT authentication bypass via flawed signature verification	⬜ Not Pwned	
Practitioner	🔑 JWT authentication bypass via weak signing key	⬜ Not Pwned	
Practitioner	🧩 JWT authentication bypass via jwk header injection	⬜ Not Pwned	
Practitioner	🔗 JWT authentication bypass via jku header injection	⬜ Not Pwned	
Practitioner	📂 JWT authentication bypass via kid header path traversal	⬜ Not Pwned	
Expert	🔄 JWT authentication bypass via algorithm confusion	⬜ Not Pwned	
Expert	🔒 JWT authentication bypass via algorithm confusion with no exposed key	⬜ Not Pwned	
2️⃣4️⃣ Essential Skills (2 Labs) 🧠
What? Core techniques used during real-world assessments to discover vulnerabilities faster.
Impact: Improves efficiency and effectiveness of bug hunting.

📋 Lab List
Difficulty	Title	Status	Writeup
Practitioner	🔍 Discovering vulnerabilities quickly with targeted scanning	⬜ Not Pwned	
Practitioner	🧹 Scanning non-standard data structures	⬜ Not Pwned	
2️⃣5️⃣ Prototype Pollution (10 Labs) 🧬
What? Exploiting JavaScript object prototype manipulation to affect application logic.
Impact: Can lead to XSS, privilege escalation, or RCE depending on implementation.

📋 Lab List
Difficulty	Title	Status	Writeup
Practitioner	🌐 Client-side prototype pollution via browser APIs	⬜ Not Pwned	
Practitioner	💬 DOM XSS via client-side prototype pollution	⬜ Not Pwned	
Practitioner	🔄 DOM XSS via an alternative prototype pollution vector	⬜ Not Pwned	
Practitioner	🧼 Client-side prototype pollution via flawed sanitization	⬜ Not Pwned	
Practitioner	🧱 Client-side prototype pollution in third-party libraries	⬜ Not Pwned	
Practitioner	👑 Privilege escalation via server-side prototype pollution	⬜ Not Pwned	
Practitioner	🔍 Detecting server-side prototype pollution without polluted property reflection	⬜ Not Pwned	
Practitioner	🧯 Bypassing flawed input filters for server-side prototype pollution	⬜ Not Pwned	
Practitioner	💥 Remote code execution via server-side prototype pollution	⬜ Not Pwned	
Expert	📦 Exfiltrating sensitive data via server-side prototype pollution	⬜ Not Pwned	
2️⃣6️⃣ GraphQL API Vulnerabilities (5 Labs) 📊
What? Misconfigurations or logical flaws in GraphQL APIs that allow data leakage or abuse.
Impact: Unauthorized access to private data, account takeover, or SSRF.

📋 Lab List
Difficulty	Title	Status	Writeup
Apprentice	🧾 Accessing private GraphQL posts	⬜ Not Pwned	
Practitioner	🔐 Accidental exposure of private GraphQL fields	⬜ Not Pwned	
Practitioner	🔍 Finding a hidden GraphQL endpoint	⬜ Not Pwned	
Practitioner	🕵️ Bypassing GraphQL brute force protections	⬜ Not Pwned	
Practitioner	🔁 Performing CSRF exploits over GraphQL	⬜ Not Pwned	
2️⃣7️⃣ Race Conditions (6 Labs) ⏳
What? Exploiting timing flaws in how a system handles concurrent requests.
Impact: Bypassing rate limits, gaining unauthorized access, or manipulating transactions.

📋 Lab List
Difficulty	Title	Status	Writeup
Apprentice	🧱 Limit overrun race conditions	⬜ Not Pwned	
Practitioner	🔄 Bypassing rate limits via race conditions	⬜ Not Pwned	
Practitioner	🔄 Multi-endpoint race conditions	⬜ Not Pwned	
Practitioner	🕐 Single-endpoint race conditions	⬜ Not Pwned	
Practitioner	🧪 Exploiting time-sensitive vulnerabilities	⬜ Not Pwned	
Expert	🧩 Partial construction race conditions	⬜ Not Pwned	
2️⃣8️⃣ NoSQL Injection (4 Labs) 🚀
What? Injecting malicious queries into NoSQL databases like MongoDB to bypass authentication or extract data.
Impact: Can lead to full database compromise and privilege escalation.

📋 Lab List
Difficulty	Title	Status	Writeup
Apprentice	🔍 Detecting NoSQL injection	⬜ Not Pwned	
Apprentice	🔐 Exploiting NoSQL operator injection to bypass authentication	⬜ Not Pwned	
Practitioner	📁 Exploiting NoSQL injection to extract data	⬜ Not Pwned	
Practitioner	🧲 Exploiting NoSQL operator injection to extract unknown fields	⬜ Not Pwned	
2️⃣9️⃣ API Testing (5 Labs) 🔎
What? Identifying and exploiting misconfigurations or vulnerabilities in RESTful APIs.
Impact: Data leakage, account takeover, or privilege escalation.

📋 Lab List
Difficulty	Title	Status	Writeup
Apprentice	📚 Exploiting an API endpoint using documentation	⬜ Not Pwned	
Practitioner	📥 Exploiting server-side parameter pollution in a query string	⬜ Not Pwned	
Practitioner	🔍 Finding and exploiting an unused API endpoint	⬜ Not Pwned	
Practitioner	🧨 Exploiting a mass assignment vulnerability	⬜ Not Pwned	
Expert	📡 Exploiting server-side parameter pollution in a REST URL	⬜ Not Pwned	
3️⃣0️⃣ Web LLM Attacks (4 Labs) 🤖
What? Exploiting Large Language Model (LLM) integrations in web apps for prompt manipulation or data exfiltration.
Impact: Prompt injections, data leaks, or unintended behavior from AI models.

📋 Lab List
Difficulty	Title	Status	Writeup
Apprentice	🤖 Exploiting LLM APIs with excessive agency	⬜ Not Pwned	
Practitioner	🧠 Exploiting vulnerabilities in LLM APIs	⬜ Not Pwned	
Practitioner	🧠 Indirect prompt injection	⬜ Not Pwned	
Expert	🧠 Exploiting insecure output handling in LLMs	⬜ Not Pwned	
3️⃣1️⃣ Web Cache Deception (5 Labs) 🧪
What? Tricking caching systems into storing sensitive user data like session tokens or private content.
Impact: Stealing sensitive data from cache servers accessible to attackers.

📋 Lab List
Difficulty	Title	Status	Writeup
Apprentice	🛰️ Exploiting path mapping for web cache deception	⬜ Not Pwned	
Practitioner	🔗 Exploiting path delimiters for web cache deception	⬜ Not Pwned	
Practitioner	🧹 Exploiting origin server normalization for web cache deception	⬜ Not Pwned	
Practitioner	🧼 Exploiting cache server normalization for web cache deception	⬜ Not Pwned	
Expert	🎯 Exploiting exact-match cache rules for web cache deception	⬜ Not Pwned	
