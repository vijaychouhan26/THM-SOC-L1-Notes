# Room 4 — Systems as Attack Vectors

## What This Room Covers
How attackers exploit technical weaknesses in systems — the non-human side of the attack surface that SOC analysts need to monitor and understand.

---

## Main System Weaknesses Attackers Exploit

| Weakness | What It Means | Real Example |
|----------|--------------|--------------|
| **Unpatched Software** | Software with known vulnerabilities that hasn't been updated | A server running an old Apache version with a public CVE |
| **Misconfigurations** | Systems set up incorrectly, leaving gaps in security | S3 bucket set to public, exposing sensitive files |
| **Default Credentials** | Devices or software shipped with username/password that was never changed | Router still using admin/admin |
| **Exposed Services** | Ports and services open to the internet that shouldn't be | RDP (port 3389) exposed publicly, enabling brute force |

---

## How These Connect to Real Attacks

Attackers use tools like Shodan, Nmap, and port scanners to find exposed services and unpatched systems at scale — before even targeting a specific organization. Once a weakness is found, exploitation can be automated.

The SOC monitors for signs that these weaknesses are being probed or exploited:
- Port scan activity (many connection attempts across ports)
- Failed login spikes (brute force on exposed services)
- Alerts from vulnerability scanners or IDS systems
- Unusual outbound traffic after a system is compromised

---

## Key Terms

| Term | Definition |
|------|------------|
| CVE | Common Vulnerabilities and Exposures — public database of known vulnerabilities |
| Attack Surface | The total number of ways an attacker can try to get in |
| Misconfiguration | An incorrect or insecure system setting that creates a vulnerability |
| Exposed Service | A network service accessible from the internet that shouldn't be |
| Default Credentials | Factory-set username/password that hasn't been changed |

---

## Real-World Connection
During VAPT recon on a target, tools like Nmap and Subfinder reveal exactly these weaknesses — exposed ports, staging environments left public, outdated headers. What this room teaches from a defensive angle maps directly to what recon uncovers from an offensive one. Knowing both sides makes the picture complete.

---

## My Takeaway
Systems don't need a human to click a phishing link to get compromised. A forgotten open port or a never-updated service can be just as dangerous. A good SOC analyst understands the technical attack surface, not just the human one.
