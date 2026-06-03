# 🔐 E3 — Privilege Escalation Detection (4720, 4732)

![Banner](https://img.shields.io/badge/Attack-Privilege%20Escalation-purple)

---

## 🎯 Objective

Detect unauthorized privilege escalation.

---

## 🛠️ Attack Simulation

1. Created new user (Event ID 4720)
2. Added user to Administrators group (Event ID 4732)

### 📸 Attack Evidence

![attack](./images/e3-1.png)

---

## 🔍 Detection Query

```spl
index="*" (EventCode=4720 OR EventCode=4732)
| table _time EventCode Account_Name ComputerName
```

---

## 🚨 Alert

* Trigger: Any match

---
![attack](../assets/e3-01.png)

![attack](../assets/e3-02.png)

![attack](../assets/e3-03.png)

![attack](../assets/e3-04.png)

![attack](../assets/e3-05.png)

## 🧠 MITRE ATT&CK Mapping

| Field     | Value                |
| --------- | -------------------- |
| Tactic    | Privilege Escalation |
| Technique | Account Manipulation |
| ID        | T1098                |

---

## ✅ Result

Privilege escalation detected successfully.
