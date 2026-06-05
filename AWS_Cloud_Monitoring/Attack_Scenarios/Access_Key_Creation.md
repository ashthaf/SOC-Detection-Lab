# ⚔️ Access Key Creation Attack

## 🎯 Objective

Simulate an attacker generating access keys to gain programmatic access to AWS.

---

## 🧠 Attack Description

An attacker creates access keys for an IAM user to:

* Access AWS via CLI/API
* Bypass console monitoring
* Maintain persistence

---

## ⚙️ Attack Steps

1. Go to AWS Console → IAM
2. Navigate to:

   ```
   Users → Select User → Security Credentials
   ```
3. Click:

   ```
   Create Access Key
   ```
4. Select:

   * CLI / Application access

---

## 📸 Screenshot

![Access Key Attack](../../assets/accesskey-attack.png)

---

## 🔍 Logs Generated

```text
eventName=CreateAccessKey
```

---

## 🚨 Why This Is Dangerous

* Enables remote access
* Used for automation attacks
* Harder to detect than console login

---

## 🧠 MITRE ATT&CK

| Tactic            | Technique         | ID    |
| ----------------- | ----------------- | ----- |
| Credential Access | Cloud Credentials | T1528 |

---

## 🔗 Next Step

➡️ Detection Rule:
`../Detection_Rules/Access_Key_Creation_Detection.md`
