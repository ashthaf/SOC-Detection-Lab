# 🚨 Access Key Creation Detection

![Detection](https://img.shields.io/badge/Detection-Credential%20Creation-green)
![LogSource](https://img.shields.io/badge/Logs-CloudTrail-blue)
![Severity](https://img.shields.io/badge/Severity-High-red)

## 🎯 Objective

Detect creation of new AWS access keys which may indicate unauthorized credential generation.

---

## 🧠 Detection Logic

When an access key is created, CloudTrail logs:

```
eventName=CreateAccessKey
```

This can indicate:

* Legitimate admin activity
* OR attacker establishing programmatic access

---

## 🔍 Basic Splunk Query

```spl
index=aws_index eventName=CreateAccessKey
```

---

## 📊 Improved Detection Query

```spl
index=aws_index eventName=CreateAccessKey
| table _time userIdentity.userName requestParameters.userName sourceIPAddress
```

---

## 🔥 SOC-Level Detection

```spl
index=aws_index eventName=CreateAccessKey
| stats count by userIdentity.userName sourceIPAddress
| sort - count
```

---

## 📌 Field Explanation

| Field                      | Meaning             |
| -------------------------- | ------------------- |
| userIdentity.userName      | Who created the key |
| requestParameters.userName | Target user         |
| sourceIPAddress            | Source IP           |
| _time                      | Event timestamp     |

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

![Access Key Detection](../../assets/accesskey-detection.png)

---

## 🔎 SOC Analysis

Investigate:

* Who created the access key?
* Was it expected activity?
* Is the IP trusted?

---

## 🚨 Response Actions

* Disable the access key immediately
* Rotate all credentials
* Investigate associated activity
* Check for further compromise

---

## 🧠 MITRE ATT&CK Mapping

| Tactic            | Technique         | ID    |
| ----------------- | ----------------- | ----- |
| Credential Access | Cloud Credentials | T1528 |

---

## 🔗 Related Attack

➡️ `../Attack_Scenarios/Access_Key_Creation.md`
