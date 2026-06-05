# ⚔️ Security Group Modification Attack

## 🎯 Objective

Simulate an attacker modifying a security group to allow unrestricted access to AWS resources.

---

## 🧠 Attack Description

An attacker modifies security group rules to:

* Allow inbound traffic from anywhere (`0.0.0.0/0`)
* Expose services like SSH (22), RDP (3389), HTTP (80)
* Gain remote access to instances

---

## ⚙️ Attack Steps

### Method: Open Security Group to Public

1. Go to AWS Console → EC2
2. Navigate to:

   ```
   Security Groups
   ```
3. Select a security group
4. Click:

   ```
   Edit Inbound Rules
   ```
5. Add rule:

* Type:

  ```
  SSH
  ```
* Port:

  ```
  22
  ```
* Source:

  ```
  0.0.0.0/0
  ```

6. Save rules

---

## 📸 Screenshot

![Security Group Attack](../../assets/sg-attack.png)

---

## 🔍 Logs Generated (CloudTrail)

```text
eventName=AuthorizeSecurityGroupIngress
eventName=ModifySecurityGroupRules
```

---

## 📊 Key Fields

| Field                     | Description           |
| ------------------------- | --------------------- |
| eventName                 | Action performed      |
| requestParameters.groupId | Target security group |
| ipPermissions             | Opened ports          |
| sourceIPAddress           | Source IP             |

---

## 🚨 Why This Is Dangerous

* Exposes infrastructure to internet
* Enables brute-force attacks
* Allows unauthorized remote access
* Increases attack surface

---

## 🧠 MITRE ATT&CK Mapping

| Tactic          | Technique       | ID    |
| --------------- | --------------- | ----- |
| Defense Evasion | Modify Firewall | T1562 |

---

## 🔗 Next Step

➡️ Detection Rule:
`../Detection_Rules/CloudTrail_Tampering_Detection.md`
