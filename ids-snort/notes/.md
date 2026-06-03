# Snort IDS Notes

## What is Snort?
Snort is an open-source Intrusion Detection System (IDS) and Intrusion Prevention System (IPS) used to analyze network traffic and detect malicious activity.

### Key Functions
- Traffic and protocol analysis
- Content matching against signatures
- Attack detection and prevention
- Alerting and logging based on rules


## Operational Modes

### Packet Sniffing Mode
- Captures and displays network traffic in real time
- Similar to tools like Wireshark

### Packet Logging Mode
- Saves captured traffic to log files
- Useful for later analysis and investigations

### Network Intrusion Detection (NID) Mode
- Primary operating mode
- Compares traffic against predefined rules
- Generates alerts when threats are detected

---

## Understanding Rules

Rules are the foundation of Snort. Without rules, Snort cannot detect malicious activity.

### Purpose of Rules
- Define what traffic should be monitored
- Identify known attack signatures
- Trigger alerts, logging, or blocking actions

### Rule Sources
- Community Rules
- Registered User Rules (Free)
- Paid Subscriber Rules

---

## Rule Structure

A Snort rule consists of two main parts:

### Rule Header
Defines:
- Action (alert, log, drop, etc.)
- Protocol (TCP, UDP, ICMP)
- Source IP and Port
- Destination IP and Port

### Rule Options
Defines:
- Detection criteria
- Alert messages
- Signature ID (SID)
- Additional rule parameters

---

## Snort Versions

### Snort 2
- Most widely used version
- Large community support
- Extensive documentation

### Snort 3
- Improved performance and scalability
- Modern architecture
- Uses Lua-based configuration
- Different syntax from Snort 2

---

## Snort Workflow

1. Traffic enters the network
2. Packets are captured by Snort
3. Decoders process packet data
4. Detection engine compares traffic against rules
5. Matching traffic triggers alerts or logs

---

## Deployment Scenarios

### IDS Mode
- Connected to a network switch
- Monitors network traffic
- Detects threats without blocking traffic

### IPS Mode
- Positioned at a network choke point
- Usually between the router and switch
- Can actively block or drop malicious traffic

---

## Lab Environment Example

Example setup:
- Kali Linux (Attacker)
- Ubuntu/Linux Target
- Snort Sensor
- Virtual Switch

All systems share the same subnet, allowing Snort to monitor traffic between hosts and detect suspicious activity.
