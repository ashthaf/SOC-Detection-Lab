# 🔐 SOC Detection Lab (AWS + Splunk)

## 📌 Overview

This project demonstrates a **Hybrid Security Operations Center (SOC)** lab combining:

- 🖥️ Traditional Infrastructure (Active Directory, Web Server, Endpoint)
- ☁️ AWS Cloud Monitoring (CloudTrail + CloudWatch Pipeline)
- 📊 Splunk SIEM for centralized logging, detection, and alerting

It simulates **real-world attacks across multiple environments** and detects them using **log pipelines and SIEM correlation**.

---

## 🧠 Objectives

- Build a **Hybrid SOC (On-Prem + Cloud)**
- Centralize logs into Splunk SIEM
- Simulate attacks across:
  - Active Directory
  - Web Applications
  - AWS Cloud
- Perform detection engineering
- Map detections to MITRE ATT&CK

---

## 🏗️ Architecture Overview

This SOC lab consists of **two integrated pipelines**:

### 🖥️ On-Prem / EC2 Infrastructure
- Windows Server (Active Directory)
- Ubuntu Web Server (Apache + DVWA)
- Splunk Universal Forwarders
- Splunk Enterprise (SIEM)

### ☁️ AWS Cloud Monitoring Pipeline
- AWS CloudTrail (API logging)
- S3 (Log storage)
- CloudWatch (Detection engine)
- SNS → SQS (Alert pipeline)
- Splunk (Cloud ingestion)

---

## 🔗 Unified SOC Data Flow

- Logs from **AD + Web Servers** → Splunk Forwarder → Splunk SIEM  
- Logs from **AWS CloudTrail** → S3 + CloudWatch  
- CloudWatch → SNS → SQS → Splunk  
- Splunk correlates everything → SOC Analyst investigates  

---

## 📊 Log Sources

| Source | Logs |
|------|------|
| Active Directory | Windows Event Logs |
| Web Server | Apache Logs |
| AWS Cloud | CloudTrail Events |

---

## 📦 Indexing Strategy

| Index | Data |
|------|------|
| main | AD Logs |
| webserver | Apache Logs |
| *  | Endpoint Logs|
| aws_cloudtrail | AWS Logs |

---

## 🚀 Project Modules

### 🛡️ Active Directory Attacks
👉 [View Lab](./active-directory-attacks/README.md)

### 🌐 Web Attacks
👉 [View Lab](./Web_Attacks/)

### 🖥️ Endpoint Attacks
👉 [View Lab](./endpoint-attack-detection/README.md)

### ☁️ AWS Cloud Monitoring
👉 **[View AWS Cloud Lab](./AWS_Cloud_Monitoring/README.md)**

---

## 🧠 Detection Coverage

- IAM Abuse Detection
- Credential Access (Access Keys)
- S3 Public Exposure
- Security Group Misconfiguration
- Web Attacks (SQLi, XSS)
- AD Attacks (Privilege Escalation)

---

## 🏗️ Full SOC Architecture

> 📍 Located in `/assets/architecture.png`

![SOC Architecture](./assets/architecture.png)

---

## 🔍 Description

### 🖥️ On-Prem Detection
- AD logs → privilege escalation detection  
- Apache logs → web attack detection
- Enpoint logs → Endpoint detection

### ☁️ Cloud Detection
- CloudTrail → tracks AWS activity  
- CloudWatch → detection rules  
- SNS/SQS → alert pipeline  
- Splunk → correlation & alerting  

---

## 🛠️ Tools Used

- AWS (CloudTrail, CloudWatch, S3, SNS, SQS)
- Splunk Enterprise
- Splunk Universal Forwarder
- Windows Server (Active Directory)
- Apache2 (DVWA)

---

## 🎯 Project Status

- [x] Infrastructure Setup
- [x] Log Ingestion
- [x] Attack Simulation
- [x] Detection Engineering
- [ ] Incident Response (Future Work)

---

## 👨‍💻 Author

**Abdull Ashthaf CK**
