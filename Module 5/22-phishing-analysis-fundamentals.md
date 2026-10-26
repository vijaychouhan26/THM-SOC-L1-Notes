# Room — Phishing Analysis Fundamentals

**Room:** https://tryhackme.com/room/phishingemails1tryoe

## What This Room Covers

Phishing Analysis Fundamentals is part of the SOC Level 1 Phishing Analysis module. It focuses on investigating suspicious emails from raw headers and message bodies through safe enrichment, authentication checks, and campaign-level response.

---

## Email Delivery and Structure

A mailbox address consists of a local part, an @ sign, and a domain. **SMTP** transfers messages between clients and mail servers; **IMAP** synchronizes mailbox contents, while **POP3** generally downloads messages. DNS **MX records** help identify the recipient domain's mail infrastructure.

An email has **headers** (metadata and routing) and a **body** (plain text or HTML). MIME structures may also contain attachments.

## Email Header Investigation

| Header | What I Check |
|---|---|
| From | Claimed sender; display name is not proof of identity |
| To / Cc | Intended recipients and campaign scope |
| Reply-To | Is the response redirected to a different mailbox? |
| Return-Path | Envelope/bounce identity; compare with From |
| Received | Mail delivery hops; trust boundaries are important |
| X-Originating-IP | Origin indicator, if present and trustworthy |
| Authentication-Results | SPF/DKIM/DMARC evaluation from the receiving system |
| Content-Type | Text, HTML, or multipart attachment structure |

**In the lab:** Open an .eml sample in Thunderbird, then **View → Message Source** (Ctrl+U). Inspect headers, HTML links and MIME attachment metadata without executing content.

## Phishing Indicators

- Brand spoofing and mismatched sender domains
- A link whose displayed text hides a different destination
- Unexpected attachments or double extensions such as `invoice.pdf.exe`
- Urgent requests to reveal credentials or approve MFA requests
- Encoded attachment data, which is normal MIME behavior but still needs scrutiny

**Defanging:** write `hxxps://login[.]example[.]test` in reports rather than an active suspicious URL.

## Key Terms

| Term | Meaning |
|---|---|
| MIME | Standard for email body types and attachments |
| SMTP | Sending and relaying mail |
| IMAP | Mailbox synchronization |
| BEC | Business email compromise, often involving legitimate compromised mailboxes |
| Phishing | Deceptive message attempting to induce harmful action |

## My Takeaway

Before deciding an email is malicious, I need to inspect its raw source and separate what the sender **claims** from what the delivery metadata actually proves.
