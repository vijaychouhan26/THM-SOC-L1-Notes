# Room — Windows Threat Detection 3

**Room:** https://tryhackme.com/room/windowsthreatdetection3

## What This Room Covers

Windows Threat Detection 3 follows an intrusion into command and control, persistence and impact. It focuses on linking suspicious network activity with the processes and persistence mechanisms that allow an attacker to retain access.

---

## Command and Control

C2 lets a compromised host receive instructions and return results. Useful Windows evidence includes:

- Sysmon 22 DNS queries from an unexpected process
- Sysmon 3 outbound connections to rare destinations or unusual ports
- Repeated connections with regular timing that may indicate beaconing
- A process in a user-writable directory initiating external traffic
- Network activity that begins immediately after a suspicious download or execution

Periodicity alone is not proof of C2 because update agents and monitoring software also beacon. Validate destination reputation, process identity, binary signature/hash, user context and organizational baseline.

## Persistence Mechanisms

| Mechanism | Relevant Evidence | Investigation Focus |
|---|---|---|
| Scheduled task | Security 4698/4702 when enabled; task files and process events | Trigger, action, author, executable path and creation time |
| New service | Security 4697 or System 7045 when available | Service name, start type, account and binary path |
| Registry Run key | Sysmon 13 or registry auditing | Value name/data, modifying process and user scope |
| Startup folder | Sysmon 11 and later process creation | Written file, hash, writer and logon execution |

Event coverage depends on audit and Sysmon policy. Confirm that the relevant channel was collecting during the incident before interpreting missing events.

## Scheduled Tasks and Services

Legitimate software frequently creates tasks and services, so the name alone is weak evidence. Stronger warning signs include:

- Executables or scripts in temporary or user-writable directories
- Encoded or obfuscated task actions
- A task created shortly after suspicious remote access
- A service running under an unexpected account
- A misleading name that imitates Windows or approved software
- The configured binary contacting the same suspicious destination as earlier malware

Always pivot from configuration to the referenced file and its execution/network behavior.

## Run Keys and Startup Locations

Common per-user and machine-wide Run locations include:

```text
HKCU\Software\Microsoft\Windows\CurrentVersion\Run
HKLM\Software\Microsoft\Windows\CurrentVersion\Run
```

Startup folders provide another logon-triggered execution path. During triage, identify who wrote the value or file, what executable it references, whether the path exists, and whether the binary is expected across comparable hosts.

## Impact Analysis

Impact may include file encryption or deletion, account disruption, service interruption and other actions that affect confidentiality, integrity or availability. The analyst should distinguish:

- **Capability:** a suspicious tool could perform an action
- **Attempt:** a command or operation was initiated
- **Observed impact:** files, services or users were measurably affected

For suspected ransomware, correlate process creation with rapid file changes, extension/name changes, shadow-copy or recovery-related commands, security-control interference and user/service impact. Follow the approved incident response process rather than executing samples or making uncoordinated changes.

## End-to-End Investigation Workflow

1. Identify the suspicious process responsible for external communication.
2. Trace its parent, file origin, user and Logon ID back to Initial Access.
3. Review DNS and connection history for C2 patterns and related hosts.
4. Search the same time window for new tasks, services, Run keys and Startup files.
5. Inspect every referenced binary or script using path, hash, signature and behavior.
6. Determine whether destructive or disruptive actions occurred.
7. Build a timeline from access through impact and state confidence for each conclusion.
8. Escalate containment and eradication recommendations through authorized procedures.

## My Takeaway

A persistence alert becomes convincing when configuration, artifact and execution evidence agree. The full case should explain how the attacker entered, maintained control, communicated and affected the host—not just list isolated suspicious events.
