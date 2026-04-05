# 🚨 SQL Injection Detection Report

---

## 📌 Overview

SQL Injection (SQLi) is a web application attack where an attacker manipulates backend database queries by injecting malicious SQL statements into input fields. This can lead to authentication bypass, data leakage, or full database compromise.

---

## 🎯 Objective

The objective of this lab was to:

* Simulate SQL Injection attacks on a vulnerable web application (DVWA)
* Capture attack traces in web server logs
* Detect malicious activity using Splunk SPL queries
* Generate alerts for real-time monitoring

---

## 🧪 Lab Environment

| Component      | Details                                |
| -------------- | -------------------------------------- |
| Target App     | DVWA (Damn Vulnerable Web Application) |
| Web Server     | Apache2                                |
| Log Source     | /var/log/apache2/access.log            |
| SIEM Tool      | Splunk Enterprise                      |
| Log Forwarding | Splunk Universal Forwarder             |

---

## ⚔️ Attack Simulation

### 🔹 Attack Method

SQL Injection was performed through the DVWA login/input fields.

### 🔹 Payload Used

```
' OR '1'='1
```

### 🔹 Attack Explanation

* The payload manipulates the SQL query logic
* `'1'='1'` always evaluates to TRUE
* This bypasses authentication and grants unauthorized access

---

## 📸 Evidence (Screenshots)

* DVWA SQL Injection exploitation
  ![sql](../../assets/sqli-spl-2-clean.png)
* Splunk logs showing injected payload
  ![sql-1](../../assets/sqli-spl-2-clean.png)
* Alert trigger in Splunk
  ![tri](../../assets/sqlinjection-triggered-clean.png)


---

## 📊 Log Analysis

### 🔍 Observed Behavior

* Suspicious HTTP GET requests
* SQL keywords present in query parameters
* Repeated attempts from same IP

### 🔍 Example Log Pattern

```
GET /DVWA/vulnerabilities/sqli/?id=' OR '1'='1 HTTP/1.1
```

### 🔍 Indicators of Compromise (IOCs)

* Presence of SQL keywords:

  * `OR 1=1`
  * `UNION SELECT`
  * `'--`
* Abnormal query parameters

---

## 🔍 SPL Query (Detection)

```spl
index=webserver ("' OR '1'='1" OR "UNION" OR "SELECT" OR "1=1" OR "'--")
```

### ✅ Detection Logic

* Searches for common SQL injection payload patterns
* Matches malicious query strings in web logs

---

## 🚨 Alert Configuration

| Setting           | Value                   |
| ----------------- | ----------------------- |
| Alert Type        | Scheduled               |
| Cron Schedule     | */5 * * * *             |
| Time Range        | Last 15 minutes         |
| Trigger Condition | Number of results > 0   |
| Trigger Action    | Add to Triggered Alerts |

---

## 🧠 MITRE ATT&CK Mapping

| Tactic         | Technique ID | Technique Name                    |
| -------------- | ------------ | --------------------------------- |
| Initial Access | T1190        | Exploit Public-Facing Application |

### 🔍 Explanation

* SQL Injection exploits vulnerabilities in public-facing applications
* Allows attackers to gain unauthorized access to backend systems

---

## ⚠️ Severity

**High**

### Reason:

* Can lead to full database compromise
* Enables authentication bypass
* Often used as an initial entry point

---

## 🛡️ Mitigation Strategies

* Use parameterized queries / prepared statements
* Implement input validation and sanitization
* Deploy Web Application Firewall (WAF)
* Restrict database permissions
* Enable logging and monitoring

---

## ✅ Conclusion

The SQL Injection attack was successfully simulated and detected using Splunk.
The SPL query effectively identified malicious payloads in web logs, and alerts were configured to notify analysts in near real-time.

This demonstrates how SIEM can be used to detect and respond to web-based attacks in a SOC environment.

---

