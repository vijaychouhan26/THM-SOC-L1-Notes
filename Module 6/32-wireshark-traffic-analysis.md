# Room — Wireshark: Traffic Analysis

**Room:** https://tryhackme.com/room/wiresharktrafficanalysis

## What This Room Covers

Wireshark: Traffic Analysis is part of the SOC Level 1 Network Traffic Analysis module. It focuses on learning how to capture, filter and interpret network packets and extract artifacts useful for SOC alert investigations.

---

## What This Room Covers

Using Wireshark to recognize network anomalies such as reconnaissance, ARP poisoning, suspicious DNS behavior, unusual ICMP traffic and potential command-and-control activity.

## Attack Patterns

| Pattern | Possible Packet Evidence | Validate Against |
|---|---|---|
| TCP port scan | SYNs to many ports, often many RSTs | Approved scan windows |
| ARP spoofing | Conflicting ARP announcements for gateway IP | Switch/ARP/DHCP records |
| DNS tunneling | Frequent long subdomains, unusual TXT records | Legitimate DNS services |
| ICMP tunneling | Unusual payload sizes or high-frequency requests | Monitoring and diagnostic tools |
| C2 beaconing | Similar connections at repeating intervals | Software update/health checks |

## Example Display Filters

```wireshark
arp
icmp
dns
tcp.flags.syn == 1 && tcp.flags.ack == 0
dns.qry.type == 16
```

**Investigation sequence:** Start from the alert time → isolate involved hosts → identify the protocol → measure frequency and content → compare normal traffic → pivot to endpoint/process evidence.

## TCP Scan Interpretation

SYN packets to multiple ports may represent reconnaissance. However, a **SYN → SYN/ACK → ACK** handshake indicates a completed TCP connection; a **SYN → RST** pattern often indicates refused connection. Capture loss can complicate interpretation.

## ARP Investigation

Compare claims of `gateway-IP is-at MAC` over time. Multiple MAC addresses claiming the same gateway IP deserve investigation, but planned failover and virtual gateways can explain transitions.

## My Takeaway

Traffic patterns generate hypotheses. Reliable SOC analysis demands packet context, a timeline and checks for authorized or expected network activity.
