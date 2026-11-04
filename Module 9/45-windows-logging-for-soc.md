# Room — Windows Logging for SOC

**Room:** https://tryhackme.com/room/windowsloggingforsoc

## What This Room Covers

Windows Logging for SOC introduces the main Windows evidence sources used during alert triage: Security logs, Sysmon telemetry and PowerShell history. The focus is not memorizing every event ID, but learning how to connect authentication, process, file, registry and network activity into one timeline.

---

## Windows Event Evidence

Windows event logs are stored as EVTX files under:

```text
C:\Windows\System32\winevt\Logs
```

Event Viewer parses these files and lets an analyst filter by log source, timestamp, Event ID and event fields. Windows timestamps use the system's configured time zone, so the case timeline should record the time-zone context before correlating data from other systems.

## High-Value Events

| Source / Event ID | Meaning | Useful Investigation Fields |
|---|---|---|
| Security 4624 | Successful logon | Account, Logon Type, source address, workstation, Logon ID |
| Security 4625 | Failed logon | Target account, source address, failure reason, Logon Type |
| Security 4720 | User account created | Subject account, new account, Logon ID |
| Security 4732 | Member added to a local security group | Subject, member, target group, Logon ID |
| Security 4688 | Process creation when auditing is enabled | New process, creator process, command line |
| Sysmon 1 | Process creation | Image, command line, hashes, parent, user, Logon ID |
| Sysmon 3 | Network connection | Process, source/destination address and port |
| Sysmon 11 | File creation | Process and target file path |
| Sysmon 13 | Registry value set | Process, registry path and value |
| Sysmon 22 | DNS query | Process and queried domain |

Event availability depends on audit policy and Sysmon configuration. An absent event does not prove an action did not occur.

## Authentication Analysis

Logon Types help explain how a session was created:

| Logon Type | Common Interpretation |
|---|---|
| 2 | Local interactive logon |
| 3 | Network logon |
| 5 | Service logon |
| 10 | Remote interactive logon, commonly RDP |

For suspected RDP compromise, compare repeated 4625 failures with a later 4624 success. Network Level Authentication can produce related Type 3 and Type 10 events, so the analyst should use the account, source, timestamp and Logon ID together instead of treating one event as the complete story.

## Correlation Pivots

```text
4624/4625 authentication
        ↓ Logon ID
4720/4732 account changes
        ↓ same session
Sysmon 1 process creation
        ↓ Process ID / Process GUID
Sysmon 11, 13, 3 and 22
```

- **Logon ID** connects activity performed in the same authenticated session.
- **Process ID / Process GUID** links a process to file, registry, DNS and network events.
- **Parent process** helps explain how execution started.
- **Hashes and paths** provide pivots into reputation checks and fleet-wide searches.

## PowerShell Evidence

The PSReadLine history for each user is normally stored at:

```text
C:\Users\<USER>\AppData\Roaming\Microsoft\Windows\PowerShell\PSReadLine\ConsoleHost_history.txt
```

It can reveal interactive discovery or download commands, but it has important limitations: it records commands rather than their output, does not expose the contents of every executed script, is per-user, and can be cleared or bypassed. Treat it as one evidence source, not a complete PowerShell audit trail.

## Practical Investigation Workflow

1. Confirm host, time window, time zone and available log channels.
2. Identify suspicious authentication and preserve the Logon ID.
3. Check account creation or group membership changes from the same session.
4. Pivot to Sysmon 1 and build the parent-child process chain.
5. Use Process ID or Process GUID to locate related files, registry changes, DNS and connections.
6. Review PowerShell history and any enabled PowerShell operational logs.
7. Separate observed facts, analyst interpretation and missing telemetry in the case notes.

## My Takeaway

Windows investigations become manageable when I pivot on stable identifiers. Event IDs identify the activity type; Logon ID and process context connect those individual events into an attack chain.
