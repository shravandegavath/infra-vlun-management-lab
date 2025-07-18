
# Infrastructure Vulnerability Management - Remediation Plan  
**Author:** Shravan Degavath  
**Tools Used:** pfSense, Kali Linux, Nessus Essentials, Nmap, CVSS

---

## Executive Summary

This remediation plan documents the vulnerabilities identified through Nessus scanning of a segmented virtual lab environment configured with pfSense, Windows 10, and Ubuntu Desktop machines. The goal is to assess the internal infrastructure for known security issues and define actionable mitigation steps aligned with industry standards.

---

## Objectives

- Identify and assess system vulnerabilities using Nessus Essentials.
- Analyze severity using CVSS v2 base scores.
- Recommend targeted remediation for high/medium-risks.
- Strengthen the system security posture through prioritized patching and configuration hardening.



## High and Medium Severity Findings

### 1. SWEET32 - SSL Medium Strength Cipher Suites Supported  
- **Risk Level:** High  
- **CVSS v2 Score:** 5.0  
- **Host:** 192.168.240.100  
- **Port:** 3389  
- **CVE:** CVE-2016-2183

**Description:**  
The host supports 64-bit block ciphers (e.g., 3DES) making it vulnerable to the SWEET32 birthday attack.

**Remediation Steps:**  
- Disable 3DES and legacy cipher suites on the server.
- Restrict to TLS 1.2 or 1.3 only.
- On Windows, oepn gpedit.msc, go to computer configuration-> Administrative templates -> networl -> SSL configuration settings.
- upate the SSL cipher suite order to exclude 3DES.
- Restart the system or services.

---

### 2. SSL Self-Signed Certificate  
- **Risk Level:** Medium  
- **CVSS v2 Score:** 6.4  
- **Host:** 192.168.240.100  
- **Port:** 3389

**Description:**  
The server presents a self-signed certificate, which cannt be verified and may lead to  potential MITM attacks.

**Remediation Steps:**  
- Replace the self signed certificate with a trusted certitifcate authority(CA).
- For internal services, configure an internal CA and distribute root certertificate accordingly.
- Restart the service using the new certificate.

---

### 3. SSL Certificate Cannot Be Trusted  
- **Risk Level:** Medium  
- **CVSS v2 Score:** 6.4  
- **Host:** 192.168.240.100  
- **Port:** 3389

**Description:**  
The certificate presented by the server is not signed by a recognized CA, reducing client trust.

**Remediation Steps:**  
- Obtain a certificate from a trusted CA.
- Ensure the complete certificate chain is installed and configured correctly.
- Use openssl s_client to verify certificate chain after installation.

---

### 4. TLS 1.0 Protocol Enabled  
- **Risk Level:** Medium  
- **CVSS v2 Score:** 6.1  
- **Host:** 192.168.240.100  
- **Port:** 3389

**Description:**  
TLS 1.0 is an outdated protocol vulnerable to known exploits like BEAST and POODLE.

**Remediation Steps:**  
- Disable TLS 1.0 and TLS 1.1 in the server settings or registry.
- Enable only TLS 1.2 and TLS 1.3 in server configurations.
- Reboot the system or restart affected services after changes.

---

## Supporting Files

| File | Description |
|------|-------------|
| Basic_Scan_Report.csv | Exported Nessus scan results |
| vuln_register.xlsx    | Custom vulnerability tracking dashboard |
| screenshots          | Visual evidence of scans and Nessus findings |
| README.md             | Project overview, setup, and skills used |

---

## ✅ Next Steps

- Implement remediation steps on affected hosts.
- Re-run Nessus scans post-fix to validate.
- Monitor continuously and automate scans where possible.

---

## 🛡️ Skills Demonstrated

- Vulnerability Scanning (Nessus Essentials)  
- CVSS Scoring and Analysis  
- Remediation Planning  
- Markdown Documentation  
- Network Segmentation via pfSense  
- Virtual Lab Deployment and Hardening  

---
