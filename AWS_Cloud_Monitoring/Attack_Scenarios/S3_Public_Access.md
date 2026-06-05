# ⚔️ S3 Bucket Public Access Attack

## 🎯 Objective

Simulate an attacker making an S3 bucket publicly accessible, exposing sensitive data.

---

## 🧠 Attack Description

An attacker modifies S3 bucket permissions to:

* Allow public access (`Principal: *`)
* Expose sensitive files to the internet
* Enable data exfiltration

This is one of the most critical cloud misconfigurations.

---

## ⚙️ Attack Steps

### Method 1: Disable Block Public Access

1. Go to AWS Console → S3
2. Select your bucket
3. Navigate to:

   ```
   Permissions → Block Public Access
   ```
4. Click:

   ```
   Edit
   ```
5. Uncheck:

   * Block all public access
6. Save changes

---

### Method 2: Add Public Bucket Policy

1. Go to:

   ```
   Permissions → Bucket Policy
   ```
2. Add:

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "PublicRead",
      "Effect": "Allow",
      "Principal": "*",
      "Action": "s3:GetObject",
      "Resource": "arn:aws:s3:::your-bucket-name/*"
    }
  ]
}
```

---

## 📸 Screenshot

![S3 Public Attack](../../assets/s3-public-attack.png)

---

## 🔍 Logs Generated (CloudTrail)

```text
eventName=PutBucketPolicy
eventName=PutBucketPublicAccessBlock
```

---

## 📊 Key Fields

| Field                        | Description      |
| ---------------------------- | ---------------- |
| eventName                    | Action performed |
| requestParameters.bucketName | Target bucket    |
| userIdentity.userName        | Who made change  |
| sourceIPAddress              | Source IP        |

---

## 🚨 Why This Is Dangerous

* Data exposure to internet
* Sensitive files leaked
* Compliance violations
* Possible data breach

---

## 🧠 MITRE ATT&CK Mapping

| Tactic       | Technique                     | ID    |
| ------------ | ----------------------------- | ----- |
| Exfiltration | Exfiltration Over Web Service | T1567 |

---

## 🔗 Next Step

➡️ Detection Rule:
`../Detection_Rules/S3_Public_Access_Detection.md`
