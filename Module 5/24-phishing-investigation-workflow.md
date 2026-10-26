# Phishing Investigation Workflow

## Scenario

An employee reports an email asking them to sign in through a link to prevent account suspension. Treat this as a **hypothetical training example**, not a completed TryHackMe case.

## Investigation

1. **Scope:** Determine recipients, delivery time, subject and message ID.
2. **Preserve:** Save raw message, relevant mail logs and sanitized indicators.
3. **Analyze:** Compare sender identities; inspect SPF/DKIM/DMARC and URL destination via safe analysis methods.
4. **Correlate:** Search DNS/proxy logs for access and identity logs for unusual logins or MFA activity.
5. **Assess:** Distinguish email delivery, URL click, credential submission and actual unauthorized access.
6. **Respond:** Recommend message removal, URL blocking, account reset, token/session revocation or endpoint isolation only as evidence and authorization justify.
7. **Report:** State observed facts, gaps, severity, confidence and next steps.

## Example searches

### Splunk (field names depend on data source)

```spl
index=mail recipient="employee@example.com"
| table _time sender recipient subject message_id action
```

```spl
index=proxy url_domain="suspicious.example"
| stats count by src_ip user action
```

### Analyst questions

- Did the message reach the inbox or get quarantined?
- Did the user click the link?
- Was a credential actually submitted?
- Is there evidence of a new unauthorized session?
- Were other employees targeted?

## Common mistakes

- Calling an account compromised based only on receipt of an email.
- Assuming reputation-service absence means benign.
- Opening suspicious attachments on a normal workstation.
- Publishing private mail content or challenge answers.

## Key takeaway

Use a clear timeline and evidence chain to support an actionable SOC triage decision.
