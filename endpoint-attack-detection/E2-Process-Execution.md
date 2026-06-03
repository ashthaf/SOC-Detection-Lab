# ⚡ E2 — PowerShell Execution Detection (Event ID 4688)

![Attack](https://img.shields.io/badge/Attack-PowerShell%20Execution-blue)
![Event ID](https://img.shields.io/badge/Event%20ID-4688-blueviolet)
![Severity](https://img.shields.io/badge/Severity-High-critical)
![MITRE](https://img.shields.io/badge/MITRE-T1059.001-orange)
![Status](https://img.shields.io/badge/Status-Detected-success)


---

## 🎯 Objective

Detect suspicious PowerShell execution.

---

## 🛠️ Attack Simulation

Executed PowerShell on the endpoint.

### 📸 Attack Evidence

![attack](../assets/powershell....png)

---

## 🔍 Detection Query

```spl
index="*" EventCode=4688 New_Process_Name="*powershell*"
| table _time ComputerName Account_Name New_Process_Name Process_Command_Line
```

---

## 🚨 Alert

* Trigger: Any PowerShell execution

---

![attack](../assets/e2-01.png)

![attack](../assets/e2-02.png)

![attack](../assets/e2-03.png)




## 🧠 MITRE ATT&CK Mapping

| Field     | Value                                         |
| --------- | --------------------------------------------- |
| Tactic    | Execution                                     |
| Technique | Command and Scripting Interpreter: PowerShell |
| ID        | T1059.001                                     |

---

## ✅ Result

PowerShell execution detected successfully.
