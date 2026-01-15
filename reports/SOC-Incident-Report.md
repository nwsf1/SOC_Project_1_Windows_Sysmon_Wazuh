# SOC Incident Report  
**Incident Title:** Suspicious PowerShell Execution  
**Severity:** High  
**Date:** YYYY-MM-DD  

---

## 📌 Summary
Wazuh detected an encoded PowerShell command executed on a monitored Windows endpoint.  
Sysmon captured detailed telemetry, allowing correlation and classification.

---

## 📁 Indicators
| Type | Value |
|------|-------|
| Process | powershell.exe |
| CommandLine | -nop -w hidden -enc |
| MITRE | T1059.001 |

---

## 📊 Timeline
| Time | Event |
|------|--------|
| 21:03:22 | Sysmon logs Event ID 1 (ProcessCreate) |
| 21:03:23 | Wazuh ingests event |
| 21:03:24 | Rule 900001 triggers |

---

## 🧠 Analysis
The encoded PowerShell command suggests obfuscated malicious execution.  
Such behavior is typical in:
- Empire  
- Cobalt Strike  
- Powershell Empire scripts  

---

## 🚨 Conclusion
This activity is classified as **malicious** and warrants immediate response action.

---

## 🛡 Recommendations
- Restrict PowerShell usage  
- Apply script block logging  
- Deploy EDR with behavior monitoring  
