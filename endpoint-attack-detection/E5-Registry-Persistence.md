# 🧬 E5 — Registry Persistence Detection (Event ID 4657)

![Banner](https://img.shields.io/badge/Attack-Registry%20Persistence-green)

---

## 🎯 Objective

Simulate persistence by modifying Windows Registry Run key and detect it using Splunk.

---

# ⚙️ Step 1 — Enable Registry Auditing (GPO)

Navigate to:

```id="nav1"
gpedit.msc
```

Path:

```id="nav2"
Computer Configuration  
→ Windows Settings  
→ Security Settings  
→ Advanced Audit Policy Configuration  
→ System Audit Policies  
→ Object Access  
```

Enable:

* ✅ Audit Registry → Success
* ✅ Audit Registry → Failure

### 📸 Screenshot — Audit Registry Enabled

![gpo](./images/e5-1.png)

---

# ⚙️ Step 2 — Enable Auditing on Registry Key

Open Registry Editor:

```id="nav3"
regedit
```

Go to:

```id="nav4"
HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion\Run
```

### Steps:

1. Right-click → **Permissions**
2. Click → **Advanced**
3. Go to → **Auditing tab**
4. Click → **Add**

Set:

* Principal → `Everyone`
* Type → `Success`
* Applies to → `This key and subkeys`

Check:

* ✅ Set Value
* ✅ Create Subkey

### 📸 Screenshot — Registry Auditing Entry

![audit](./images/e5-2.png)

---

# 💀 Step 3 — Execute Persistence Attack

Run in CMD:

```cmd id="attackcmd"
reg add "HKLM\Software\Microsoft\Windows\CurrentVersion\Run" /v EvilPersistence /t REG_SZ /d "cmd.exe"
```

This creates a malicious startup entry.

### 📸 Screenshot — Attack Execution

![attack](./images/e5-3.png)

---

# 🔍 Step 4 — Detection in Splunk

## SPL Query

```spl id="detectspl"
index="*" EventCode=4657
```

### 📸 Screenshot — Detection Result

![detect](./images/e5-4.png)

---

# 🚨 Step 5 — Create Alert

## Alert SPL

```spl id="alertspl"
index="*" EventCode=4657
| table _time Object_Name Object_Value_Name
```

### Alert Config:

* Trigger: Any match
* Schedule: Every 5 minutes

### 📸 Screenshot — Alert Creation

![alert](./images/e5-5.png)

---

# 📊 Step 6 — Triggered Alerts

### 📸 Screenshot — Alerts Dashboard

![alerts](./images/e5-6.png)

---

# 🧠 MITRE ATT&CK Mapping

| Field     | Value                             |
| --------- | --------------------------------- |
| Tactic    | Persistence                       |
| Technique | Boot or Logon Autostart Execution |
| ID        | T1547.001                         |

---

# 🧠 Detection Logic

Registry Run keys are commonly used by attackers to maintain persistence.
Any modification to this key is highly suspicious.

---

# ⚠️ Possible False Positives

* Legitimate software adding startup entries
* System updates

---

# ✅ Result

* Registry modification detected via Event ID 4657
* Alert triggered successfully
* Persistence attack successfully identified

---
