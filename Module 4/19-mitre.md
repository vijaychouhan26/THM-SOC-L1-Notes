# Room — MITRE

**Room:** https://tryhackme.com/room/mitre

## What Is MITRE ATT&CK?

MITRE ATT&CK is a globally accessible knowledge base of real-world adversary behaviours. It documents tactics, techniques, sub-techniques, mitigations and detections and is used by both offensive and defensive security teams.

## Core Components

### Tactics
The "why" — the adversary's goal at each stage.

### Techniques
The "how" — the specific method used to achieve a tactic. Example: **T1566 — Phishing**.

### Sub-techniques
More specific variations of a technique, such as **T1566.001 — Spearphishing Attachment**.

### Mitigations
Defensive controls that reduce the effectiveness of a technique.

### Detections
How to identify when a technique is being used.

## MITRE Tools

| Tool | What It Does |
|---|---|
| **ATT&CK Navigator** | Visualise, annotate, and compare ATT&CK matrices |
| **CAR (Cyber Analytics Repository)** | Detection analytics mapped to ATT&CK techniques |
| **MITRE Engage** | Adversary engagement — deception and denial strategies |
| **D3FEND** | Defensive techniques knowledge graph |
| **AEP (ATT&CK Emulation Plans)** | Step-by-step plans based on real APT behaviour |

## Key Questions Answered

- Phishing technique: **T1566**
- Social-engineering mitigation covered in the room: **M1017 — User Training**
- Executables with the same hash but different names: **Masquerading**

## Key Terms

- APT — Advanced Persistent Threat
- TTP — Tactic, Technique, Procedure
- ATT&CK Navigator — visual ATT&CK matrix tool
- Technique ID — unique identifier such as T1566
- CAR — Cyber Analytics Repository

## My Takeaway

ATT&CK provides a common language for describing adversary behaviour. For SOC work, mapping observed activity to ATT&CK techniques helps structure investigations and detection coverage.
