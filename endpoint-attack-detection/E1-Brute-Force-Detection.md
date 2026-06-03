# E1 — Brute Force Login Simulation

## 🎯 Objective
Simulate a brute force login attack on a Windows endpoint EC2 instance and detect it in Splunk.

---

## 🛠️ Attack Simulation

Manually entered incorrect passwords multiple times on the Windows endpoint EC2 instance to generate failed login attempts.

This triggers **Windows Security Event ID 4625** — An account failed to log on.

---

## 📋 MITRE ATT&CK Mapping

| Field | Value |
|-------|-------|
| Tactic | Credential Access |
| Technique | Brute Force |
| ID | T1110 |

---

## 🔍 Splunk Detection Query

```spl
index="*" EventCode=4625
| stats count by Account_Name src_ip
| where count > 5
```

---

## 🚨 Alert Configuration

| Field | Value |
|-------|-------|
| Alert Name | Brute Force Login Detected |
| Trigger Condition | count > 5 failed attempts |
| Schedule | Every 5 minutes |
| Severity | High |

---

## ✅ Result

Alert successfully created and triggered in Splunk on detecting multiple failed login attempts from the endpoint. ✅
