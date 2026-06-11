# Suricata Labs
> Date: 2026-06-04

## Overview

This lab documents the installation, configuration, testing, and integration of Suricata IDS with Wazuh SIEM.

---

# Lab 1 - Installing and Managing Suricata

After installing Suricata on my Kali Linux machine, I verified that the service could be started, stopped, and monitored using systemd.

### Service Management

```bash
sudo systemctl start suricata
sudo systemctl stop suricata
sudo systemctl status suricata
```

<img width="1912" height="741" alt="image" src="https://github.com/user-attachments/assets/9db5a5c9-8d88-479c-bfd4-017e8ea734a2" />

### What I Learned
- How to manage the Suricata service
- How to verify whether the IDS is running correctly

---

# Lab 2 - Exploring the Configuration Files

I located the Suricata configuration files.

```bash
ls -al /etc/suricata
```

<img width="344" height="107" alt="image" src="https://github.com/user-attachments/assets/c0e001a6-4ce6-475f-bc96-7b370b76ef8a" />

### What I Learned
- Suricata stores its configuration files under `/etc/suricata`
- The main configuration file is `suricata.yaml`

---

# Lab 3 - Configuring HOME_NET

I identified my local network address using `ip a` and updated the `HOME_NET` variable inside `suricata.yaml`.

This allows Suricata to understand which network should be considered internal and monitored.

<img width="419" height="358" alt="image" src="https://github.com/user-attachments/assets/1f162c38-dc32-4bfa-a3be-31ac11c6c1c8" />

### What I Learned
- The importance of correctly defining the internal network
- How HOME_NET affects rule matching and alerting

---

# Lab 4 - Verifying the Monitoring Interface

Next, I verified that the interface configured under the `af-packet` section matched my active network interface.

I checked my interface using:

```bash
ip a
```

Then searched for:

```bash
/af-packet
```

inside `suricata.yaml`.

<img width="506" height="272" alt="image" src="https://github.com/user-attachments/assets/a09d8b9c-41e5-482f-9f21-2d790d9d037f" />

### What I Learned
- How Suricata captures traffic from a network interface
- Why interface configuration is critical for packet inspection

---

# Lab 5 - Updating Detection Rules

I updated Suricata to download the latest detection signatures.

<img width="724" height="397" alt="image" src="https://github.com/user-attachments/assets/cacf2672-618e-44aa-bb59-f60874579979" />

To view available rule sources:

```bash
suricata-update list-sources
```

<img width="1115" height="786" alt="image" src="https://github.com/user-attachments/assets/c0f87cc4-0c6c-4cf5-95be-f322d8deeddd" />

### What I Learned
- How to keep Suricata signatures updated
- How community and vendor rule sources are managed

---

# Lab 6 - Running Suricata

I ran Suricata in verbose mode to observe startup activity.

<img width="1867" height="400" alt="image" src="https://github.com/user-attachments/assets/8764432a-48f7-42b6-b030-ecd5608e8545" />

I then started the service so it could continue monitoring traffic in the background.

<img width="1564" height="475" alt="image" src="https://github.com/user-attachments/assets/684f8146-6972-48b9-9ac0-384e26e34fe5" />

<img width="386" height="119" alt="image" src="https://github.com/user-attachments/assets/7acc33aa-1643-45dd-adfb-e8016490fc94" />

### Important Log Files

- `fast.log` – Human-readable alert format
- `eve.json` – Structured JSON format for SIEM integration

### What I Learned
- How Suricata generates alerts
- The difference between `fast.log` and `eve.json`

---

# Lab 7 - Testing IDS Functionality

To confirm that Suricata was capturing events correctly, I generated test traffic.

<img width="286" height="47" alt="image" src="https://github.com/user-attachments/assets/e5500078-3e2d-4201-ba5c-27c2a21d2c01" />

<img width="956" height="378" alt="image" src="https://github.com/user-attachments/assets/b32a5c35-1c26-4cd2-a62e-6aae2a832fea" />

### Results

The alerts confirmed that Suricata was actively monitoring network traffic and generating detections.

### What I Learned
- How to validate IDS functionality
- How alerts are generated and logged

---

# Lab 8 - Creating a Custom Rule

To better understand how Suricata rules work, I created a custom rule that generates an alert whenever ICMP ping traffic is detected.

### Creating the Rule File

```bash
sudo vim /etc/suricata/rules/local.rules
```

### Custom ICMP Alert Rule

<img width="970" height="67" alt="image" src="https://github.com/user-attachments/assets/8948f777-d68d-4d60-bc0e-a524f9784586" />

After creating the rule, I enabled it inside `suricata.yaml`.

<img width="919" height="439" alt="image" src="https://github.com/user-attachments/assets/d09b1615-e81e-48fa-abd2-44bfb59dd446" />

### Testing the Rule

I sent ICMP ping packets to my home router.

<img width="829" height="337" alt="image" src="https://github.com/user-attachments/assets/14e63092-abae-46af-a624-24bd3031cb0d" />

### Alert Generated

<img width="1912" height="475" alt="image" src="https://github.com/user-attachments/assets/cec4bd4a-759c-4fa7-8134-cf009bd1fec5" />

### What I Learned
- How Suricata rules are structured
- How custom detections can be created
- How to test rule functionality

---

# Lab 9 - Integrating Suricata with Wazuh SIEM

To centralize alerts and improve visibility, I integrated Suricata with Wazuh.

### Wazuh Server

<img width="1918" height="910" alt="image" src="https://github.com/user-attachments/assets/7dced210-ef96-4a28-9372-ccd67881ba55" />

### Ubuntu Server Hosting Wazuh

<img width="1626" height="868" alt="image" src="https://github.com/user-attachments/assets/7dc908ff-d3f0-4b25-8ffa-8933df16f9b3" />

### Configuring Wazuh

I edited the Wazuh manager configuration file:

```bash
sudo vim /var/ossec/etc/ossec.conf
```

Then added a localfile entry to ingest Suricata's `eve.json` logs.

<img width="391" height="382" alt="image" src="https://github.com/user-attachments/assets/88efc70d-0323-4836-af7b-948b3af3899a" />

### What I Learned
- How SIEM platforms ingest IDS alerts
- How Wazuh processes Suricata logs
- The benefits of centralized monitoring

---

# Key Takeaways

✅ Installed and configured Suricata IDS

✅ Configured HOME_NET and monitoring interfaces

✅ Updated and managed Suricata rule sources

✅ Verified IDS functionality using test traffic

✅ Created and tested a custom ICMP detection rule

✅ Integrated Suricata with Wazuh SIEM

✅ Centralized network security monitoring and alert analysis

---

## Skills Practiced

- Network Intrusion Detection
- Suricata Administration
- Rule Creation and Tuning
- Linux System Administration
- Log Analysis
- SIEM Integration
- Blue Team Monitoring
- Security Event Investigation
