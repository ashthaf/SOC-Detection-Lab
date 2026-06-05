# 🚨 IAM Policy Modification Detection

![Detection](https://img.shields.io/badge/Detection-Privilege%20Escalation-green)
![LogSource](https://img.shields.io/badge/Logs-CloudTrail-blue)
![Severity](https://img.shields.io/badge/Severity-High-red)

## 🎯 Objective

Detect privilege escalation attempts by monitoring IAM policy changes in AWS CloudTrail logs using Splunk.

---

## 🧠 Detection Logic

When an attacker modifies IAM permissions, CloudTrail logs events such as:

```
eventName=AttachUserPolicy
eventName=PutUserPolicy
eventName=AddUserToGroup
```

These indicate that permissions are being granted or modified.

---

## 🔍 Basic Splunk Query

```spl
index=aws_index eventName=AttachUserPolicy
```

---

## 📊 Improved Detection Query

```spl
index=aws_index eventName=AttachUserPolicy
| table _time userIdentity.userName requestParameters.userName requestParameters.policyArn sourceIPAddress
```

---

## 🔥 SOC-Level Detection (IMPORTANT)

Detect admin privilege assignment:

```spl
index=aws_index eventName=AttachUserPolicy
| search requestParameters.policyArn="*AdministratorAccess*"
| table _time userIdentity.userName requestParameters.userName sourceIPAddress
```

---

## 📌 Field Explanation

| Field                      | Meaning              |
| -------------------------- | -------------------- |
| userIdentity.userName      | Who performed action |
| requestParameters.userName | Target user          |
| policyArn                  | Policy attached      |
| sourceIPAddress            | Origin of action     |

---

## 🚨 Alert Configuration

### Condition

```
Number of results > 0
```

### Schedule

* Every 5 minutes

### Time Range

* Last 5 minutes

### Severity

* 🔴 High

---

## 📸 Screenshot

![Policy Detection](../../assets/policy-detection.png)

---

## 🔎 SOC Analysis

Investigate:

* Who granted permissions?
* Was it expected admin activity?
* Was admin access given to suspicious user?

---

## 🚨 Response Actions

* Remove attached policy immediately
* Disable affected user
* Investigate activity logs
* Rotate credentials

---

## 🧠 MITRE ATT&CK Mapping

| Tactic               | Technique            | ID    |
| -------------------- | -------------------- | ----- |
| Privilege Escalation | Account Manipulation | T1098 |

---

## 🔗 Related Attack

➡️ `../Attack_Scenarios/IAM_Policy_Modification.md`
