# Room — Eviction

**Room:** https://tryhackme.com/room/eviction

## What This Room Covers

A hands-on MITRE ATT&CK Navigator practical. You investigate a real APT group's TTPs using the ATT&CK framework and Navigator to identify, map, and hunt for techniques within a compromised environment.

## The Scenario

**Organization:** E-Corp (moving to cloud)  
**APT Group:** APT28 (Fancy Bear) — Russian state-sponsored threat actor, as identified by the room  
**Role:** SOC analyst Sunny

## Investigating APT28 on MITRE ATT&CK

### Step 1 — Find the APT Group
Navigate to the MITRE ATT&CK Groups catalogue and search for APT28 (G0007). The group page shows associated software, documented techniques, and intrusion examples.

### Step 2 — Identify Cloud-Relevant Techniques
The room identifies **T1078.004 — Valid Accounts: Cloud Accounts** as a cloud-relevant technique and associates it with **Ruler**.

### Step 3 — Load APT28 into ATT&CK Navigator
Create a new layer in ATT&CK Navigator and load APT28's technique profile to visualise its documented techniques.

### Step 4 — Map Techniques to Hunt For

- **T1078.004** — Valid Accounts: Cloud Accounts
- **T1566** — Phishing
- **T1071** — Application Layer Protocol
- **T1003** — OS Credential Dumping

### Step 5 — Build Detection Priorities

For each high-priority technique, consider:
- What logs to enable
- What SIEM rules to write
- What to look for in EDR

For cloud-account abuse, relevant examples include Azure AD sign-in logs and unusual authentication behaviour.

## Key ATT&CK Navigator Skills

| Action | How |
|---|---|
| Load an APT group | New Layer → Threat Groups → search APT name |
| Colour-code by frequency | Scoring → assign scores to techniques |
| Compare two groups | Multi-select layers → compare overlap |
| Export layer | Download as JSON or image |
| Filter by platform | Layer controls → Windows/Cloud/Linux |

## My Takeaway

Eviction showed how ATT&CK Navigator can turn threat intelligence into actionable hunting and detection priorities for a specific environment.
