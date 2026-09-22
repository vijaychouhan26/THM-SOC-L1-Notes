# Room — Summit

**Room:** https://tryhackme.com/room/summit

## What This Room Covers

A purple-team practical challenge. You work as a SOC analyst alongside a penetration tester in an iterative scenario — the attacker tries different techniques, you detect and block them, pushing them higher up the Pyramid of Pain until they give up.

## The Scenario

You are SOC analyst **Sunny** at **PicoSecure**. A pen tester simulates an adversary and adapts after each block. The objective is to identify and block indicators at progressively higher levels of the Pyramid of Pain.

## Round by Round — Pyramid of Pain in Action

### Round 1 — Hash (MD5)
A malicious file is identified by its MD5 hash and blocked. The attacker recompiles it with a minor change, creating a new hash.

**Lesson:** Hash blocking is easy to bypass.

### Round 2 — IP Address
A C2 IP is identified and blocked at the firewall. The attacker moves to a new VPS/IP.

**Lesson:** IP blocking can buy time but is relatively easy to evade.

### Round 3 — Domain
A malicious C2 domain is identified through DNS activity and blocked. The attacker registers another domain.

**Lesson:** Domain replacement costs time and money but remains practical.

### Round 4 — Network Artifact
A distinctive HTTP URI pattern is detected. Changing it requires modifying and rebuilding the malware.

**Lesson:** Network artifacts are more difficult to change.

### Round 5 — Tool Signature
A specific tool is identified through signature or behaviour and blocked.

**Lesson:** Replacing the tooling requires more effort.

### Round 6 — TTP
A behavioural detection is created for suspicious PowerShell activity rather than a specific indicator.

**Lesson:** Changing the underlying behaviour requires substantially changing the attack method.

## Key Takeaway

The practical demonstrated how detections based on higher-level behaviour can be more difficult for an attacker to bypass than static indicators.
