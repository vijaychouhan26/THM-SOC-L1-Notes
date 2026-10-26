# Room — Phishing Prevention

**Room:** https://tryhackme.com/room/phishingemails4gkxh

## What This Room Covers

Phishing Prevention is part of the SOC Level 1 Phishing Analysis module. It focuses on investigating suspicious emails from raw headers and message bodies through safe enrichment, authentication checks, and campaign-level response.

---

## Defence-in-Depth for Email

Prevention combines domain authentication, filtering, secure clients, awareness and rapid response. No single control blocks every attempt.

## Email Authentication

| Control | What It Checks | Important Limitation |
|---|---|---|
| SPF | Authorized sending servers for the envelope sender domain | Mail forwarding and alignment can complicate results |
| DKIM | Cryptographic signature of selected headers/body | Signed mail can still be malicious |
| DMARC | SPF or DKIM alignment with visible From plus domain policy | Correct setup does not prevent compromised accounts |
| S/MIME | Email signing and encryption where configured | It does not validate the content's business intent |

DMARC policies are commonly `none` (monitor), `quarantine` and `reject`, but enforcement depends on the receiving service.

## Email Security Controls

- Secure email gateways and anti-spam/anti-malware filtering
- Attachment detonation in approved sandboxes
- URL rewriting and time-of-click inspection
- MFA and strong conditional-access controls
- User reporting buttons and phishing-awareness exercises
- Restricting macro/script execution and patching endpoints
- Monitoring mail forwarding rules and suspicious sign-in activity

## Investigating SMTP Responses

SMTP replies provide delivery context. **2xx** usually means success, **4xx** temporary failure, and **5xx** permanent failure. A successful delivery response does not prove that the recipient viewed or clicked the email.

## SOC Response Playbook

1. Identify sender, Message-ID, malicious links and recipient scope.
2. Search mail gateway logs for matching delivered messages.
3. Quarantine/remove malicious mail where authorized.
4. Search proxy, DNS, endpoint and identity logs for interaction.
5. Escalate any confirmed credential exposure, session hijack or execution.
6. Propose blocking and detection improvements based on findings.

## My Takeaway

SPF, DKIM and DMARC help authenticate sending identity; SOC triage must still establish content risk and whether any recipient or endpoint was actually affected.
