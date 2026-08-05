#  PortSwigger Web Security Academy Lab Tracker & Vault

[![Labs Completed](https://img.shields.io/badge/Labs%20Completed-120%2B-brightgreen?style=flat-square)](https://portswigger.net/web-security/all-labs)


A structured tracking repository, documentation vault, and methodology cheat sheet for challenges across the **PortSwigger Web Security Academy**. This repository contains write-ups, proof-of-concept (PoC) automation scripts, payload references, and remediation guides.

---

## Features

- **Structured Walkthroughs:** Categorized by topic and difficulty level (*Apprentice*, *Practitioner*, *Expert*).
- **PoC Scripts:** Automated Python exploit scripts using `requests` and Burp Suite integrations.
- **Root-Cause Analyses:** Explanations of dynamic context rendering, parameter handling, and security controls.
- **Payload Cheatsheets:** Quick-reference payloads tailored for specific filtering bypasses.

---

## 🗂️ Repository Structure

```text
.
├── 📂 sql-injection/
│   ├── 📄 lab-01-retrieving-unhidden-data.md
│   ├── 📄 lab-02-subverting-login-logic.md
│   └── 📄 README.md
├── 📂 xss/
│   ├── 📂 DOM-XSS/
│   ├── 📂 Reflected-XSS/
│   └── 📂 Stored-XSS/
├── 📂 csrf/
├── 📂 ssrf/
├── 📂 authentication/
├── 📂 scripts/           # Custom Python automation scripts
└── 📄 PROGRESS.md        # Interactive checklist & status tracker
