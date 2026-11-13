
<div align="center">

# NETWORKWALKS CYBERSECURITY INTERNSHIP

### WEEK 2 — FOOTPRINTING, RECONNAISSANCE & NETWORK SCANNING

<p>
  <img src="https://img.shields.io/badge/NETWORKWALKS-CYBERSECURITY-1565C0?style=for-the-badge" alt="NetworkWalks Cybersecurity">
  <img src="https://img.shields.io/badge/BATCH-B084-2E7D32?style=for-the-badge" alt="Batch B084">
  <img src="https://img.shields.io/badge/WEEK-02-ED6C02?style=for-the-badge" alt="Week 2">
  <img src="https://img.shields.io/badge/STATUS-COMPLETED-00897B?style=for-the-badge" alt="Completed">
</p>

<p>
  <img src="https://img.shields.io/badge/Kali_Linux-557C94?style=flat-square&logo=kalilinux&logoColor=white" alt="Kali Linux">
  <img src="https://img.shields.io/badge/Nmap-004B87?style=flat-square" alt="Nmap">
  <img src="https://img.shields.io/badge/Zenmap-Network_Scanning-0078D4?style=flat-square" alt="Zenmap">
  <img src="https://img.shields.io/badge/Focus-Penetration_Testing-red?style=flat-square" alt="Penetration Testing">
</p>

**A practical cybersecurity project documenting website footprinting, information gathering, network discovery and topology visualization.**

[GitHub Profile](https://github.com/josuemutsiirwa) •
[LinkedIn Profile](https://www.linkedin.com/in/josue-matembera-37a269407/)

</div>

---

# 1. Project Overview

Welcome to my **Week 2 Cybersecurity Internship Project**, completed as part of the NetworkWalks Cybersecurity Internship, Batch B084.

This repository contains my practical work covering two important early stages of penetration testing:

1. **Footprinting and Reconnaissance:** Collecting publicly available information about a target website using Kali Linux tools.
2. **Network Scanning and Discovery:** Identifying active hosts within a virtual network and visualizing the discovered network topology using Nmap and Zenmap.

The exercises helped me understand how cybersecurity professionals gather information about systems, identify technologies, examine network services and document their observations before proceeding to more advanced security testing.

This repository includes:

- Practical activities and explanations.
- Commands used during the exercises.
- Screenshots showing the execution of the tools.
- Saved command outputs.
- Network topology documentation.
- A separate formal penetration testing report.

## Project Modules

| Module | Title | Main Activity |
|---|---|---|
| W2-PM1 | Multiple Kali Tools | Website footprinting and reconnaissance |
| W2-PM5 | Zenmap Scanning | Network host discovery and topology visualization |

---

# 2. Intern Information

| Field | Details |
|---|---|
| **Name** | MUTSIIRWA MATEMBERA JOSUE |
| **Program** | NetworkWalks Cybersecurity Internship |
| **Batch** | B084 |
| **Week** | Week 2 |
| **Project** | Footprinting and Network Scanning |
| **Operating System** | Kali Linux |
| **GitHub** | [josuemutsiirwa](https://github.com/josuemutsiirwa) |
| **LinkedIn** | [Josue Matembera](https://www.linkedin.com/in/josue-matembera-37a269407/) |

---

# 3. Project Objectives

The objectives of this project were to:

- Understand the fundamentals of penetration testing reconnaissance.
- Gather publicly available information about a target domain.
- Identify domain registration information and name servers.
- Discover website technologies and server information.
- Perform DNS resolution and enumeration.
- Inspect HTTP response headers.
- Identify possible Web Application Firewall technologies.
- Understand IP addressing, MAC addresses and network interfaces.
- Discover active hosts within a network.
- Perform network discovery using Nmap.
- Visualize discovered hosts using Zenmap.
- Save screenshots and command outputs as technical evidence.
- Develop the ability to document security findings professionally.

---

# 4. Tools and Technologies

The following tools were used during the practical exercises.

| Tool | Purpose |
|---|---|
| Kali Linux | Penetration testing and reconnaissance environment |
| WHOIS | Retrieves domain registration information |
| WhatWeb | Identifies website technologies |
| Nslookup | Performs DNS queries and domain resolution |
| cURL | Inspects HTTP requests and response headers |
| WAFW00F | Identifies possible Web Application Firewall technologies |
| DNSRecon | Performs DNS enumeration |
| Nmap | Discovers active hosts on a network |
| Zenmap | Graphical interface for Nmap and network topology visualization |
| VirtualBox | Provides the virtual machine environment |

---

# 5. W2-PM1 — Multiple Kali Tools

<p>
  <img src="https://img.shields.io/badge/MODULE-W2--PM1-blue?style=for-the-badge" alt="W2-PM1">
  <img src="https://img.shields.io/badge/PHASE-Footprinting%20%26%20Reconnaissance-6A1B9A?style=for-the-badge" alt="Footprinting and Reconnaissance">
</p>

## 5.1 Introduction

The first practical module focused on **website footprinting and reconnaissance**.

Footprinting is the process of collecting information about a target system or organization. This information can help a security professional understand the target's publicly visible infrastructure and technologies.

For this exercise, I used six Kali Linux tools to collect different types of information about the assigned target.

**Target domain:** `networkwalks.com`

The six tools used were:

1. WHOIS
2. WhatWeb
3. Nslookup
4. cURL
5. WAFW00F
6. DNSRecon

## 5.2 Step 1 — WHOIS: Domain Information Gathering

### Purpose

WHOIS is a tool used to retrieve publicly available domain registration information.

It can help identify:
- Domain registrar.
- Domain creation and expiry dates.
- Domain name servers.
- Registration information.

### Command Used

```bash
whois networkwalks.com
```

### Procedure

1. Opened the Kali Linux terminal.
2. Entered the WHOIS command with the target domain.
3. Executed the command.
4. Examined the returned domain registration information.
5. Identified the registrar, registration dates and name servers.

### Key Observations

- Registrar: GoDaddy.
- Creation date: 6 November 2019.
- Expiry date: 6 November 2027.
- Name servers included HostGator name servers.
- Domain registration information was privacy protected.

### Screenshot Evidence

![WHOIS Domain Information](W2-PM1/screenshots/01-whois.png)

*Figure 1: WHOIS output showing publicly available domain registration information.*

### Learning Point

This exercise helped me understand how domain registration information can be used during the reconnaissance phase to learn more about a target's domain infrastructure.

---

## 5.3 Step 2 — WhatWeb: Website Technology Identification

### Purpose

WhatWeb is a website fingerprinting tool. It identifies technologies and components used by websites.

It can help identify:
- Web server technologies.
- Content Management Systems (CMS).
- JavaScript libraries.
- Website plugins and other detectable components.

### Command Used

```bash
whatweb https://networkwalks.com
```

### Procedure

1. Opened the Kali Linux terminal.
2. Entered the WhatWeb command followed by the target website.
3. Executed the command.
4. Examined the technologies identified by the tool.
5. Recorded the detected server, CMS and plugin information.

### Key Observations

The scan identified:

| Component | Observed Result |
|---|---|
| HTTP Status | 200 OK |
| Web Server | Apache |
| CMS | WordPress 7.1.4 |
| Plugin | WordPress Download Manager 3.3.76 |
| JavaScript Library | jQuery 3.7.1 |
| IP Address | 192.232.216.135 |

### Screenshot Evidence

![WhatWeb Technology Identification](W2-PM1/screenshots/02-whatweb.png)

*Figure 2: WhatWeb output identifying technologies associated with the target website.*

### Learning Point

I learned how website fingerprinting can reveal technologies used by a web application. This information can help security professionals determine which software components may require further security review.

---

## 5.4 Step 3 — Nslookup: DNS Resolution

### Purpose

Nslookup is a command-line tool used to query the Domain Name System (DNS).

DNS translates human-readable domain names into IP addresses that computers use to communicate.

### Command Used

```bash
nslookup networkwalks.com
```

### Procedure

1. Opened the Kali Linux terminal.
2. Entered the Nslookup command.
3. Executed the DNS query.
4. Examined the DNS server used to resolve the domain.
5. Recorded the IP address returned by the query.

### Key Observation

The domain resolved to:

```text
192.232.216.135
```

The DNS query used Google's public DNS resolver at `8.8.8.8`.

### Screenshot Evidence

![Nslookup DNS Resolution](W2-PM1/screenshots/03-nslookup.png)

*Figure 3: Nslookup output showing the DNS resolution of networkwalks.com.*

### Learning Point

I learned how DNS resolution works and how a domain name can be translated into an IP address. This is an important step in understanding the infrastructure associated with a target.

---

## 5.5 Step 4 — cURL: HTTP Response Header Inspection

### Purpose

cURL is a command-line tool used to transfer data and communicate with web servers.

The `-I` option requests the HTTP response headers without downloading the full webpage body.

### Command Used

```bash
curl -I https://networkwalks.com
```

### Procedure

1. Opened the Kali Linux terminal.
2. Entered the cURL command with the `-I` option.
3. Executed the HTTP request.
4. Examined the response status and server headers.
5. Identified useful technical information returned by the server.

### Key Observations

The response showed:

- HTTP status: `200 OK`.
- Server information identifying Apache.
- Content type: HTML.
- A WordPress REST API reference through `/wp-json/`.
- Security-related response headers and cookie attributes.

### Screenshot Evidence

![cURL HTTP Headers](W2-PM1/screenshots/04-curl.png)

*Figure 4: cURL output displaying HTTP response headers from the target website.*

### Learning Point

I learned how HTTP response headers can reveal information about a web server and its application. I also learned that a successful HTTP response does not automatically mean a website is secure.

---

## 5.6 Step 5 — WAFW00F: Web Application Firewall Detection

### Purpose

WAFW00F is a tool used to identify Web Application Firewalls (WAFs).

A WAF helps protect web applications by inspecting HTTP traffic and applying security rules to requests.

### Command Used

```bash
wafw00f https://networkwalks.com
```

### Procedure

1. Opened the Kali Linux terminal.
2. Entered the WAFW00F command with the target website.
3. Executed the detection test.
4. Examined the tool's response.
5. Recorded the WAF technology identified by the tool.

### Key Observation

WAFW00F identified:

**ModSecurity (SpiderLabs)**

### Screenshot Evidence

![WAFW00F Detection](W2-PM1/screenshots/05-wafw00f.png)

*Figure 5: WAFW00F output identifying ModSecurity (SpiderLabs).*

### Learning Point

I learned how security professionals can identify technologies used to protect web applications. Detecting a WAF does not prove that it is configured correctly or that it blocks every attack.

---

## 5.7 Step 6 — DNSRecon: DNS Enumeration

### Purpose

DNSRecon is a DNS enumeration tool used to collect information about a domain's DNS infrastructure.

It can identify different DNS record types, including:

- A records.
- NS records.
- MX records.
- SOA records.
- TXT records.
- SRV records.

### Command Used

```bash
dnsrecon -d networkwalks.com
```

### Procedure

1. Opened the Kali Linux terminal.
2. Entered the DNSRecon command.
3. Specified the target domain using the `-d` option.
4. Executed the enumeration.
5. Examined the DNS records returned by the tool.
6. Recorded the discovered DNS infrastructure information.

### Key Observations

The enumeration identified:

- SOA records.
- Name server records.
- Mail exchange records.
- TXT and SPF information.
- Service records.
- DNS software information.

The results also showed no DNSSEC response to the query performed during the exercise.

### Screenshot Evidence

![DNSRecon Enumeration](W2-PM1/screenshots/06-dnsrecon.png)

*Figure 6: DNSRecon output showing DNS records associated with the target domain.*

### Learning Point

I learned how DNS enumeration can reveal additional information about a domain's infrastructure, including name servers, mail services and other publicly available DNS records.

---

## 5.8 PM1 Summary

The six tools provided different types of information about the target.

| Tool | Main Result |
|---|---|
| WHOIS | Domain registration and name server information |
| WhatWeb | Apache, WordPress and detected plugin information |
| Nslookup | Domain resolved to `192.232.216.135` |
| cURL | HTTP 200 response and technical headers |
| WAFW00F | ModSecurity (SpiderLabs) identified |
| DNSRecon | DNS, mail and service-related records |

### PM1 Learning Outcomes

After completing this module, I gained practical experience in:

- Performing website footprinting.
- Gathering domain registration information.
- Identifying website technologies.
- Understanding DNS resolution.
- Inspecting HTTP response headers.
- Identifying possible WAF technologies.
- Enumerating publicly available DNS records.
- Saving technical evidence for reporting.

---

# 6. W2-PM5 — Network Scanning with Zenmap

<p>
  <img src="https://img.shields.io/badge/MODULE-W2--PM5-0078D4?style=for-the-badge" alt="W2-PM5">
  <img src="https://img.shields.io/badge/PHASE-Network%20Discovery-00897B?style=for-the-badge" alt="Network Discovery">
</p>

## 6.1 Introduction

The second practical module focused on **network scanning and topology visualization**.

Network scanning is used to discover devices and hosts connected to a network. It helps administrators understand which devices are active and how a network is organized.

For this exercise, I used Nmap for host discovery and Zenmap to visualize the discovered network topology.

The scan was performed within the virtual network available to my Kali Linux virtual machine.

## 6.2 Step 1 — Identify the Network Configuration

### Purpose

Before scanning a network, it is important to understand the network configuration.

I needed to identify:
- My Kali Linux IP address.
- The network address and subnet.
- The default gateway.

### Command Used

```bash
ip route
```

### Procedure

1. Opened the Kali Linux terminal.
2. Entered the `ip route` command.
3. Examined the routing information.
4. Identified the default gateway.
5. Identified the network range and Kali Linux source IP address.

### Observed Network Information

| Network Detail | Value |
|---|---|
| Network Address | `10.0.0.0/24` |
| Kali Linux IP | `10.0.0.2` |
| Default Gateway | `10.0.0.1` |

### Learning Point

I learned how to identify the network range and default gateway before performing a network discovery scan.

---

## 6.3 Step 2 — Perform Host Discovery Using Nmap

### Purpose

Nmap is a network discovery and security auditing tool.

For this exercise, I used its host discovery option to identify active devices within the assigned network range.

### Command Used

```bash
nmap -sn 10.0.0.0/24
```

### Understanding the Command

| Command Part | Meaning |
|---|---|
| `nmap` | Starts the Nmap scanning tool |
| `-sn` | Performs host discovery without a port scan |
| `10.0.0.0/24` | Specifies the network range to examine |

### Procedure

1. Opened the Kali Linux terminal.
2. Entered the Nmap command.
3. Specified the network range `10.0.0.0/24`.
4. Executed the host discovery scan.
5. Examined the active hosts returned by Nmap.
6. Recorded their IP and available MAC address information.

### Scan Results

The scan examined 256 IP addresses and identified two active hosts.

| IP Address | Identification | MAC Address |
|---|---|---|
| `10.0.0.1` | Virtual network gateway | `52:54:00:12:35:00` |
| `10.0.0.2` | Kali Linux virtual machine | Not displayed |

### Screenshot Evidence

![Nmap Host Discovery](W2-PM5/screenshots/01-kali-ping-scan.png)

*Figure 7: Nmap host discovery results showing two active hosts in the virtual network.*

### Learning Point

I learned how Nmap can discover active hosts within a network. I also understood that the `-sn` option performs host discovery without conducting a port scan.

---

## 6.4 Step 3 — Visualize the Network Using Zenmap

### Purpose

Zenmap is the graphical interface for Nmap.

It allows users to perform scans, examine results and visualize discovered hosts using its topology feature.

### Procedure

1. Opened Zenmap in the Kali Linux environment.
2. Selected the network discovery scan configuration.
3. Entered the assigned network range.
4. Executed the scan.
5. Examined the discovered hosts.
6. Opened the **Topology** tab.
7. Viewed the graphical representation of the discovered network.
8. Saved the network topology as a PDF document.

### Screenshot Evidence

![Zenmap Network Topology](W2-PM5/screenshots/02-kali-network-topology.png)

*Figure 8: Zenmap topology view showing the discovered hosts in the virtual network.*

### Additional Evidence

The saved topology PDF is available here:

[View W2-PM5 Network Topology PDF](W2-PM5/outputs/W2-PM5-Network-Topology.pdf)

### Learning Point

I learned how Zenmap converts network discovery results into a graphical representation. This helped me understand how network administrators can use topology visualization to study discovered devices and network relationships.

---

## 6.5 Step 4 — Save Scan Results and Evidence

After completing the scan, I organized the collected evidence into separate folders.

The following files were saved:

**Scan output:**

`W2-PM5/outputs/kali-ping-scan.txt`

**Topology document:**

`W2-PM5/outputs/W2-PM5-Network-Topology.pdf`

**Screenshots:**

- `W2-PM5/screenshots/01-kali-ping-scan.png`
- `W2-PM5/screenshots/02-kali-network-topology.png`

This organization makes it easier to review the results and verify the practical activities.

---

## 6.6 PM5 Summary

| Activity | Result |
|---|---|
| Network identification | `10.0.0.0/24` |
| Kali Linux IP | `10.0.0.2` |
| Default gateway | `10.0.0.1` |
| Host discovery | Two active hosts identified |
| Scanning tool | Nmap |
| Visualization tool | Zenmap |
| Topology evidence | PDF saved successfully |

### PM5 Learning Outcomes

After completing this module, I gained practical experience in:

- Understanding network addressing and subnet notation.
- Identifying a default gateway.
- Performing host discovery with Nmap.
- Understanding IP and MAC addresses.
- Using Zenmap for network scanning.
- Visualizing discovered hosts.
- Saving network scan results and topology evidence.

**Lab Environment Note:** The discovered hosts belong to the virtual network visible to the Kali Linux virtual machine. The results should not be interpreted as a scan of every device on a physical Wi-Fi or LAN network.

---

# 7. Risk Analysis and Security Considerations

The activities performed during PM1 and PM5 revealed several observations that may be relevant during a security assessment.

| Observation | Potential Security Consideration |
|---|---|
| Website technology information was identifiable. | Software and plugin information may help identify components requiring further security review. |
| The target domain resolved to a public IP address. | Public IP information can assist infrastructure reconnaissance. |
| HTTP response headers exposed technical information. | Header information may support further technology fingerprinting. |
| ModSecurity was identified by WAFW00F. | The WAF configuration and effectiveness should be reviewed by authorized administrators. |
| DNS records revealed infrastructure information. | DNS information can help build a profile of publicly visible infrastructure. |
| Two hosts were discovered in the virtual network. | Network administrators should maintain awareness of devices connected to their networks. |

### Important Security Note

The observations above are not confirmed vulnerabilities.

The practical exercises focused on reconnaissance and host discovery. No exploitation or vulnerability validation was performed.

The presence of an IP address, software version, DNS record or WAF does not automatically mean that a system is vulnerable.

Further testing would require appropriate authorization and a clearly defined scope.

---

# 8. Security Recommendations

Based on the observations collected during the practical exercises, the following recommendations are suggested:

1. **Update software regularly:** Keep website platforms, plugins and server software updated.
2. **Review exposed technologies:** Examine what technical information is publicly visible.
3. **Review HTTP headers:** Check response headers and cookie security attributes.
4. **Maintain DNS security:** Regularly review DNS records and configurations.
5. **Monitor WAF configuration:** Ensure Web Application Firewall rules are properly configured and monitored.
6. **Perform network discovery:** Regularly identify active devices within authorized networks.
7. **Investigate unknown devices:** Verify unexpected devices discovered during network scans.
8. **Maintain network documentation:** Keep network diagrams and device records updated.
9. **Respect authorization:** Conduct security testing only within an approved scope.

---

# 9. Repository Structure

The repository is organized into separate directories for the two practical modules.

```text
NETWORKWALKS-MUTSIIRWA-B084-WK2-PENETRATION-TESTING/
│
├── README.md
│
├── WEEK-2-PENETRATION-TESTING-REPORT.md
│
├── W2-PM1/
│   ├── screenshots/
│   │   ├── 01-whois.png
│   │   ├── 02-whatweb.png
│   │   ├── 03-nslookup.png
│   │   ├── 04-curl.png
│   │   ├── 05-wafw00f.png
│   │   └── 06-dnsrecon.png
│   │
│   └── outputs/
│       ├── whois.txt
│       ├── whatweb.txt
│       ├── nslookup.txt
│       ├── curl.txt
│       ├── wafw00f.txt
│       └── dnsrecon.txt
│
└── W2-PM5/
    ├── screenshots/
    │   ├── 01-kali-ping-scan.png
    │   └── 02-kali-network-topology.png
    │
    └── outputs/
        ├── kali-ping-scan.txt
        └── W2-PM5-Network-Topology.pdf
```

---

# 10. Formal Penetration Testing Report

The detailed formal report is maintained separately from this README.

It follows the reporting structure provided in the internship sample and contains:

- Liability disclaimer.
- Introduction and project objectives.
- Tools and technologies used.
- Activities performed.
- Findings and observations.
- Risk analysis and potential impact.
- Security recommendations.
- Evidence collected.
- Conclusion and author information.

### Read the Complete Report

[**WEEK 2 — PENETRATION TESTING REPORT**](WEEK-2-PENETRATION-TESTING-REPORT.md)

---

# 11. Overall Learning Outcomes

Completing these practical exercises helped me develop a stronger understanding of the early stages of penetration testing.

I gained experience in:

- Website footprinting and reconnaissance.
- Domain registration information gathering.
- Website technology identification.
- DNS resolution and enumeration.
- HTTP response analysis.
- Web Application Firewall detection.
- Network host discovery.
- IP and MAC address identification.
- Network topology visualization.
- Technical evidence collection and documentation.

Most importantly, I learned that reconnaissance and scanning are important steps in understanding a target environment before performing more advanced security assessments.

---

# 12. Disclaimer

This repository is intended for educational and cybersecurity training purposes as part of the NetworkWalks Cybersecurity Internship.

All activities must be conducted only on systems and networks owned by the tester or for which appropriate authorization has been obtained.

The information documented here represents observations collected during the practical exercises. It does not constitute confirmation that the assessed systems contain exploitable vulnerabilities.

The author is not responsible for unauthorized use or misuse of the information contained in this repository.

---

<div align="center">

# AUTHOR

### MUTSIIRWA MATEMBERA JOSUE

**NetworkWalks Cybersecurity Internship**

**Batch B084 | Week 2**

<p>
  <a href="https://github.com/josuemutsiirwa">
    <img src="https://img.shields.io/badge/GitHub-josuemutsiirwa-181717?style=for-the-badge&logo=github" alt="GitHub">
  </a>
  <a href="https://www.linkedin.com/in/josue-matembera-37a269407/">
    <img src="https://img.shields.io/badge/LinkedIn-Josue%20Matembera-0A66C2?style=for-the-badge&logo=linkedin" alt="LinkedIn">
  </a>
</p>

**LEARN • PRACTICE • DOCUMENT • IMPROVE**

</div>
