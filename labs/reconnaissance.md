# Lab 02 — Passive and Active Reconnaissance

## Aim
Understand the difference between passive information gathering and direct interaction with a target.

## Passive reconnaissance
Examples include reviewing publicly available domain registration information, public documentation and search-engine-indexed information. Avoid collecting personal or sensitive information unnecessarily.

## DNS information gathering
For a domain you are authorized to investigate:
```bash
dig example.com A
dig example.com AAAA
dig example.com MX
dig example.com NS
nslookup example.com
```

`example.com` is a reserved example domain used for documentation.

## Active reconnaissance
Active reconnaissance directly sends queries or probes to infrastructure. Perform it only within an approved scope. Record the target, authorization, time, commands and results.

## Observation
Record which DNS record type was queried, the response received, the resolver used and any limitations. Do not assume that one DNS response represents the complete infrastructure.
