## Lab 03 — Nmap Scanning (Host-Only)

**Target:** Ubuntu Desktop (Host-Only: 192.168.56.102)

### Initial scan
A fresh Ubuntu install showed no open TCP ports in the default top-1000 scan.

### Change applied
Enabled a realistic service for enumeration:
- Installed and started OpenSSH server (port 22/tcp)

### Result
Re-ran Nmap service/version detection to identify exposed services and versions for further enumeration and hardening.
