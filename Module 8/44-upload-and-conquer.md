# Room — Upload and Conquer

**Room:** https://tryhackme.com/soc-sim/scenarios?scenario=upload-and-conquer&thm-business=true

## What This Room Covers

Upload and Conquer is part of the SOC Level 1 Web Security Monitoring module. It focuses on this module teaches defenders to interpret HTTP and server-side evidence to identify attempted web exploitation, malicious uploads, web shells and denial-of-service activity.

---

## What This Scenario Covers

An SOC Simulator investigation centered on an exposed upload feature in a web application. The analyst must determine whether upload activity represents normal usage, an attempted intrusion or confirmed exploitation.

## Threat Model

A file-upload feature can be dangerous when applications trust filenames, extensions, MIME declarations or save files into executable web directories. SOC monitoring must correlate application, web server and endpoint events.

## Alert Investigation Workflow

1. Read the alert and establish the vulnerable application and upload endpoint.
2. Inspect web requests: user/session, method, target, upload time and server response.
3. Determine the actual file content/type when authorized, not merely extension.
4. Check whether the uploaded file landed in a web-accessible or executable location.
5. Search subsequent GET/POST requests to the uploaded path.
6. Look for file creation, web-server child processes and unusual outbound network traffic.
7. Identify source scope and further suspicious requests.
8. Record verified impact and choose appropriate escalation.

## Evidence Matrix

| Signal | What It Supports | What It Cannot Prove Alone |
|---|---|---|
| POST to upload route | An upload was attempted | File was stored |
| 200 response | Request processed successfully at HTTP layer | File executed |
| New script file | An artifact appeared | It is malicious |
| Request to script | Someone accessed the URL | OS command execution |
| Web worker spawning shell | Potential command execution | Complete attacker objectives |

## Five Ws for the SOC Report

- **Who:** Source account/IP and affected host
- **What:** File upload and observed follow-on actions
- **When:** Evidence-backed ordered timeline with timezone
- **Where:** Application route, server path and destination
- **Why:** Indicators that activity is suspicious or unauthorized
- **How:** Validated mechanism of upload abuse, if established

## Response Considerations

Containment might involve disabling unsafe uploads, blocking verified indicators, isolating affected servers and reviewing persistence. All actions should follow authorized incident response procedures.

## My Takeaway

Upload investigations require separating **attempted upload**, **stored file**, **web access** and **executed payload**. Each escalation claim needs its own evidence.

*No case-specific simulator verdict or challenge answers are claimed without original lab artifacts.*
