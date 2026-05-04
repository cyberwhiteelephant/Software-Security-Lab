# 🛡️ Software Security Lab — Semester 6
### B.Tech in Computer Science Engineering (Cybersecurity)

---

![Software Security](https://img.shields.io/badge/Domain-Software%20Security-red?style=for-the-badge&logo=shield)
![Semester](https://img.shields.io/badge/Semester-6th-orange?style=for-the-badge)
![Experiments](https://img.shields.io/badge/Experiments-10-green?style=for-the-badge)
![Stack](https://img.shields.io/badge/Stack-Python%20%7C%20C%20%7C%20Web-blue?style=for-the-badge&logo=python)

---

## 📋 Overview

This repository contains the lab outputs, source code, reports, and documentation for the **Software Security** course undertaken in **Semester 6** of B.Tech CSE (Cybersecurity). The experiments span the core pillars of application security — from vulnerability identification and input-based attack simulation to threat modeling, secure authentication, and incident response — grounded in both theory and practical implementation.

> **Course:** Software Security Lab
> **Program:** B.Tech CSE — Cybersecurity Specialization
> **Semester:** 6th Semester

---

## 📁 Repository Structure

```
software-security-lab/
│
├── Experiment-01_Code-Vulnerability-Analysis/
│   ├── vulnerable_samples/
│   ├── analysis_report.md
│   └── screenshots/
│
├── Experiment-02_Input-Attack-Simulation/
│   ├── sqli_demo/
│   ├── xss_demo/
│   ├── mitigations/
│   └── report.md
│
├── Experiment-03_Cryptographic-Hashing/
│   ├── hashing_scripts/
│   ├── salted_password_demo/
│   └── report.md
│
├── Experiment-04_Secure-Code-Review/
│   ├── vulnerable_login_module/
│   ├── reviewed_login_module/
│   └── review_report.md
│
├── Experiment-05_Network-Traffic-Analysis/
│   ├── pcap_captures/
│   ├── screenshots/
│   └── report.md
│
├── Experiment-06_Threat-Modeling/
│   ├── stride_diagram/
│   ├── threat_model_report.md
│   └── screenshots/
│
├── Experiment-07_Secure-Authentication/
│   ├── login_app/
│   ├── screenshots/
│   └── report.md
│
├── Experiment-08_Vulnerability-Scanning/
│   ├── scan_results/
│   ├── screenshots/
│   └── report.md
│
├── Experiment-09_Browser-Artifact-Analysis/
│   ├── artifact_dumps/
│   ├── screenshots/
│   └── report.md
│
├── Experiment-10_Incident-Response-Simulation/
│   ├── sample_logs/
│   ├── incident_report.md
│   └── screenshots/
│
└── README.md
```

---

## 🧪 List of Experiments

---

### Experiment 1 — Static Code Analysis for Security Flaws

**Tools:** Flake8 · Bandit (Python) · Cppcheck (C) · Manual Code Review

**Objective:**
Analyze C and Python code snippets to identify common security vulnerabilities through static analysis and manual code walkthroughs.

**Key Concepts:**
- Buffer overflow vulnerabilities in C (`strcpy`, `gets`, unsafe memory operations)
- Insecure input handling — missing bounds checks and unvalidated user input
- Hard-coded credentials and secrets embedded in source code
- Use of deprecated or unsafe standard library functions
- CWE (Common Weakness Enumeration) classification of identified flaws

**Vulnerabilities Identified:**
- `CWE-121` — Stack-based Buffer Overflow
- `CWE-798` — Use of Hard-coded Credentials
- `CWE-20` — Improper Input Validation

**Outcome:**
Identified and documented multiple security flaws in provided C and Python code samples using both automated static analyzers and manual review, with recommendations for secure coding alternatives.

---

### Experiment 2 — Input-Based Attack Simulation & Mitigation

**Tools:** DVWA (Damn Vulnerable Web App) · Burp Suite · Browser DevTools

**Objective:**
Simulate SQL injection and Cross-Site Scripting (XSS) attacks on a vulnerable test web application and implement input validation and sanitization as countermeasures.

**Key Concepts:**
- SQL Injection — error-based, blind boolean-based, and time-based techniques
- Reflected and Stored XSS — payload injection and DOM manipulation
- Input validation vs. input sanitization — understanding the difference
- Parameterized queries / prepared statements as SQLi defense
- Content Security Policy (CSP) and output encoding for XSS defense
- OWASP Top 10 context — A03 (Injection) and A07 (XSS)

**Payloads Tested:**
```sql
' OR 1=1 --
' UNION SELECT username, password FROM users --
```
```javascript
<script>alert('XSS')</script>
<img src=x onerror=alert(document.cookie)>
```

**Outcome:**
Demonstrated successful exploitation of SQLi and XSS vulnerabilities on DVWA, then applied input validation and parameterized queries to neutralize the attack vectors and confirmed mitigation effectiveness.

---

### Experiment 3 — Cryptographic Hashing & Secure Password Storage

**Tools:** Python (`hashlib`, `bcrypt`, `secrets`) · OpenSSL

**Objective:**
Experiment with hashing algorithms and demonstrate secure password storage using hashing combined with salting techniques.

**Key Concepts:**
- MD5 and SHA-256 hash generation and their cryptographic properties
- Why MD5 is broken for security purposes (collision attacks, rainbow tables)
- Salt generation — preventing rainbow table and dictionary attacks
- `bcrypt` and `PBKDF2` for adaptive password hashing
- Key stretching and iteration count tuning
- Difference between encryption and hashing in the context of password storage

**Code Snippet (Python):**
```python
import hashlib, secrets

password = "SecureP@ss123"
salt = secrets.token_hex(16)
hashed = hashlib.sha256((salt + password).encode()).hexdigest()
print(f"Salt: {salt}\nHash: {hashed}")
```

**Outcome:**
Implemented and compared MD5, SHA-256, and bcrypt hashing with salting in Python, demonstrating why bcrypt/PBKDF2 are the correct choices for production password storage.

---

### Experiment 4 — Secure Code Review of a Login System

**Tools:** Manual Review · VS Code · OWASP Secure Coding Practices Checklist

**Objective:**
Conduct a structured secure code review of a basic login module to identify insecure coding practices and propose hardened alternatives.

**Key Concepts:**
- Plain-text password storage identification and remediation
- Missing input validation — SQL injection and XSS entry points
- Improper session management — insecure cookies, missing `HttpOnly`/`Secure` flags
- Error message verbosity leaking system information
- Principle of least privilege in authentication logic
- OWASP Code Review Guide methodology

**Issues Found & Fixed:**

| Issue | Severity | Fix Applied |
|---|---|---|
| Plain-text password storage | Critical | Replaced with bcrypt hashing |
| No input sanitization | High | Added parameterized queries |
| Verbose error messages | Medium | Replaced with generic messages |
| Missing session expiry | Medium | Added session timeout logic |
| No rate limiting on login | Medium | Documented recommendation |

**Outcome:**
Identified and documented critical security flaws in a vulnerable login module, then produced a hardened version of the code with detailed annotations explaining each fix.

---

### Experiment 5 — Network Traffic Capture & HTTP Analysis

**Tools:** Wireshark · tcpdump · Firefox (HTTP test site)

**Objective:**
Capture live network traffic to observe plaintext HTTP login transmissions, analyze packet headers, and understand the risks of unencrypted credential transmission.

**Key Concepts:**
- OSI Layer 7 (Application) packet analysis
- HTTP vs. HTTPS — why plaintext HTTP is dangerous
- Credential extraction from captured HTTP POST packets
- TCP handshake and session tracking in packet captures
- Identifying sensitive headers: `Authorization`, `Cookie`, `Set-Cookie`
- Practical demonstration of why HTTPS and HSTS are mandatory

**Filters Used (Wireshark):**
```
http.request.method == "POST"
http contains "password"
tcp.stream eq 0
```

**Outcome:**
Successfully captured HTTP login traffic and extracted plaintext credentials directly from packet data, demonstrating in a controlled lab environment why all web applications must enforce HTTPS.

---

### Experiment 6 — Threat Modeling for a Web Application (STRIDE)

**Tools:** draw.io / Microsoft Threat Modeling Tool · STRIDE Framework

**Objective:**
Identify possible threats and attack surfaces for a sample web application (e.g., an online bookstore) using the structured STRIDE threat modeling methodology.

**Key Concepts:**
- STRIDE categories: **S**poofing, **T**ampering, **R**epudiation, **I**nformation Disclosure, **D**enial of Service, **E**levation of Privilege
- Data Flow Diagram (DFD) construction — identifying trust boundaries, data stores, processes, and external entities
- Attack surface mapping and risk prioritization
- Mapping STRIDE threats to MITRE ATT&CK techniques
- Threat mitigation strategies per STRIDE category

**STRIDE Analysis Summary (Online Bookstore):**

| Threat Type | Example Threat | Mitigation |
|---|---|---|
| Spoofing | Attacker impersonates a user | MFA, strong session tokens |
| Tampering | Modifying order price in transit | HTTPS, input validation |
| Repudiation | User denies placing an order | Audit logging, digital receipts |
| Info Disclosure | Leaking user payment data | Encryption at rest and in transit |
| Denial of Service | Flooding checkout endpoint | Rate limiting, WAF |
| Elevation of Privilege | User accessing admin panel | RBAC, authorization checks |

**Outcome:**
Produced a complete threat model with DFD diagrams, STRIDE threat classification table, and risk-prioritized mitigation recommendations for the sample application.

---

### Experiment 7 — Secure Authentication Implementation with Password Hashing

**Tools:** Python (Flask / vanilla) · `bcrypt` · HTML/CSS

**Objective:**
Develop a functional login form with secure backend password hashing and verification to demonstrate how authentication should be correctly implemented.

**Key Concepts:**
- Secure registration flow — hashing before storage using `bcrypt`
- Login verification — comparing input against stored hash (never decrypting)
- Session token generation and management
- Preventing timing attacks in password comparison (`bcrypt.checkpw`)
- Defense-in-depth: combining hashing, sessions, and input validation

**Implementation Highlights:**
```python
import bcrypt

# Registration
hashed_pw = bcrypt.hashpw(password.encode(), bcrypt.gensalt())

# Login verification
is_valid = bcrypt.checkpw(input_password.encode(), hashed_pw)
```

**Outcome:**
Built a working secure login system demonstrating end-to-end hashed password authentication, with documented comparison against a vulnerable plain-text implementation to highlight the security delta.

---

### Experiment 8 — Web Application Vulnerability Scanning

**Tools:** OWASP ZAP (Passive Scan Mode) · Nikto · Target: DVWA / Local App

**Objective:**
Use automated vulnerability scanning tools to identify common security issues — outdated software, default credentials, misconfigurations — in a web application environment.

**Key Concepts:**
- Difference between passive and active scanning
- OWASP ZAP spider and passive scan workflow
- Identifying missing security headers: `X-Frame-Options`, `Content-Security-Policy`, `Strict-Transport-Security`
- Default credential detection and directory enumeration
- CVE correlation with detected software versions
- Risk scoring and vulnerability prioritization

**Scan Findings (Sample):**

| Finding | Risk Level | Description |
|---|---|---|
| Missing CSP Header | Medium | No Content-Security-Policy defined |
| X-Frame-Options Absent | Medium | Clickjacking risk |
| Cookie Without HttpOnly | Low | Session cookie accessible via JS |
| Outdated jQuery Version | Medium | Known XSS vulnerabilities |

**Outcome:**
Performed passive vulnerability scans on a target web application, documented all findings with risk levels, and provided remediation recommendations for each identified security misconfiguration.

---

### Experiment 9 — Browser Artifact Inspection & Privacy Analysis

**Tools:** Browser Developer Tools · Nirsoft BrowsingHistoryView · SQLite Browser

**Objective:**
Explore browser-stored artifacts — history, cookies, and saved data — to understand user tracking mechanisms and associated privacy risks.

**Key Concepts:**
- Browser artifact storage locations (SQLite databases, JSON files)
- Cookie anatomy: name, value, domain, expiry, `HttpOnly`, `Secure`, `SameSite` flags
- Session vs. persistent cookies — security implications
- Third-party tracking cookies and fingerprinting techniques
- `localStorage` and `sessionStorage` as data exposure vectors
- GDPR and privacy implications of browser data retention

**Artifacts Examined:**

| Artifact | Location | Risk |
|---|---|---|
| Browsing History | `places.sqlite` (Firefox) | Activity reconstruction |
| Session Cookies | DevTools → Application | Session hijacking |
| Saved Passwords | Browser password manager | Credential exposure |
| Cache | Browser cache directory | Content disclosure |

**Outcome:**
Extracted and analyzed browser artifacts from a local browser instance, documenting the types of sensitive data stored and the privacy/security risks they represent to end users.

---

### Experiment 10 — Incident Response Simulation from Log Analysis

**Tools:** Text Editor / Excel · Linux CLI (`grep`, `awk`, `sort`) · Sample Log Files

**Objective:**
Analyze provided access logs and system event data to identify suspicious activities, reconstruct the attack sequence, and produce a structured incident response report.

**Key Concepts:**
- Web server access log format (Apache/Nginx Combined Log Format)
- Identifying brute force login attempts through failed authentication patterns
- Detecting directory traversal and SQLi attempts in URL logs
- IP-based anomaly detection — high request volume from single source
- Incident timeline construction — identifying T0 (first indicator) to containment
- Incident report structure: Executive Summary, Timeline, IOCs, Recommendations

**Log Analysis Commands:**
```bash
# Find failed login attempts
grep "POST /login" access.log | grep " 401 "

# Count requests per IP (detect brute force)
awk '{print $1}' access.log | sort | uniq -c | sort -rn | head -20

# Detect directory traversal attempts
grep "\.\." access.log
```

**Indicators of Compromise (IOCs) Identified:**
- Repeated `401 Unauthorized` responses from a single IP
- Sequential directory enumeration attempts
- Unusual access patterns at off-hours timestamps
- SQLi strings present in URL parameters within logs

**Outcome:**
Reconstructed a simulated security incident from raw log data, identified all attacker actions from initial reconnaissance to attempted exploitation, and produced a formal incident report with timeline, IOCs, and recommended containment actions.

---

## 🛠️ Tools & Technologies Summary

| Category | Tools Used |
|---|---|
| **Static Analysis** | Bandit, Cppcheck, Flake8, Manual Review |
| **Attack Simulation** | DVWA, Burp Suite, Browser DevTools |
| **Cryptography** | Python `hashlib`, `bcrypt`, `secrets`, OpenSSL |
| **Code Review** | VS Code, OWASP Secure Coding Checklist |
| **Network Analysis** | Wireshark, tcpdump |
| **Threat Modeling** | STRIDE, draw.io, MS Threat Modeling Tool |
| **Secure Dev** | Python, Flask, bcrypt |
| **Vulnerability Scanning** | OWASP ZAP, Nikto |
| **Browser Forensics** | Nirsoft Tools, SQLite Browser, DevTools |
| **Incident Response** | Linux CLI, Excel, Log Analysis |

---

## 🔐 Security Concepts Covered

| Concept | Experiments |
|---|---|
| Input Validation & Sanitization | Exp 1, 2, 4 |
| Cryptography & Hashing | Exp 3, 7 |
| Secure Authentication | Exp 4, 7 |
| Network Security | Exp 5 |
| Threat Modeling | Exp 6 |
| Vulnerability Assessment | Exp 8 |
| Privacy & Data Exposure | Exp 9 |
| Incident Response (IR) | Exp 10 |

---

## 💻 Environment

| Component | Details |
|---|---|
| **OS** | Kali Linux / Ubuntu / Windows 10 |
| **Languages** | Python 3.x, C, HTML/CSS |
| **Virtualization** | VMware Workstation / VirtualBox |
| **Web Platform** | DVWA, localhost (Apache/Flask) |

---

## 📌 Key Takeaways

- Gained practical experience in **identifying, exploiting, and mitigating** real-world software vulnerabilities.
- Understood the **OWASP Top 10** from an attacker's and defender's perspective.
- Implemented **secure-by-design** principles including input validation, password hashing, and least privilege.
- Applied **STRIDE threat modeling** to systematically identify attack surfaces before development.
- Developed foundational skills in **log analysis and incident response** essential for SOC and DFIR roles.

---

## 👤 Author

**Aneesh Sangran**
B.Tech CSE (Cybersecurity) — 6th Semester

[![GitHub](https://img.shields.io/badge/GitHub-aneeshsangran84-black?style=flat-square&logo=github)](https://github.com/aneeshsangran84)
[![YouTube](https://img.shields.io/badge/YouTube-CWE%20%7C%20Cyber%20White%20Elephant-red?style=flat-square&logo=youtube)](https://youtube.com/@CyberWhiteElephant)

---

> ⚠️ **Disclaimer:** All experiments were conducted in isolated, controlled lab environments using intentionally vulnerable applications (DVWA, local test servers) or provided sample data. No real systems were targeted. This repository is intended strictly for educational purposes under academic supervision.
