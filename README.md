# Wireshark Packet Capture Analysis — README

## Overview
This repository documents the results of analyzing a **Wireshark capture (`wireshark_capture.pcap`)**, which was recorded and provided in the form of a screen recording. The goal was to observe captured traffic, interpret packet-level behavior, and highlight notable findings.

---

## Contents
- `wireshark_capture.pcap` — The raw packet capture file (to be included in the repo).
- `wireshark_report_detailed.pdf` — Detailed PDF report with objectives, methodology, findings, and recommendations.
- `screenshots/` or `frames/` — Extracted frames/screenshots from the recording showing Wireshark interface and captured packets.
- `README.md` — This file.

---

## Environment
- **Tool:** Wireshark (GUI packet capture analyzer)
- **Capture file:** `wireshark_capture.pcap`
- **Source:** Screen recording evidence (converted into frames for analysis)
- **Network:** Local machine/VM network traffic during scan/testing

---

## Findings (example based on capture)
From the observed Wireshark session in the recording:
- **Traffic Type:** Both TCP and UDP packets were visible.
- **Protocols Identified:** HTTP, DNS, TCP handshakes, and ICMP packets.
- **Notable Activity:**
  - DNS queries resolving domain names.
  - TCP 3-way handshake showing host communication establishment.
  - HTTP requests sent to a web server (port 80).
- **Timing:** Packets captured during a live scan session around `2025-09-14`.

---

## Security Significance
- **Cleartext Traffic:** HTTP packets in capture were unencrypted → sensitive data could be exposed.
- **Recon Evidence:** DNS queries reveal domains accessed by the system, useful for attackers in profiling.
- **TCP Analysis:** Handshakes confirm host connectivity and open ports.
- **Best Practice:** Sensitive traffic should be encrypted using HTTPS/TLS, and captures restricted to authorized environments only.

---

## Recommendations
1. Use **encrypted protocols** (HTTPS, SSH) instead of HTTP/telnet to avoid plain-text data exposure.
2. Limit unnecessary DNS queries and secure DNS with DNSSEC if possible.
3. Monitor packet captures for **suspicious IPs or unusual traffic patterns**.
4. Use Wireshark filters (e.g., `http`, `tcp.port==80`, `dns`) to quickly narrow down relevant traffic.
5. Store `.pcap` files securely as they may contain sensitive information.

---

## Deliverables for GitHub
1. `wireshark_capture.pcap` — Raw capture file.
2. `README.md` — This documentation file.
3. `screenshots/frames/` — Extracted frames or screenshots from the Wireshark session.
4. `wireshark_report_detailed.pdf` — Full detailed report with findings and recommendations.
5. *(Optional)* `demo_video.mp4` — The original screen recording of the Wireshark session.

---

## Quick Reproduction Steps
1. Open the capture file in Wireshark:
   ```bash
   wireshark wireshark_capture.pcap
   ```
2. Apply filters to analyze specific traffic (examples):
   - `http` → Show only HTTP packets
   - `dns` → Show DNS queries/responses
   - `tcp.handshake` → Show TCP handshakes
3. Export packet details as `.txt` or `.csv` for documentation.
4. Document results and include screenshots in your submission.


