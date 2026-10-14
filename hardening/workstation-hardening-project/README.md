# Workstation Hardening Project

## Overview

This project documents the migration of a personal workstation from Windows 10 to Ubuntu 26.04 LTS, with Windows 10 retained as a virtual machine for legacy software compatibility.

The primary objective is to improve security, maintain long-term usability, and establish a Linux-based platform suitable for cybersecurity learning, development, and daily use while preserving access to applications that cannot yet be migrated.

---

## Objectives

- Replace Windows 10 as the primary operating system.
- Adopt Ubuntu 26.04 LTS as the daily-use platform.
- Maintain access to legacy Windows applications through virtualization.
- Improve system security and maintainability.
- Develop practical Linux administration skills.
- Establish a foundation for future hardening activities.
- Document the complete migration process.

---

## Target Architecture

```text
Internet
    │
    ▼
Ubuntu 26.04 LTS
    │
    ├── Firefox
    ├── GIMP
    ├── Inkscape
    └── VirtualBox
          │
          ▼
     Windows 10 VM
          ├── Photoshop
          └── Illustrator
```

---

## Documentation

| Document | Description |
|-----------|-----------|
| assessment.md | Initial assessment, requirements, risks, and decision-making process |
| assessment-es.md | Spanish version of the assessment document |
| architecture.md | Target architecture and design decisions |
| implementation.md | Implementation activities, configuration steps, and evidence |
| validation.md | Validation activities, testing results, and final project verification |

---

## Technologies

- Ubuntu 26.04 LTS
- VirtualBox
- Windows 10
- Disk2Vhd
- Firefox
- GIMP
- Inkscape
- Git
- GitHub

---

## Project Status

Current phase: Completed.

Project activities, implementation evidence, and validation results are documented throughout the project documentation set.

---

## Key Outcomes

- Linux becomes the primary operating system.
- Windows is isolated within a virtual machine.
- Existing workflows remain functional.
- Security posture is improved through platform modernization.
- The complete migration process is documented for future reference.