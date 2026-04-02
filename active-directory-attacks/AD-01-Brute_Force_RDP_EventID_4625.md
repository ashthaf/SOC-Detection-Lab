# 🔴 AD-01 — Brute Force Attack via RDP (Event ID 4625)

---

## 📌 Objective

To detect brute force login attempts against Active Directory user accounts by analyzing failed login events in Splunk.

---

## 🧠 Attack Description

A brute force attack is a credential access technique where an attacker attempts multiple password combinations to gain unauthorized access to a system.

In this scenario, repeated failed login attempts were generated using Remote Desktop Protocol (RDP) targeting a domain user.

---

## ⚙️ Lab Environment

| Component        | Description                                         |
| ---------------- | --------------------------------------------------- |
| Target System    | Windows Server (Active Directory Domain Controller) |
| Attacker Machine | manual bruteforcing (guessing)                      |
| SIEM             | Splunk Enterprise                                   |
| Log Forwarding   | Splunk Universal Forwarder                          |

---

## ⚔️ Attack Simulation Steps

1. Open Remote Desktop Connection (RDP)
2. Enter target machine IP
3. Attempt login using incorrect passwords multiple times
4. Repeat login attempts to simulate brute force activity

---

## 📜 Log Analysis

### 🔹 Event ID 4625 — Failed Logon

This event is generated when a login attempt fails.

### Important Fields:

* **Account_Name** → Target user account
* **Source_Network_Address** → Attacker IP
* **Logon_Type** → Type of login (10 = RDP)

---

## 🔍 Splunk Detection Query

```spl
index="main" EventCode=4625 
| stats count by Account_Name, Source_Network_Address
```

---

## 📊 Detection Logic

* Monitor failed login attempts
* Group by username and source IP
* Identify abnormal spikes in failed attempts
* Flag repeated failures from same IP

---

## 🚨 Alert Configuration

| Parameter | Value                 |
| --------- | --------------------- |
| Condition | Failed attempts > 5   |
| Severity  | High                  |
| Trigger   | Real-time / Scheduled |

---

## 🧠 MITRE ATT&CK Mapping

| Category     | Details           |
| ------------ | ----------------- |
| Tactic       | Credential Access |
| Technique    | Password Guessing |
| Technique ID | T1110             |

---

## 🖼️ Screenshots

![Failed Login](assets/log in fail.png)
> * Source IP
> * Detection results

---

## 📚 Analysis

* Multiple failed login attempts observed
* Same source IP targeting a user account
* Pattern consistent with brute force attack

---

## 🛡️ Mitigation Strategies

* Implement account lockout policies
* Enforce strong password policies
* Enable Multi-Factor Authentication (MFA)
* Monitor login activity continuously

---

## 🧹 Cleanup Actions

* No persistent changes made to system
* Verified no successful login occurred
* Logs retained for analysis

---

## 🔐 Notes

Sensitive data such as:

* IP addresses
* Domain names
* Usernames

have been sanitized before publishing.
