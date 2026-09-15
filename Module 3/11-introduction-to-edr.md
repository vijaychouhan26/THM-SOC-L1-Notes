# Room — Introduction to EDR

**Room:** https://tryhackme.com/room/introductiontoedr

## What is EDR?

EDR (Endpoint Detection and Response) continuously monitors endpoint devices such as laptops, servers, and workstations for suspicious activity. Compared with traditional antivirus, EDR provides behavioral detection, deeper endpoint visibility, historical activity, and response capabilities.

## Antivirus vs EDR

| Feature | Antivirus | EDR |
|---|---|---|
| Detection method | Signature-based | Behavioral + signature |
| Visibility | File scanning | Process, network, file activity |
| Response | Quarantine file | Isolate host, kill process, collect artifacts |
| Historical data | None | Full activity timeline |
| ATT&CK mapping | No | Yes |

## Key EDR Features

- **Visibility:** Process trees, parent/child relationships, timelines, and historical activity.
- **Telemetry:** Process creation/termination, network connections, file changes, registry changes, and user logon/logoff events.
- **Detection:** IOC matching, behavioral detection, anomaly detection, and MITRE ATT&CK mapping.
- **Response:** Host isolation, process termination, file quarantine, remote shell, and artifact collection.

## Reading EDR Alerts as an L1 Analyst

When an EDR alert fires, check:

1. Process tree — what spawned what?
2. Command line — what exact command was executed?
3. User context — which account and privileges were involved?
4. Network connections — were there suspicious outbound connections?
5. ATT&CK technique — what adversary behavior does it map to?

## Key Terms

| Term | Definition |
|---|---|
| EDR | Endpoint Detection and Response |
| Telemetry | Data collected from endpoints |
| Process Tree | Parent → child process hierarchy |
| Host Isolation | Cutting an endpoint off from the network |
| IOC Matching | Checking artifacts against known indicators |
| ATT&CK | MITRE framework of adversary tactics and techniques |

## My Takeaway

EDR provides the endpoint-level visibility needed to reconstruct process chains, commands, timestamps, and other evidence during an investigation. Without this telemetry, activity on an endpoint can be much harder to detect and investigate.

---

*Part of my THM SOC Level 1 Notes*  
*TryHackMe: https://tryhackme.com/p/Vijaychouhan*
