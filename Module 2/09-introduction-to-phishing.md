# Room — Introduction to Phishing (SOC Simulator)

**Room:** https://tryhackme.com/room/socl1phishing

---

## What This Room Covers

A hands-on SOC Simulator scenario where you investigate real phishing alerts end-to-end — triage, analyze, report, and close. Uses either Splunk or Elastic as the SIEM.

---

## Phishing — Quick Reference

| Type | Method |
|------|--------|
| Phishing | Mass email targeting many victims |
| Spear Phishing | Targeted email using personal details |
| Vishing | Voice call social engineering |
| Smishing | SMS-based phishing |
| Business Email Compromise (BEC) | Impersonating executives or suppliers |

---

## Key Phishing Indicators to Check

**Email headers:**
- SPF: Fail → sending server not authorized for that domain
- DKIM: Fail → email not signed by the domain
- DMARC: Fail → domain policy violated
- Reply-To different from From → classic spoofing sign

**Email body:**
- Urgency language ("act now", "your account will be closed")
- Generic greetings ("Dear Customer")
- Mismatched or suspicious URLs (hover before clicking)
- Unexpected attachments (especially .zip, .exe, .docm)

**Attachments:**
- Archive files (.zip, .rar) — often used to bypass email filters
- Office macros (.docm, .xlsm) — can execute malicious code
- Executables (.exe, .bat) — direct malware delivery

---

## SOC Simulator — Investigation Flow

```
Alert received in SIEM
    ↓
Open alert → read all fields (sender, recipient, subject, attachments, security checks)
    ↓
Check SPF / DKIM / DMARC results
    ↓
Analyze body keywords for social engineering
    ↓
Check attachments — file type, name, hash on VirusTotal
    ↓
Check URLs — paste in VirusTotal / URLScan
    ↓
Write Five Ws report
    ↓
Verdict: True Positive → escalate | False Positive → close with notes
```

---

## What the Simulator Tests

- Identifying True Positive phishing alerts vs False Positives
- Reading SIEM alert fields accurately
- Applying the Five Ws framework to a real phishing scenario
- Making escalation decisions
- Writing a professional alert comment

---

## Key Terms

| Term | Definition |
|------|------------|
| SPF | Sender Policy Framework — validates sending mail server |
| DKIM | DomainKeys Identified Mail — validates email signature |
| DMARC | Domain-based Message Authentication — combines SPF + DKIM policy |
| BEC | Business Email Compromise — impersonating executives via email |
| Header Analysis | Examining email metadata to detect spoofing |
| IOC | Indicator of Compromise — sender IP, domain, attachment hash, URL |

---

## My Takeaway
The simulator makes triage feel real — you're not answering questions, you're making judgment calls on actual alert data. The key skill is reading all available fields before making a verdict. Missing one detail (like a DMARC fail) can mean misclassifying a phishing attack as legitimate.

---

*GitHub: https://github.com/vijaychouhan26/THM-SOC-L1-Notes*
*TryHackMe: https://tryhackme.com/p/Vijaychouhan*
*LinkedIn: https://www.linkedin.com/in/vijay-chouhan-1130632b7/*
