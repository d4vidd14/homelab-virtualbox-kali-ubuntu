## Lab 04 — Netcat Enumeration (Metasploitable2)

**Attacker:** Kali Linux  
**Target:** Metasploitable2 (Host-Only network)

### Goal
Practice manual enumeration using **netcat**:
- Identify open ports with a TCP sweep
- Manually interact with HTTP to grab banners/headers and discover endpoints

### 1) TCP port sweep (20–1023)
Command:
```bash
nc -nvv -w 2 -z 192.168.56.103 20-1023
```

Key findings (example from my run):

Open ports included: 139/tcp, 445/tcp, 512/tcp, 513/tcp, 514/tcp

Evidence:

outputs/netcat/01_port_sweep_20-1023.txt

2) Manual HTTP enumeration (port 80)

Connected and requested / to obtain server info and page content:

Status: HTTP/1.1 200 OK

Server: Apache/2.2.8 (Ubuntu) DAV/2

X-Powered-By: PHP/5.2.4-2ubuntu5.10

Discovered endpoints from the returned HTML (examples): /dvwa/, /mutillidae/, /phpMyAdmin/, /twiki/, /dav/

Evidence:

outputs/netcat/02_http_get_root.txt

Notes
