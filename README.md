# VirtualBox Cybersecurity Homelab (Kali + Ubuntu)

Reproducible VirtualBox cybersecurity homelab with Kali Linux and Ubuntu: NAT + Host-Only networking, baseline snapshots, shared folders, and lab-ready documentation.

## Goal
Practice cybersecurity safely in an isolated environment and keep everything reproducible for portfolio/CV use.

## Environment
- Host OS: Windows 11 (16 GB RAM)
- Hypervisor: Oracle VirtualBox
- VMs:
  - Kali Linux (attacker / tooling)
  - Ubuntu Desktop (target / defender)

## Network Topology
Each VM uses **two network adapters**:

### Adapter 1 — NAT (Internet)
Used only for:
- system updates
- downloading tools

### Adapter 2 — Host-Only (Lab Network)
Used for:
- Kali ↔ Ubuntu communication
- scanning/testing **only inside the lab**

## IP Addresses
> Use the **Host-Only** IPs for ping, nmap, ssh, etc.

| Machine | NAT (Internet) | Host-Only (Lab) |
|--------|------------------|-----------------|
| Ubuntu | `10.0.2.15` | `192.168.56.102` |
| Kali  | `10.0.2.X` | `192.168.56.X` |

To check the current IPs on any VM:
```bash
hostname -I
ip a
ip r

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
