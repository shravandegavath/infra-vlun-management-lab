# Infrastructure Vulnerablilty Management - Remediation Plan

Prepared by : shravan Degavath
Tools Used: Nessus Essentials.
Target Hosst : Internal Network and DMZ - 192.168.xxx.xxx, 192.168.xxx.xxx

Summary
This document provides a formal remediation plan for security vulnerabilities identified during the basic vulnerability assessment performed on internal infrastructure systems. The goal is to mitigate risk by prioritizing vulnerabilities based on their severity (CVSS), business impact, and ease of exploitation.


##1. SWEET32 - SSL Medium Strength Cipher Suites Supported
Risk Level: High
CVSS Base Score: 5.0
Host: 192.168.240.100
Port: 3389 (Remote Desktop Protocol)
CVE Reference: CVE-2016-2183

Summary
The system is configured to support 64-bit block ciphers such as 3DES, which are vulnerable to the SWEET32 birthday attack. Exploiting this may allow partial plaintext recovery in secure communications.

## Remediation:
1.Disable 3DES and other legacy cipher suites on the server.
2.Enforce modern protocols (TLS 1.2 and above).
## Windows Servers:
 a.Open gpedit.msc
 b.Navigate to Computer Configuration > Administrative Templates > Network > SSL Configuration Settings
 c.Modify the SSL Cipher Suite order to exclude 3DES.
3.Reboot the system or restart affected services. 