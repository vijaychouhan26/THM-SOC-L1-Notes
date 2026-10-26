# Room — Snapped Phish-ing Line

**Room:** https://tryhackme.com/room/snappedphishingline

## What This Room Covers

Snapped Phish-ing Line is part of the SOC Level 1 Phishing Analysis module. It focuses on investigating suspicious emails from raw headers and message bodies through safe enrichment, authentication checks, and campaign-level response.

---

## What This Room Covers

A phishing campaign investigation challenge: the task is to connect email and URL artifacts into a coherent picture of malicious infrastructure and potential victims.

## Investigation Stages

```text
Suspicious Message
      ↓
Header + Body Analysis
      ↓
Extract Domains / URLs / Files
      ↓
Enrich Indicators Safely
      ↓
Pivot Across Related Infrastructure
      ↓
Assess Campaign Scope and Impact
      ↓
Report Evidence + Recommendations
```

## Pivoting from One Indicator

| Starting Evidence | Next Useful Pivot |
|---|---|
| Redirect URL | Final destination and intermediate domains |
| Sending domain | Domain registration / DNS / mail authentication |
| Attachment hash | Known detections and possible related files |
| Message-ID or subject | Other recipients in mail logs |
| Suspicious landing page | Credential collection indicators and related web telemetry |

## Case-Handling Rules

- Keep **observed artifacts** separate from **inferred attacker infrastructure**.
- Use an isolated browser or approved URL-analysis platform for suspicious pages.
- Do not submit credentials to a live phishing page.
- Record each pivot's source, date and confidence.
- Use destination domains and URLs carefully; shared hosting can create misleading associations.

## Example Case Conclusion Template

**Classification:** Suspected/confirmed phishing campaign.  
**Evidence:** List message metadata and confirmed malicious destinations.  
**Scope:** Count delivered messages and any verified interactions.  
**Impact:** Unknown / attempted credential collection / verified credential misuse.  
**Next action:** Block indicators, search for additional recipients and escalate where evidence warrants.

## My Takeaway

Campaign analysis is about relationships between indicators, not collecting as many reputation hits as possible. The strongest write-up explains the chain from email to infrastructure to observed victim activity.

*Challenge-specific IOCs or completed answers have not been invented.*
