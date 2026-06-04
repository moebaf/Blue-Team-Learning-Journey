# Suricata IDS Notes

## Overview

Suricata is a free and open-source threat detection engine developed by the Open Information Security Foundation (OISF). It combines multiple security functions into a single platform:

- Intrusion Detection System (IDS)
- Intrusion Prevention System (IPS)
- Network Security Monitoring (NSM)

Suricata analyzes network traffic in real time and compares it against predefined or custom rules to detect suspicious or malicious activity.

---

## How Suricata Works

Suricata captures and inspects network traffic flowing through a network.

### Detection Process

1. Network traffic is captured.
2. Packets are analyzed by the Suricata engine.
3. Traffic is compared against rule sets and signatures.
4. If a match is found:
   - An alert is generated.
   - Relevant information is logged.
   - (In IPS mode) the traffic can be blocked.

### Core Components

- Packet Capture Engine
- Detection Engine
- Rule Sets
- Logging and Alerting System
- Protocol Analysis Engine

---

## Operational Modes

### Passive Mode (IDS)

In Intrusion Detection System mode, Suricata monitors traffic without affecting it.

#### Characteristics

- Detects suspicious activity
- Generates alerts
- Logs events
- Does not block traffic
- Ideal for monitoring and visibility

#### Network Placement

```text
Internet
    |
 Router
    |
 Switch ---- Suricata Sensor
    |
 Internal Hosts
```

The sensor receives a copy of network traffic and analyzes it without interrupting communications.

---

### Active Mode (IPS)

In Intrusion Prevention System mode, Suricata is placed inline with network traffic.

#### Characteristics

- Detects malicious activity
- Generates alerts
- Logs events
- Blocks malicious packets
- Prevents attacks in real time

#### Network Placement

```text
Internet
    |
 Router
    |
 Suricata IPS
    |
 Switch
    |
 Internal Hosts
```

In this configuration all traffic passes through Suricata before reaching internal systems.

---

## Why Suricata is Popular

### Advantages

- Open source and free
- High performance
- Multi-threaded architecture
- Deep packet inspection
- Supports IDS, IPS, and NSM
- Extensive protocol support
- Easy integration with SIEM platforms
- Compatible with many Snort rules

---

## Suricata and Wazuh Integration

Suricata can be integrated with Wazuh to centralize security monitoring.

### Workflow

```text
Network Traffic
       |
    Suricata
       |
 Alerts & Logs
       |
     Wazuh
       |
 Dashboard & Analysis
```

### Benefits

- Centralized log management
- Correlation of security events
- Improved threat visibility
- Faster incident response
- Unified security dashboard

### Example

1. Suricata detects a port scan.
2. An alert is written to the Suricata log.
3. Wazuh collects the alert.
4. The alert appears in the Wazuh dashboard.
5. Security analysts investigate and respond.

---

## Why Ubuntu is Commonly Used

Many labs and deployments use Ubuntu because:

- Easy package installation and updates
- Large community support
- Stable Long-Term Support (LTS) releases
- Extensive documentation
- Simplified dependency management

Ubuntu 20.04 and newer LTS versions are commonly used for Suricata deployments.

---

## Suricata vs Snort

Both Suricata and Snort are network-based IDS/IPS solutions that use rules and signatures to detect threats.

### Similarities

- Signature-based detection
- IDS and IPS capabilities
- Real-time monitoring
- Rule-based alerting
- Similar rule syntax
- Large community support

### Differences

| Feature | Suricata | Snort |
|----------|----------|---------|
| Architecture | Multi-threaded | Traditionally single-threaded |
| Performance | Generally faster | Good but often slower on high-volume networks |
| Protocol Analysis | Strong protocol awareness | Good protocol support |
| Management | Easier for many users | More manual tuning |
| Rule Compatibility | Supports many Snort rules | Native rule format |

### Why Many Blue Teams Prefer Suricata

- Better performance on modern hardware
- Multi-core CPU utilization
- Easier scaling
- Rich protocol analysis
- Strong integration with modern SIEM platforms

---

## Blue Team Use Cases

### Threat Detection

Identify:
- Port scans
- Malware communication
- Exploit attempts
- Brute-force attacks

### Network Monitoring

Monitor:
- Internal traffic
- External connections
- Suspicious protocols
- Unauthorized services

### Incident Response

- Generate alerts for investigations
- Preserve logs for analysis
- Support threat hunting activities

### Security Validation

- Verify security controls
- Test detection rules
- Measure network visibility

---

## Key Takeaways

- Suricata is a powerful open-source IDS, IPS, and NSM platform.
- IDS mode monitors and alerts without blocking traffic.
- IPS mode sits inline and actively blocks malicious traffic.
- Suricata detects threats using rules and signatures.
- It integrates well with Wazuh for centralized monitoring.
- Ubuntu is commonly used due to ease of deployment and management.
- Suricata and Snort are very similar, but Suricata is often preferred for performance and scalability.
