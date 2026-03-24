🖥️ Setup-02 — Splunk Enterprise Deployment on AWS EC2 (Windows)
📋 Overview

Splunk Enterprise was deployed on a Windows EC2 instance inside the custom SOC-VPC to act as the central SIEM for the SOC Detection Lab. Logs from the Active Directory server and Ubuntu web server are forwarded to this instance using Splunk Universal Forwarders for centralized monitoring and analysis.

🏗️ Architecture
Active Directory Server (Windows) ──┐
                                   ├──► Splunk Universal Forwarder ──► Splunk Server (Windows EC2) ──► SOC Analyst
Ubuntu Web Server (Apache) ────────┘                                      Port 9997 (receiving)      Port 8000 (UI)
⚙️ EC2 Instance Configuration
Setting	Value
AMI	Windows Server 2022
Instance Type	t2.large / t3.large
Network	SOC-VPC
Subnet	Public Subnet
Auto-assign Public IP	Enabled
Storage	50 GB
🔐 Security Group — Inbound Rules
Port	Protocol	Purpose
3389	TCP	RDP access
8000	TCP	Splunk Web Interface
9997	TCP	Log receiving from Forwarders
⚙️ Deployment Steps
Step 1 — Connect to Windows EC2 (RDP)
Download .rdp file from AWS
Connect using Administrator credentials
Step 2 — Download Splunk Enterprise
Open browser inside EC2
Download Splunk Enterprise (.msi) from official site
Step 3 — Install Splunk
Run .msi installer
Follow setup wizard
Choose installation path (default)
Set admin username and password
Step 4 — Verify Installation

Open browser:

http://localhost:8000

OR

http://<EC2-Public-IP>:8000

Login with:

Username: admin
Password: (created during setup)
Step 5 — Enable Receiving Port (IMPORTANT)

Inside Splunk Web:

Go to Settings → Forwarding and Receiving
Click Configure Receiving
Add new port:
9997

✅ Splunk is now ready to receive logs

Step 6 — Verify Splunk Service
Ensure Splunk service is running in Windows Services
Confirm UI is accessible
📊 Log Ingestion Configuration

Splunk Universal Forwarders were configured on:

🔹 Active Directory Server
Forwarded Windows Event Logs
🔹 Ubuntu Web Server
Forwarded Apache logs:
/var/log/apache2/access.log

Configured in inputs.conf:

[monitor:///var/log/apache2/access.log]
index=webserver
sourcetype=access_combined

Configured in outputs.conf:

[tcpout:splunk]
server=<Splunk-Server-IP>:9997
📸 Screenshots

(Add your images from /assets)

![Splunk Installation](assets/splunk-install.png)
![Splunk Login](assets/splunk-login.png)
![Receiving Port](assets/port-9997.png)
![Log Ingestion](assets/logs.png)
📊 Verification

Logs successfully visible in Splunk:

index=*
index=webserver

Observed data:

Apache access logs (Ubuntu server)
Windows system & security logs (AD server)
Performance metrics
✅ Deployment Summary
Component	Status
Windows EC2 launched	✅
Splunk installed	✅
Web UI accessible (8000)	✅
Receiving enabled (9997)	✅
Forwarders configured	✅
Logs successfully ingested	✅
🚀 Outcome
Successfully deployed Splunk Enterprise on Windows EC2
Configured centralized SIEM environment
Ingested logs from multiple sources
Verified real-time monitoring capability
🔜 Next Steps
Create detection rules
Simulate attacks (Brute Force, Web Attacks)
Build dashboards and alerts
