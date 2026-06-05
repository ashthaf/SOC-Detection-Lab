# 🚨 IAM User Creation Detection

![Detection](https://img.shields.io/badge/Detection-User%20Creation-green)
![LogSource](https://img.shields.io/badge/Logs-CloudTrail-blue)
![Severity](https://img.shields.io/badge/Severity-Medium-yellow)

## 🎯 Objective

Detect unauthorized creation of IAM users using AWS CloudTrail logs in Splunk.

---

## 🧠 Detection Logic

Whenever a new IAM user is created, AWS CloudTrail generates an event:

```
eventName=CreateUser
```

This event can indicate:

* Legitimate admin activity
* OR attacker persistence attempt

---

## 🔍 Splunk Query (SPL)

```spl
index=aws_index eventName=CreateUser
```

---

## 📊 Improved Detection Query

```spl
index=aws_index eventName=CreateUser
| table _time userIdentity.userName sourceIPAddress requestParameters.userName
```

---

## 📌 Field Explanation

| Field                      | Meaning              |
| -------------------------- | -------------------- |
| _time                      | Time of event        |
| userIdentity.userName      | Who created the user |
| requestParameters.userName | New user created     |
| sourceIPAddress            | Source IP            |

---

## 🚨 Alert Configuration

### Condition

* Trigger when:

```
Number of results > 0
```

### Schedule

* Every 5 minutes

### Time Range

* Last 5 minutes

### Severity

* Medium

---

## 📸 Screenshot

![Detection](../../assets/IAM3.png)

![Detection](../../assets/IAM4.png)

![Detection](../../assets/IAM5.png)

![Detection](../../assets/IAM6.png)

![Detection](../../assets/IAM7.png)

---

## 🔎 SOC Analysis

### Investigate:

* Who created the user?
* Is the IP trusted?
* Was this change authorized?

---

## 🚨 Response Actions

* Disable the IAM user
* Rotate credentials
* Investigate source IP

---

## 🧠 MITRE ATT&CK Mapping

| Tactic      | Technique      | ID    |
| ----------- | -------------- | ----- |
| Persistence | Create Account | T1136 |

---

## 🔗 Related Attack

➡️ `../Attack_Scenarios/IAM_User_Creation.md`
