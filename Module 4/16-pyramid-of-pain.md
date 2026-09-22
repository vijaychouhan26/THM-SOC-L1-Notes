# Room — Pyramid of Pain

**Room:** https://tryhackme.com/room/pyramidofpainax

## What Is the Pyramid of Pain?

The Pyramid of Pain ranks IOCs by how much difficulty blocking them causes an attacker. Higher levels represent indicators that are harder for attackers to change.

## The Six Levels

| Level | Type | Why it matters |
|---|---|---|
| **Hash Values** | MD5, SHA1, SHA256 | Easy to change by modifying a file |
| **IP Addresses** | C2/infrastructure | New infrastructure can be obtained quickly |
| **Domain Names** | C2/phishing domains | Requires registration and replacement |
| **Network & Host Artifacts** | URI patterns, user-agent strings, registry keys, dropped files | Requires changing malware behaviour/components |
| **Tools** | Mimikatz, Cobalt Strike, custom tools | Replacing the tooling is more difficult |
| **TTPs** | Attacker behaviours and techniques | Requires changing how the attack is conducted |

## SOC Analyst Perspective

Lower-level indicators such as hashes and IPs can be useful for immediate blocking, but behavioural detection based on TTPs is harder for an attacker to evade. For example, detecting suspicious PowerShell behaviour can remain useful even when the malware hash changes.

## Key Terms

| Term | Definition |
|---|---|
| IOC | Indicator of Compromise |
| TTP | Tactic, Technique, Procedure |
| C2 | Command and Control |
| Hash | File fingerprint |
| Artifact | Evidence left by malicious activity |

## My Takeaway

The Pyramid of Pain helped me understand why SOC detections should move beyond static indicators toward behaviour and TTP-based detection.
