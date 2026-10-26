# Room — Web Security Essentials

**Room:** https://tryhackme.com/room/websecurityessentials

## What This Room Covers

Web Security Essentials is part of the SOC Level 1 Web Security Monitoring module. It focuses on this module teaches defenders to interpret HTTP and server-side evidence to identify attempted web exploitation, malicious uploads, web shells and denial-of-service activity.

---

## How Web Applications Work

A typical web service consists of an **application**, **web server** (such as Apache, Nginx or IIS), and an underlying **host**. The browser sends HTTP requests; the server responds with content, status codes and headers.

## HTTP Basics

| Element | SOC Relevance |
|---|---|
| GET / POST / PUT | Requested action or data submission |
| URL path and query | Endpoint and parameters attacked |
| Status 200 / 302 | Success / redirection; not proof of exploitation |
| Status 401 / 403 | Unauthorized / forbidden |
| Status 404 | Resource not found |
| Status 500 | Application error needing investigation |
| User-Agent | Client identifier; easily forged |
| Cookie / session | Authentication context and possible misuse |

## Defence in Depth

| Layer | Key Controls |
|---|---|
| Application | Secure coding, validation, strong access controls |
| Web server | Logging, WAF, secure configuration, TLS |
| Host | Patching, least privilege, EDR, hardening |
| Network edge | CDN, rate limiting, anti-DDoS, segmentation |

## Important Web Logs

- Access logs: client, request method/URI, status, bytes, time, user agent
- Error logs: failed operations and exceptions
- WAF events: matched rules, action and payload summary
- Reverse-proxy/CDN logs: upstream metadata and request distribution

**Attribution warning:** The logged source IP may be a proxy. Honor `X-Forwarded-For` only from trusted proxies and validated configurations.

## Example Analyst Question

A request to `/admin/login` returns many 401 errors. Is it password guessing, legitimate user mistakes, a vulnerability scan, or an automated health check? Correlate identity logs and client history.

## Key Terms

| Term | Definition |
|---|---|
| WAF | Web Application Firewall |
| CDN | Content Delivery Network |
| HTTP | Web request/response protocol |
| Reverse proxy | Front-end service forwarding requests to applications |
| Hardening | Reducing unnecessary attack surface |

## My Takeaway

To investigate a web alert, I need to understand how the application handles requests and where each security layer records evidence.
