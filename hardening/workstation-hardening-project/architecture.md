# Architecture

## 1. Objective

The objective of this architecture is to replace Windows 10 as the primary operating system with Ubuntu 26.04 LTS while maintaining compatibility with legacy applications that cannot be migrated to Linux.

Ubuntu serves as the main operating system for daily use, Internet access, development, and cybersecurity activities. Windows 10 is retained exclusively as a virtual machine to support software with no viable Linux alternative.

This approach reduces exposure to an operating system approaching end of support while preserving access to required applications and existing workflows.

---

## 2. Design Requirements

The architecture has been designed to meet the following requirements:

- Maintain compatibility with Adobe Photoshop and Adobe Illustrator.
- Preserve access to historical documents and project files.
- Minimize security risks associated with continued Windows 10 usage.
- Extend the useful life of existing hardware.
- Provide a platform suitable for cybersecurity learning and tooling.
- Support future hardening and security monitoring activities.
- Enable efficient backup and recovery procedures.
- Reduce dependency on proprietary software where practical.

---

## 3. Architecture Components

| Component | Purpose |
|------------|------------|
| Ubuntu 26.04 LTS | Primary operating system |
| VirtualBox | Virtualization platform |
| Windows 10 Virtual Machine | Legacy software execution |
| Recovered SSD | Dedicated virtual machine storage |
| Storage Drive (ALMACÉN) | Shared data and backups |
| Firefox | Primary web browser |
| GIMP | Photoshop alternative |
| Inkscape | Illustrator alternative |
| Development Toolchain | Software development and scripting |
| Security Tooling | Cybersecurity learning and experimentation |

---

## 4. Logical Architecture

```text
                       INTERNET
                           │
                           ▼
                 Ubuntu 26.04 LTS
                    Primary Host
                           │
        ┌──────────────────┼──────────────────┐
        │                  │                  │
        ▼                  ▼                  ▼
   Applications       Storage Drive      VirtualBox
      Linux             (ALMACÉN)             │
        │                  │                  ▼
        │                  │         Windows 10 VM
        │                  │           (Legacy)
        │                  │
        └────────────┬─────┘
                     │
                     ▼
              Shared Workspace
```

---

## 5. Storage Architecture

The storage design separates the host operating system, legacy environment, and user data.

```text
Primary System Drive
└── Ubuntu 26.04 LTS

Recovered SSD
└── Windows 10 Virtual Machine
    ├── Virtual Disk
    ├── Configuration
    └── Snapshots

ALMACÉN
├── User Data
├── Documentation
├── Project Files
├── Backups
├── VM Exports
└── Shared Workspace
```

This separation simplifies backup management and reduces the risk of data loss during maintenance or migration activities.

---

## 6. Network Architecture

Ubuntu is the primary system responsible for Internet connectivity. Windows 10 is treated as a controlled legacy environment.

```text
                    INTERNET
                        │
                        ▼
               Ubuntu 26.04 LTS
                  Primary Host
                        │
          ┌─────────────┴─────────────┐
          │                           │
          ▼                           ▼
    Daily Operations            VirtualBox
                                      │
                                      ▼
                               Windows 10 VM
                              Legacy Applications
```

The architecture is designed to minimize direct dependence on Windows 10 for online activities and to centralize daily operations within Ubuntu.

---

## 7. Operational Workflow

The expected workflow is shown below.

```text
Internet
    │
    ▼
Ubuntu Host
    │
    ▼
Shared Workspace
    │
    ▼
Windows 10 VM
    │
    ▼
Photoshop / Illustrator / InDesign
    │
    ▼
Shared Workspace
    │
    ▼
Ubuntu Host
```

This workflow allows Linux to become the primary operating environment while preserving access to software that still requires Windows.

---

## 8. Security Design Principles

The solution follows several security-focused principles:

- Ubuntu acts as the primary operating system.
- Windows 10 is limited to legacy application support.
- Virtualization provides isolation between host and guest systems.
- Backups are performed before major configuration changes.
- The Windows environment should remain minimal and purpose-specific.
- Security hardening is applied to the Ubuntu host.
- Cybersecurity tooling is executed within the Linux environment whenever possible.
- Long-term dependency on Windows is reduced through gradual software migration.

---

## 9. Architecture

### 9.1 Physical Architecture

    INTERNET
        │
        ▼

Ubuntu 26.04 LTS Workstation
        │
        ├── Internal System SSD
        │
        └── Recovered SSD
              │
              ├── Documentation
              ├── Backups
              ├── Shared Workspace
              └── VM Exports


### 9.2 Logical Architecture

Ubuntu 26.04 LTS Primary Host
│
├── Security Analysis
│   ├── Lynis
│   ├── OpenVAS
│   └── Audit Scripts
│
├── Development
│   ├── Git
│   ├── Python
│   └── VS Code
│
├── Design Tools
│   ├── GIMP
│   └── Inkscape
│
└── Virtualization
    └── VirtualBox
        └── Windows 10 VM
            ├── Photoshop
            └── Illustrator


### Architecture Overview

The project is built around an Ubuntu 26.04 LTS workstation that serves as the primary platform for security analysis, development, documentation, and virtualization activities.

The physical architecture separates the operating system from the recovered SSD used for project storage, backups, shared workspace data, and virtual machine exports.

The logical architecture organizes the environment into security analysis, development, design, and virtualization domains. A dedicated Windows 10 virtual machine is maintained for Adobe-based workflows while the primary security and development activities are performed directly on the Ubuntu host.

---

## 10. Architecture Summary

The architecture establishes Ubuntu 26.04 LTS as the primary operating system while retaining Windows 10 in a controlled virtualized environment for legacy application support. This design improves maintainability, reduces operational risk, enables future hardening activities, and provides a platform for ongoing cybersecurity learning and development without sacrificing compatibility with existing workflows.