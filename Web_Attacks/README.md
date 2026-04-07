# 🌐 Web Attacks Detection Lab (DVWA + Splunk)

![Status](https://img.shields.io/badge/Status-Completed-success)
![SIEM](https://img.shields.io/badge/SIEM-Splunk-blue)
![Platform](https://img.shields.io/badge/Lab-DVWA-orange)
![Focus](https://img.shields.io/badge/Focus-Detection%20Engineering-red)
![MITRE](https://img.shields.io/badge/MITRE-ATT%26CK-purple)

---

## 📌 Overview

This repository contains a **hands-on Web Application Security Detection Lab** where multiple web attacks were:

* Exploited on **DVWA (Damn Vulnerable Web Application)**
* Monitored through **Apache Web Logs**
* Detected using **Splunk SIEM**
* Converted into **real-world SOC detection rules**

---

## 🎯 Objectives

* Perform real-world web attacks in a controlled lab
* Analyze web server logs for malicious activity
* Create **Splunk SPL detection queries**
* Build **alerting rules for SOC monitoring**
* Map attacks to **MITRE ATT&CK framework**

---

## 🧪 Lab Architecture

```
Attacker (Browser / Kali)
        │
        ▼
DVWA Web Server (Apache Logs)
        │
        ▼
Splunk SIEM (Detection + Alerts)
```

---

## ⚔️ Attacks Covered

| Attack Type | Description | Detection |
|-------------|------------|----------|
| [SQL Injection](./SQL_Injection.md) | Authentication bypass & DB extraction | ✅ |
| [Command Injection](./Command_Injection.md) | OS command execution | ✅ |
| [File Inclusion (LFI)](./File_Inclusion.md) | Access local system files | ✅ |
| [Cross-Site Scripting (XSS)](./XSS.md) | Client-side script injection | ✅ |
| [Brute Force](./Brute_Force.md) | Multiple login attempts | ✅ |

---

## 🔍 Detection Engineering

Each attack includes:

* 🔹 Real attack payloads
* 🔹 Web log analysis
* 🔹 Splunk SPL queries
* 🔹 Alert creation steps
* 🔹 Triggered alert evidence

---

## 🚨 Example Detection (SQL Injection)

```spl
index=webserver ("' OR" OR "1=1" OR "%27+OR")
```

---

## 🧠 MITRE ATT&CK Coverage

| Technique                         | ID    |
| --------------------------------- | ----- |
| Exploit Public-Facing Application | T1190 |
| Command and Scripting Interpreter | T1059 |
| Brute Force                       | T1110 |
| Input Capture                     | T1056 |

---


## 🛡️ Skills Demonstrated

* Web Application Security Testing
* SIEM Log Analysis (Splunk)
* Detection Engineering
* Alert Development
* MITRE ATT&CK Mapping

---

## 📚 Tools Used

* DVWA
* Splunk Enterprise
* Apache Web Server
* Burp Suite
* Kali Linux

---

## 📌 Conclusion

This project demonstrates the ability to **simulate real-world attacks and build detection mechanisms**, making it highly relevant for **SOC Analyst and Detection Engineer roles**.

---

## ⭐ If you found this useful

Give this repo a ⭐ and feel free to connect!

---
