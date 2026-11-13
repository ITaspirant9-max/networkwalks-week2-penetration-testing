# W2-PM1 – Footprinting with Multiple Tools

## Objective
Perform footprinting and information gathering on the assigned Networkwalks domain using Kali Linux tools.

## Target
networkwalks.com

## Tools Used

1. WHOIS – Domain registration and registrar information.
2. WhatWeb – Website technology fingerprinting.
3. Nslookup – DNS lookup and IP resolution.
4. cURL – HTTP response headers inspection.
5. WAFW00F – Web Application Firewall detection.
6. DNSRecon – DNS record enumeration.

## Key Findings

- WHOIS: Collected domain registration, registrar and nameserver information.
- WhatWeb: Identified Apache and WordPress technologies.
- Nslookup: Resolved networkwalks.com to 192.232.216.135.
- cURL: Received HTTP/2 200 response.
- WAFW00F: Identified ModSecurity (SpiderLabs) WAF.
- DNSRecon: Enumerated 8 DNS records, including A, NS, SOA, MX and SRV records.

## Evidence

Each task has a corresponding text output file and terminal screenshots.

## Project Structure

- task1-whois.txt
- task2-whatweb.txt
- task3-nslookup.txt
- task4-curl.txt
- task5-wafw00f.txt
- task6-dnsrecon.txt
- Screenshots/

## Environment
Kali Linux 2026.2 running in Oracle VirtualBox.

## Note
This work was performed as part of the Networkwalks cybersecurity internship.
