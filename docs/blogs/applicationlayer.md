# **OSI Model Attacks  Layer 7 (Application Layer)**

## **1. Overview**

Layer 7 is responsible for delivering application-level services such as HTTP, HTTPS, DNS, SMTP, and API communication.
Because it interfaces directly with users and business logic, it is the most targeted layer in modern cyberattacks.



## **2. Why Layer 7 Is High-Risk**

* Direct access to sensitive data and application logic
* Complex codebases with frequent vulnerabilities
* Heavy reliance on APIs and web technologies
* High value targets such as authentication systems, payment flows, and user data

Most practical security incidents occur at this layer.



## **3. Key Layer 7 Attacks**

### **3.1 SQL Injection (SQLi)**

Occurs when user-controlled input is concatenated into SQL queries, allowing unauthorized query execution.

Example payload:
`' OR 1=1 --`

Impact:

* Unauthorized data access
* Authentication bypass
* Modification or deletion of records
* Potential remote code execution on some platforms



### **3.2 Cross-Site Scripting (XSS)**

Injection of malicious JavaScript into a trusted web page.

Impact:

* Cookie/session theft
* Unauthorized actions on behalf of the user
* Redirection to malicious sites
* Data exfiltration



### **3.3 Broken Authentication**

Weaknesses in login, session, or token mechanisms.

Examples:

* Predictable session IDs
* Missing brute-force protections
* Exposed session tokens
* Weak or misconfigured MFA

Impact: account compromise and privilege escalation.



### **3.4 API Attacks**

APIs often expose business logic and data directly, making them common attack targets.

Common failures:

* BOLA (Broken Object Level Authorization)
* Excessive data exposure
* Missing rate limits
* Parameter tampering

Impact: data leakage, account takeover, or mass enumeration.


### **3.5 Server-Side Request Forgery (SSRF)**

Forces the server to make internal or external requests on behalf of the attacker.

Impact:

* Access to internal services
* Cloud metadata exposure
* Token or credential theft
* Network pivoting



### **3.6 Remote Code Execution (RCE)**

Execution of arbitrary code on the server due to unsafe input handling, insecure file parsing, or vulnerable components.

Impact:

* Full system compromise
* Ransomware deployment
* Data destruction or exfiltration



### **3.7 Business Logic Vulnerabilities**

Flaws in the application's workflow rather than technical vulnerabilities.

Examples:

* Skipping authentication steps
* Manipulating price or quantity fields
* Unlimited OTP attempts
* Abusing admin workflows

Impact varies but can include financial fraud and privilege escalation.



## **4. Example Scenario: SQL Injection**

A login form directly inserts user input into a SQL query:

```sql
SELECT * FROM users 
WHERE username = '<input>' 
AND password = '<input>';
```

An attacker submits:
`' OR 1=1 --`

The resulting query always evaluates to true, resulting in unauthorized access.



## **5. Defensive Measures**

Effective mitigation requires a combination of secure coding and infrastructure controls:

* Parameterized queries / prepared statements
* Output encoding and strict input validation
* Strong session management
* Brute-force protection and MFA
* Least-privilege database permissions
* API gateways and rate limiting
* Web Application Firewalls (WAF)
* Continuous logging and monitoring





