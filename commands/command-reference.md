# Consolidated Command & Filter Reference

## Linux
```bash
pwd
ls -la
id
getent group
stat FILE
chmod 640 FILE
chown USER:GROUP FILE
ps aux
top
systemctl status SERVICE
```

## DNS / reconnaissance
```bash
dig example.com A
dig example.com AAAA
dig example.com MX
dig example.com NS
nslookup example.com
```

## Nmap — authorized targets only
```bash
nmap -sS 127.0.0.1
nmap -sT 127.0.0.1
nmap -sV 127.0.0.1
nmap -p 22,80,443 127.0.0.1
```

## Wireshark display filters
```wireshark
tcp
udp
dns
icmp
tcp.flags.syn == 1 && tcp.flags.ack == 0
tcp.flags.syn == 1 && tcp.flags.ack == 1
tcp.flags.reset == 1
tcp.analysis.retransmission
tcp.analysis.duplicate_ack
tcp.stream eq 0
```

These commands and filters are references. Execute only within a permitted lab scope.
