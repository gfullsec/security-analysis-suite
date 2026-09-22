# Vulnerability Assessment – Linksys WRT54G

## 1. Overview

**Target:** Linksys WRT54G (legacy SOHO router, lab-isolated)  
**IP Address:** `192.168.1.250`  
**Assessment Type:** Authenticated web interface review + network vulnerability scan  
**Tooling:** OpenVAS (Greenbone Community Edition), Nmap (optional), manual inspection  

This assessment focuses on a legacy Linksys WRT54G device that was **intentionally isolated in a lab environment**, connected to a dedicated Ethernet port and separated from the home Wi‑Fi network. The goal is to evaluate its exposure, configuration weaknesses, and known vulnerabilities without impacting the production network.

---

## 2. Scope and Objectives

**Scope:**

- Web management interface (`http://192.168.1.250/`) in an isolated lab segment  
- Network services exposed by the device  
- Firmware version and known CVEs  
- Configuration and hardening status  

**Objectives:**

- Identify exposed services and potential attack surface  
- Detect known vulnerabilities (CVEs) via OpenVAS  
- Assess configuration weaknesses (default creds, outdated firmware, insecure protocols)  
- Provide remediation steps and recommendations for safe reuse (lab, IoT segment) or decommissioning  

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

## 4. Key Findings

**Example structure:**

- **Finding 1 – Insecure default configuration in lab context**  
  - Severity: Critical  
  - Description: Device running with near-default settings, including weak or default credentials and insecure management exposure.  
  - Impact: Full control of router configuration and potential pivot within any network segment where it is deployed.  
  - Recommendation: Enforce strong, unique credentials; harden configuration; restrict access to trusted hosts; avoid using as primary router.

- **Finding 2 – Insecure management protocols (HTTP only)**  
  - Severity: Medium  
  - Description: Management interface exposed over cleartext HTTP.  
  - Impact: Credentials can be intercepted by an attacker with access to the same network segment.  
  - Recommendation: Enable HTTPS if possible; otherwise, strictly limit access and consider replacement or use only in isolated lab/IoT environments.

- **Finding 3 – Legacy firmware and limited vendor support**  
  - Severity: Medium  
  - Description: Device relies on legacy firmware with limited or no vendor support.  
  - Impact: Increased long-term risk due to unpatched vulnerabilities and lack of security updates.  
  - Recommendation: Upgrade to the latest available firmware if possible; otherwise, restrict usage to lab or non-critical roles and plan eventual decommissioning.

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
