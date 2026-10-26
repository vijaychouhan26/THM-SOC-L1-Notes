# Room — Phishing Emails in Action

**Room:** https://tryhackme.com/room/phishingemails2rytmuv

## What This Room Covers

Phishing Emails in Action is part of the SOC Level 1 Phishing Analysis module. It focuses on investigating suspicious emails from raw headers and message bodies through safe enrichment, authentication checks, and campaign-level response.

---

## What the Room Demonstrates

The room uses example phishing messages to highlight impersonation, URL manipulation, tracking pixels, credential harvesting, and risky attachments. A convincing logo is never sufficient evidence that the sender is legitimate.

## Social-Engineering Red Flags

| Pattern | What an Analyst Should Check |
|---|---|
| Fake payment or order notice | Verify sender domain and whether recipient made the purchase |
| Shortened URL | Determine redirect destination through safe tooling |
| Branded HTML | Compare actual link target to known official domain |
| Tracking pixel | Inspect externally loaded images and domains |
| Credential collection | Identify the form destination and whether sign-in telemetry shows misuse |
| Unexpected attachment | Inspect file name, extension, type and hash without executing |

## Practical Email Analysis

1. Preserve the original message and its unique Message-ID.
2. Compare **displayed sender** with actual email address and Return-Path.
3. Read the email source to find the real URL in HTML `href` attributes.
4. Look for URL shorteners, redirects, lookalike domains or unusual subdomains.
5. Note attachment MIME types and hashes where safely available.
6. Query other recipients and determine whether anyone interacted with the lure.
7. Form a verdict supported by evidence rather than spelling errors alone.

## Safe URL Handling

A link might display “Cancel Order” while pointing to a different domain. Hovering may reveal it, but use the source or approved isolated tools for inspection. Do not submit private company messages to public reputation websites without authorization.

## SOC Investigation Questions

- Was this merely delivered or did a user click?
- Does a login attempt match the phishing timeline?
- Did mail protections quarantine the message?
- Is the same Message-ID, URL or sender infrastructure present in other alerts?

## My Takeaway

Modern phishing can look professional. The useful evidence is in the real destination, message metadata, related telemetry and user action—not just the appearance of an email.
