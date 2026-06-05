# ☁️ AWS Cloud Monitoring (Attack & Detection Lab)

![Module](https://img.shields.io/badge/Module-AWS%20Monitoring-blue)
![Focus](https://img.shields.io/badge/Focus-Detection-green)
![Source](https://img.shields.io/badge/Logs-CloudTrail-orange)

---

## 📌 Description

This module focuses on simulating AWS cloud attacks and detecting them using **CloudTrail logs + Splunk**.

---

## 🧭 Quick Navigation

### ⚔️ Attack → 🚨 Detection Flow

➡️ [IAM User Creation](./Attack_Scenarios/IAM_User_Creation.md)  
➡️ [Detection](./Detection_Rules/IAM_User_Creation_Detection.md)

➡️ [Policy Modification](./Attack_Scenarios/IAM_Policy_Modification.md)  
➡️ [Detection](./Detection_Rules/Policy_Modification_Detection.md)

➡️ [Access Key Creation](./Attack_Scenarios/Access_Key_Creation.md)  
➡️ [Detection](./Detection_Rules/Access_Key_Detection.md)

➡️ [S3 Public Access](./Attack_Scenarios/S3_Public_Access.md)  
➡️ [Detection](./Detection_Rules/S3_Public_Access_Detection.md)

➡️ [Security Group Modification](./Attack_Scenarios/Security_Group_Modification.md)  
➡️ [Detection](./Detection_Rules/Security_Group_Detection.md)

---

## 📂 Sections

### ⚔️ Attack Scenarios

- 🔹 [IAM User Creation](./Attack_Scenarios/IAM_User_Creation.md)
- 🔹 [IAM Policy Modification](./Attack_Scenarios/IAM_Policy_Modification.md)
- 🔹 [Access Key Creation](./Attack_Scenarios/Access_Key_Creation.md)
- 🔹 [S3 Public Access](./Attack_Scenarios/S3_Public_Access.md)
- 🔹 [Security Group Modification](./Attack_Scenarios/Security_Group_Modification.md)

---

### 🚨 Detection Rules

- 🔹 [IAM User Creation Detection](./Detection_Rules/IAM_User_Creation_Detection.md)
- 🔹 [Policy Modification Detection](./Detection_Rules/Policy_Modification_Detection.md)
- 🔹 [Access Key Detection](./Detection_Rules/Access_Key_Detection.md)
- 🔹 [S3 Public Access Detection](./Detection_Rules/S3_Public_Access_Detection.md)
- 🔹 [Security Group Detection](./Detection_Rules/Security_Group_Detection.md)

---

## 🔄 Recommended Flow

1. ⚔️ Perform Attack  
2. 📜 Observe CloudTrail Logs  
3. 🔍 Analyze in Splunk  
4. 🚨 Create Detection Rule  
5. 🔔 Trigger Alert  

---

## 🧠 MITRE Mapping

➡️ [View MITRE ATT&CK Mapping](./MITRE_ATTACK/MITRE_Mapping.md)

---

## 🔗 Related

➡️ [Main SOC Lab](../AWS_SOC_CloudTrail_Lab/README.md)
