# Room — Windows Threat Detection 2

**Room:** https://tryhackme.com/room/windowsthreatdetection2

## What This Room Covers

Windows Threat Detection 2 examines common actions after a foothold: system discovery, collection of useful data and transfer of additional tools. These behaviors are often performed with legitimate Windows utilities, so context and sequence matter more than a single command name.

---

## Post-Compromise Objectives

| Activity | ATT&CK Example | Analyst Question |
|---|---|---|
| Account discovery | T1087 | Which users and groups exist? |
| System information discovery | T1082 | What host and OS was compromised? |
| Process discovery | T1057 | Which security and business processes are running? |
| File and directory discovery | T1083 | Where is valuable data stored? |
| Local data collection | T1005 | Which files were opened, copied or staged? |
| Ingress tool transfer | T1105 | Which payload or utility was brought onto the host? |

## Detecting Discovery

Common commands are dual-use: administrators and support tools run them too. Detection should combine command line, user, parent process, working directory, frequency and surrounding activity.

| Behavior | Example Processes or Commands | Useful Evidence |
|---|---|---|
| Identity discovery | `whoami`, `net user`, `net localgroup` | Sysmon 1 / Security 4688 and session context |
| Host discovery | `hostname`, `systeminfo` | Process command line and parent |
| Network discovery | `ipconfig`, `arp`, `route`, `netstat` | Process creation plus related connections |
| Process discovery | `tasklist`, PowerShell process queries | Process creation or PowerShell logs/history |
| File discovery | `dir`, `tree`, PowerShell enumeration | Shell/PowerShell evidence and later file access |

High-confidence context includes a cluster of discovery commands immediately after unusual RDP or phishing execution, especially when launched by an unexpected parent or user.

## Detecting Collection

Collection can involve searching for documents, reading browser or application data, copying files into a staging directory, or compressing material before exfiltration.

Potential signals:

- Rapid access to multiple sensitive paths
- Archive utilities or PowerShell compression after discovery
- New archives in `C:\Users\Public`, `C:\ProgramData` or temporary paths
- File copies from several user profiles into one directory
- Unusual access by a service account or newly compromised user

File creation proves that an artifact appeared, not what it contains or whether it was exfiltrated. Validate the file type, source paths and later network activity.

## Detecting Ingress Tool Transfer

Attackers can download tools using browsers, PowerShell, `curl`, BITS or other built-in utilities. A useful transfer chain is:

```text
Suspicious command or script
        ↓
DNS query / outbound connection
        ↓
New file written to disk
        ↓
Hash and file metadata
        ↓
Execution or additional staging
```

Review the complete command line, destination path, remote host, initiating user and parent process. If a newly written binary executes, pivot from Sysmon 11 into Sysmon 1 and then into DNS/network events.

## Timeline Workflow

1. Anchor the investigation on the known access session or first suspicious process.
2. Group discovery commands by Logon ID, user and parent shell.
3. Determine what the commands revealed and whether the behavior matches the user's role.
4. Search for files created, copied or compressed after discovery.
5. Trace downloads through DNS, network, file and process telemetry.
6. Hash suspicious artifacts and preserve them according to incident procedures.
7. Document what was discovered, what was collected and whether transfer or execution is confirmed.

## Detection Pitfalls

- Alerting on a single administrative command without context
- Assuming compression proves exfiltration
- Treating a download as execution without a process event
- Ignoring PowerShell because only one `powershell.exe` launch appears
- Losing the sequence by reviewing each log source independently

## My Takeaway

Post-compromise activity is best recognized as a sequence: learn the environment, locate valuable data, stage it, and obtain more capability. Correlating that sequence is more reliable than treating every legitimate utility as malicious.
