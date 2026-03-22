# 🔐 SOC Detection Lab (AWS + Splunk)

## 📌 Overview

This project demonstrates the implementation of a Security Operations Center (SOC) lab using AWS infrastructure and Splunk SIEM for centralized logging, monitoring, and detection.

---

## 🧠 Objectives

- Build a cloud-based SOC lab
- Ingest logs from multiple sources
- Perform detection and analysis using Splunk
- Simulate real-world attack scenarios

---

## 🏗️ Architecture

- Ubuntu EC2 (Apache Web Server)
- Windows Server EC2 (Active Directory)
- Splunk Enterprise (SIEM)
- Splunk Universal Forwarder (Log forwarding)

---

                        ┌──────────────────────────────┐
                        │        Attacker Machine      │
                        └──────────────┬───────────────┘
                                       │
                                       ▼
                             Internet (AWS)
                                       │
                        ┌──────────────▼──────────────┐
                        │     SOC VPC (AWS EC2)       │
                        │     CIDR: 172.31.0.0/16     │
                        │                             │
                        │  ┌───────────────────────┐  │
                        │  │   Windows Server AD    │  │
                        │  │   (Domain Controller)  │  │
                        │  │   Splunk Forwarder     │  │
                        │  └──────────┬────────────┘  │
                        │             │ Logs           │
                        │             ▼                │
                        │  ┌───────────────────────┐  │
                        │  │   Ubuntu Web Server    │  │
                        │  │   Apache2              │  │
                        │  │   Splunk Forwarder     │  │
                        │  └──────────┬────────────┘  │
                        │             │ Logs           │
                        │             ▼                │
                        │  ┌───────────────────────┐  │
                        │  │   Splunk Enterprise    │  │
                        │  │   (SIEM Server)        │  │
                        │  │   Port 8000 (Web UI)   │  │
                        │  │   Port 9997 (Receiver) │  │
                        │  └──────────┬────────────┘  │
                        │             │                │
                        └─────────────┼────────────────┘
                                      │
                                      ▼
                             SOC Analyst (You)

## 🔍 Description

- Windows Server AD sends logs via Splunk Universal Forwarder  
- Ubuntu Web Server (Apache2) sends access logs  
- Splunk Enterprise collects and analyzes logs  
- SOC Analyst monitors logs via Splunk Web UI  

## 📊 Log Sources

| Source | Logs |
|-------|------|
| Web Server | Apache access & error logs |
| AD Server | Windows Event Logs |

---

## 📦 Indexing Strategy

| Index | Data |
|------|------|
| webserver | Apache logs |
| main | Active Directory logs |

---

## 🚀 Project Phases

- [x] Environment Setup
- [x] Log Ingestion
- [ ] Detection Engineering
- [ ] Incident Response

---

## 📸 Screenshots

(Add screenshots here)

---

## 🛠️ Tools Used

- AWS EC2
- Splunk Enterprise
- Splunk Universal Forwarder
- Apache2
- Windows Server (AD)

---

## 👨‍💻 Author

- Abdull Ashthaf
