# Task 1 — Local Network Port Scan

## Objective
Discover open ports on devices in my local network and analyze potential risks.

## Environment
- OS: Windows
- Tools: Nmap (v7.98), Wireshark (with Npcap)
- Network scanned: `10.38.145.0/24`

## Commands run
- Host discovery:
nmap -sn 10.38.145.0/24 > host_discovery.txt

- TCP SYN (or connect) scan with version detection:
nmap -sS -sV 10.38.145.0/24 -oN scan_results.txt -oA myscan

- Full host scan for gateway:
nmap -sS -p- -sV -O 10.38.145.94 -oN gateway_fullscan.txt -oA gateway_fullscan


## Findings
- Hosts found:
- `10.38.145.94` — gateway/router (MAC redacted)
- `10.38.145.165` — my machine
- Open ports & services (paste exact lines from `scan_results.txt` here; redact MACs):
- Example:
  - `10.38.145.94` — `80/tcp open http`  
  - `10.38.145.165` — `22/tcp open ssh`

## Wireshark evidence
- `scan_capture_summary.txt` — handshake summaries exported from Wireshark (redacted).
- `screenshots/wireshark_handshake.png` — screenshot showing SYN / SYN-ACK.

## Risk assessment & recommendations
- Close unnecessary services or restrict access via Windows Firewall.
- Use key-based SSH authentication and strong passphrases.
- Keep services updated; patch outdated server versions.
- Consider network segmentation and VPN for remote admin ports.

## Files included
- `scan_results.txt` — Nmap output (redacted)
- `myscan.*` — optional Nmap outputs
- `scan_capture_summary.txt` — Wireshark export (redacted)
- `screenshots/` — `ipconfig_output.png`, `nmap_run.png`, `wireshark_handshake.png`

> All scans performed on my own devices within my local network `10.38.145.0/24`.
