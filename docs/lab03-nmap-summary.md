## Lab 03 — Nmap Scanning (Host-Only)

**Target:** Ubuntu Desktop (Host-Only: `192.168.56.102`)  
> Note: Host-Only IPs may change if DHCP is enabled. Verify with `hostname -I`.

### Initial scan
A fresh Ubuntu install showed no open TCP ports in the default top-1000 scan.

### Change applied
Enabled a realistic service for enumeration:
- Installed and started OpenSSH server (port `22/tcp`)

### Finding
- `22/tcp open` — SSH service detected  
- **Version:** OpenSSH `9.6p1` (Ubuntu package `3ubuntu13.14`)

### Commands used
```bash
# Ubuntu (enable SSH)
sudo apt update
sudo apt install -y openssh-server
sudo systemctl enable --now ssh

# Kali (scan)
sudo nmap -sS -sV -Pn 192.168.56.102 -oN outputs/nmap/03_services_versions.txt
