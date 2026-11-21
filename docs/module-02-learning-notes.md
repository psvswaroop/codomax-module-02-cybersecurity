# Module 02 — Learning Notes
## Linux, Security Tools & Reconnaissance

### 1. Linux security fundamentals
Linux organizes information in a hierarchical filesystem. Directories contain files and other directories. Common navigation and inspection commands include `pwd`, `ls -la`, `cd`, `cat` and `find`.

#### Permissions
Linux permissions are defined for the file owner, group and others. The basic permissions are:
- `r` — read
- `w` — write
- `x` — execute

Examples:
- `chmod 600 file` — owner can read/write; group and others have no permissions.
- `chmod 644 file` — owner can read/write; group and others can read.
- `chmod 640 file` — owner can read/write; group can read; others have no access.

`chown` changes ownership. `id` displays user and group identifiers. `getent group GROUPNAME` can look up group information. Apply least privilege: grant only the access required.

#### Users, processes and services
`useradd`, `passwd`, `groupadd` and `usermod` manage local accounts and groups. `ps aux` and `top` help inspect processes. `systemctl status SERVICE` checks a systemd service. Use administrative privileges only when needed.

### 2. Reconnaissance
Reconnaissance is information gathering performed before a security assessment.

- **Passive reconnaissance:** uses information already publicly available without directly probing the target systems.
- **Active reconnaissance:** directly interacts with target infrastructure, such as DNS queries, host discovery or port scans. It requires authorization.

DNS records commonly encountered:
- `A` — hostname to IPv4 address.
- `AAAA` — hostname to IPv6 address.
- `MX` — mail exchange servers.
- `NS` — authoritative name servers.
- `TXT` — text data, often used for verification and email security policies.
- `CNAME` — alias to another hostname.

WHOIS and DNS tools can help collect domain registration and DNS information. Results can be incomplete, privacy-protected or out of date.

### 3. Nmap
Nmap discovers hosts, ports and services. Examples:
- `nmap -sS 127.0.0.1` — TCP SYN scan of localhost (where supported and authorized).
- `nmap -sT 127.0.0.1` — TCP connect scan.
- `nmap -sV 127.0.0.1` — attempts service/version detection.
- `nmap -p 22,80,443 127.0.0.1` — scans selected TCP ports.
- `nmap -p- 127.0.0.1` — scans all TCP ports.

A port reported as `open` has an application accepting connections; `closed` means the host responded but no application is listening; `filtered` means Nmap cannot determine the state because filtering or network conditions prevent a clear response. Service/version identification is a probe-based estimate, not a guarantee.

### 4. Wireshark
Wireshark captures and analyses packets. A capture filter controls what is captured; a display filter controls which already-captured packets are shown.

Useful display filters:
```wireshark
tcp
udp
dns
icmp
tcp.flags.syn == 1 && tcp.flags.ack == 0
tcp.flags.syn == 1 && tcp.flags.ack == 1
tcp.flags.reset == 1
tcp.analysis.retransmission
tcp.stream eq 0
```

A TCP three-way handshake is:
1. Client sends SYN.
2. Server replies SYN-ACK.
3. Client sends ACK.

The connection is established when the server receives and processes the final ACK. A SYN scan commonly sends SYN, receives SYN-ACK from an open port, then sends RST rather than completing the handshake. A closed port commonly responds with RST-ACK.

`Follow TCP Stream` displays the data exchanged in a selected TCP conversation. HTTPS application content is encrypted unless suitable decryption keys and configuration are available.

### 5. Burp Suite
Burp Suite is an intercepting proxy used for web application security testing.
- **Proxy:** intercepts and inspects HTTP/S requests and responses.
- **Repeater:** manually edits and resends requests.
- **Intruder:** automates customized request variations.
- **Decoder:** encodes/decodes data.
- **Comparer:** compares data.

Use a local training application or an application for which testing is explicitly authorized. Do not test real accounts or third-party websites without permission.

### 6. OWASP ZAP
OWASP ZAP is an open-source web application security testing proxy.
- **Passive scan:** analyses observed traffic without sending attack payloads.
- **Active scan:** sends test requests to identify potential vulnerabilities and can affect the application.
- **Spider/crawler:** discovers pages and endpoints.
- **Alerts:** reports potential issues for manual validation.

An alert is not automatically a confirmed vulnerability. Validate findings, assess impact and document evidence.

### 7. Analyst mindset
A large number of SYN packets across many ports may indicate port scanning, but can also have benign explanations. Retransmissions may indicate packet loss or congestion. Always correlate timestamps, endpoints, packet direction, application context and other evidence before concluding that activity is malicious.
