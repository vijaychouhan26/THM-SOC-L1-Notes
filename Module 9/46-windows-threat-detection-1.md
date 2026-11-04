# Room — Windows Threat Detection 1

**Room:** https://tryhackme.com/room/windowsthreatdetection1

## What This Room Covers

Windows Threat Detection 1 applies Windows logs to common Initial Access paths: exposed remote services, phishing attachments and infected removable media. The goal is to determine how execution began and which user, session and process chain were involved.

---

## Initial Access Paths

| Access Path | ATT&CK Example | Primary Evidence |
|---|---|---|
| Exposed remote service | T1133 External Remote Services | Authentication, firewall and remote-service logs |
| Public-facing application exploit | T1190 Exploit Public-Facing Application | Application, web, process and network telemetry |
| Phishing attachment or link | T1566 Phishing | Email, browser, file creation and process events |
| Infected removable media | T1091 Replication Through Removable Media | Device, file and process telemetry |

The access mechanism should be proven from evidence. A process launched by `explorer.exe` shows user-driven execution, but it does not by itself distinguish an email attachment, a download or a USB device.

## Detecting RDP Access

```text
Many Security 4625 failures
          ↓ same source/account pattern
Security 4624 success
          ↓ Logon Type 10 and Logon ID
Sysmon 1 processes in that session
```

Useful questions:

- Was the service expected to be Internet-accessible?
- Did failures target one account or many accounts?
- Did a successful Type 10 logon follow the failures?
- Is the source address or workstation expected for that user?
- What processes were created under the successful session's Logon ID?

An RDP success from an unfamiliar address is suspicious, not automatically malicious. Confirm business context and look for follow-on behavior.

## Detecting Phishing Execution

Threat actors may disguise executable formats, use double extensions or place commands behind LNK shortcut files. Windows hiding known extensions can make `invoice.pdf.exe` appear less suspicious to a user.

A useful evidence chain is:

1. Browser or mail client activity near the reported time.
2. Sysmon 11 showing an archive, shortcut, script or executable written to disk.
3. Extraction or movement into a user-writable directory.
4. Sysmon 1 showing execution, often with `explorer.exe` as parent.
5. Child PowerShell, script host or unusual binary activity.
6. Sysmon 22/3 showing suspicious DNS queries or outbound connections.

For an LNK attachment, Explorer may appear to launch the payload directly. The earlier shortcut file-creation event and its target/command are therefore important for proving the delivery mechanism.

## Detecting USB-Based Execution

Removable media attacks may use misleading icons, LNK files, hidden originals or double-extension binaries. Useful indicators include:

- Execution from a removable drive letter
- A suspicious file copied from removable media to a local staging path
- Similar files appearing on additional removable drives
- Explorer spawning an executable from an unusual location
- Follow-on persistence or network traffic

The drive letter alone is not a durable identifier; correlate timestamps, volume/device information and file hashes where available.

## Initial Access Investigation Workflow

1. Start from the first suspicious execution or authentication event.
2. Establish the user and session with account and Logon ID fields.
3. Move backward to find the delivery artifact or failed access attempts.
4. Move forward through the process tree, file writes, DNS and connections.
5. Identify the earliest evidence-supported compromise point.
6. Record whether access was attempted, successful or followed by confirmed execution.
7. Preserve suspicious artifacts without launching them during triage.

## Common Pitfalls

- Treating every 4625 burst as a confirmed brute-force compromise
- Assuming an HTTP download is malicious without examining the artifact and context
- Classifying every LNK or USB-launched file as malware
- Relying on filenames and extensions instead of hashes, paths and behavior
- Skipping the parent process and earlier file-creation events

## My Takeaway

The strongest Initial Access finding explains both delivery and execution. I should trace backward from the suspicious process to the source artifact, then forward into the resulting host and network activity.
