# PENETRATION TESTING REPORT
## Footprinting & Network Scanning Phases

**Project:** W2-PM-FINAL  
**Program:** Networkwalks Cybersecurity Internship  
**Prepared By:** Abdul Qadir Lakho  
**Batch:** B084B  
**Report Date:** 11 November 2026  
**Modules Completed:** W2-PM1 and W2-PM5

---

# 1. Liability Disclaimer

This report documents educational cybersecurity activities performed within the assigned project scope.

The W2-PM1 activities involved public-information footprinting of the assigned Networkwalks domain. The W2-PM5 activities were performed within my own VirtualBox NAT Network lab.

All activities were conducted for educational and research purposes. No exploitation, unauthorized access, or destructive testing was performed.

These findings should not be interpreted as confirmation of vulnerabilities.

# 2. Executive Summary

This report documents two cybersecurity project modules completed during Week 2 of the Networkwalks internship.

W2-PM1 focused on footprinting and reconnaissance using six Kali Linux tools:

- WHOIS
- WhatWeb
- Nslookup
- cURL
- WAFW00F
- DNSRecon

W2-PM5 focused on network discovery using Zenmap and Nmap in a VirtualBox lab environment.

The footprinting activities collected domain registration information, website technology details, DNS records, HTTP response headers, and Web Application Firewall information.

The network scanning activity identified three live IP addresses on the local VirtualBox subnet, recorded their available MAC addresses, and produced a network topology PDF.

The exercises demonstrated how reconnaissance and network discovery help security professionals understand an environment before conducting further authorized security assessments.

# 3. Introduction

Footprinting and network scanning are important early stages of a cybersecurity assessment.

Footprinting collects publicly available information about a domain, website, and its infrastructure. Network scanning helps identify active hosts and understand the structure of a network.

The purpose of these activities was to practise reconnaissance, host discovery, information collection, technical analysis, and security documentation using Kali Linux and Zenmap.

# 4. Scope and Methodology

## 4.1 W2-PM1 Scope

Target domain: networkwalks.com

The following six tools were used:

1. WHOIS
2. WhatWeb
3. Nslookup
4. cURL
5. WAFW00F
6. DNSRecon

These tools were used for domain registration lookup, website fingerprinting, DNS resolution, HTTP header inspection, WAF identification, and DNS enumeration.

## 4.2 W2-PM5 Scope

Testing environment: Oracle VirtualBox NAT Network

- Operating System: Kali Linux 2026.2
- Network Interface: eth0
- Kali IP Address: 10.0.0.2
- Subnet: 10.0.0.0/24
- Broadcast Address: 10.0.0.255
- Scan Type: Ping Scan / Host Discovery

The scan was limited to the local VirtualBox lab subnet.

# 5. Tools Used

| Tool | Purpose |
|---|---|
| WHOIS | Domain registration information |
| WhatWeb | Website technology fingerprinting |
| Nslookup | DNS resolution |
| cURL | HTTP response header inspection |
| WAFW00F | Web Application Firewall identification |
| DNSRecon | DNS record enumeration |
| Zenmap | Graphical network scanning interface |
| Nmap | Network discovery engine |

# 6. Activities Performed and Results

## 6.1 W2-PM1 – Footprinting and Reconnaissance

### Task 1 – WHOIS

Command:

whois networkwalks.com

Findings:

- Registrar identified as GoDaddy.com, LLC.
- Domain creation date reported as 6 November 2019.
- Registry expiry date reported as 6 November 2027.
- Nameservers returned: NS6135.HOSTGATOR.COM, NS6136.HOSTGATOR.COM, NS29.DOMAINCONTROL.COM, and NS30.DOMAINCONTROL.COM.
- WHOIS displayed registry-level and registrar-level timestamps with different time-zone offsets.

Purpose:

WHOIS provides publicly available domain registration information and helps understand domain ownership and registration infrastructure.

### Task 2 – WhatWeb

Command:

whatweb networkwalks.com

Findings:

- Apache web server identified.
- WordPress 7.1.4 identified.
- Bootstrap technology fingerprint reported by WhatWeb.
- jQuery 3.7.1 identified.
- WordPress Download Manager 3.3.76 identified.
- Google Tag Manager detected.

The reported technology versions are fingerprinting observations and do not independently establish that the software is vulnerable.

Purpose:

WhatWeb helps identify technologies used by a website.

### Task 3 – Nslookup

Command:

nslookup networkwalks.com

Finding:

The domain resolved to:

192.232.216.135

Purpose:

Nslookup converts a domain name into an IP address using DNS.

### Task 4 – cURL

Command:

curl -I https://networkwalks.com

Findings:

- HTTP response: 200 OK
- HTTP protocol: HTTP/2
- Apache server information was returned.
- WordPress-related response headers were observed.
- A WordPress REST API link was present.

Purpose:

cURL was used to inspect HTTP response headers without downloading the full web page.

### Task 5 – WAFW00F

Command:

wafw00f https://networkwalks.com

Finding:

WAFW00F identified ModSecurity (SpiderLabs) as the Web Application Firewall.

Purpose:

WAFW00F helps identify whether a website is protected by a Web Application Firewall.

This detection is a fingerprinting result and does not confirm how effectively the firewall blocks attacks.

### Task 6 – DNSRecon

Command:

dnsrecon -d networkwalks.com

Findings:

- SOA: ns6135.hostgator.com (50.87.144.87).
- NS: ns6135.hostgator.com (50.87.144.87).
- NS: ns6136.hostgator.com (192.232.216.131).
- MX: mail.networkwalks.com (192.232.216.135).
- A: networkwalks.com (192.232.216.135).
- SRV: Eight autodiscover service endpoints were listed, using cpanelemaildiscovery.cpanel.net on port 443.
- DNSRecon summary displayed: 8 Records Found.

The DNSSEC query returned a no-answer message. This is recorded as an observation and is not treated as a confirmed security vulnerability.

Purpose:

DNSRecon helps enumerate publicly available DNS records and understand DNS infrastructure.

## 6.2 W2-PM5 – Zenmap Network Scanning

### Task 1 – Zenmap Installation

Command:

command -v zenmap

Result:

/usr/bin/zenmap

Zenmap was already installed and successfully verified.

### Task 2 – Local IP Address and Subnet

Command:

ip -4 addr show eth0

Results:

- Interface: eth0
- IP Address: 10.0.0.2
- Prefix: /24
- Network: 10.0.0.0/24
- Broadcast: 10.0.0.255

### Task 3 – Live Host Discovery

Zenmap was launched and the Ping Scan profile was used.

Target:

10.0.0.0/24

Equivalent Nmap command:

nmap -sn 10.0.0.0/24

Results:

Three live IP addresses were discovered:

- 10.0.0.1
- 10.0.0.2
- 10.0.0.3

The scan reported 256 IP addresses scanned and three hosts up.

### Task 4 – Live Host Count

The discovered host count was recorded from the scan output.

Result:

3 live hosts.

### Task 5 – IP Addresses

The following IP addresses were recorded:

| No. | IP Address |
|---|---|
| 1 | 10.0.0.1 |
| 2 | 10.0.0.3 |
| 3 | 10.0.0.2 |

### Task 6 – MAC Addresses

The scan and local interface information returned:

| IP Address | MAC Address |
|---|---|
| 10.0.0.1 | 52:54:00:12:35:00 |
| 10.0.0.3 | 52:54:00:12:35:00 |
| 10.0.0.2 | 08:00:27:5a:87:bc |

Note:

The same MAC address was reported for 10.0.0.1 and 10.0.0.3. These observations were recorded as returned by the virtualized lab environment. Their individual device identities were not independently verified.

### Task 7 – Network Topology

The Zenmap Topology view was used to generate a network diagram.

The Legend was enabled and the topology was exported as a PDF.

Evidence file:

W2-PM5-Network-Topology.pdf

# 7. Risk Analysis and Observations

The following table records potential security observations from the completed exercises.

| Observation | Evidence | Potential Security Relevance |
|---|---|---|
| Website technology information is publicly identifiable | WhatWeb results | May help an attacker identify technologies requiring further security review |
| Domain IP address is publicly resolvable | Nslookup results | Helps identify the hosting address |
| HTTP headers expose technical information | cURL results | May assist technology fingerprinting |
| WAF technology is identifiable | WAFW00F results | Reveals information about the website's defensive architecture |
| DNS infrastructure records are publicly available | DNSRecon results | Helps map domain and mail infrastructure |
| Three live hosts were discovered | Zenmap Ping Scan | Helps administrators understand active devices in their lab network |

These are observations, not confirmed vulnerabilities.

No CVSS scores have been assigned because vulnerability validation and exploitation were outside the completed project scope.

# 8. Recommendations

Based on the observations, the following security improvements are recommended:

1. Regularly review publicly exposed website technology information.
2. Keep CMS platforms, plugins, and web server software updated.
3. Review HTTP response headers and avoid unnecessary technical information disclosure.
4. Periodically review DNS records and remove obsolete entries.
5. Keep Web Application Firewall rules updated and monitor security logs.
6. Perform regular network discovery within authorized networks.
7. Investigate unexpected devices and maintain an accurate inventory of network assets.
8. Maintain updated network topology documentation.
9. Ensure all security testing is performed within an approved scope.

# 9. Limitations

The activities were limited to the assigned footprinting tasks and host discovery exercises.

- No exploitation was performed.
- No confirmed vulnerability assessment was completed.
- The Zenmap Ping Scan identified live hosts but did not establish their running services or open ports.
- MAC address information was recorded as returned by the virtualized environment.
- The results represent observations made during the lab exercises.

# 10. Conclusion

During Week 2 of the Networkwalks Cybersecurity Internship, I completed practical activities covering footprinting, reconnaissance, and network scanning.

In W2-PM1, I used six Kali Linux tools to collect domain registration, website technology, DNS, HTTP header, and WAF information.

In W2-PM5, I used Zenmap and Nmap to discover live hosts on my VirtualBox NAT Network, record their IP and MAC addresses, and export a network topology PDF.

These exercises improved my understanding of reconnaissance, host discovery, network mapping, command-line tools, and technical reporting.

The most important lesson was that accurate documentation is essential in cybersecurity. Findings must be supported by evidence, limitations must be clearly stated, and all testing must remain within an authorized scope.

# 11. Evidence Collected

## W2-PM1 – Footprinting

Evidence includes:

- Six task output text files.
- Terminal screenshots.
- W2-PM1 README documentation.

## W2-PM5 – Zenmap Network Scanning

Evidence includes:

- Seven task output text files.
- Zenmap scan screenshot.
- Network topology screenshot.
- Network topology PDF.
- W2-PM5 README documentation.

Supporting evidence will be organized in the Evidence directory.

---

**End of Report**

EOF    


