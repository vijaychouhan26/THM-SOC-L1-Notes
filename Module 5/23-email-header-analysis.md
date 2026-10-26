# Email Header Analysis

## Header fields

| Field | Purpose |
|---|---|
| From | Displayed sender identity; may be spoofed |
| Reply-To | Address that receives replies |
| Return-Path | Envelope sender used for bounce handling |
| Received | Mail transport hops; evaluate trusted hops carefully |
| Message-ID | Message identifier useful for correlation |
| Authentication-Results | SPF, DKIM and DMARC evaluation by receiving infrastructure |
| Date | Claimed sending time; compare with server timestamps |

## SPF, DKIM and DMARC

- **SPF:** Checks whether the connecting mail server is authorized for the envelope domain.
- **DKIM:** Validates a cryptographic signature over selected message headers/body.
- **DMARC:** Evaluates alignment of SPF or DKIM identifiers with the visible From domain and applies the sender domain's policy.

Passing these checks does **not** guarantee that an email is safe. Compromised legitimate accounts can send authenticated phishing.

## Practical procedure

1. Obtain the original .eml or full raw headers through authorized channels.
2. Read Received headers from the trusted receiving boundary backward; do not blindly trust attacker-added headers.
3. Compare From, Reply-To and Return-Path.
4. Inspect Authentication-Results from your own trusted mail system.
5. Extract URLs and domains without visiting suspicious links directly.
6. Correlate mail gateway events, DNS, proxy and identity-provider logs.
7. Record findings and limitations.

## Evidence worksheet

| Evidence | Value |
|---|---|
| Message-ID | To collect |
| Recipient | To collect |
| Sender domain | To collect |
| SPF/DKIM/DMARC | To verify |
| Suspicious URL/domain | To verify |
| Delivery and user interaction | To verify |

## Key takeaway

Header analysis helps assess sender authenticity, but final classification requires context and corroboration.
