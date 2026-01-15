# SOC Project 1 — Windows Endpoint Monitoring with Sysmon + Wazuh (Cloud)

## 🛡️ Overview
This project demonstrates the setup, configuration, and analysis of Windows endpoint security monitoring using **Sysmon** for detailed host telemetry and **Wazuh Cloud** for centralized SIEM/SOC processing.  

The goal of this project is to simulate a real SOC analyst workflow:
- Deploy agent-based telemetry  
- Collect Sysmon security events  
- Build detection rules  
- Investigate suspicious activity  
- Produce a professional SOC report  

---

# 🔧 Architecture

```
Windows 11 Endpoint  
    |  
    | Sysmon (Event Logging)  
    ↓  
Wazuh Agent  
    | Sends encrypted logs  
    ↓  
Wazuh Cloud SIEM  
    |  
    ↓  
Dashboards, Alerts, Correlation, MITRE ATT&CK
```

---

# 📁 Project Structure

```
SOC_Project_1_Windows_Sysmon_Wazuh/
│
├── configs/
│   ├── sysmon-config.xml
│   ├── wazuh-agent.conf
│   ├── custom-rules.xml
│   ├── decoders.xml
│
├── detection-lab/
│   ├── attack-scenario-1.md
│   ├── attack-scenario-2.md
│   ├── example-sysmon-logs.txt
│
├── reports/
│   ├── SOC-Incident-Report.md
│   ├── Project-Summary.md
│
├── screenshots/
│   ├── wazuh-dashboard.png
│   ├── sysmon-events.png
│   ├── detection-alert.png
│
└── README.md
```

---

# 🧰 Tools Used
- **Sysmon v15.15**
- **Wazuh Agent v4.14**
- **Wazuh Cloud Console**
- **MITRE ATT&CK Mapping**
- **PowerShell**
- **Event Viewer**
- **Windows 11 Endpoint (Test Machine)**

---

# 📊 Detection Use Cases Implemented

### 🔍 1. Suspicious Process Creation (Sysmon Event ID 1)
Detects:
- LOLBins (cmd, powershell, wmic, regsvr32)
- Unsigned binaries in user directories
- Suspicious parent-child relationships

### 📁 2. File Modification (Sysmon Event ID 2 + Wazuh Syscheck)
Detects:
- Unauthorized EXE creation  
- Startup persistence  
- Registry autoruns  

### 🌐 3. Network Connections (Sysmon Event ID 3)
Detects:
- Outbound C2 patterns  
- Unknown remote IP connections  

---

# 🧪 Attack Simulations Performed
- Suspicious PowerShell execution  
- Creation of unauthorized EXE in Desktop folder  
- Network connection to unknown IP  
- Registry autorun modification  

---

# 📈 Results
All attacks successfully generated Sysmon logs, which were collected by Wazuh and produced alerts.

Screenshots, logs, and alerts are included in the project folders.

---

# 📝 Conclusion
This project demonstrates:
✔ Ability to configure enterprise endpoint security telemetry  
✔ Practical SIEM/SOC investigation workflow  
✔ Creation of custom detection rules  
✔ Documentation similar to real SOC environments  

---
