# Phishing Fundamentals

## What is phishing?

Phishing is a social-engineering technique that uses deceptive messages to induce a victim to disclose information, open malicious content, transfer money or take another harmful action.

## Common types

| Type | Meaning | Analyst clue |
|---|---|---|
| Bulk phishing | Mass-distributed deceptive messages | Reused template across recipients |
| Spear phishing | Targeted message | Context tailored to person/team |
| Whaling | Targets senior staff | Executive impersonation |
| Smishing | SMS phishing | Short links and urgent text |
| Vishing | Voice phishing | Caller impersonation |
| Business email compromise (BEC) | Impersonation or takeover to redirect business activity | Payment change or sensitive-data request |

## Initial triage

1. Preserve the original message including headers and attachments.
2. Note sender, recipient, subject, timestamp, message ID and reported user action.
3. Inspect sender identity, reply-to address, domains, links and attachment names.
4. Review authentication results and known-good business context.
5. Search for other recipients and any clicks, downloads, sign-ins or endpoint alerts.
6. Record a verdict with confidence and escalation criteria.

## Indicators versus evidence

An urgent tone or misspelled domain is suspicious but not proof of compromise. A successful sign-in from an attacker-controlled endpoint, confirmed credential submission, or malicious process execution requires corroborating telemetry.

## Key takeaway

SOC L1 analysts must separate **attempted phishing**, **confirmed malicious content**, and **confirmed account/endpoint compromise**.
