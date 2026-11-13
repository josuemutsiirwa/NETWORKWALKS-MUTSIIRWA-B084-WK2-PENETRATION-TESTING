
# PENETRATION TESTING REPORT
## Footprinting, Reconnaissance and Network Scanning

**W2-PM-FINAL | CYBERSECURITY INTERNSHIP | NETWORKWALKS**

| Report Information | Details |
|---|---|
| **Pentester Name** | MUTSIIRWA MATEMBERA JOSUE |
| **Program** | NetworkWalks Cybersecurity Internship |
| **Batch** | B084 |
| **Date** | 13 November 2026 |
| **Modules Completed** | W2-PM1 – Multiple Kali Linux Tools; W2-PM5 – Network Scanning Using Zenmap |
| **Primary Target** | `networkwalks.com` |
| **Scanning Environment** | Kali Linux VirtualBox virtual network |
| **Phases Covered** | Phase 1 – Reconnaissance and Footprinting; Phase 2 – Network Scanning and Host Discovery |
| **LinkedIn** | [Josue Matembera](https://www.linkedin.com/in/josue-matembera-37a269407/) |

---

# 1. LIABILITY DISCLAIMER

This report documents practical cybersecurity activities completed as part of the NetworkWalks Cybersecurity Internship.

The activities described were conducted for educational and security-learning purposes within the assigned practical scope. The domain reconnaissance activity used `networkwalks.com` as the assigned training target, while network discovery was restricted to the Kali Linux VirtualBox virtual network used for the laboratory exercise.

No exploitation, unauthorized access, data modification or disruption of services was performed as part of these two modules.

The observations in this report should not be interpreted as proof that the target systems contain exploitable vulnerabilities. Any additional testing must be conducted only with appropriate authorization and within an explicitly approved scope.

The author accepts responsibility for using the knowledge gained from these exercises ethically and lawfully.

# 2. INTRODUCTION

This report presents the practical activities completed during Week 2 of the NetworkWalks Cybersecurity Internship. The work focused on two important stages of a basic cybersecurity assessment: reconnaissance and network scanning.

The first practical module, W2-PM1, involved using multiple Kali Linux tools to collect publicly available information about the `networkwalks.com` domain. The objective was to understand how security professionals gather information about domain registration, website technologies, DNS infrastructure, HTTP response headers and web application firewall technologies.

The second module, W2-PM5, involved network discovery using Nmap and Zenmap. The exercise focused on identifying active hosts within a network, examining their IP and MAC address information where available, and generating a visual network topology.

These exercises demonstrated how information gathering can provide an initial understanding of a web application and its surrounding network environment before more advanced security assessments are considered.

This report documents the tools used, commands executed, observations obtained, potential security implications, recommendations and screenshots collected during the practical exercises.

# 3. OBJECTIVES

The main objectives of the Week 2 practical exercises were:

1. Understand the purpose of reconnaissance and footprinting in cybersecurity.
2. Collect publicly available domain registration information using WHOIS.
3. Identify website technologies and services using WhatWeb.
4. Understand how DNS translates domain names into IP addresses.
5. Examine HTTP response headers using cURL.
6. Identify web application firewall technologies using WAFW00F.
7. Enumerate DNS records using DNSRecon.
8. Perform network host discovery using Nmap and Zenmap.
9. Generate and save a network topology diagram.
10. Document findings and identify areas that may require further security review.

# 4. TOOLS AND TECHNOLOGIES USED

| Tool | Purpose |
|---|---|
| Kali Linux | Operating system used for cybersecurity reconnaissance and scanning activities. |
| WHOIS | Retrieves publicly available domain registration information. |
| WhatWeb | Identifies website technologies, content management systems and server information. |
| Nslookup | Queries DNS servers to resolve domain names into IP addresses. |
| cURL | Sends requests to web servers and examines HTTP responses and headers. |
| WAFW00F | Identifies web application firewall technologies where detectable. |
| DNSRecon | Enumerates DNS records and gathers information about domain infrastructure. |
| Nmap | Performs network discovery and identifies active hosts. |
| Zenmap | Graphical interface for Nmap that displays scan results and network topology. |
| VirtualBox | Provides the virtual environment used for the Kali Linux network-scanning exercise. |

# 5. ACTIVITIES PERFORMED

## 5.1 W2-PM1 – FOOTPRINTING AND RECONNAISSANCE

### Target Information

The domain used for the reconnaissance exercise was:

`networkwalks.com`

Six Kali Linux tools were used to collect different categories of information about the domain and its web infrastructure.

### 5.1.1 WHOIS – Domain Registration Information

**Command executed:**

```bash
whois networkwalks.com
```

**Purpose:**

WHOIS retrieves publicly available domain registration information. It can provide details such as the registrar, registration dates, expiration dates and authoritative name servers.

**Observations:**

The WHOIS query returned the following information:

- Registrar: GoDaddy.
- Domain creation date: 6 November 2019.
- Domain expiration date: 6 November 2027.
- DNSSEC status: Unsigned.
- Name servers included `NS6135.HOSTGATOR.COM` and `NS6136.HOSTGATOR.COM`.
- The registration information indicated that domain registration privacy protection was enabled.

**Security relevance:**

Domain registration information can help a security professional understand the administrative and DNS infrastructure associated with a domain. Name server information can also support further DNS investigation.

The presence of publicly available registration information is not itself a vulnerability. However, it contributes to the information that may be collected during reconnaissance.

**Evidence:**

![WHOIS domain registration results](W2-PM1/screenshots/01-whois.png)

### 5.1.2 WhatWeb – Website Technology Identification

**Command executed:**

```bash
whatweb https://networkwalks.com
```

**Purpose:**

WhatWeb identifies technologies used by a website, including its web server, content management system, frameworks, libraries and other detectable components.

**Observations:**

The scan identified the following technologies and information:

- Website response: `200 OK`.
- Web server: Apache.
- Content management system: WordPress 7.1.4.
- WordPress Download Manager: 3.3.76.
- JavaScript library: jQuery 3.7.1.
- Resolved server IP: `192.232.216.135`.
- Website title: Networkwalks Academy.

Other technologies and website components were also detected.

**Security relevance:**

Technology identification helps security professionals understand the software components used by a web application. Software names and versions can be compared with reliable security advisories to determine whether further investigation is necessary.

However, detecting a software version does not establish that it is vulnerable. A proper assessment would require checking the exact component version, configuration, patch status and applicable security advisories.

**Evidence:**

![WhatWeb website technology identification](W2-PM1/screenshots/02-whatweb.png)

### 5.1.3 Nslookup – DNS Resolution

**Command executed:**

```bash
nslookup networkwalks.com
```

**Purpose:**

Nslookup is a DNS query utility used to retrieve information from DNS servers. In this exercise, it was used to determine the IP address associated with the target domain.

**Observations:**

The query used DNS server `8.8.8.8` and returned the following IPv4 address:

`192.232.216.135`

**Security relevance:**

DNS resolution provides information about the IP address associated with a domain. This information can help security professionals understand where a web service is hosted and support further infrastructure investigation.

An IP address being publicly resolvable is normal website behavior and is not, by itself, a security vulnerability.

**Evidence:**

![Nslookup DNS resolution results](W2-PM1/screenshots/03-nslookup.png)

### 5.1.4 cURL – HTTP Response Header Analysis

**Command executed:**

```bash
curl -I https://networkwalks.com
```

**Purpose:**

cURL is a command-line tool used to communicate with web servers. The `-I` option requests the HTTP response headers without downloading the full page content.

**Observations:**

The server returned an HTTP `200 OK` response.

The response included:

- Server information identifying Apache.
- Content type indicating an HTML document with UTF-8 encoding.
- A WordPress REST API endpoint exposed through the `Link` response header: `/wp-json/`.
- A `__wpdm_client` cookie with Secure and HttpOnly attributes.
- Additional server and cache-related headers.

**Security relevance:**

HTTP headers provide useful information about how a web server responds to requests. They can reveal server technologies, application behavior and available endpoints.

The presence of a WordPress REST API endpoint is not automatically a vulnerability. Its access controls and exposed functionality would require separate authorized testing.

**Evidence:**

![cURL HTTP response headers](W2-PM1/screenshots/04-curl.png)

### 5.1.5 WAFW00F – Web Application Firewall Detection

**Command executed:**

```bash
wafw00f https://networkwalks.com
```

**Purpose:**

WAFW00F is used to identify whether a website is protected by a Web Application Firewall (WAF). A WAF helps monitor and filter HTTP traffic based on configured security rules.

**Observations:**

The tool detected:

- Web Application Firewall: ModSecurity.
- Identification: ModSecurity (SpiderLabs).

**Security relevance:**

A WAF can help protect web applications by filtering suspicious requests and reducing exposure to certain web-based attacks.

Identifying the WAF technology provides information about the website's security architecture. However, detection alone does not prove that the WAF is correctly configured or that it blocks every attack.

**Evidence:**

![WAFW00F firewall detection results](W2-PM1/screenshots/05-wafw00f.png)

### 5.1.6 DNSRecon – DNS Enumeration

**Command executed:**

```bash
dnsrecon -d networkwalks.com
```

**Purpose:**

DNSRecon is a DNS enumeration tool used to collect information about a domain's DNS infrastructure. It can identify records such as A, NS, MX, SOA, TXT and SRV records.

**Observations:**

The enumeration returned DNS information including:

- SOA records.
- Authoritative name server records.
- Mail exchange (MX) records.
- IPv4 address records.
- TXT records, including SPF-related information.
- SRV records related to services such as autodiscover.
- DNS software information identifying BIND version `9.16.23-RH`.
- DNSSEC query with no answer, consistent with the unsigned status observed in WHOIS.

DNSRecon reported eight records during the enumeration.

**Security relevance:**

DNS records can reveal information about an organization's domain infrastructure, mail services and other network-related services.

This information can help security professionals understand the publicly visible DNS configuration and identify records that may require further review.

The discovery of DNS records does not automatically indicate a weakness. Their security significance depends on their configuration and intended purpose.

**Evidence:**

![DNSRecon DNS enumeration results](W2-PM1/screenshots/06-dnsrecon.png)

## 5.2 W2-PM5 – NETWORK SCANNING USING NMAP AND ZENMAP

### 5.2.1 Overview

The second practical exercise focused on identifying active devices within a network using Nmap and its graphical interface, Zenmap.

The Kali Linux virtual machine was used to perform host discovery on the VirtualBox virtual network.

**Network scope:**

`10.0.0.0/24`

This network represents the virtual laboratory environment. It should not be confused with the physical Wi-Fi network.

### 5.2.2 Nmap Host Discovery

**Command executed:**

```bash
nmap -sn 10.0.0.0/24
```

**Purpose:**

Nmap is a network scanning tool used to discover hosts and examine network services.

The `-sn` option performs host discovery without conducting a port scan. It helps determine which devices are responding within the specified network range.

**Observations:**

The scan identified two active hosts:

| IP Address | Status | MAC Address | Identification |
|---|---|---|---|
| `10.0.0.1` | Up | `52:54:00:12:35:00` | QEMU virtual NIC |
| `10.0.0.2` | Up | Not displayed | Kali Linux virtual machine |

The scan completed after checking 256 IP addresses and reported two hosts as active.

**Security relevance:**

Host discovery helps administrators and security professionals understand which devices are active on a network.

It can assist with network inventory, identification of unexpected devices and preparation for further authorized security assessments.

However, discovering an active host does not establish that the device is vulnerable. Additional authorized checks would be required to identify running services or security weaknesses.

**Evidence:**

![Nmap Kali virtual network host discovery](W2-PM5/screenshots/01-kali-ping-scan.png)

### 5.2.3 Zenmap Network Topology

**Purpose:**

Zenmap provides a graphical interface for Nmap and makes it easier to view scan results and understand relationships between discovered hosts.

After performing network discovery, the topology view was used to represent the discovered hosts visually.

The network topology was saved in PDF format as part of the practical evidence.

**Observation:**

The topology represented the discovered devices in the Kali VirtualBox virtual network. The visualization helped provide a graphical understanding of the network discovery results.

**Evidence:**

![Zenmap network topology](W2-PM5/screenshots/02-kali-network-topology.png)

**Additional topology document:**

`W2-PM5/outputs/W2-PM5-Network-Topology.pdf`

### 5.2.4 Network Scanning Limitations

The scan was restricted to the Kali Linux VirtualBox virtual network rather than the physical Wi-Fi LAN.

The exercise successfully demonstrated host discovery, but it did not include:

- A complete inventory of physical LAN devices.
- Port scanning or service version detection.
- Operating system fingerprinting.
- Vulnerability scanning or exploitation.

These activities would require separate authorized exercises and should not be inferred from the host discovery results.

# 6. RISK ANALYSIS AND POTENTIAL SECURITY IMPLICATIONS

The following table summarizes observations made during the practical exercises and their possible security implications.

These are potential risks identified through information gathering, not confirmed vulnerabilities.

| No. | Observation | Evidence | Potential Security Impact | Suggested Priority |
|---|---|---|---|---|
| 1 | Website technology information is publicly identifiable. | WhatWeb detected WordPress and plugin versions. | Technology information may help an attacker identify components requiring security review. | Medium |
| 2 | Server IP address is publicly resolvable. | Nslookup returned `192.232.216.135`. | Provides infrastructure information that may support further reconnaissance. | Low |
| 3 | HTTP response headers reveal technical information. | cURL returned server and application-related headers. | May assist technology fingerprinting and further enumeration. | Low |
| 4 | WordPress REST API endpoint is advertised. | cURL exposed `/wp-json/` in the Link header. | May provide additional application information depending on endpoint permissions and configuration. | Informational |
| 5 | WAF technology is identifiable. | WAFW00F detected ModSecurity (SpiderLabs). | Reveals information about the web application's defensive technology. | Low |
| 6 | DNS infrastructure records are publicly available. | DNSRecon identified SOA, NS, MX, TXT and SRV records. | DNS information can assist infrastructure mapping and targeted reconnaissance. | Medium |
| 7 | Two active hosts were discovered in the virtual network. | Nmap host discovery results. | Unknown devices on a network may require identification and verification. | Informational |

### Risk Assessment Notes

The priority labels above are preliminary assessments of the possible information-security implications, not formal vulnerability severity ratings.

The exercises did not include exploitation, authentication testing, configuration review or vulnerability validation.

Consequently, no confirmed exploitable vulnerability is claimed in this report.

# 7. RECOMMENDATIONS

Based on the information collected during the practical exercises, the following recommendations are proposed:

### 7.1 Review Publicly Exposed Technology Information

Organizations should periodically review the technologies and software versions exposed by their websites. Unnecessary information disclosure should be minimized where practical.

### 7.2 Maintain Updated Software

Content management systems, plugins, frameworks and server software should be maintained with appropriate security updates.

Software versions should be checked against reliable security advisories to identify components that require attention.

### 7.3 Review HTTP Security Headers

Website administrators should review HTTP response headers and consider appropriate security headers based on their application requirements.

Examples include Content-Security-Policy, X-Content-Type-Options, Strict-Transport-Security and Referrer-Policy.

### 7.4 Review DNS Configuration

DNS records should be reviewed periodically to ensure that only necessary services and records are publicly exposed.

DNSSEC should also be considered where supported and appropriate for the organization's DNS infrastructure.

### 7.5 Maintain and Monitor Web Application Firewall Protection

The detected ModSecurity WAF should be maintained, monitored and configured according to the application's security requirements.

Its effectiveness should be evaluated through authorized testing rather than assumed from its detection alone.

### 7.6 Perform Regular Network Discovery

Organizations should periodically perform authorized network discovery to maintain an accurate inventory of active devices.

### 7.7 Investigate Unknown Devices

Unexpected devices discovered during network scans should be identified and verified by the network administrator.

### 7.8 Maintain Network Documentation

Network topology diagrams, IP address assignments and device inventories should be maintained and updated regularly.

### 7.9 Conduct Further Authorized Security Assessments

Reconnaissance and host discovery provide an initial understanding of an environment. Additional authorized assessments may be required to examine open ports, running services, configurations and potential vulnerabilities.

# 8. EVIDENCE COLLECTED

The following screenshots were captured during the practical exercises to demonstrate the tools used and the results obtained.

## 8.1 W2-PM1 – Footprinting and Reconnaissance Evidence

**Evidence 1: WHOIS – Domain Registration Information**

![WHOIS Screenshot](W2-PM1/screenshots/01-whois.png)

**Evidence 2: WhatWeb – Website Technology Identification**

![WhatWeb Screenshot](W2-PM1/screenshots/02-whatweb.png)

**Evidence 3: Nslookup – DNS Resolution**

![Nslookup Screenshot](W2-PM1/screenshots/03-nslookup.png)

**Evidence 4: cURL – HTTP Response Headers**

![cURL Screenshot](W2-PM1/screenshots/04-curl.png)

**Evidence 5: WAFW00F – Web Application Firewall Detection**

![WAFW00F Screenshot](W2-PM1/screenshots/05-wafw00f.png)

**Evidence 6: DNSRecon – DNS Enumeration**

![DNSRecon Screenshot](W2-PM1/screenshots/06-dnsrecon.png)

## 8.2 W2-PM5 – Network Scanning Evidence

**Evidence 7: Nmap – Kali Virtual Network Host Discovery**

![Nmap Host Discovery Screenshot](W2-PM5/screenshots/01-kali-ping-scan.png)

**Evidence 8: Zenmap – Network Topology Visualization**

![Zenmap Topology Screenshot](W2-PM5/screenshots/02-kali-network-topology.png)

**Additional Evidence:**

The complete Nmap output and generated topology PDF are available in:

- `W2-PM5/outputs/kali-ping-scan.txt`
- `W2-PM5/outputs/W2-PM5-Network-Topology.pdf`

The detailed command outputs for the reconnaissance activities are stored in `W2-PM1/outputs/`.

# 9. CONCLUSION

During Week 2 of the NetworkWalks Cybersecurity Internship, I completed practical exercises covering footprinting, reconnaissance and network scanning.

In W2-PM1, I used six Kali Linux tools to gather information about the `networkwalks.com` domain. WHOIS helped me understand domain registration information, WhatWeb identified website technologies, Nslookup demonstrated DNS resolution, cURL provided insight into HTTP response headers, WAFW00F identified a web application firewall, and DNSRecon provided additional information about DNS infrastructure.

In W2-PM5, I used Nmap and Zenmap to perform host discovery within my Kali Linux VirtualBox virtual network. I identified two active hosts and generated a network topology document to represent the discovered network environment.

These exercises improved my understanding of how cybersecurity professionals gather information about websites and networks before conducting more advanced security assessments.

I also learned the importance of documenting commands, preserving evidence, interpreting results carefully and distinguishing between an observation and a confirmed security vulnerability.

Finally, the practical activities reinforced the importance of conducting reconnaissance and network scanning responsibly and only within an authorized scope.

# 10. AUTHOR INFORMATION

**Name:** MUTSIIRWA MATEMBERA JOSUE

**Program:** NetworkWalks Cybersecurity Internship

**Batch:** B084

**Project:** Week 2 – Penetration Testing

**LinkedIn:** [https://www.linkedin.com/in/josue-matembera-37a269407/](https://www.linkedin.com/in/josue-matembera-37a269407/)

**GitHub Repository:** [NETWORKWALKS-MUTSIIRWA-B084-WK2-PENETRATION-TESTING](https://github.com/josuemutsiirwa/NETWORKWALKS-MUTSIIRWA-B084-WK2-PENETRATION-TESTING)

---

**END OF REPORT**

*NetworkWalks Cybersecurity Internship – Week 2*
