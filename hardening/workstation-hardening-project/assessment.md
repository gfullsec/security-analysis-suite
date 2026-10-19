# Initial Analysis of the Legacy System

## Summary

This document presents the initial assessment of the computer used for professional graphic design in a screen-printing workshop, along with the technical considerations preceding migration to a more secure virtualization-based architecture.

The objective of this phase is to identify risks, limitations, dependencies, and opportunities for improvement before making any changes to the system.

---

## Context

The computer is used daily for graphic design and document production.

The applications and peripherals currently in use are essential to the user's professional work and must remain operational during and after the migration.

The project is not solely intended to improve the system's security posture. It also aims to extend the service life of a platform that remains functional for the user's needs, avoiding premature hardware replacement through a combination of virtualization, free software, and the gradual modernization of the work environment.

Additionally, this strategy helps reduce reliance on new proprietary software purchases and recurring subscription models, supporting a gradual transition to open tools that can ensure business continuity without increasing licensing costs.

### Critical Software

- Adobe Photoshop CS6
- Adobe Illustrator CS6
- Adobe InDesign CS4

### Critical Hardware

- Wacom CTL-460 graphics tablet
![Wacom Bamboo CTL-460 graphics tablet](./images/assessments/Captura%20desde%202026-10-13%2012-56-31.png)

![Wacom Bamboo CTL-460 graphics tablet](./images/assessments/Captura%20desde%202026-10-13%2013-00-03.png)

- Canon MF3010 printer and scanner
![Impresora 2](./images/assessments/Captura%20desde%202026-10-19%2019-01-53.png)

- HP LaserJet 5000N printer
![Impresora 1](./images/assessments/Captura%20desde%202026-10-19%2019-01-18.png)

### User Profile

- Non-technical user
- Daily reliance on the computer for professional work
- Need to minimize service interruptions
- Need to avoid increasing licensing or new subscription costs given the business's operating scale


---

## Hardware Inventory

### Main Computer

The computer was designed, purchased, and assembled in 2012 specifically to meet the needs of a professional graphic design environment.

The platform was initially deployed with Windows 7 and designed for long-term use, prioritizing reliable, easily maintainable components with an estimated service life longer than that typical of a desktop computer of its era.

Fourteen years after it was put into service, the system remains functional for the user's current needs and continues to support daily professional work without significant performance limitations.

The main limitation identified is not related to the hardware but to the lifecycle of the software in use. The platform does not meet Microsoft's requirements for an official upgrade to Windows 11, while Windows 10 has reached the end of its support lifecycle.

This makes operating system obsolescence the primary risk factor, even though the hardware remains fully usable.

#### Main Configuration

- CPU: Intel Core i5-3330
- Motherboard: Gigabyte GA-Z77-DS3H
- RAM: 16 GB DDR3-1333
- Graphics card: NVIDIA GeForce GT 630 2 GB
- Power supply: Zalman ZM700-GT
- CPU cooler: Zalman CNPS9900A LED
- Case: Zalman Z9

#### Assessment

Despite its age, the platform continues to provide sufficient resources for:

- Ubuntu 26.04 LTS as the host operating system.
- Windows 10 virtualization using VirtualBox.
- Running graphic design applications.
- Simultaneous use of productivity tools and a web browser.

The preliminary assessment indicates that there is no immediate need to replace the hardware and that the technology migration can be carried out using the existing infrastructure.

The proposed strategy aims to extend the platform's operational life by at least another decade through virtualization, an upgrade of the host operating system, and a gradual reduction in reliance on proprietary and unsupported software.

Considering the current state of the hardware and the user's actual needs, no technical limitations have been identified that would require immediate replacement of the platform.

![Main computer tower](./images/assessments/Captura%20desde%202026-10-13%2012-36-44.png)

![Main computer tower](./images/assessments/Captura%20desde%202026-10-13%2012-36-06.png)

![CPU-Z information](./images/assessments/Captura%20de%20pantalla%202026-10-06%20212016.png)

![CPU-Z information](./images/assessments/Captura%20de%20pantalla%202026-10-06%20212037.png)

![CPU-Z information](./images/assessments/Captura%20de%20pantalla%202026-10-06%20212058.png)

![CPU-Z information](./images/assessments/Captura%20de%20pantalla%202026-10-06%20212121.png)

![CPU-Z information](./images/assessments/Captura%20de%20pantalla%202026-10-06%20212146.png)

![CPU-Z information](./images/assessments/Captura%20de%20pantalla%202026-10-06%20212224.png)

![CPU-Z information](./images/assessments/Captura%20de%20pantalla%202026-10-06%20212532.png)

![Computer components and purchase prices](./images/assessments/Captura%20desde%202026-10-13%2018-23-22.png)

### Current Storage

- Disk 1: 1 TB (current Windows 10 system)
- Disk 2: 1 TB

![Windows Disk Management showing the partitions](./images/assessments/Captura%20de%20pantalla%202026-10-06%20214011.png)

### Components Planned for the Migration

Components from other computers will be reused to extend the service life of the current platform and improve its performance during the transition.

Components to be added:

- Reclaimed SSD to host the Windows 10 virtual machine.
![OCZ Agility 3 2.5-inch SSD](./images/assessments/Captura%20desde%202026-10-13%2012-37-38.png)

![OCZ Agility 3 2.5-inch SSD](./images/assessments/Captura%20desde%202026-10-13%2012-37-03.png)

- Internal Wi-Fi network card to provide connectivity to the Ubuntu host system.

![TP-Link TL-WN951N 300 Mbps PCI Wi-Fi adapter](./images/assessments/Captura%20desde%202026-10-13%2012-38-08.png)


---

## Current Situation

### Operating System

The computer currently uses Windows 10 as its primary operating system.

![About Windows 10 Home, version 22H2](./images/assessments/Captura%20de%20pantalla%202026-10-06%20213052.png)

### Identified Risks

- Reliance on an unsupported operating system.
- Exposure to vulnerabilities without the possibility of receiving future security updates.
- Reliance on legacy applications for professional work.
- Reliance on peripherals with limited compatibility outside the Windows environment.

### Limitations

Completely replacing the Windows environment is not currently feasible because of the reliance on Adobe Photoshop, Adobe Illustrator, Adobe InDesign, and the workshop's peripheral ecosystem.

---
## Peripheral Compatibility Assessment

The viability of the project depends largely on the compatibility of the devices used daily by the user.

A preliminary assessment of the critical peripherals and their planned integration into the target architecture was carried out before beginning the migration.

### Wacom CTL-460

**Use:**

- Graphic design.
- Illustration.
- Editing with a graphics tablet.

**Planned Strategy:**

- Native compatibility in Ubuntu using the drivers included in Linux.
- Direct use with applications such as GIMP and Inkscape.
- Use in Windows 10 through USB passthrough from VirtualBox when necessary.

**Objective:**

Maintain the graphics tablet's functionality in both the Linux and Windows environments during the transition period.

**Estimated Risk Level:** Low


### Canon MF3010

**Use:**

- Document scanning.
- Digitization of graphic material.

**Planned Strategy:**

- Evaluate native compatibility with Ubuntu.
- Validate both printing and scanning functions.
- If necessary, use USB passthrough to the Windows 10 virtual machine to ensure operational continuity.

**Objective:**

Use the Canon MF3010 directly from Ubuntu whenever possible, reducing reliance on the Windows environment.

USB passthrough will be retained as a compatibility and contingency mechanism.

**Notes:**

Linux compatibility is not guaranteed for all device functions, especially those related to the scanner, so specific tests will need to be carried out during the implementation phase.

**Estimated Risk Level:** Medium


### HP LaserJet 5000N

**Use:**

- Document printing.
- Printing graphic design work.

**Planned Strategy:**

- Direct integration with Ubuntu.
- Receive documents through a shared folder from the virtual machine.
- Manage printing from the host system.

**Objective:**

Manage all printing from Ubuntu to reduce reliance on Windows and simplify the daily workflow.

**Estimated Risk Level:** Low


### Expected Outcome

```text
Ubuntu
├── HP LaserJet 5000N
├── Canon MF3010
├── Wacom CTL-460
├── GIMP
├── Inkscape
└── Browsing and sensitive tasks

Windows 10 VM
├── Photoshop
└── Illustrator
└── InDesign
```

The Wacom tablet must work in both Ubuntu and virtualized Windows 10, allowing it to be used with native Linux applications (GIMP and Inkscape) as well as with the Adobe applications that remain in the virtual machine during the transition period.

The objective is for as much hardware as possible to work directly from Ubuntu, reserving the virtual machine solely for the Adobe applications that are still needed during the transition.

## Issue Identified During Planning

As part of the migration strategy, a full image of the Windows 10 system will be created using Macrium Reflect and later restored inside a virtual machine.

An important limitation was identified during the initial review:

```text
The current Windows installation is larger than the available capacity of the reclaimed SSD.
```

This prevents the full image from being restored directly to the SSD intended to host the future virtual machine.


---

## Planned Corrective Action

Before generating the final system image, the space occupied by Windows must be reduced.

### Strategy

1. Identify non-critical files stored on the primary drive.
2. Move historical documents and large data files to the 1 TB storage drive.
3. Keep only the operating system, applications, and work data needed for daily operations.
4. Verify the new installation size.
5. Create the final system image using Macrium Reflect.

### Expected Outcome

```text
Windows 10 reduced to a size compatible with the available SSD.
```

This will:

- Produce a smaller image.
- Reduce copy and restoration times.
- Improve the performance of the future virtual machine.
- Simplify maintenance and backup tasks.


---

## Technology Transition Strategy

In addition to improving the environment's security, the project aims to gradually reduce reliance on proprietary software and services that affect the user's operational continuity.

The adopted strategy does not seek to replace the current workflow immediately, but rather to facilitate a gradual transition to modern, sustainable alternatives.

### Objectives

- Maintain current productivity without interruption.
- Reduce reliance on Windows 10.
- Gradually reduce reliance on the Adobe ecosystem.
- Introduce Linux-compatible tools.
- Support the gradual learning of new applications.
- Avoid abrupt changes for a non-technical user.

### GIMP as an Alternative to Photoshop

Although Photoshop will remain available in the Windows 10 virtual machine, GIMP will be installed in Ubuntu to support a gradual migration to a tool native to the host operating system.

Having both applications available will allow the user to:

- Compare workflows.
- Reduce reliance on Photoshop.
- Identify tasks that can be completed entirely in Linux.
- Improve the user's technological independence.

### Inkscape as an Alternative to Illustrator

In addition to Photoshop, the user used Adobe Illustrator as a vector design tool in the workshop's regular workflow. However, during preliminary validation, the software was found not to work.

To reduce reliance on proprietary software and facilitate a future full migration to Linux, Inkscape will be evaluated as a free alternative for illustration and vector design work.

Initially having both Illustrator and Inkscape available will allow the user to:

- Compare workflows.
- Gradually reduce reliance on Illustrator.
- Maintain compatibility with standard vector formats.
- Encourage the adoption of tools native to Ubuntu.
- Improve the user's technological independence.

### Scribus as an Alternative to InDesign

Adobe InDesign CS4 was also part of the user's workflow, but validation showed that its license appears to have expired and the application does not start. For this reason, Scribus will be evaluated as a free alternative for page layout and desktop publishing in Ubuntu, verifying its suitability for the workflow and compatibility with existing documents.

### Adoption Strategy

The transition will not be immediate.

During an initial phase, the following applications will coexist:

```text
Photoshop → GIMP
Illustrator → Inkscape
InDesign → Scribus
```

This will allow the user to become familiar with the new tools without affecting the business's daily productivity.


### Assistance Using Artificial Intelligence

A Proton account will be created for the user, providing access to the tools available in the Proton ecosystem.

Lumo will be used to support the learning process and help with:

- Answering questions about Ubuntu.
- Learning equivalent features in Photoshop and GIMP.
- Learning equivalent features in Illustrator and Inkscape.
- Learning equivalent features in InDesign and Scribus.
- Guiding basic configuration and administration tasks.
- Reducing the learning curve during the transition.

### Expected Outcome

#### Short Term

- Photoshop continues to run in the virtual machine.
- Illustrator is replaced by Inkscape.
- InDesign is replaced by Scribus.
- The current workflow remains operational.
- There is no significant impact on productivity.

#### Medium Term

- The user regularly works with GIMP for image editing.
- The user regularly works with Inkscape for vector design.
- The user regularly works with Scribus for page layout and desktop publishing.
- The user uses Ubuntu independently for routine tasks.
- Daily reliance on Windows is gradually reduced.

#### Long Term

- The user can perform much of their professional work in Linux, using GIMP, Inkscape, and Scribus as the primary alternatives to Photoshop, Illustrator, and InDesign.
- Reliance on Windows 10 is minimized or eliminated.
- The need to maintain unsupported software as an operational requirement is eliminated.


---

## Alternatives Evaluated

### Complete Hardware Replacement

**Outcome:** Rejected.

**Reason:**

- Increased costs.
- The current hardware remains functional for the user's needs.

### Full Migration to Linux

**Outcome:** Rejected.

**Reason:**

- Direct reliance on Photoshop and Illustrator.
- Possible compatibility issues with specific peripherals.

### Dual Boot

**Outcome:** Rejected.

**Reason:**

- Windows would continue to run directly on physical hardware.
- It does not eliminate the risks associated with a legacy operating system.

### Isolated Virtualization

**Outcome:** Selected.

**Reason:**

- Maintains the required functionality.
- Allows Windows 10 to be fully isolated.
- Significantly reduces the attack surface.
- Simplifies backup and recovery using snapshots.

---

## Target Architecture

The proposed solution is to separate the system's critical functions through virtualization and storage segmentation.

### Disk Layout

```text
1 TB disk (current system)
└── Ubuntu 26.04 LTS (Host)

Reclaimed SSD
└── Virtualized Windows 10 (VirtualBox)

1 TB disk (STORAGE)
├── Historical data
├── Backups
├── Work files
└── Shared folder Host ↔ VM
```


### Ubuntu 26.04 LTS (Host)

Installed on the primary disk currently used by Windows.

**Responsibilities:**

- Web browsing.
- Email.
- Online banking.
- Administrative procedures.
- Multimedia.
- Printing.
- Gradual learning and use of GIMP.
- Gradual learning and use of Inkscape.
- Use of AI-based assistance tools.

### Virtualized Windows 10

Installed in VirtualBox on the reclaimed SSD.

**Responsibilities:**

- Adobe Photoshop.
- Adobe Illustrator.
- Scanning with the Canon MF3010.
- Use of the Wacom CTL-460.
- Professional graphic design work.

### STORAGE Disk

**Functions:**

- Storage for historical files.
- Backups.
- Information sharing between Ubuntu and the virtual machine.
- Location of the shared folder used by the user.

### Security Principle

```text
Windows 10 will remain isolated from the Internet.
```

All network access will take place from Ubuntu, drastically reducing the exposure of the legacy system.

---

## Next Steps

1. Install the reclaimed SSD.
2. Install the internal Wi-Fi card.
3. Inventory the stored data.
4. Clean up and reorganize files.
5. Create a system image using Macrium Reflect.
6. Install Ubuntu 26.04 LTS.
7. Install GIMP and Inkscape and perform the initial configuration.
8. Create a Proton account for the user.
9. Set up VirtualBox.
10. Restore Windows 10 in a virtualized environment.
11. Configure the STORAGE disk as shared storage.
12. Validate the critical peripherals and software.
13. Apply hardening measures to the host system.


---

## Risk and Control Assessment

The proposed solution addresses not only the need for operational continuity but also significantly reduces the environment's attack surface. The following assessment complements the initial analysis with a greater focus on security and on presenting the case as a professional project.

### Risk Matrix

| Risk | Impact | Likelihood | Description | Proposed Mitigation |
| --- | --- | --- | --- | --- |
| Unsupported Windows 10 | High | High | The primary operating system receives no patches or security updates, increasing exposure to malware and known vulnerabilities. | Isolate the Windows 10 VM, limit Internet access, and use it only for critical software. |
| Reliance on legacy software | High | High | Adobe Photoshop and Illustrator remain critical tools for the workshop's operations, but depend on an old and less secure environment. | Keep these applications in an isolated virtual machine and gradually reduce reliance on them in favor of Linux. |
| Host exposure to the Internet | High | Medium | A modern operating system directly exposed to the network provides a safer entry point for browsing and email, but must be configured with strict controls. | Access the Internet only from Ubuntu, with host hardening and network restrictions in place. |
| File sharing between host and VM | Medium | Medium | Transferring documents between systems can expose sensitive data if the shared folder is not restricted or monitored. | Separate storage, define least-privilege permissions, and keep the shared folder limited to designated work. |
| Peripherals with limited compatibility | Medium | Medium | Devices such as the Canon MF3010 scanner may have Linux support issues and require contingency measures. | Test native compatibility, retain USB passthrough as an alternative, and document the recovery workflow. |
| Loss of critical information | High | Medium | The user works with design files and professional documentation; data loss could affect business continuity. | Perform regular backups, separate storage, and maintain snapshots of the virtual environment. |

### Critical Assets

- Ubuntu 26.04 LTS as the host operating system and secure network access point.
- Virtualized Windows 10 as a limited-use environment for legacy software.
- Graphic design data and workshop documentation.
- Wacom CTL-460, Canon MF3010, and HP LaserJet 5000N.
- Backup and disaster recovery strategy.

### Key Proposed Controls

- Isolate the Windows 10 virtual machine from direct Internet access.
- Use Ubuntu as the sole environment for browsing, email, banking, and non-critical tasks.
- Segment storage for the system, data, and backups.
- Maintain a controlled shared folder for file exchange between the host and VM.
- Gradually reduce reliance on proprietary software through the use of GIMP and Inkscape.
- Harden the host system, including user management, permissions, and network controls.
- Verify peripheral compatibility before the full migration.
- Back up the virtual machine and test its restoration.


---

## Conclusion

The initial assessment confirms that the current hardware remains suitable for the user's professional work. However, reliance on Windows 10 and legacy applications requires an isolation strategy that maintains operations without incurring the risks associated with using an unsupported operating system.


The proposed solution is not limited to isolating a legacy system. It also lays the groundwork for a gradual technology transition that reduces reliance on unsupported software, encourages the use of open tools such as GIMP and Inkscape, and facilitates the adoption of new technologies through guided assistance and continuous learning.


The ultimate goal is to extend the platform's service life by at least another decade, preserving business continuity and maximizing the use of infrastructure that, despite its age, remains technically suitable for current needs.


The gradual adoption of free software solutions will also help reduce reliance on proprietary licenses and subscription services, improving the long-term economic sustainability of the work environment.