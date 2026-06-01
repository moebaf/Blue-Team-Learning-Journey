# Wireshark Notes
> Date: 2026-05-31

## What is Wireshark?

Wireshark is a free and open-source network protocol analyzer used to capture and inspect network traffic in real time. It is commonly used for network troubleshooting, traffic analysis, incident response, and threat hunting.

## How It Works

1. Select a network interface.
2. Start packet capture.
3. Observe packets in real time.
4. Apply display filters.
5. Inspect packet details.
6. Follow packet streams.
7. Save captures as PCAP files.

## Common Display Filters

### Protocol Filters

```wireshark
icmp
dns
tcp
udp
http
https
telnet
arp
```

### IP Filters

```wireshark
ip.addr == 192.168.1.10
ip.src == 192.168.1.10
ip.dst == 192.168.1.10
```

### Port Filters

```wireshark
tcp.port == 80
udp.port == 53
```

## Operators

| Operator | Meaning |
|-----------|----------|
| == | Equal |
| != | Not Equal |
| && | AND |
| \|\| | OR |
| ! | NOT |
| > | Greater Than |
| < | Less Than |

## Common Ports

| Port | Protocol | Purpose |
|------|----------|----------|
| 20 | FTP Data | File Transfer |
| 21 | FTP Control | FTP Authentication |
| 22 | SSH | Secure Remote Access |
| 23 | Telnet | Unencrypted Remote Access |
| 53 | DNS | Name Resolution |
| 80 | HTTP | Web Traffic |
| 88 | Kerberos | Authentication |
| 123 | NTP | Time Synchronization |
| 135 | MS RPC | Windows Services |
| 139 | NetBIOS | File Sharing |
| 389 | LDAP | Directory Services |
| 443 | HTTPS | Secure Web Traffic |
| 445 | SMB | File Sharing |
| 3389 | RDP | Remote Desktop |
| 3306 | MySQL | Database Traffic |
| 5432 | PostgreSQL | Database Traffic |
| 5900 | VNC | Remote Desktop |
| 8080 | Alternate HTTP | Web Applications |
