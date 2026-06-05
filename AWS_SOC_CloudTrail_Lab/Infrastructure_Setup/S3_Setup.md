# 🪣 S3 Bucket Configuration

## 🎯 Objective

To configure an S3 bucket for storing AWS CloudTrail logs and forwarding events to the monitoring pipeline.

---

## 🧠 Why S3?

Amazon S3 is used to:

- Store CloudTrail logs securely
- Act as the central log repository
- Trigger notifications (SNS) when new logs arrive
- Enable log ingestion into Splunk

---

## 🏗️ Architecture Role

```
CloudTrail → S3 → SNS → SQS → Splunk
```

S3 acts as the **log storage + trigger point**

---

## ⚙️ Configuration Steps

### Step 1: Create S3 Bucket

1. Go to AWS Console → S3
2. Click **Create bucket**

- Bucket name:
  ```
  soc-cloudtrail-logs-bucket
  ```
- Region:
  - Same as CloudTrail

---

### Step 2: Configure Settings

- ❌ Block Public Access → KEEP ENABLED (Important)
- Versioning → ✅ Enable (Recommended)
- Encryption → ✅ Enable (AES-256)

---

### Step 3: Allow CloudTrail to Write Logs

This is automatically handled if you created the bucket via CloudTrail.

If manual:

1. Go to **Bucket → Permissions → Bucket Policy**
2. Add policy allowing CloudTrail:

```
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "AWSCloudTrailWrite",
      "Effect": "Allow",
      "Principal": {
        "Service": "cloudtrail.amazonaws.com"
      },
      "Action": "s3:PutObject",
      "Resource": "arn:aws:s3:::soc-cloudtrail-logs-bucket/AWSLogs/*"
    }
  ]
}
```

---

### Step 4: Enable Event Notifications

1. Go to:
   ```
   Properties → Event Notifications
   ```
2. Click **Create Event Notification**

- Name:
  ```
  CloudTrail-Log-Trigger
  ```
- Event types:
  - ✅ All object create events

---

⚠️ Destination (SNS) will be configured in next step

---

## 📸 Screenshots

![S3 Setup](../../assets/s3-setup.png)

---

## 🔍 What Happens Here?

Whenever a new CloudTrail log is stored:

➡️ S3 triggers SNS  
➡️ SNS sends notification  
➡️ SQS queues message  
➡️ Splunk pulls logs  

---

## 🔐 Security Best Practices

- Keep bucket private
- Enable encryption
- Enable versioning (protect against deletion)
- Monitor access logs

---

## ✅ Validation

1. Perform an AWS action (e.g., create IAM user)
2. Go to S3 bucket
3. Verify new log files appear under:

```
AWSLogs/<account-id>/CloudTrail/
```

---

## 🚨 SOC Insight

S3 is critical for:

- Log retention
- Forensic investigation
- Feeding SIEM (Splunk)

---

## 🔗 Navigation

⬅️ Previous: [CloudTrail Setup](./CloudTrail_Setup.md)

➡️ Next: [SNS Setup](./SNS_Setup.md)
