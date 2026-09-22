# Room — Summit

**Room:** https://tryhackme.com/room/summit

## What This Room Covers

A purple-team practical challenge that applies the Pyramid of Pain through an iterative attacker-versus-defender scenario.

## Scenario

I worked as SOC analyst Sunny at PicoSecure while a simulated penetration tester adapted after each detection. The objective was to identify and block indicators at progressively higher levels of the Pyramid of Pain.

## Round by Round

### Round 1 — Hash
A malicious file was identified by MD5 and blocked. The attacker changed the file slightly, producing a new hash.

### Round 2 — IP Address
A C2 IP was blocked. The attacker moved to a different VPS/IP address.

### Round 3 — Domain
A malicious C2 domain was identified through DNS activity and blocked. The attacker registered another domain.

### Round 4 — Network Artifact
A distinctive HTTP URI pattern was detected. Changing it required modifying and rebuilding the malware.

### Round 5 — Tool Signature
A specific tool was identified through signature/behaviour. Replacing the tool required additional effort.

### Round 6 — TTP
A behavioural detection was created for suspicious PowerShell activity rather than a specific indicator. Changing this behaviour required substantially changing the attack method.

## Key Takeaway

The practical demonstrated how detections based on higher-level behaviour can be more difficult for an attacker to bypass than static indicators.
