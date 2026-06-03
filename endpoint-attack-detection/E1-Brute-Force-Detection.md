# 🚨 E1 — Brute Force Detection

## 🛠️ Attack

Multiple wrong password attempts.

### 📸 Attack

![attack](./images/e1-1.png)

---

## 🔍 Detection

```spl
index="*" EventCode=4625
| stats count by Account_Name
| where count > 5
```

### 📸 Logs

![logs](./images/e1-2.png)

---

## 🚨 Alert

### 📸 Alert

![alert](./images/e1-3.png)

---

## ✅ Result

Brute force detected successfully.
