# 🛡 SOC Project 1 — Windows Sysmon + Wazuh Cloud  
**Complete Endpoint Detection & Telemetry Pipeline (SOC Portfolio Project)**  

![Status](https://img.shields.io/badge/Project-Active-brightgreen)
![Sysmon](https://img.shields.io/badge/Sysmon-15.14-blue)
![Wazuh](https://img.shields.io/badge/Wazuh-4.14-purple)
![Windows](https://img.shields.io/badge/Windows-11-lightgrey)
![MITRE ATT&CK](https://img.shields.io/badge/MITRE%20ATT%26CK-Mapped-orange)

---

## 📌 Project Overview
This project demonstrates a **real-world SOC detection pipeline** using:

- **Sysmon** for advanced Windows event telemetry  
- **Wazuh Cloud** for log ingestion, rule processing & alerting  
- **Custom detection engineering** mapped to MITRE ATT&CK  
- **Threat simulations** including:
  - Encoded PowerShell execution  
  - DNS-based C2 beaconing  

This project mirrors what Tier 1–2 SOC Analysts do:  
**collect logs → normalize → detect → triage → document.**

---

## 📁 Repository Structure

```
SOC_Project_1_Windows_Sysmon_Wazuh/
│
├── configs/                 # Sysmon + Wazuh config files
├── detection-lab/           # Attack scenarios, logs, simulation instructions
├── architecture/            # Data flow & architecture diagrams
├── reports/                 # SOC incident reports & project summary
├── screenshots/             # Screenshots to support documentation
└── README.md                # This file
```

---

## 🚀 Key Features

### ✔ Sysmon Telemetry  
Captures:
- Process Creation (ID 1)  
- Network Connections (ID 3)  
- DNS Queries (ID 22)  
- File & Registry events  

### ✔ Wazuh Cloud SIEM  
- Real-time log ingestion  
- MITRE mapping  
- Custom detection rules  
- Threat Hunting query console  

### ✔ Custom Detection Rules  
Included in `/configs/custom_rules.xml`:

| Rule ID | Description | MITRE |
|---------|-------------|--------|
| **900001** | Encoded PowerShell execution | T1059.001 |
| **900003** | DNS C2-like repeated queries | T1071.004 |

---

## 🧪 Detection Lab Scenarios
Stored inside:  
➡ `detection-lab/`

### **Scenario 1 — Encoded PowerShell Execution**
Simulates obfuscated payload execution using:

```
powershell.exe -nop -w hidden -enc <payload>
```

### **Scenario 2 — DNS C2 Beaconing**
Simulates repeated suspicious DNS requests:

```
while ($true) { Resolve-DnsName "c2.malicious-domain.xyz"; sleep 5 }
```

---

## 📊 Sample Outputs

### **Sysmon Log Example**
```
Event ID: 1 (ProcessCreate)
Image: powershell.exe
CommandLine: -enc SQBFAFgA...
```

### **Wazuh Alert Example**
```
Rule: 900001
Level: 10
Description: Suspicious PowerShell encoded command detected
MITRE: T1059.001
```

---

## 📘 Reports Included
Located in `/reports/`:

- **Project-Summary.md**  
- **SOC-Incident-Report.md**  
- MITRE mapping tables  
- Analyst triage notes  

---

## 🧠 Skills Demonstrated
- Threat detection engineering  
- SIEM configuration & tuning  
- Telemetry analysis  
- Windows event channel monitoring  
- MITRE ATT&CK mapping  
- SOC reporting & documentation  

---

## 🏁 Conclusion
This project simulates a complete SOC workflow, showcasing real-world ability to:

✔ Deploy Sysmon  
✔ Configure Wazuh  
✔ Build detections  
✔ Test with simulations  
✔ Produce SOC-quality incident documentation  

---

## 📬 Contact
If reviewing for hiring purposes, feel free to reach out via GitHub Issues or email.
