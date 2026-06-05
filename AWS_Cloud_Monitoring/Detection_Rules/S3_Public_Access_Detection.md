# 🚨 S3 Public Access Detection

## 🎯 Objective

Detect when an S3 bucket is modified to allow public access, potentially exposing sensitive data.

---

## 🧠 Detection Logic

When an S3 bucket is made public, CloudTrail logs events such as:

```
eventName=PutBucketPolicy
eventName=PutBucketPublicAccessBlock
```

These indicate changes in bucket access configuration.

---

## 🔍 Basic Splunk Query

```spl
index=aws_index eventName=PutBucketPolicy
```

---

## 📊 Improved Detection Query

```spl
index=aws_index eventName=PutBucketPolicy
| table _time userIdentity.userName requestParameters.bucketName sourceIPAddress
```

---

## 🔥 SOC-Level Detection (IMPORTANT)

Detect public access policy:

```spl
index=aws_index eventName=PutBucketPolicy
| search "Principal"
| table _time userIdentity.userName requestParameters.bucketName sourceIPAddress
```

---

## 🔥 Detect Public Access Block Disabled

```spl
index=aws_index eventName=PutBucketPublicAccessBlock
| search "false"
| table _time userIdentity.userName requestParameters.bucketName sourceIPAddress
```

---

## 📌 Field Explanation

| Field                        | Meaning        |
| ---------------------------- | -------------- |
| requestParameters.bucketName | Target bucket  |
| userIdentity.userName        | Who modified   |
| sourceIPAddress              | Source IP      |
| eventName                    | Type of change |

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

![S3 Detection](../../assets/s3-detection.png)

---

## 🔎 SOC Analysis

Investigate:

* Which bucket was modified?
* Was public access intentional?
* Who made the change?
* Is the data sensitive?

---

## 🚨 Response Actions

* Re-enable block public access immediately
* Remove public bucket policy
* Audit access logs
* Investigate potential data exposure

---

## 🧠 MITRE ATT&CK Mapping

| Tactic       | Technique                     | ID    |
| ------------ | ----------------------------- | ----- |
| Exfiltration | Exfiltration Over Web Service | T1567 |

---

## 🔗 Related Attack

➡️ `../Attack_Scenarios/S3_Public_Access.md`
