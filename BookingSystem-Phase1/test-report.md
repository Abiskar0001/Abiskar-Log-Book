# 1️⃣ Introduction

**Testers**  
- Name:  Abiskar Sapkota, Raman Moktan

**Purpose:**  
- Identify security vulnerabilities in the registration and authentication flows of the Booking System web application.

**Scope:**  
- Tested components: Registration page (/register), root (/), static files served from /static/*   
- Exclusions: Admin endpoints, API endpoints beyond registration
- Test approach: Black-box (local Docker environment)

**Test environment & dates:**  
- Start:  2025-12-19
- End:  2025-12-19
- Test environment details (OS, runtime, DB, browsers): Docker local environment, Browser: Firefox, Server: localhost:8000, Tool: OWASP ZAP

**Assumptions & constraints:**  
- Testing performed only on the local Docker instance.

---

# 2️⃣ Executive Summary

**Short summary (1-2 sentences):**  
Automated ZAP scan identified two high-risk vulnerabilities (SQL Injection, Path Traversal), several medium-risk issues (missing CSRF tokens, CSP missing, format string error), and low-risk misconfigurations (missing security headers). Immediate remediation is recommended before deployment.

**Overall risk level:** High

**Top 5 immediate actions:**  
1.  Fix SQL Injection vulnerability in /register.
2.  Fix Path Traversal vulnerability in username input handling.
3.  Implement Anti-CSRF tokens in forms.
4.  Add security headers: CSP, X-Frame-Options, X-Content-Type-Options.
5.  Implement custom error pages to prevent application error disclosure.

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
| F-01 | 🔴 High | SQL Injection in registration | Input field username allows injection, returning HTTP 500 | ZAP evidence: POST /register with ' triggers error |
| F-02 | 🔴 High | Path Traversal in registration | username input could allow access outside web root  | ZAP evidence: POST /register parameter username |
| F-03 | 🟠 Medium | Absence of Anti-CSRF Tokens | Registration form lacks CSRF protection | <form action="/register" method="POST"> |
| F-04 | 🟠 Medium |Missing CSP Header | No Content-Security-Policy header on / and /register | ZAP alert |
| F-05 | 🟡 Low | X-Content-Type-Options Missing |  Header nosniff missing on multiple endpoints | ZAP alert |

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
  
