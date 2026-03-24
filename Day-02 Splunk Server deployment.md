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

