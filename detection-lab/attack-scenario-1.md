# Attack Scenario 1 — Suspicious PowerShell Execution  
**MITRE Technique: T1059.001 (PowerShell)**

## 🎯 Objective
Simulate an attacker launching an obfuscated PowerShell payload and validate:
- Sysmon telemetry collection  
- Wazuh ingestion  
- Custom rules firing  

---

## 🧪 Steps to Reproduce
Run the following command:

```powershell
powershell -nop -w hidden -enc SQBFAFgA...
```

This simulates:
- Encoded payload execution  
- Hidden window  
- No-profile PowerShell launch  

---

## 🔍 Expected Sysmon Logs
- **Event ID 1 — Process Creation**
- Parent: `explorer.exe`
- Image: `powershell.exe`
- CommandLine includes: `-enc`

---

## 🚨 Expected Wazuh Alerts
Triggered Rule: **900001**  
> Suspicious PowerShell encoded command execution  
> MITRE: T1059.001

Screenshot placeholder:  
`/screenshots/powershell-encoded-alert.png`
