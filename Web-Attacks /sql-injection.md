🔴 SQL Injection Attack Detection
📌 Attack Overview

SQL Injection (SQLi) is a web application vulnerability that allows an attacker to manipulate backend database queries by injecting malicious SQL statements into input fields.

This can lead to:

Authentication bypass
Data leakage
Database manipulation
⚔️ Attack Execution

The attack was performed on the login functionality of DVWA (Damn Vulnerable Web Application).

🔹 Payload Used:
' OR '1'='1
🔹 Explanation:
' → closes the original query
OR '1'='1' → always evaluates to TRUE
This bypasses authentication and logs in without valid credentials
🧪 Vulnerable Query (Conceptual)
SELECT * FROM users WHERE username='admin' AND password='' OR '1'='1';

👉 Since '1'='1' is always TRUE, access is granted.

📜 Logs Generated

The web server logs captured suspicious input patterns such as:

SQL keywords (OR, UNION)
Special characters (', ")
Encoded payloads (%27)

These indicators are commonly associated with SQL Injection attempts.

🔍 SPL Query
index=webserver ("' OR" OR "1=1" OR "UNION" OR "%27")
🧠 SPL Breakdown
index=webserver → searches web server logs
" ' OR " → detects authentication bypass patterns
"1=1" → identifies always-true conditions
"UNION" → detects data extraction attempts
"%27" → detects encoded single quote
🚨 Alert Triggered

An alert was configured in Splunk with the following conditions:

Trigger when SQL keywords are detected in requests
Real-time monitoring enabled
🔴 Severity: Critical
🧬 MITRE ATT&CK Mapping
Technique: Exploit Public-Facing Application
ID: T1190
🧠 Detection Logic

SQL Injection attempts can be identified by:

Presence of SQL operators (OR, AND)
Logical conditions (1=1)
Special characters (', ")
Encoded payloads

These patterns indicate manipulation of backend queries.

📸 Evidence






🛡️ Mitigation (Blue Team Insight)
Use prepared statements / parameterized queries
Implement input validation & sanitization
Deploy Web Application Firewall (WAF)
Monitor logs for abnormal query patterns
🎯 Key Takeaway

SQL Injection is one of the most critical web vulnerabilities.
Effective detection requires identifying both raw and encoded payload patterns in web logs and converting them into actionable alerts
