Overview

In this lab, I used DNS Nslookup as part of the Asset Discovery section in Hub 1. The goal was to understand how DNS records can be queried interactively and non-interactively to discover assets such as domains, subdomains, IP addresses, and name servers.

Nslookup is a fundamental DNS enumeration tool that helps identify how a domain resolves and what infrastructure exists behind it. This knowledge is critical during the reconnaissance phase of security testing.

Objective

The objective of this task was to:

Query DNS records using nslookup

Identify IP addresses linked to domains

Discover authoritative name servers

Understand how DNS queries reveal assets during reconnaissance

Environment Setup

Operating System: Kali Linux

Shell: training-shell

Lab Platform: Hub 1 – Asset Discovery

Browser Access: http://localhost

I confirmed the lab was running by executing:

running


This showed that hub-1 was active.

Tool Description: Nslookup

nslookup (Name Server Lookup) is a DNS query tool used to retrieve information from DNS servers. It can be used in:

Non-interactive mode – single command execution

Interactive mode – continuous querying of DNS records

Nslookup is useful for quick DNS lookups and validation of DNS configurations.

Why Nslookup is Important in Asset Discovery

Nslookup helps in:

Mapping domains to IP addresses

Identifying DNS infrastructure

Finding name servers (NS records)

Discovering potential subdomains

Verifying DNS misconfigurations

This information helps attackers or testers understand the attack surface of a target.

Task Execution and Commands Used
1. Basic Domain Lookup

To find the IP address associated with a domain, I ran:

nslookup targetdomain.com


What this does:

Queries the default DNS server

Returns the IP address of the domain

Why this matters:
This reveals the server hosting the application, which can later be scanned for open ports or vulnerabilities.

2. Querying a Specific DNS Record Type
Name Server (NS) Records
nslookup -type=NS targetdomain.com


Result:

Lists authoritative name servers for the domain

Security relevance:
Knowing name servers helps identify DNS providers and can be useful when testing for DNS-related weaknesses like zone transfers.

A Record
nslookup -type=A targetdomain.com


Purpose:

Retrieves IPv4 addresses linked to the domain

MX Record
nslookup -type=MX targetdomain.com


Purpose:

Identifies mail servers handling emails for the domain

Security relevance:
Mail servers are often separate assets and can be targeted for phishing or misconfiguration testing.

3. Using Interactive Mode

I started interactive mode by typing:

nslookup


Inside interactive mode, I could run:

set type=NS
targetdomain.com


or

set type=A
targetdomain.com


To exit interactive mode:

exit


Why interactive mode is useful:
It allows multiple DNS queries without restarting the tool, making exploration faster.

4. Querying a Specific DNS Server

I queried a specific name server directly:

nslookup targetdomain.com ns1.targetdomain.com


Why this is important:

Allows verification of DNS responses from authoritative servers

Helps detect inconsistencies or misconfigurations

Key Observations

Nslookup quickly revealed IP addresses linked to the domain

Name servers were clearly identified

DNS data provided insight into backend infrastructure

The tool is simple but powerful for early reconnaissance

Limitations of Nslookup

Limited automation compared to tools like Amass

No built-in brute-forcing of subdomains

Less detailed output than dig

Because of these limitations, nslookup is best used as a basic reconnaissance tool, often combined with more advanced asset discovery tools.

Conclusion

This lab helped me understand how DNS Nslookup fits into the asset discovery phase. I learned how to extract valuable DNS information such as IP addresses, name servers, and mail servers, all of which represent potential assets.

Nslookup is easy to use, fast, and effective for initial DNS enumeration, making it a valuable tool before moving on to advanced enumeration tools like Subfinder and Amass.