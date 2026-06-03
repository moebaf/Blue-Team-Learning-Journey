# Wazuh Notes

## Overview

Wazuh is a free and open-source security platform that combines SIEM, XDR, and HIDS capabilities. It helps security teams collect,
analyze, and monitor security data from endpoints, servers, network devices, cloud services, and containers.

---

## What is Wazuh?

Wazuh collects, aggregates, indexes, and analyzes security-related data to detect:

- Intrusions and attacks
- Malware activity
- Vulnerabilities
- Misconfigurations
- Policy violations
- Indicators of Compromise (IOCs)

It transforms raw log data into actionable security insights for Blue Team operations.

---

## Why it Matters for Blue Teams

- Centralized security monitoring
- Real-time threat detection
- Endpoint visibility
- Vulnerability management
- Incident response support
- Regulatory compliance monitoring
- File integrity monitoring
- Security event correlation

---

# Core Components

## 1. Wazuh Agent

A lightweight program installed on endpoints such as:

- Windows systems
- Linux servers
- Virtual machines
- Cloud instances

### Responsibilities

- Collect logs
- Monitor system activity
- Detect malware indicators
- Perform configuration assessments
- Monitor file integrity
- Send data securely to the Wazuh Server

### Agent Daemon

The agent daemon is the background service running on the endpoint.

It is responsible for:

- Monitoring the host
- Collecting security events
- Running security checks
- Sending collected data to the Wazuh Server

---

## 2. Wazuh Server

The central analysis engine of the platform.

### Responsibilities

- Receive data from agents
- Decode and process logs
- Match events against detection rules
- Identify suspicious activity
- Generate alerts
- Correlate security events

The server acts as the brain of the Wazuh environment.

---

## 3. Elastic Stack (ELK)

Wazuh uses the Elastic Stack for storage, searching, and visualization.

### Elasticsearch

- Search engine
- Data indexing
- Long-term storage
- Fast querying of alerts and logs

### Logstash

- Data processing pipeline
- Parses and transforms incoming data

### Kibana

- Web-based dashboard
- Data visualization
- Alert monitoring
- Reporting and investigations

---

# How Wazuh Works

## Workflow

1. Agents collect logs and security events from endpoints.
2. Data is encrypted and sent to the Wazuh Server.
3. The server processes and analyzes the data.
4. Events are matched against predefined rules.
5. Alerts are generated when suspicious activity is detected.
6. Data is indexed and stored in Elasticsearch.
7. Analysts investigate alerts through Kibana dashboards.

---

# Key Features

## Security Analytics & Intrusion Detection

- Detects malicious activity
- Analyzes logs for threats
- Generates security alerts

## File Integrity Monitoring (FIM)

- Tracks changes to important files
- Detects unauthorized modifications
- Alerts on suspicious file activity

## Vulnerability Detection

- Identifies vulnerable software
- Detects outdated packages
- Highlights security weaknesses

## Configuration Assessment

- Evaluates system configurations
- Detects security misconfigurations
- Supports system hardening

## Incident Response

- Supports investigation workflows
- Helps analysts respond to threats

## Log Collection

- Collects logs automatically
- Centralizes security data
- Supports threat hunting activities

## Regulatory Compliance

Supports compliance monitoring for:

- PCI DSS
- HIPAA
- GDPR
- NIST
- CIS Benchmarks

---

# Deployment Models

## All-in-One Deployment

All components are installed on a single machine.

### Advantages

- Easy setup
- Beginner friendly
- Lower resource requirements

### Best For

- Home labs
- Learning environments
- Small organizations

---

## Distributed Deployment

Components are separated across multiple servers.

### Advantages

- Better scalability
- Higher performance
- Improved reliability
- Easier management of large environments

### Why Choose a Distributed Setup?

- Handles larger amounts of data
- Supports more agents
- Prevents a single point of failure
- Improves overall performance

### Best For

- Enterprises
- Large organizations
- High-volume logging environments

---

# Network Device Monitoring

## Can Routers Use Wazuh?

Most routers cannot run a Wazuh agent directly.

Instead, they can:

- Forward Syslog logs
- Send logs to the Wazuh Server
- Be monitored without an installed agent

The same applies to:

- Firewalls
- Switches
- Other network appliances

---

# Agent Communication

## How Do Agents Know What Data to Report?

Agents use configuration files that define:

- Which logs to collect
- Which directories to monitor
- What security checks to perform
- File Integrity Monitoring settings
- Vulnerability scan settings

The Wazuh Server can also push configuration updates to agents.

---

# Log Filtering

## Why Does Wazuh Filter Displayed Logs?

Filtering helps:

- Reduce noise
- Highlight important events
- Improve dashboard performance
- Simplify investigations
- Focus on security-relevant alerts

Without filtering, analysts would be overwhelmed by large volumes of log data.

---

# Practice Environment

## Where Can Beginners Practice Wazuh?

- VirtualBox Labs
- VMware Labs
- Home Lab Environments
- Docker Deployments
- Cloud Test Instances

### Recommended Beginner Lab

- Kali Linux
- Ubuntu Server
- Wazuh All-in-One Deployment

This setup provides a realistic Blue Team environment for monitoring, detection, and investigation.

---

# Key Takeaway

Wazuh provides centralized visibility across endpoints, servers, cloud environments, and network devices.
By collecting and analyzing security data, it helps Blue Teams detect threats, investigate incidents,
manage vulnerabilities, and improve overall security posture.
