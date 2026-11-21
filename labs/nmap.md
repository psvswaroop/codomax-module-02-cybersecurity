# Lab 03 — Nmap Localhost Enumeration

## Aim
Understand how Nmap reports TCP port states and service information on a system you own.

## Authorized example commands
```bash
nmap -sS 127.0.0.1
nmap -sT 127.0.0.1
nmap -sV 127.0.0.1
nmap -p 22,80,443 127.0.0.1
```

Run only against localhost or a target explicitly authorized for testing. SYN scan behaviour and privileges vary by operating system and execution context.

## Interpreting states
- `open`: an application is accepting connections.
- `closed`: the host responds, but no application is listening on that port.
- `filtered`: filtering or network conditions prevent Nmap from determining whether the port is open.

## Illustrative sample (not an actual scan result)
```text
PORT    STATE    SERVICE
22/tcp  closed   ssh
80/tcp  closed   http
443/tcp closed   https
```

Your results will depend on which services are running. Replace this illustrative sample with your own captured output if you execute the lab.
