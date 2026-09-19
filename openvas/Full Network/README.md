# Full Network – OpenVAS Vulnerability Assessment

This directory contains the complete vulnerability assessment performed against the entire home network using **OpenVAS (Greenbone Community Edition)**.  
The goal of this module is to provide a baseline view of the security posture of all active hosts, identify exposed services, and highlight potential weaknesses across the network.

---

## 🔎 Assessment Overview

**Task:** Full Network Scan – Complete Network  
**Date:** September 19, 2026  
**Scan Duration:** 16:34 UTC → 17:38 UTC  
**Total Hosts Scanned:** 12  
**Total Findings (after filtering QoD ≥ 70):**  
- **Medium:** 3  
- **Low:** 8  
- **Critical/High:** 0  

This baseline scan provides an initial snapshot of the network’s security state.  
Future scans can be compared against this baseline to track improvements or detect regressions.

---

## 🧩 Key Findings

### ✔ Medium Severity
Detected on host **192.168.1.135** (Smart TV):

- **SSL/TLS Renegotiation MITM Vulnerability (CVE‑2009‑3555)**  
- **SSL/TLS Renegotiation DoS Vulnerability (CVE‑2011‑1473 / CVE‑2011‑5094)**  
- **Deprecated TLSv1.0 / TLSv1.1 Protocols Enabled**

These issues are common in embedded devices such as smart TVs, which often rely on outdated SSL/TLS stacks.

### ✔ Low Severity (Multiple Hosts)
- **ICMP Timestamp Reply Information Disclosure**  
- **TCP Timestamp Information Disclosure**

These findings are informational and generally low-risk, but they can be mitigated through firewall rules or OS-level configuration.

---

## 🗂 Directory Structure

- **reports/** → Exported OpenVAS reports (PDF, XML, JSON)  
- **raw/** → Raw scan data, logs, and auxiliary outputs  
- **notes/** → Analyst notes, observations, and follow-up actions  
- **assets/** → Diagrams, screenshots, and supporting visuals  
- **README.md** → This document  

---

## 🎯 Purpose of This Module

This module serves as the foundation for:

- Establishing a **baseline security posture** of the entire network  
- Identifying devices with outdated or insecure protocols  
- Tracking changes across future scans  
- Supporting portfolio documentation through GitHub Pages  

This assessment is part of the broader **Security Analysis Suite**, which includes host-level, network-level, and OSINT-based evaluations.

