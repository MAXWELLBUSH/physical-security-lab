DNS Zone Transfer – Asset Discovery Lab (Hub 1)
Overview

In this lab, I explored DNS Zone Transfer as part of the Asset Discovery section in Hub 1. The purpose of this task was to understand how DNS zone transfers work and how misconfigured DNS servers can expose sensitive domain information.

DNS zone transfer is one of the most critical DNS misconfigurations because, if allowed publicly, it can reveal all DNS records of a domain at once, including subdomains and internal infrastructure.

Objective

The objective of this task was to:

Understand what a DNS zone transfer is

Identify authoritative name servers for a domain

Test whether a DNS server allows zone transfers

Observe the type of information exposed during a successful zone transfer

Learn why zone transfers are dangerous if misconfigured

Environment Setup

Operating System: Kali Linux

Shell: training-shell

Lab Platform: Hub 1 – Asset Discovery

Browser: Kali Firefox

Lab Access: http://localhost

I verified the lab was running by executing:

running


This confirmed that hub-1 was active.

What is a DNS Zone Transfer?

A DNS zone transfer is a process where a DNS server sends a full copy of its DNS records (zone file) to another DNS server.

Legitimate purpose:

Synchronizing DNS records between primary and secondary DNS servers

Security risk:

If zone transfers are allowed to anyone, attackers can download the entire DNS database of a domain.

Why DNS Zone Transfer Matters in Asset Discovery

A successful zone transfer can reveal:

All subdomains

Internal hostnames

IP addresses

Mail servers

Development or staging environments

This information gives an attacker a complete map of the target’s assets.

Tools Used

dig

nslookup

Task Execution and Commands Used
1️⃣ Identifying Name Servers

Before attempting a zone transfer, I first identified the authoritative name servers for the domain.

Using nslookup:

nslookup -type=NS targetdomain.com


Or using dig:

dig NS targetdomain.com


Why this step is important:
Zone transfers can only be requested from authoritative name servers, not random DNS servers.

2️⃣ Attempting DNS Zone Transfer Using dig

Once I identified the name server, I attempted a zone transfer using the following command:

dig AXFR targetdomain.com @ns1.targetdomain.com


Explanation of the command:

AXFR → Request a full zone transfer

targetdomain.com → The target domain

@ns1.targetdomain.com → The authoritative name server

3️⃣ Observing the Response
❌ If Zone Transfer is Blocked:

The server responds with an error such as:

Transfer failed.


This indicates proper DNS security configuration.

✅ If Zone Transfer is Successful:

The server returns:

All DNS records

Subdomains

IP addresses

Mail servers

This confirms a critical DNS misconfiguration.

Key Observations

Zone transfer attempts only work on authoritative name servers

A successful transfer exposes the entire DNS structure

Most modern systems block zone transfers by default

This vulnerability provides massive asset discovery in a single step

Security Impact

A public DNS zone transfer can lead to:

Exposure of hidden subdomains

Discovery of internal systems

Easier network mapping

Increased attack surface

Because of this, zone transfers should only be allowed between trusted DNS servers.

Limitations

Zone transfers rarely succeed on well-configured systems

Requires knowledge of authoritative name servers

Modern DNS security practices usually block AXFR requests

Conclusion

This lab demonstrated how DNS zone transfers work and why they are dangerous when misconfigured. I learned how to identify authoritative name servers and attempt a zone transfer using dig.

Although zone transfers are often blocked, testing for them is essential because a successful transfer reveals complete domain asset information, making it one of the most powerful asset discovery techniques.