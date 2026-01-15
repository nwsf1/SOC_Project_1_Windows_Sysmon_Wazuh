# Data Flow — Sysmon → Wazuh Agent → Wazuh Cloud

## 🔹 Step 1 — Sysmon Telemetry
Sysmon logs:
- Process creation  
- File creation  
- Network connections  
- DNS queries  

Stored under:
`Microsoft-Windows-Sysmon/Operational`

---

## 🔹 Step 2 — Wazuh Agent Collection
The Wazuh agent subscribes to Sysmon’s event channel using:

```
<localfile>
  <location>Microsoft-Windows-Sysmon/Operational</location>
  <log_format>eventchannel</log_format>
</localfile>
```

---

## 🔹 Step 3 — Wazuh Cloud Processing
Logs are:
- Parsed  
- Decoded  
- Mapped to rules  
- Assigned MITRE IDs  
- Trigger alerts  

---

## 🔹 Step 4 — SOC Analyst Review
Events appear in:
- Security Events  
- Threat Hunting Query Console  
- MITRE Attack Matrix View  
