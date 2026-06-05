# 🚨 Security Group Modification Detection

## 🎯 Objective

Detect when security group rules are modified to allow public access, exposing AWS resources to the internet.

---

## 🧠 Detection Logic

When a security group is modified, CloudTrail logs events such as:

```
eventName=AuthorizeSecurityGroupIngress
eventName=ModifySecurityGroupRules
```

These events indicate changes to inbound traffic rules.

---

## 🔍 Basic Splunk Query

```spl
index=aws_index eventName=AuthorizeSecurityGroupIngress
```

---

## 📊 Improved Detection Query

```spl
index=aws_index eventName=AuthorizeSecurityGroupIngress
| table _time userIdentity.userName sourceIPAddress requestParameters.groupId
```

---

## 🔥 SOC-Level Detection (IMPORTANT)

Detect open access to the internet:

```spl
index=aws_index eventName=AuthorizeSecurityGroupIngress
| search "0.0.0.0/0"
| table _time userIdentity.userName sourceIPAddress requestParameters.groupId
```

---

## 📌 Field Explanation

| Field                     | Meaning                    |
| ------------------------- | -------------------------- |
| userIdentity.userName     | Who made the change        |
| requestParameters.groupId | Target security group      |
| sourceIPAddress           | Origin IP                  |
| ipPermissions             | Ports and IP ranges opened |

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

![SG Detection](../../assets/sg-detection.png)

---

## 🔎 SOC Analysis

Investigate:

* Which port was opened?
* Was access given to `0.0.0.0/0`?
* Is this expected change?
* Who made the modification?

---

## 🚨 Response Actions

* Remove open rule immediately
* Restrict access to trusted IPs
* Audit related activity
* Investigate potential compromise

---

## 🧠 MITRE ATT&CK Mapping

| Tactic          | Technique       | ID    |
| --------------- | --------------- | ----- |
| Defense Evasion | Modify Firewall | T1562 |

---

## 🔗 Related Attack

➡️ `../Attack_Scenarios/Security_Group_Modification.md`
