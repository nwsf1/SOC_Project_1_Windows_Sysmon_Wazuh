# 🛡 SOC Project 1 — Windows Sysmon + Wazuh Cloud

**Complete Endpoint Detection & Telemetry Pipeline (SOC Portfolio Project)**

[Overview](#overview) • [Configs](configs/) • [Detection Lab](detection-lab/) • [Reports](reports/) • [Screenshots](screenshots/) • [Architecture](architecture/)

---

## Status & Compatibility

- Project status: Active
- Tested with: Windows 10/11, Sysmon 15.14, Wazuh 4.14
- MITRE ATT&CK: Mapped where applicable

---

## Overview

This repository demonstrates an end-to-end SOC detection pipeline for Windows endpoints built with:

- Sysmon — high-fidelity Windows endpoint telemetry
- Wazuh Cloud — SIEM ingestion, normalization, alerting, and rule evaluation
- Custom detection engineering mapped to MITRE ATT&CK
- Threat simulation scenarios used to validate detections

Typical workflow: Collect → Parse → Detect → Triage → Report

---

## Repository structure

- configs/ — Sysmon configuration and Wazuh custom rules
- detection-lab/ — Attack scenarios, test data, and simulation instructions
- architecture/ — Diagrams and telemetry/data-flow documentation
- reports/ — Project summary, incident reports, and triage notes
- screenshots/ — Dashboard and alert screenshots
- README.md — This file

---

## Key features

### Sysmon telemetry
Captures high-value Windows activity including:
- Process creation (Event ID 1)
- Network connections (ID 3)
- DNS queries (ID 22)
- File creation (ID 11)
- Registry modifications (ID 13/14)

### Wazuh Cloud integration
- Real-time event forwarding from Wazuh Agent
- Log normalization and parsing
- Custom rule matching and alerting
- Dashboards and MITRE ATT&CK mapping

### Custom detection rules
Custom rules are stored in `configs/custom-rules.xml`.
Example rule IDs:
- 900001 — Encoded PowerShell execution (T1059.001)
- 900002 — Persistence via Registry Run keys (T1547.001)
- 900003 — DNS C2-like repetitive queries (T1071.004)
- 900004 — Suspicious child process execution / injection patterns (T1055)

---

## MITRE ATT&CK coverage (summary)

| Tactic | Technique ID | Technique | Source | Sysmon Event | Wazuh Rule |
|--------|--------------:|----------|--------|--------------:|-----------:|
| Execution | T1059.001 | PowerShell (encoded) | Sysmon | 1 | 900001 |
| Persistence | T1547.001 | Registry Run Keys | Sysmon | 13/14 | 900002 |
| Command & Control | T1071.004 | DNS C2 | Sysmon | 22 | 900003 |
| Privilege Escalation | T1055 | Process Injection | Sysmon | 8 | 900004 |

Note: Some mappings are marked TBD and can be found in `reports/MITRE-Mapping.md`.

---

## Detection lab scenarios (examples)

### Scenario 1 — Encoded PowerShell execution

Command:

powershell.exe -NoProfile -WindowStyle Hidden -EncodedCommand <payload>

Expected results:
- Sysmon Event ID 1 (Process Create)
- Wazuh rule 900001 triggers

### Scenario 2 — DNS C2 beaconing

PowerShell example:

while ($true) { Resolve-DnsName "c2.malicious-domain.xyz"; Start-Sleep -Seconds 5 }

Expected results:
- Sysmon Event ID 22 (DNS Query)
- Wazuh rule 900003 triggers

Detailed walk-throughs and logs are in `detection-lab/`.

---

## Sample outputs

Sysmon example (Process Create):

- Event ID: 1
- Image: powershell.exe
- CommandLine: -EncodedCommand AAAAA...

Wazuh alert example:
- Rule: 900001
- Level: 10
- Description: Suspicious PowerShell encoded command detected

---

## Architecture and diagrams

See `architecture/` for diagrams that show how Sysmon generates structured logs and how the Wazuh agent forwards telemetry to Wazuh Cloud.

---

## Using external capture and simulation tools

If you want to capture or synthesize telemetry for tests, you can reuse capture tooling from other projects. For example, a capture helper script is available here:

- RedShelf Capture Tool: https://github.com/nwsf1/RedShelf-Capture-Tool/blob/main/redshelf_capture.py

Use that script to collect and package test artifacts, then place them under `detection-lab/` when adding scenario evidence.

---

## Reports

Reports are in `/reports/`:
- Project-Summary.md
- SOC-Incident-Report.md
- MITRE-Mapping.md
- Triage-Notes.md

---

## Screenshots

Stored in `/screenshots/` (examples):
- wazuh-dashboard.png
- sysmon-events.png
- powershell-alert.png
- dns-c2-alert.png

---

## Skills demonstrated

- Endpoint logging engineering
- Windows event channel analysis
- SIEM ingestion and normalization
- Detection engineering (Sysmon + Wazuh)
- MITRE ATT&CK mapping
- Threat simulation and validation
- SOC incident reporting

---

## Contributing

Contributions are welcome. If you want to add scenarios, rules, or documentation:
1. Fork the repository
2. Create a branch for your change
3. Open a pull request with a clear description and test artifacts

---

## License & Contact

This repository is provided as-is for educational and portfolio purposes. If reviewing for hiring, please contact via GitHub Issues or email listed on my GitHub profile.

---

(End of file)