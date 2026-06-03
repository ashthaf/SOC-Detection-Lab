# 🛡️ Endpoint Attack Detection Lab
![SOC Lab](https://img.shields.io/badge/SOC-Lab-blue)
![SIEM](https://img.shields.io/badge/SIEM-Splunk-black)
![Cloud](https://img.shields.io/badge/Cloud-AWS-orange)
![Level](https://img.shields.io/badge/Level-Intermediate-yellow)
![Project](https://img.shields.io/badge/Project-Detection%20Engineering-green)


This project demonstrates real-world endpoint attacks detected using Splunk SIEM.

---

## ⚙️ Setup

* Windows EC2
* Splunk Enterprise
* Universal Forwarder

---

## 📌 Index Used

```spl
index="*"
```

---

## 🚨 Attacks Covered

| ID | Attack               | Event ID  |
| -- | -------------------- | --------- |
| E1 | Brute Force          | 4625      |
| E2 | PowerShell Execution | 4688      |
| E3 | Privilege Escalation | 4720,4732 |
| E4 | Log Cleared          | 1102      |
| E5 | Registry Persistence | 4657      |

---

## 📂 Labs

* [E1 - Brute Force](./E1-Brute-Force.md)
* [E2 - Process Execution](./E2-Process-Execution.md)
* [E3 - Privilege Escalation](./E3-Privilege-Escalation.md)
* [E4 - Log Cleared](./E4-Log-Cleared.md)
* [E5 - Registry Persistence](./E5-Registry-Persistence.md)

---

## 🎯 Result

All attacks detected and alerts triggered successfully.
