# Room — Cyber Kill Chain

**Room:** https://tryhackme.com/room/cyberkillchainzmt

## What Is the Cyber Kill Chain?

The Cyber Kill Chain, developed by Lockheed Martin, models a cyberattack from reconnaissance through the attacker's final objective. Defenders can use the stages to identify where an attack can be detected or disrupted.

## The 7 Stages

| # | Stage | Attacker Activity |
|---|---|---|
| 1 | Reconnaissance | Gathers information about the target |
| 2 | Weaponization | Creates a malicious payload |
| 3 | Delivery | Delivers the payload |
| 4 | Exploitation | Triggers exploitation or execution |
| 5 | Installation | Establishes malware/persistence |
| 6 | Command & Control | Communicates with attacker infrastructure |
| 7 | Actions on Objectives | Performs the intended goal |

## How SOC Analysts Use It

A detected phishing email can indicate Delivery, malware execution can indicate Exploitation or Installation, outbound C2 can indicate Command & Control, and unusual large outbound transfers can indicate Actions on Objectives.

## Key Terms

- Kill Chain
- Reconnaissance
- Weaponization
- Command & Control
- Persistence
- Lateral Movement

## My Takeaway

The framework helps shift an investigation from simply asking whether activity is malicious to asking where the attacker is in the attack lifecycle and what should be investigated next.
