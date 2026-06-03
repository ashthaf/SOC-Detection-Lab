# 🧹 E4 — Log Clearing Detection (Event ID 1102)

![Attack](https://img.shields.io/badge/Attack-Log%20Clearing-black)
![Event ID](https://img.shields.io/badge/Event%20ID-1102-blue)
![Severity](https://img.shields.io/badge/Severity-Critical-red)
![MITRE](https://img.shields.io/badge/MITRE-T1070.001-orange)
![Status](https://img.shields.io/badge/Status-Detected-success)


---

## 🎯 Objective

Detect log clearing activity.

---

## 🛠️ Attack Simulation

```cmd
wevtutil cl security
```

### 📸 Attack Evidence

![attack](../assets/e4-01.png)

---

## 🔍 Detection Query

```spl
index="*" EventCode=1102
```

---

## 🚨 Alert Query

```spl
index="*" EventCode=1102
| table _time ComputerName
```

![attack](../assets/e4-02.png)

![attack](../assets/e4-03png)

![attack](../assets/e4-04.png)

---

## 🧠 MITRE ATT&CK Mapping

| Field     | Value                     |
| --------- | ------------------------- |
| Tactic    | Defense Evasion           |
| Technique | Indicator Removal on Host |
| ID        | T1070.001                 |

---

## ✅ Result

Log clearing attack detected successfully.
