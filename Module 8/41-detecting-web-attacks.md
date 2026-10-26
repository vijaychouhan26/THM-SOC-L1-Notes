# Room — Detecting Web Attacks

**Room:** https://tryhackme.com/room/detectingwebattacks

## What This Room Covers

Detecting Web Attacks is part of the SOC Level 1 Web Security Monitoring module. It focuses on this module teaches defenders to interpret HTTP and server-side evidence to identify attempted web exploitation, malicious uploads, web shells and denial-of-service activity.

---

## Web Attacks in Logs

SOC analysts use web access logs, WAF events, PCAPs and application telemetry to detect attempted exploitation.

## Common Patterns

| Attack Type | Possible Evidence | Follow-Up |
|---|---|---|
| SQL injection | SQL-like input in URL/body, DB errors | Was the DB query affected? |
| XSS | Script-like input or encoded payloads | Did client-side execution occur? |
| Path traversal | `../`, encoded traversal sequences | Was a protected file returned? |
| Command injection | Shell metacharacters in inputs | Any child process or command execution? |
| Authentication attacks | Many login failures, source distribution | Any successful unauthorized session? |
| Enumeration | Large volumes of 404/403 paths | Approved scanner or real probing? |

## Example Access Log (Synthetic)

```text
192.0.2.45 - - [27/Oct/2026:10:15:00 +0000] "GET /../../etc/passwd HTTP/1.1" 403 169 "-" "ExampleClient"
```

This shows a request **attempting traversal** and a `403` response, not proof that the file was read.

## Practical Detection Workflow

1. Determine affected application and alert window.
2. Filter by route, method, response status and client.
3. Decode relevant URL encodings before interpreting the pattern.
4. Compare access and WAF logs, looking for blocks versus successful responses.
5. Correlate with server error, database audit and EDR process events.
6. Check other target paths and whether suspicious requests persisted.
7. State attempted attack vs confirmed impact.

## Example Splunk Search (Illustrative)

```spl
index=web
| stats count dc(uri_path) as unique_paths by client_ip status
| sort -count
```

Fields vary by data source. Investigate unusual path diversity and errors rather than assuming a fixed count proves an attack.

## Key Terms

| Term | Meaning |
|---|---|
| SQLi | SQL injection |
| XSS | Cross-site scripting |
| Traversal | Attempts to access unintended file-system paths |
| WAF | Web Application Firewall |
| RCE | Remote code execution |

## My Takeaway

Finding exploit-looking text is only the first step. A convincing case connects the request to a response, any application errors and, when possible, host-level evidence.
