# Room — Phishing Unfolding

**Room:** https://tryhackme.com/soc-sim/scenarios?scenario=phishing-unfolding-v2&thm-business=true

## What This Room Covers

Phishing Unfolding is part of the SOC Level 1 Phishing Analysis module. It focuses on investigating suspicious emails from raw headers and message bodies through safe enrichment, authentication checks, and campaign-level response.

---

## What This Room Covers

An SOC Simulator scenario where phishing-related activity unfolds over time. Unlike a static email exercise, a live-style triage requires prioritizing new evidence as it arrives.

## Investigation and Response Flow

1. Open the incoming alert and record its detection time and severity.
2. Review message delivery, sender domain, URL and recipient.
3. Assess whether the employee received, clicked or acted on the message.
4. Pivot into identity, DNS, proxy and endpoint telemetry as available.
5. Look for unusual sign-ins, suspicious redirects, downloads or processes.
6. Escalate confirmed or high-risk signs according to the SOC workflow.
7. Update the ticket when new activity changes confidence or impact.

## Evidence Timeline

| Sequence | Evidence Question |
|---|---|
| Email received | When and to whom was it delivered? |
| URL visited | Was the suspicious destination contacted? |
| Credentials entered | Is there direct evidence or only a click? |
| New login | Does account activity corroborate credential misuse? |
| Response | Which actions were approved and recorded? |

## Classification Discipline

A clicked phishing URL is an important event but does not by itself prove that credentials were stolen. Conversely, a suspicious sign-in after a click may require urgent escalation even before every detail is resolved.

## Example SOC Alert Comment

```text
Alert: Suspicious phishing activity
Observed: [email / URL / identity / endpoint evidence]
Affected user/host: [value]
Timeline: [timestamps with timezone]
Assessment: [TP / FP / inconclusive, with reasons]
Actions taken: [approved actions only]
Next step: [escalation and evidence to collect]
```

## My Takeaway

In a developing case, I need to make timely, evidence-based decisions and document what changed between the initial alert and the final verdict.

*This file documents the scenario workflow, not an unverified personal simulator outcome.*
