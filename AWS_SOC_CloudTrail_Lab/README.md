# ☁️ AWS Cloud Security Monitoring Lab (SOC Project)

![AWS](https://img.shields.io/badge/AWS-Cloud-orange)
![Splunk](https://img.shields.io/badge/SIEM-Splunk-green)
![CloudTrail](https://img.shields.io/badge/Logs-CloudTrail-blue)
![SOC](https://img.shields.io/badge/Type-SOC%20Lab-purple)
![Status](https://img.shields.io/badge/Project-Completed-brightgreen)

---

## 🏗️ Architecture

![Architecture](../assets/architecture.png)

---

## 📌 Overview

This project demonstrates a real-world **SOC (Security Operations Center)** pipeline built using **AWS + Splunk**.

It simulates cloud attacks and detects them using **CloudTrail logs**, enabling alerting and monitoring workflows.

---

## 📂 Project Structure

### ⚙️ Infrastructure Setup

- 🔹 [IAM Setup](./Infrastructure_Setup/IAM_Setup.md)
- 🔹 [CloudTrail Setup](./Infrastructure_Setup/CloudTrail_Setup.md)
- 🔹 [S3 Setup](./Infrastructure_Setup/S3_Setup.md)
- 🔹 [SNS Setup](./Infrastructure_Setup/SNS_Setup.md)
- 🔹 [SQS Setup](./Infrastructure_Setup/SQS_Setup.md)
- 🔹 [Splunk Integration](./Infrastructure_Setup/Splunk_Integration.md)

---

### ⚔️ Attack Scenarios → 🚨 Detection Rules

| Attack | Detection |
|------|----------|
| [IAM User Creation](../AWS_Cloud_Monitoring/Attack_Scenarios/IAM_User_Creation.md) | [Detection](../AWS_Cloud_Monitoring/Detection_Rules/IAM_User_Creation_Detection.md) |
| [Policy Modification](../AWS_Cloud_Monitoring/Attack_Scenarios/IAM_Policy_Modification.md) | [Detection](../AWS_Cloud_Monitoring/Detection_Rules/Policy_Modification_Detection.md) |
| [Access Key Creation](../AWS_Cloud_Monitoring/Attack_Scenarios/Access_Key_Creation.md) | [Detection](../AWS_Cloud_Monitoring/Detection_Rules/Access_Key_Detection.md) |
| [S3 Public Access](../AWS_Cloud_Monitoring/Attack_Scenarios/S3_Public_Access.md) | [Detection](../AWS_Cloud_Monitoring/Detection_Rules/S3_Public_Access_Detection.md) |
| [Security Group Modification](../AWS_Cloud_Monitoring/Attack_Scenarios/Security_Group_Modification.md) | [Detection](../AWS_Cloud_Monitoring/Detection_Rules/Security_Group_Detection.md) |

---

## 🧭 Guided Workflow (Recommended Path)

👉 Follow this order for best understanding:

1. ⚙️ Setup Infrastructure  
2. ⚔️ Perform Attack  
3. 📜 Analyze Logs  
4. 🚨 Create Detection  
5. 🔔 Trigger Alerts  

---

## 🚀 Quick Navigation

### 🔹 Start Here

➡️ [IAM Setup](./Infrastructure_Setup/IAM_Setup.md)

---

### 🔹 First Attack Flow

➡️ [IAM User Creation Attack](../AWS_Cloud_Monitoring/Attack_Scenarios/IAM_User_Creation.md)  
➡️ [IAM User Creation Detection](../AWS_Cloud_Monitoring/Detection_Rules/IAM_User_Creation_Detection.md)

---

### 🔹 Continue Lab

➡️ [Next: Policy Modification Attack](../AWS_Cloud_Monitoring/Attack_Scenarios/IAM_Policy_Modification.md)

---

## 🧠 MITRE ATT&CK Mapping

➡️ [View MITRE Mapping](../AWS_Cloud_Monitoring/MITRE_ATTACK/MITRE_Mapping.md)

---

## 📌 Outcome

✔️ Hands-on AWS Security Monitoring  
✔️ Real SOC Detection Engineering Workflow  
✔️ Cloud Attack Simulation + Detection  
✔️ Splunk SIEM Integration  

---

## 👨‍💻 Author

**Abdull Ashthaf**  
Cybersecurity Enthusiast | SOC Analyst Path 🚀
