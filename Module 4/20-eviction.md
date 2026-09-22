# Room — Eviction

**Room:** https://tryhackme.com/room/eviction

## What This Room Covers

A hands-on MITRE ATT&CK Navigator practical focused on investigating an APT group's documented TTPs and identifying relevant techniques for a compromised environment.

## Scenario

**Organization:** E-Corp, moving to cloud  
**APT Group:** APT28 (Fancy Bear) — as identified by the room  
**Role:** SOC analyst Sunny

## Investigation

### Step 1 — Find the APT Group
APT28 was located in MITRE ATT&CK's Groups catalogue. Its profile provides associated software, documented techniques and intrusion examples.

### Step 2 — Identify Cloud-Relevant Techniques
The room identifies **T1078.004 — Valid Accounts: Cloud Accounts** as a cloud-relevant technique and associates it with the Ruler tool.

### Step 3 — Load APT28 into ATT&CK Navigator
An ATT&CK Navigator layer can be created for APT28 to visualise its documented techniques.

### Step 4 — Map Techniques to Hunt For
Examples identified in the room:
- **T1078.004** — Valid Accounts: Cloud Accounts
- **T1566** — Phishing
- **T1071** — Application Layer Protocol
- **T1003** — OS Credential Dumping

### Step 5 — Build Detection Priorities
For each technique, consider the logs required, SIEM detections and EDR telemetry. For cloud-account abuse, relevant examples include Azure AD sign-in logs and unusual authentication behaviour.

## ATT&CK Navigator Skills

| Action | Use |
|---|---|
| Load an APT group | Threat Groups → search the APT name |
| Colour-code techniques | Assign scoring to techniques |
| Compare groups | Compare multiple layers |
| Export a layer | JSON or image |
| Filter by platform | Windows, Cloud, Linux, etc. |

## My Takeaway

Eviction showed how ATT&CK Navigator can turn threat intelligence into actionable hunting and detection priorities for a specific environment.
