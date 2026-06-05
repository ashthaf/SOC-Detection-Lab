# 📥 SQS Queue Configuration

## 🎯 Objective

To configure Amazon SQS (Simple Queue Service) to receive notifications from SNS and act as a buffer for log ingestion into Splunk.

---

## 🧠 Why SQS?

SQS is used to:

- Store messages from SNS temporarily
- Ensure reliable log delivery
- Prevent data loss during ingestion
- Allow Splunk to pull logs at its own pace

---

## 🏗️ Architecture Role

```
S3 → SNS → SQS → Splunk
```

SQS acts as the **buffer + queue system**

---

## ⚙️ Configuration Steps

### Step 1: Create SQS Queue

1. Go to AWS Console → SQS
2. Click **Create Queue**

- Type:
  - ✅ Standard Queue
- Name:
  ```
  soc-alert-queue
  ```

---

### Step 2: Configure Queue Settings

- Visibility Timeout:
  - Default (OK for lab)
- Message Retention:
  - 4 days (default)

---

### Step 3: Allow SNS to Send Messages (IMPORTANT)

1. Go to:
   ```
   Queue → Permissions → Access Policy
   ```

2. Add this policy:

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "Allow-SNS-SendMessage",
      "Effect": "Allow",
      "Principal": "*",
      "Action": "sqs:SendMessage",
      "Resource": "YOUR_SQS_ARN",
      "Condition": {
        "ArnEquals": {
          "aws:SourceArn": "YOUR_SNS_ARN"
        }
      }
    }
  ]
}
```

⚠️ Replace:
- `YOUR_SQS_ARN`
- `YOUR_SNS_ARN`

---

### Step 4: Subscribe SQS to SNS

1. Go to SNS → Topics
2. Open:
   ```
   soc-alerts-topic
   ```
3. Click **Create Subscription**

- Protocol:
  - Amazon SQS
- Endpoint:
  - Select your queue:
    ```
    soc-alert-queue
    ```

---

## 📸 Screenshots

![SQS Setup](../../assets/sqs-setup.png)

---

## 🔍 What Happens Here?

When CloudTrail logs are created:

➡️ S3 triggers SNS  
➡️ SNS sends message  
➡️ SQS stores message  
➡️ Splunk pulls logs from SQS  

---

## 🚨 SOC Insight

SQS ensures:

- No log loss
- Reliable ingestion
- Scalability for large environments

---

## 🔐 Security Best Practices

- Restrict access to trusted SNS topics
- Avoid public access to queue
- Monitor queue metrics

---

## ✅ Validation

1. Perform an AWS action (e.g., create IAM user)
2. Go to:
   ```
   SQS → Queue → Send and Receive Messages
   ```
3. Click:
   ```
   Poll for messages
   ```

You should see messages arriving.

---

## 🔗 Next Step

➡️ `Splunk_Integration.md`
