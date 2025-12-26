# homelab-virtualbox-kali-ubuntu
Reproducible VirtualBox cybersecurity homelab with Kali Linux and Ubuntu: NAT + Host-Only networking, baseline snapshots, shared folders, and lab-ready documentation.
# VirtualBox Cybersecurity Homelab (Kali + Ubuntu)

This repository documents my local cybersecurity homelab built with VirtualBox.  
The goal is to practice safely in an isolated environment and keep everything reproducible for portfolio/CV use.

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

## Current IP Addresses
> Use the **Host-Only** IPs for ping, nmap, ssh, etc.

| Machine | NAT (Internet) | Host-Only (Lab) |
|--------|------------------|-----------------|
| Ubuntu | `10.0.2.15` | `192.168.56.102` |
| Kali  | (run `hostname -I`) | (run `hostname -I`) |

## Verification Commands
### Check IPs
On both machines:
```bash
hostname -I
ip a
ip r
