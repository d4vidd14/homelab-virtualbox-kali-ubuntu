## Lab 03 — Nmap Scanning (Host-Only)

**Target:** Ubuntu Desktop (Host-Only: 192.168.56.102)

### Initial scan
A fresh Ubuntu install showed no open TCP ports in the default top-1000 scan.

### Change applied
Enabled a realistic service for enumeration:
- Installed and started OpenSSH server (port 22/tcp)

### Result
### Finding
- **22/tcp open** — SSH service detected
- **Version:** OpenSSH 9.6p1 (Ubuntu package 3ubuntu13.14)

### Why it matters
SSH is a common remote administration service and a typical enumeration/hardening target. Version detection helps identify configuration issues and potential vulnerabilities (in a controlled lab).
