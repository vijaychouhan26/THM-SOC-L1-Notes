# Room — MITRE

**Room:** https://tryhackme.com/room/mitre

## What Is MITRE ATT&CK?

MITRE ATT&CK is a knowledge base of observed adversary behaviour. It documents tactics, techniques, sub-techniques, mitigations and detections and is used by both offensive and defensive security teams.

## Core Components

### Tactics
The adversary's goal or objective at a stage of activity.

### Techniques
The method used to achieve a tactic. Example: **T1566 — Phishing**.

### Sub-techniques
More specific variations of techniques, such as **T1566.001 — Spearphishing Attachment**.

### Mitigations
Defensive controls that reduce the effectiveness of a technique.

### Detections
Ways to identify when a technique is being used.

## MITRE Tools

| Tool | Purpose |
|---|---|
| ATT&CK Navigator | Visualise and annotate ATT&CK techniques |
| CAR | Detection analytics mapped to ATT&CK |
| MITRE Engage | Adversary engagement, deception and denial |
| D3FEND | Defensive techniques knowledge graph |
| ATT&CK Emulation Plans | Plans based on real adversary behaviour |

## Key Questions

- Phishing technique: **T1566**
- Social-engineering mitigation covered in the room: **M1017 — User Training**
- Executables with the same hash but different names: **Masquerading**

## My Takeaway

MITRE ATT&CK provides a common language for describing adversary behaviour. For SOC work, mapping observed activity to ATT&CK techniques helps structure investigations and detection coverage.
