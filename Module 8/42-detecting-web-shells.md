# Room — Detecting Web Shells

**Room:** https://tryhackme.com/room/detectingwebshells

## What This Room Covers

Detecting Web Shells is part of the SOC Level 1 Web Security Monitoring module. It focuses on this module teaches defenders to interpret HTTP and server-side evidence to identify attempted web exploitation, malicious uploads, web shells and denial-of-service activity.

---

## What Is a Web Shell?

A web shell is a script or executable planted on a web server to permit remote actions via web requests. Detecting one requires combining application logs, file-system evidence and process telemetry.

## High-Signal Indicators

| Source | Suspicious Clue |
|---|---|
| File system | New .php/.aspx/.jsp files in unexpected upload locations |
| Access logs | Repeated POST requests to obscure script paths |
| Web server logs | Requests for a recently created executable endpoint |
| EDR / process tree | Web worker spawning `cmd.exe`, `powershell.exe` or a shell |
| Network telemetry | Unusual outbound connections from the web host |
| File integrity monitoring | Unauthorized changes to public web directories |

## Typical Attack Sequence

```text
Insecure upload or RCE
          ↓
Unexpected server-side file
          ↓
HTTP request to that script
          ↓
Web-server process spawns commands
          ↓
Additional persistence or network activity
```

Not all web shells follow the same chain; look for verified evidence at each stage.

## SOC Investigation Workflow

1. Identify suspect URL and first observed request.
2. Review upload requests and web server response codes.
3. Check file creation time, owner, permissions and hash.
4. Inspect related web requests and user/session identity.
5. Review parent-child processes and outbound connections.
6. Preserve the artifact; **do not execute it** during triage.
7. Recommend isolation and eradication through approved IR procedures.

## Detection Pitfalls

- A new PHP file may be part of legitimate deployment.
- HTTP 200 on a script endpoint proves a response, not necessarily command execution.
- Attackers may masquerade as normal scripts or avoid leaving an obvious file.

## Key Terms

| Term | Meaning |
|---|---|
| Web shell | Server-side remote-access script |
| RCE | Remote code execution |
| FIM | File Integrity Monitoring |
| Process tree | Parent/child process lineage |
| Persistence | Mechanism to retain access |

## My Takeaway

The strongest web-shell case links **upload or write → file creation → HTTP access → server process behavior** rather than classifying a strange filename alone.
