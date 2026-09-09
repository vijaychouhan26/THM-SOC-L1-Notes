# Room 3 — Humans as Attack Vectors

## What This Room Covers
How attackers exploit people rather than systems — social engineering techniques that bypass technical defenses entirely by targeting human psychology.

---

## Why Humans Are Targeted

Technical defenses like firewalls and antivirus can be patched and updated. Humans cannot be patched. Attackers know that tricking one employee is often faster and easier than breaking through hardened infrastructure.

---

## Main Social Engineering Techniques

| Technique | What It Is | Example |
|-----------|------------|---------|
| **Phishing** | Fake emails designed to steal credentials or deliver malware | Email pretending to be IT asking you to reset your password |
| **Spear Phishing** | Targeted phishing aimed at a specific person using personal details | Email addressing you by name, referencing your company project |
| **Vishing** | Voice phishing — social engineering over phone calls | Caller pretending to be from bank support |
| **Smishing** | Phishing via SMS text messages | Fake delivery notification with a malicious link |
| **Pretexting** | Creating a fake scenario/identity to manipulate the target | Attacker pretending to be an IT technician to get access |
| **Baiting** | Leaving malicious USB drives or offering fake downloads | USB labelled "Salary 2024" left in a parking lot |

---

## How SOC Analysts Detect Human-Based Attacks

- Email gateway alerts on suspicious sender domains or attachments
- SIEM alerts on unusual login times or locations after credential theft
- Endpoint alerts if a malicious payload executes after a phishing click
- User reports — employees flagging suspicious emails or calls

---

## Key Terms

| Term | Definition |
|------|------------|
| Social Engineering | Manipulating people psychologically to gain unauthorized access or information |
| Phishing | Email-based deception to steal credentials or deliver malware |
| Vishing | Voice call-based social engineering |
| Pretexting | Using a fabricated scenario to manipulate a target |
| IOC | Indicator of Compromise — evidence that an attack may have occurred |

---

## My Takeaway
Most breaches start with a human, not a firewall bypass. As a SOC analyst, detecting the *aftermath* of a successful social engineering attack — a strange login, an unusual process, a new scheduled task — is just as important as preventing the attack itself.
