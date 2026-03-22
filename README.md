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
