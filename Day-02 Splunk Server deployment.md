# Setup-02 — Splunk Enterprise Deployment on AWS EC2

![AWS](https://img.shields.io/badge/Platform-AWS-FF9900?style=flat-square&logo=amazonaws)
![Splunk](https://img.shields.io/badge/SIEM-Splunk%20Enterprise-FF6B35?style=flat-square&logo=splunk)
![Windows](https://img.shields.io/badge/OS-Windows%20Server-0078D6?style=flat-square&logo=windows)
![Status](https://img.shields.io/badge/Status-Completed-brightgreen?style=flat-square)

---

## 📋 Overview

Splunk Enterprise was deployed on a Windows EC2 instance inside the custom SOC-VPC to act as the central SIEM for the SOC Detection Lab. All logs from Active Directory and the web server are forwarded to this instance for real-time monitoring, detection, and investigation.

---

## 🏗️ Architecture
                 ┌────────────────────────────┐
                 │   Active Directory Server   │
                 │   (Windows + UF)           │
                 └────────────┬───────────────┘
                              │
                              │ Logs (UF)
                              ▼
                 ┌────────────────────────────┐
                 │     Ubuntu Web Server      │
                 │     (Apache + UF)          │
                 └────────────┬───────────────┘
                              │
                              │ Logs (UF)
                              ▼
                 ┌────────────────────────────┐
                 │   Splunk Enterprise (EC2)  │
                 │   Port 9997 (Receiving)    │
                 │   Port 8000 (Web UI)       │
                 └────────────┬───────────────┘
                              │
                              ▼
                 ┌────────────────────────────┐
                 │        SOC Analyst         │
                 │     (Monitoring via UI)    │
                 └────────────────────────────┘




## ⚙️ EC2 Instance Configuration

| Setting | Value |
|---|---|
| AMI | Windows Server 2022 |
| Instance Type | t2.large |
| Network | SOC-VPC |
| Subnet | SOC-Public-Subnet |
| Auto-assign Public IP | Enabled |
| Storage | 50GB gp2 |

---

## 🔐 Security Group — Inbound Rules

| Port | Protocol | Purpose |
|---|---|---|
| 3389 | TCP | RDP access for administration |
| 8000 | TCP | Splunk Web Interface |
| 9997 | TCP | Log receiving from Universal Forwarders |

---

## ⚙️ Deployment Steps

### Step 1 — Connect to EC2 via RDP

Download the RDP file and connect to the instance using Administrator credentials.

---

### Step 2 — Install Splunk Enterprise

- Download Splunk Enterprise (.msi) from official website  
- Run installer on Windows server  
- Complete setup wizard  

---

### Step 3 — Start Splunk and Configure Admin Account

- Launch Splunk after installation  
- Set admin username  
- Set admin password  

---

### Step 4 — Verify Splunk is Running

Open browser:
http://localhost:8000

---


### Step 5 — Access Splunk Web Interface

Open browser and navigate to:
http://<EC2 Public IP >:8000


Login with the admin credentials created during installation.

---


### Step 6 — Enable Log Receiving on Port 9997

Inside Splunk Web UI:
Settings → Forwarding and Receiving → Configure Receiving → New Receiving Port → 999


This opens port 9997 to receive logs from Universal Forwarders installed on endpoint machines.

---

### Step 7 — Create SOC Lab Indexes
Settings → Indexes → New Index


Create the following indexes used across the lab:

| Index Name | Purpose |
|---|---|
| `main` | Active Directory / Windows logs |
| `webserver` | Apache web server logs |

---

## ✅ Deployment Summary

| Component | Status |
|---|---|
| Windows EC2 launched | ✅ |
| Security group configured | ✅ |
| Splunk Enterprise installed | ✅ |
| Web interface accessible on port 8000 | ✅ |
| Log receiving enabled on port 9997 | ✅ |
| SOC indexes created | ✅ |

---

## 🔗 Next Steps

- Setup-03 → Universal Forwarder Configuration  
- Setup-04 → Log Ingestion & Monitoring  
- Detection → Web & AD Attack Analysis  

---

*SOC Lab Infrastructure | Splunk Enterprise | Windows Server | AWS | Author: Abdull Ashthaf*

