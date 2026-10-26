# Room — Data Exfiltration Detection

**Room:** https://tryhackme.com/room/dataexfildetection

## What This Room Covers

Data Exfiltration Detection is part of the SOC Level 1 Network Security Monitoring module. It focuses on this module covers practical defensive monitoring: network visibility, discovery, exfiltration, interception and IDS/Snort-based detection.

---

## What Is Data Exfiltration?

Data exfiltration is the unauthorized transfer of information outside a trusted environment. It can use ordinary channels such as HTTPS, DNS, FTP, email or less common protocols.

## Possible Exfiltration Channels

| Channel | Detection Clues |
|---|---|
| HTTP(S) uploads | Large outbound POST/PUT traffic to unusual destinations |
| DNS tunneling | Many long, unique subdomains or unusual TXT queries |
| FTP/SFTP | Unexpected external file transfers and volume |
| ICMP | Abnormal payload sizes or frequent repeated traffic |
| Cloud storage | High-volume transfers to unfamiliar tenants/accounts |

## Useful Indicators

- Unusually high **outbound bytes** from a host
- Large or frequent transfers outside normal working patterns
- Rare destination domains or IPs
- Repeated DNS requests containing high-entropy subdomains
- Host processes unrelated to expected business workflows
- Matching alerts from DLP, proxy or endpoint protection

## Hypothetical Splunk Search

```spl
index=netflow
| stats sum(bytes_out) as total_out by src_ip dest_ip
| sort -total_out
```

Field availability varies; confirm that `bytes_out` genuinely reflects outbound data from the internal host.

## Investigation Workflow

1. Determine what data transfer occurred and its direction.
2. Quantify bytes and duration.
3. Identify remote infrastructure and source endpoint/process.
4. Compare with backup jobs, scheduled uploads and other legitimate activity.
5. Inspect DNS/HTTP metadata or authorized PCAP where available.
6. Check DLP, data access and identity logs.
7. Escalate if confidential data transfer is likely or confirmed.

## Evidence Versus Conclusion

**Excessive traffic** is an anomaly, not necessarily exfiltration. To establish data theft, seek evidence of the dataset accessed, process responsible, and unauthorized destination or transfer.

## My Takeaway

The best evidence combines network volume with destination context and endpoint/data-access telemetry. I should quantify the transfer rather than describe it merely as “a lot of traffic.”
