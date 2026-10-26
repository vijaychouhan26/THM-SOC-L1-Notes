# Room — NetworkMiner

**Room:** https://tryhackme.com/room/networkminer

## What This Room Covers

NetworkMiner is part of the SOC Level 1 Network Traffic Analysis module. It focuses on learning how to capture, filter and interpret network packets and extract artifacts useful for SOC alert investigations.

---

## What Is NetworkMiner?

NetworkMiner is a passive network forensics tool that can analyze PCAPs and organize extracted evidence by host and session. It complements Wireshark rather than replacing manual packet inspection.

## Important Tabs / Views

| View | Useful Evidence |
|---|---|
| Hosts | IP addresses, hostnames and associated details |
| Sessions | Conversation endpoints and activity |
| DNS | Queried names and responses |
| Files | Extracted transferred objects where supported |
| Credentials | Potentially exposed plaintext authentication data |
| Parameters | Extracted protocol/application parameters |

## Practical PCAP Workflow

1. Load the provided capture into NetworkMiner.
2. Review the **Hosts** view for internal and external systems.
3. Identify suspicious remote endpoints and relevant sessions.
4. Review transferred file metadata, hostnames and DNS information.
5. Cross-check timing and raw packets in Wireshark.
6. Compute SHA-256 hashes for exported objects in the authorized lab.
7. Record the origin of each extracted artifact.

## Example Evidence Table

| Artifact | Source Host | Destination | Why Useful |
|---|---|---|---|
| DNS query | Internal endpoint | DNS resolver | Reveals contacted domain |
| HTTP download | Client | Web server | Potential delivered file |
| Session record | Client | External host | Shows communication timeline |

## Limitations

NetworkMiner cannot reveal application payload protected by TLS without the appropriate authorized decryption material. Exports may contain personal or sensitive information; never upload them publicly without review.

## Key Terms

| Term | Definition |
|---|---|
| Network forensics | Reconstructing activity from network evidence |
| Passive analysis | Inspecting existing traffic without probing systems |
| Artifact | Extracted file, credential, hostname or metadata |
| Session | A related exchange between communicating endpoints |

## My Takeaway

NetworkMiner speeds up artifact discovery, while Wireshark is useful to verify exactly which packets produced that evidence.
