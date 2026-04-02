# 🛡️ Active Directory Attack Detection Lab

This section of the SOC Detection Lab focuses on simulating and detecting real-world Active Directory attacks using Splunk SIEM.

---

## 🎯 Objectives

* Simulate common Active Directory attacks
* Analyze Windows Security Event Logs
* Build detection queries in Splunk
* Map attacks to MITRE ATT&CK framework
* Create alerts for SOC monitoring
* Document attack patterns and mitigation strategies

---

## 🧱 Lab Architecture

* **Domain Controller:** Windows Server (Active Directory)
* **Log Forwarding:** Splunk Universal Forwarder
* **SIEM:** Splunk Enterprise
* **Monitoring:** Windows Event Logs (Security)

---

## ⚔️ Attacks Covered

| ID    | Attack                | Event IDs  | Description                      |
| ----- | --------------------- | ---------- | -------------------------------- |
| AD-01 | Brute Force (RDP)     | 4625       | Multiple failed login attempts   |
| AD-02 | Account Lockout       | 4740       | Account locked after brute force |
| AD-03 | Privilege Escalation  | 4728       | Added to Domain Admins           |
| AD-04 | Kerberoasting         | 4769       | Service ticket requests          |
| AD-05 | User & Group Creation | 4720, 4728 | Backdoor user + admin access     |

---

## 🔍 Detection Approach

Each attack includes:

* Attack simulation steps
* Event log analysis
* Splunk detection queries
* Alert configuration
* MITRE ATT&CK mapping
* Screenshots for validation
* Cleanup procedures

---

## 🧠 MITRE ATT&CK Coverage

| Tactic               | Techniques                                 |
| -------------------- | ------------------------------------------ |
| Credential Access    | T1110 (Brute Force), T1558 (Kerberoasting) |
| Persistence          | T1136 (Create Account)                     |
| Privilege Escalation | T1098 (Account Manipulation)               |

---

## 📊 Key Learnings

* Correlation of Windows Event Logs in SIEM
* Identifying brute force and lateral movement patterns
* Detecting privilege escalation in real-time
* Understanding attacker persistence techniques
* Building SOC-ready detection rules

---

## 📁 Folder Structure

```
active-directory-attacks/
│
├── AD-01-Brute_Force_RDP_EventID_4625.md
├── AD-02-Account_Lockout_EventID_4740.md
├── AD-03-Privilege_Escalation_EventID_4728.md
├── AD-04-Kerberoasting_EventID_4769.md
├── AD-05-User_Creation_EventID_4720.md
│
└── ../assets/
```

---

## 🚨 Disclaimer

This lab was performed in a controlled environment for educational purposes only.

---

## 👨‍💻 Author

**Abdull Ashthaf**
Cybersecurity Enthusiast | SOC Analyst (Aspiring)

---
