# 1️⃣ Introduction

**Testers**  
- Name:  Abiskar Sapkota, Raman Moktan

**Purpose:**  
- To identify vulnerabilities and anomalies in the user registration functionality of the booking system.

**Scope:**  
- Tested components: Registration page (client-side behavior, server response, session handling, input validation)
- Exclusions:  Login, admin features
- Test approach: Gray-box 

**Test environment & dates:**  
- Start:  2025-11-28
- End:  2025-11-28
- Test environment details :
    - OS: Windows 11
    - Runtime: Docker Desktop
    - Database: PostgreSQL (via Docker container)
    - Browser: Firefox 
    - Tools: OWASP ZAP, PostgreSQL CLI, browser dev tools


**Assumptions & constraints:**  
- Testing performed only on the local Docker instance.

---

# 2️⃣ Executive Summary

**Short summary (1-2 sentences):**  
Manual and automated testing of the registration form revealed several medium and low severity issues, including missing CSRF protection, lack of security headers, and improper error handling. No critical vulnerabilities (e.g., SQL injection) were confirmed.


**Overall risk level:** Medium

**Top 5 immediate actions:**  
1.  Implement Anti-CSRF tokens for forms.
2.  Add Content-Security-Policy header.
3.  Add X-Frame-Options / CSP frame-ancestors.
4.  Hide server error details; implement custom error pages.
5.  Add X-Content-Type-Options: nosniff

---

# 3️⃣ Severity scale & definitions

|  **Severity Level**  | **Description**                                                                                                              | **Recommended Action**           |
| -------------------- | ---------------------------------------------------------------------------------------------------------------------------- | -------------------------------- |
|      🔴 **High**     | A serious vulnerability that can lead to full system compromise or data breach (e.g., SQL Injection, Remote Code Execution). | *Immediate fix required*         |
|     🟠 **Medium**    | A significant issue that may require specific conditions or user interaction (e.g., XSS, CSRF).                              | *Fix ASAP*                       |
|      🟡 **Low**      | A minor issue or configuration weakness (e.g., server version disclosure).                                                   | *Fix soon*                       |
| 🔵 **Info** | No direct risk, but useful for system hardening (e.g., missing security headers).                                            | *Monitor and fix in maintenance* |


---

# 4️⃣ Findings


| ID | Severity | Finding | Description | Evidence / Proof |
|------|-----------|----------|--------------|------------------|
| F-01 | 🟠 Medium | Absence of Anti-CSRF Tokens | No CSRF token on registration form | ZAP evidence: `<form action="/register">` |
| F-02 | 🟠 Medium | CSP Header Missing | CSP not present on / and /register  | ZAP alert |
| F-03 | 🟠 Medium | Missing Anti-clickjacking Header | No X-Frame-Options or frame-ancestors | ZAP alert |
| F-04 | 🟡 Low | Application Error Disclosure | 500 error observed on POST /register | ZAP evidence |
| F-05 | 🟡 Low | X-Content-Type-Options Missing |  `X-Content-Type-Options` not set | ZAP alert |

---


---

# 5️⃣ OWASP ZAP Test Report (Attachment)

**Purpose:**  
- This section contains the results of the automated security scan performed using OWASP ZAP.  
The full scan results are included as a separate Markdown file.

---


### 📎 ZAP Report (Markdown)
 **[Click here to view the full ZAP report](./zap-report.md)**

 ### Notes
- The ZAP scan was run against the local testing environment (`http://localhost:8000`).
- Report includes all Medium, Low, and Informational findings.
- No manual edits were made to the ZAP output, as required.
  
