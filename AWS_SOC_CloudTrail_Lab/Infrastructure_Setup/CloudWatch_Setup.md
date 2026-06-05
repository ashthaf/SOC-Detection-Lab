# 📊 CloudWatch Logs & Detection Setup

![AWS](https://img.shields.io/badge/AWS-CloudWatch-orange?style=for-the-badge)
![Cloud](https://img.shields.io/badge/Cloud-AWS-blue?style=for-the-badge)
![SIEM](https://img.shields.io/badge/SIEM-Splunk-green?style=for-the-badge)
![Logs](https://img.shields.io/badge/Logs-CloudWatch-purple?style=for-the-badge)
![Detection](https://img.shields.io/badge/Detection-RealTime-red?style=for-the-badge)
![Type](https://img.shields.io/badge/Type-Infrastructure_Setup-darkblue?style=for-the-badge)
![Project](https://img.shields.io/badge/Project-SOC_Lab-brightgreen?style=for-the-badge)

## 🎯 Objective
Integrate CloudTrail with CloudWatch Logs for real-time monitoring and alerting.

---

## 🧠 Why CloudWatch?

CloudWatch enables:
- Real-time log monitoring
- Metric-based detection
- Alert generation

---

## ⚙️ Step 1: Enable CloudTrail → CloudWatch Logs

1. Go to AWS Console → CloudTrail
2. Select your Trail
3. Click **Edit**
4. Enable:
   - ☑ Send to CloudWatch Logs
5. Create / Select Log Group:
   - `/aws/cloudtrail/logs`

---

## ⚙️ Step 2: Create Metric Filter

1. Go to CloudWatch → Log Groups
2. Select your CloudTrail log group
3. Click **Create Metric Filter**

### Example Filter (IAM User Creation)
```bash
{ $.eventName = "CreateUser" }
