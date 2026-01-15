<p align="center">
  <a href="#overview"><img src="https://img.shields.io/badge/Go_to-Overview-blue?style=for-the-badge"></a>
  <a href="configs/"><img src="https://img.shields.io/badge/Go_to-Configs-purple?style=for-the-badge"></a>
  <a href="detection-lab/"><img src="https://img.shields.io/badge/Go_to-Detection_Lab-orange?style=for-the-badge"></a>
  <a href="reports/"><img src="https://img.shields.io/badge/Go_to-Reports-red?style=for-the-badge"></a>
  <a href="screenshots/"><img src="https://img.shields.io/badge/Go_to-Screenshots-green?style=for-the-badge"></a>
  <a href="architecture/"><img src="https://img.shields.io/badge/Go_to-Architecture-grey?style=for-the-badge"></a>
</p>

---

# 🛡 SOC Project 1 — Windows Sysmon + Wazuh Cloud  
**Complete Endpoint Detection & Telemetry Pipeline (SOC Portfolio Project)**  

![Status](https://img.shields.io/browse/Project-Active-brightgreen)
![Sysmon](https://img.shields.io/badge/Sysmon-15.14-blue)
![Wazuh](https://img.shields.io/badge/Wazuh-4.14-purple)
![Windows](https://img.shields.io/badge/Windows-11-lightgrey)
![MITRE ATT&CK](https://img.shields.io/badge/MITRE%20ATT%26CK-Mapped-orange)

---

# 🔎 Overview  
This project demonstrates a **real-world SOC detection pipeline** using:

- **Sysmon** for advanced Windows endpoint telemetry  
- **Wazuh Cloud** for SIEM ingestion, alerting, and rule evaluation  
- **Custom detection engineering** mapped to MITRE ATT&CK  
- **Threat simulations** that trigger real detections  

It mirrors real SOC workflows:  
**Collect → Parse → Detect → Triage → Document**

---

# 🏗 Architecture Overview

[ Windows Endpoint ]
|
| Sysmon Logs (Operational Channel)

[ Wazuh Agent ] → Secure TLS → [ Wazuh Cloud SIEM ]

Custom Rules → Alerts → Dashboards
|
[ SOC Analyst Investigation ]


More diagrams located in:  
📁 `/architecture/`

---

# 📁 Repository Structure

SOC_Project_1_Windows_Sysmon_Wazuh/
│
├── configs/ # Sysmon + Wazuh config files

├── detection-lab/ # Attack scenarios, logs, and simulation instructions

├── architecture/ # Data flow & architecture documentation

├── reports/ # SOC incident reports & project summaries

├── screenshots/ # Screenshots supporting analysis

└── README.md # This file


---

# 🚀 Key Features

### ✔ Sysmon Telemetry Collection  
Captures high-value Windows activity:  
- Process Creation (Event ID 1)  
- Network Connections (ID 3)  
- DNS Queries (ID 22)  
- File Creation (ID 11)  
- Registry Modification (ID 13/14)  

---

### ✔ Wazuh Cloud SIEM Integration  
Provides:  
- Real-time event forwarding  
- Log normalization & parsing  
- Custom rule matching  
- MITRE ATT&CK mapping  
- Security event dashboards  

---

### ✔ Custom Detection Rules  
Stored in `/configs/custom-rules.xml`

| Rule ID | Description | MITRE |
|---------|-------------|--------|
| **900001** | Encoded PowerShell execution | T1059.001 |
| **900002** | Persistence via registry Run keys | T1547.001 |
| **900003** | DNS C2-like repetitive queries | T1071.004 |
| **900004** | Suspicious child process execution (injection patterns) | T1055 |

---

# 🧩 MITRE ATT&CK Coverage Matrix

| Tactic | Technique ID | Technique | Source | Sysmon Event | Wazuh Rule |
|--------|--------------|-----------|--------|--------------|-------------|
| **Execution** | T1059.001 | PowerShell | Sysmon | ID 1 | 900001 |
| **Persistence** | T1547.001 | Registry Run Keys | Sysmon | ID 13/14 | 900002 |
| **Command & Control** | T1071.004 | DNS C2 | Sysmon | ID 22 | 900003 |
| **Privilege Escalation** | T1055 | Process Injection | Sysmon | ID 8 | 900004 |
| **Discovery** | T1083 | File Discovery | Sysmon | ID 1 | TBD |
| **Lateral Movement** | T1021.001 | RDP | Security Log | 4625 | TBD |
| **Impact** | T1486 | Ransomware-like behavior | Sysmon/FIM | ID 11 | TBD |

---

# 🧪 Detection Lab Scenarios

Detailed instructions are located in:  
📁 `/detection-lab/`

---

## **Scenario 1 — Encoded PowerShell Execution**

**Command:**

powershell.exe -nop -w hidden -enc <payload>

**Expected Results:**  
✔ Sysmon Event ID 1  
✔ Wazuh rule **900001** triggers  

---

## **Scenario 2 — DNS C2 Beaconing**

**Command:**

while ($true) { Resolve-DnsName "c2.malicious-domain.xyz"; Start-Sleep 5 }

**Expected Results:**  
✔ Sysmon Event ID 22  
✔ Wazuh rule **900003** triggers  

---

# 📊 Sample Outputs

### Sysmon Example

Event ID: 1
Image: powershell.exe
CommandLine: -enc SQBFAFgA...

### Wazuh Alert Example
Rule: 900001
Level: 10
Description: Suspicious PowerShell encoded command detected 

---

# 📘 Reports  
Stored in `/reports/`:

- Project-Summary.md  
- SOC-Incident-Report.md  
- MITRE-Mapping.md  
- Triage-Notes.md  

---

# 📸 Screenshots  
Stored in `/screenshots/`:

- wazuh-dashboard.png  
- sysmon-events.png  
- powershell-alert.png  
- dns-c2-alert.png  

---

# 🧠 Skills Demonstrated
- Endpoint logging engineering  
- Windows event channel analysis  
- SIEM data ingestion tuning  
- Detection engineering (Sysmon + Wazuh)  
- MITRE ATT&CK mapping  
- Threat simulation execution  
- SOC incident reporting  

---

# 🏁 Conclusion
This project demonstrates end-to-end SOC capabilities:

✔ Configured Sysmon for telemetry  
✔ Integrated logs with Wazuh  
✔ Built custom detection rules  
✔ Simulated attacks to validate detections  
✔ Produced SOC-grade reports  

A complete example of modern blue-team operations.

---

# 📬 Contact
If reviewing this project for hiring purposes, feel free to reach out via GitHub Issues or email.
