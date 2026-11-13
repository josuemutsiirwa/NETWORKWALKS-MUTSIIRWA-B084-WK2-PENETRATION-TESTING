
# NetworkWalks Cybersecurity Internship – Week 2

## Project Overview

This repository contains practical work completed during Week 2 of the NetworkWalks Cybersecurity Internship. The exercises focused on reconnaissance, information gathering, and network host discovery.

## Learning Objectives

- Understand domain reconnaissance and information gathering.
- Use Kali Linux tools to collect information about a target domain.
- Understand DNS records and HTTP response headers.
- Perform network host discovery using Nmap and Zenmap.
- Save scan results and screenshots as practical evidence.

## Module 1: W2-PM1 – Multiple Kali Linux Tools

### Tools Used

- WHOIS
- WhatWeb
- Nslookup
- cURL
- WAFW00F
- DNSRecon

### Target

`networkwalks.com`

### Activities

The following activities were performed:

1. Collected domain registration information using WHOIS.
2. Identified website technologies using WhatWeb.
3. Queried DNS information using Nslookup.
4. Examined HTTP response headers using cURL.
5. Checked for web application firewall detection using WAFW00F.
6. Enumerated DNS records using DNSRecon.

### Evidence

- Screenshots: `W2-PM1/screenshots/`
- Command outputs: `W2-PM1/outputs/`

## Module 2: W2-PM5 – Network Scanning Using Kali Linux

### Tools Used

- Kali Linux
- Nmap
- Zenmap

### Network Scope

The scan was performed on the Kali virtual machine's VirtualBox network:

`10.0.0.0/24`

### Command Used

```bash
nmap -sn 10.0.0.0/24
```

The `-sn` option performs host discovery without conducting a port scan.

### Results

Two active hosts were discovered:

| IP Address | Status | MAC Address |
|---|---|---|
| 10.0.0.1 | Up | 52:54:00:12:35:00 |
| 10.0.0.2 | Up | Not displayed |

The first host was identified as a QEMU virtual NIC.

### Evidence

- Scan screenshots: `W2-PM5/screenshots/`
- Scan output: `W2-PM5/outputs/kali-ping-scan.txt`
- Network topology: `W2-PM5/outputs/W2-PM5-Network-Topology.pdf`

## Ethical Considerations

All scanning activities were conducted within the assigned training scope and the Kali virtual lab environment. Network discovery was limited to the virtual network used for this practical exercise.

## Limitations

- The network scan identified active hosts but did not assess open ports or vulnerabilities.
- Only two active hosts responded during the scan.
- The results represent the virtual network environment, not the physical Wi-Fi network.

## Conclusion

The Week 2 practical exercises provided hands-on experience with reconnaissance tools, DNS enumeration, HTTP analysis, web technology identification, and network host discovery.

This work strengthened my understanding of basic cybersecurity assessment techniques and practical evidence documentation.
