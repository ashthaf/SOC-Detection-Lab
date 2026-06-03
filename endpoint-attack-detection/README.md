# 🖥️ Endpoint Attack Detection

This module covers real-world endpoint attack simulations performed on a Windows EC2 instance and detected using Splunk SIEM.

All attacks were executed manually on the endpoint, logs were forwarded to Splunk via Universal Forwarder, and SPL queries were built to detect and alert on each attack.

---

## 📌 Index Used

index=*

---

## 🔥 Attack Labs Summary

| Lab | Attack | Event ID | MITRE | Severity |
|-----|--------|----------|-------|----------|
| E1 | Brute Force Login Simulation | 4625 | T1110 | 🔴 High |
| E2 | PowerShell Process Execution | 4688 | T1059.001 | 🔴 High |
| E3 | Privilege Escalation via Admin Group | 4720, 4732 | T1098 | 🔴 Critical |
| E4 | Security Log Cleared | 1102 | T1070.001 | 🔴 Critical |
| E5 | Registry Persistence | 4657 | T1547.001 | 🔴 High |

---

## 🔗 Lab Files

- [E1 - Brute Force Detection](./E1-Brute-Force-Detection.md)
- [E2 - Process Execution Detection](./E2-Process-Execution-Detection.md)
- [E3 - Privilege Escalation Detection](./E3-Privilege-Escalation-Detection.md)
- [E4 - Log Cleared Detection](./E4-Log-Cleared-Detection.md)
- [E5 - Registry Persistence Detection](./E5-Registry-Persistence-Detection.md)
