# Room — Phishing Analysis Tools

**Room:** https://tryhackme.com/room/phishingemails3tryoe

## What This Room Covers

Phishing Analysis Tools is part of the SOC Level 1 Phishing Analysis module. It focuses on investigating suspicious emails from raw headers and message bodies through safe enrichment, authentication checks, and campaign-level response.

---

## Why Analysts Use Multiple Tools

One source rarely gives a conclusive answer. Combine original message analysis, passive enrichment, and local environment telemetry, and keep track of what each tool **actually** confirms.

## Common Tools

| Tool | Useful for | Limitation |
|---|---|---|
| CyberChef | Decode Base64, URLs and other encodings | Decoding alone does not establish maliciousness |
| VirusTotal | Reputation for hashes, domains, URLs and IPs | No detections does not mean safe |
| urlscan.io | Browser observations and redirect chains | Public scans may disclose URLs/data |
| WHOIS / RDAP | Domain registration metadata | Privacy masking and recent changes limit attribution |
| PhishTool | Organizing email investigation and header analysis | Findings depend on supplied artifacts |
| SIEM / email gateway | Delivery, click, DNS, proxy and login correlation | Field names depend on environment |

## Evidence Collection Workflow

1. Collect the .eml, headers, Message-ID, attachment name and suspicious URL.
2. Hash an attachment in an isolated lab: `sha256sum suspicious.bin` (Linux).
3. Defang indicators before documenting or sharing them.
4. Search reputation and registration data using approved processes.
5. Look for multiple recipients, DNS lookups, proxy hits and identity sign-ins.
6. Track **timestamp of each lookup** because reputation changes.
7. Write a reasoned verdict and distinguish “unknown” from “benign.”

## Example IOC Table

| Indicator | Source | Reputation | Confirmed in environment? |
|---|---|---|---|
| Domain from HTML link | Raw email | Not yet checked | Unknown |
| SHA-256 attachment | File artifact | Not yet checked | Unknown |
| Recipient address | Mail gateway | Not applicable | Pending |

## Avoiding False Conclusions

- Public reporting can be stale, wrong or absent.
- A recent registration is suspicious in context, not definitive proof.
- A malware hash hit does not prove the attachment executed.
- A web visit does not automatically imply stolen credentials.

## My Takeaway

Tools help with enrichment. An L1 analyst still has to connect the evidence to the organization's logs and state exactly what is known, suspected and unresolved.
