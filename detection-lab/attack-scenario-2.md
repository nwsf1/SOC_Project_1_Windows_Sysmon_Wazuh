# Attack Scenario 2 — C2-style DNS Beaconing  
**MITRE Technique: T1071.004 (DNS C2)**

## 🎯 Objective
Simulate DNS-based command & control beacon using repeated DNS lookups.

---

## 🧪 Steps to Reproduce
Run:

```powershell
while ($true) { Resolve-DnsName "c2.malicious-domain.xyz"; Start-Sleep 5 }
```

---

## 🔍 Expected Sysmon Logs
- **Event ID 22 — DNS Query**
- QueryName includes: `c2`
- Image: `powershell.exe`

---

## 🚨 Expected Wazuh Alerts
Triggered Rule: **900003**  
> C2-like DNS query observed  
> MITRE: T1071.004

Screenshot placeholder:  
`/screenshots/dns-c2-alert.png`
