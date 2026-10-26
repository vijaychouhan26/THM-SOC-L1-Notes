# Room — The Greenholt Phish

**Room:** https://tryhackme.com/room/phishingemails5fgjlzxc

## What This Room Covers

The Greenholt Phish is part of the SOC Level 1 Phishing Analysis module. It focuses on investigating suspicious emails from raw headers and message bodies through safe enrichment, authentication checks, and campaign-level response.

---

## What This Room Covers

A challenge in which the analyst examines a malicious email and extracts evidence from message structure and content. The goal is to apply the earlier rooms' methods without relying on visual appearance.

## Investigation Workflow

1. Open the supplied email artifact in the isolated lab.
2. Record sender, recipient, subject, Date, Message-ID and any Reply-To mismatch.
3. Examine original headers and identify origin-related fields carefully.
4. Inspect HTML links, embedded references and attachment metadata.
5. Extract indicators and **defang** active links in notes.
6. Check enrichment only through approved tools.
7. Explain which observations support a malicious verdict.

## Evidence to Preserve

| Evidence | Why It Matters |
|---|---|
| Full headers | Claimed sender and transmission metadata |
| Body source | Actual link destinations and hidden references |
| Attachment name/type/hash | Potential delivery mechanism |
| Timestamp with timezone | Correlation with surrounding activity |
| Reputation lookup time | Context for any verdict |

## Important Analyst Distinctions

- **Malicious email confirmed** does not imply **recipient device compromised**.
- A sender's display name cannot establish authorship.
- An IP from an untrusted header needs independent validation.
- An attachment being present is not evidence it was launched.

## Reporting Format

**Five Ws:** Who was targeted? What did the email ask the user to do? When was it sent/delivered? Where did links lead? Why is it suspicious? Add **How** the attack attempted to work and which facts remain unverified.

## My Takeaway

The challenge exercises disciplined email-source investigation. I should be able to defend each conclusion using the specific header, URL or file observation that supports it.

*Room-specific flags and my personal findings are intentionally not claimed without the original lab evidence.*
