# Lab 04 — Wireshark TCP Analysis

## Aim
Observe TCP connection establishment and identify common packet patterns.

## Suggested procedure
1. Open Wireshark and select the loopback interface (`lo`) when analysing localhost traffic on Linux.
2. Start a capture.
3. In another terminal, connect to a local service that is already running, for example `curl http://127.0.0.1:8000/` if that local service exists.
4. Stop the capture and apply the display filters below.

## Display filters
```wireshark
tcp.port == 8000
tcp.flags.syn == 1 && tcp.flags.ack == 0
tcp.flags.syn == 1 && tcp.flags.ack == 1
tcp.flags.reset == 1
tcp.analysis.retransmission
```

## What to look for
- Normal handshake: SYN → SYN-ACK → ACK.
- SYN scan against an open port: SYN → SYN-ACK → RST (typical pattern).
- Closed TCP port: SYN → RST-ACK (typical response).
- Retransmission: Wireshark identifies a segment it considers retransmitted.

## Important notes
A packet pattern alone does not prove malicious activity. Retransmissions can result from packet loss or congestion. HTTPS payloads are encrypted.

## Evidence
Attach your own screenshot of the packet list and selected packet details if you perform the capture. Do not label illustrative diagrams or sample results as captured evidence.
