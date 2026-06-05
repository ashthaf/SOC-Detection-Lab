# ☁️ AWS SOC CloudTrail Monitoring Lab

## Overview

This project demonstrates a Security Operations Center (SOC) monitoring pipeline built using AWS and Splunk.

The objective is to collect AWS activity logs, forward them to Splunk, create detections, simulate attacks, and generate alerts.

---

## Architecture

![Architecture](../assets/architecture.png)

---

## Components

- AWS IAM
- AWS CloudTrail
- AWS S3
- AWS SNS
- AWS SQS
- Splunk Enterprise

---

## Attack Scenarios

- IAM User Creation
- EC2 Instance Start
- IAM Policy Modification
- CloudTrail Enumeration
- Log Tampering

---

## MITRE ATT&CK

See:

MITRE_Mapping/MITRE.md

---

## Documentation

### AWS Setup

- IAM Setup
- CloudTrail Setup
- S3 Setup
- SNS Setup
- SQS Setup
- Splunk Integration

### Attack Simulations

- IAM User Creation
- EC2 Start Detection
- Policy Modification

### Detection Rules

- Splunk Detection Rules
- Alerting Logic
