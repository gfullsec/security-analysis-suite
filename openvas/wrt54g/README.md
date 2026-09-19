# Vulnerability Assessment – Linksys WRT54G

## 1. Overview

**Target:** Linksys WRT54G (legacy SOHO router)  
**IP Address:** `192.168.1.250`  
**Assessment Type:** Authenticated web interface review + network vulnerability scan  
**Tooling:** OpenVAS (Greenbone Community Edition), Nmap (optional), manual inspection  

This assessment focuses on a legacy Linksys WRT54G device still present in the home network, evaluating its exposure, configuration weaknesses, and known vulnerabilities.

---

## 2. Scope and Objectives

**Scope:**

- Web management interface (`http://192.168.1.250/`)
- Network services exposed by the device
- Firmware version and known CVEs
- Configuration and hardening status

**Objectives:**

- Identify exposed services and potential attack surface  
- Detect known vulnerabilities (CVEs) via OpenVAS  
- Assess configuration weaknesses (default creds, outdated firmware, insecure protocols)  
- Provide remediation steps and decommissioning recommendations  

---

## 3. Methodology

**Step 1 – Discovery**

- Identify device IP via DHCP lease table / ARP scan  
- Confirm vendor and model via web interface and banner information  

**Step 2 – Port and Service Enumeration**

- Perform TCP/UDP scan (optional, stored under raw/nmap/)  
- Confirm which services are reachable from the LAN  

**Step 3 – OpenVAS Scan**

- Create a dedicated target for 192.168.1.250  
- Use Full and fast scan configuration  
- Run vulnerability scan and export results (PDF/XML/JSON under reports/ and raw/openvas/)  

**Step 4 – Manual Review**

- Log into the web interface  
- Review:  
  - firmware version  
  - wireless security settings  
  - admin credentials policy  
  - remote management options  
  - UPnP, WPS, and other legacy features  

**Step 5 – Analysis and Reporting**

- Correlate OpenVAS findings with manual observations  
- Classify issues by severity and impact  
- Document remediation and long‑term recommendations  

---

## 4. Key Findings

> Note: This section should be updated based on the actual OpenVAS report and manual review.

**Example structure:**

- **Finding 1 – Outdated firmware with known vulnerabilities**  
  - Severity: High  
  - Description: Device is running an unsupported firmware version with multiple publicly known CVEs.  
  - Impact: Increased risk of remote or local compromise.  
  - Evidence: OpenVAS report (see reports/), vendor advisories.  
  - Recommendation: Upgrade firmware if supported; otherwise, plan decommissioning.  

- **Finding 2 – Weak or default administrative credentials**  
  - Severity: Critical  
  - Description: Administrative interface accessible with weak or default credentials.  
  - Impact: Full control of router configuration and potential pivot into the network.  
  - Recommendation: Enforce strong, unique password; disable remote management; restrict access.  

- **Finding 3 – Insecure management protocols**  
  - Severity: Medium  
  - Description: Management interface exposed over HTTP only.  
  - Impact: Credentials can be intercepted.  
  - Recommendation: Enable HTTPS if possible; otherwise, limit access and consider replacement.  

---

## 5. Risk Assessment

- Overall Risk Level: High  
- Context: Device is part of a home network but still represents a pivot point.  
- Threat Model:  
  - Local attacker on the LAN  
  - Compromised IoT device pivoting through the router  
  - Misconfiguration leading to unintended exposure  

---

## 6. Remediation Plan

**Short‑term:**

- Change admin credentials  
- Disable remote management  
- Restrict access to trusted hosts  

**Medium‑term:**

- Upgrade firmware  
- Review wireless security  
- Disable legacy features  

**Long‑term:**

- Plan decommissioning  
- Replace with modern router/firewall  
- Integrate into regular vulnerability assessments  

---

## 7. Repository Structure

openvas/wrt54g/  
├── reports/          – Exported OpenVAS reports (PDF, XML, JSON)  
├── raw/              – Raw data (Nmap results, JSON exports, screenshots)  
├── notes/            – Methodology, observations, remediation details  
├── assets/           – Diagrams, device photos, topology images  
└── README.md         – This document  

---

## 8. References

- Linksys WRT54G Series – Technical information and model variants  
  https://en.wikipedia.org/wiki/Linksys_WRT54G_series

- CVE Database – Vulnerabilities related to WRT54G  
  https://www.cve.org  
  (Search: “Linksys WRT54G”, “WRT54G firmware”)

- OpenVAS / Greenbone Documentation  
  https://docs.greenbone.net/
