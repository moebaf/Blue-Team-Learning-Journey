# Wireshark Labs
> Date: 2026-05-31

## Lab 1 - Interface Configuration

Added custom columns to display Source Port and Destination Port.

<img width="416" height="334" alt="image" src="https://github.com/user-attachments/assets/ce6edd92-7cd3-4e91-83c3-824c411fd51f" />

### Findings

- Improved packet visibility
- Easier identification of communicating services

---

## Lab 2 - ICMP Traffic Analysis

Generated ICMP traffic using:

```bash
ping google.com
```

Filter used:

```wireshark
icmp
```

<img width="1917" height="645" alt="image" src="https://github.com/user-attachments/assets/df4ad347-7937-4cd3-9076-dcc509be72a1" />

<img width="404" height="240" alt="image" src="https://github.com/user-attachments/assets/e8197d77-75b7-4e82-aee0-157a1add76d2" />

### Findings

- Captured Echo Requests
- Captured Echo Replies
- Confirmed connectivity to external host

---

## Lab 3 - DNS Resolution Analysis

Filter used:

```wireshark
dns
```

Opened a DNS capture and inspected how a domain was resolved.

<img width="956" height="350" alt="image" src="https://github.com/user-attachments/assets/d0b3f465-bb38-482a-9666-51097e1e8995" />

### IPv4 Request

<img width="239" height="169" alt="image" src="https://github.com/user-attachments/assets/2f88e0d1-34a5-4b96-ad96-06795cc0f9fc" />

### IPv6 Request

<img width="356" height="167" alt="image" src="https://github.com/user-attachments/assets/d968f144-73d4-4664-a2c6-3bb9dde8aa8d" />

### IPv4 Response

<img width="469" height="177" alt="image" src="https://github.com/user-attachments/assets/96a046cd-3b84-4d80-bdac-52f6ef257f3d" />

### IPv6 Response

<img width="469" height="182" alt="image" src="https://github.com/user-attachments/assets/16844467-2e1f-4c92-b8a6-9ac1d573ff11" />

### Findings

- Observed DNS A record requests
- Observed DNS AAAA record requests
- Identified successful DNS responses

---

## Lab 4 - Telnet Credential Exposure

Connected from Kali Linux to Metasploitable 2 using Telnet while capturing traffic.

<img width="455" height="382" alt="image" src="https://github.com/user-attachments/assets/553f1004-5683-4cff-9693-dfea0a097a61" />

Followed the TCP stream.

<img width="789" height="394" alt="image" src="https://github.com/user-attachments/assets/09c8973a-3e0c-4645-a829-06f1fdb3be44" />

### Findings

- Username visible in plaintext
- Password visible in plaintext
- No encryption present

### Security Impact

Telnet transmits credentials in clear text and should not be used on modern networks.

---

## Lab 5 - TLS Decryption & Malware Investigation

Started by identifying TLS handshake traffic.

Filter used:

```wireshark
tls.handshake.type == 1
```

<img width="710" height="121" alt="image" src="https://github.com/user-attachments/assets/02de713b-4ae8-4831-8257-aee765e9d99f" />

The traffic was encrypted.

<img width="617" height="353" alt="image" src="https://github.com/user-attachments/assets/c2c4e0de-98f6-4038-949a-c1c2087d3d6d" />

Imported the TLS key log file.

<img width="437" height="322" alt="image" src="https://github.com/user-attachments/assets/c1c0f577-4a73-4dd8-94ff-0a51c21b1b55" />

After decryption, suspicious activity was identified.

<img width="946" height="320" alt="image" src="https://github.com/user-attachments/assets/36df6983-b2c7-4582-81bc-8e3c76599da9" />

Following the HTTP stream revealed a DLL download.

<img width="626" height="389" alt="image" src="https://github.com/user-attachments/assets/6ad5f161-911f-4c15-b01f-296812016684" />

The downloaded DLL file was extracted from the HTTP stream and analyzed using VirusTotal. The analysis confirmed that the file was malicious and provided additional details such as detection results, file hashes, and threat intelligence indicators.

Based on the investigation, it was determined that the malware originated from a user-initiated download. This highlights the importance of verifying files before execution, downloading software only from trusted sources, and educating users about the risks associated with unknown or suspicious downloads.

<img width="956" height="365" alt="image" src="https://github.com/user-attachments/assets/39f425ca-ff57-4170-b534-45c253ea3129" />




### Findings

- Decrypted TLS traffic successfully
- Identified a DLL download
- Verified the file as malicious using VirusTotal

### Lesson Learned

Packet captures can provide valuable evidence during malware investigations and incident response activities.

---

## Skills Practiced

- Packet Capture
- Protocol Analysis
- DNS Investigation
- Telnet Security Assessment
- TCP Stream Analysis
- TLS Decryption
- Malware Traffic Investigation
