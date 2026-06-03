# 🚨 E1 — Brute Force Detection (Event ID 4625)

![Attack](https://img.shields.io/badge/Attack-Brute%20Force-red)
![Event ID](https://img.shields.io/badge/Event%20ID-4625-blue)
![Severity](https://img.shields.io/badge/Severity-High-critical)
![MITRE](https://img.shields.io/badge/MITRE-T1110-orange)
![Status](https://img.shields.io/badge/Status-Detected-success)


---

## 🎯 Objective

Simulate brute force login attempts and detect them using Splunk.

---

## 🛠️ Attack Simulation

Multiple incorrect password attempts were entered on the Windows login screen.

### 📸 Attack Evidence

![attack](../assets/e1-01.png)

---

## 🔍 Detection Query

```spl
index="*" EventCode=4625
| stats count by Account_Name src_ip
| where count > 5
```

### 📸 Detection

![logs](../assets/e1-02.png)
![logs](../assets/assets/e1-03.png)

---

## 🚨 Alert

* Trigger: More than 5 attempts
* Schedule: Every 5 minutes

![alert](../assets/e1-04.png)
![alert](../assets/e1-05.png)

---

## 🧠 MITRE ATT&CK Mapping

| Field     | Value             |
| --------- | ----------------- |
| Tactic    | Credential Access |
| Technique | Brute Force       |
| ID        | T1110             |

---

## ✅ Result

Brute force attack successfully detected and alert triggered.
