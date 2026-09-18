# Basic Employee Onboarding (AD)(RBAC)

An Active Directory and identity access management lab for **Northstar Medical Group**, a fictional healthcare organization.

**15 employee accounts · 4 departments · 4 security groups · 1 resolved identity configuration incident**

Built in UTM on Windows Server 2025 Standard. Lab work completed September 14–17, 2026; portfolio and directory verification completed September 18, 2026.

## Problem Statement

The fictional Northstar Medical Group inherited disorganized identity administration from its managed service provider (MSP). Manual onboarding, inconsistent account attributes, and missing departmental structure made access assignments difficult to maintain and review. In a healthcare setting, that scenario creates concerns about inappropriate access to sensitive information and HIPAA-related risk. This lab models the identity configuration work needed to address those problems; it does not represent a production healthcare deployment or a compliance assessment.

## Solution Overview

I built the `NMG.com` domain on the `NMG-DC01` domain controller and organized employee accounts into Finance, HR, IT, and Operations OUs. I created one global security group per department to establish a simple, flat RBAC model. I provisioned 15 fictional employee identities using consistent usernames, UPNs, departments, and job titles. I investigated ticket `NMG-0047` and corrected Jane Cooper's OU placement, departmental group membership, and HR profile attributes. The resulting directory provides a consistent foundation for assigning resource permissions through groups, with the configuration and verification documented in this repository.


## Tools Used

| Tool or method | Use in this project |
| --- | --- |
| Windows Server 2025 Standard | Domain controller operating system |
| Active Directory Domain Services | Domain, employee identities, OUs, and security groups |
| Active Directory Users and Computers | Account provisioning and incident remediation |
| UTM on macOS | Virtual machine hosting |
| Windows PowerShell / Active Directory module | Read-only verification of the completed directory |
| Group Policy | OU scope concepts and inspection of existing GPOs |
| RBAC | Departmental role and group design |
| Git and GitHub | Versioned portfolio documentation |

## Project Timeline

| Phase | Completed | Result |
| --- | --- | --- |
| Day 1 — Domain setup | September 14, 2026 | Created `NMG.com`, promoted `NMG-DC01`, and configured the lab's static address |
| Day 2 — Directory organization | September 14, 2026 | Created four departmental OUs and four security groups |
| Day 3 — User provisioning | September 15, 2026 | Created 15 accounts and assigned departmental memberships |
| Day 4 — Incident response | September 17, 2026 | Corrected Jane Cooper's identity configuration for ticket `NMG-0047` |
| Day 5 — Portfolio packaging | September 18, 2026 |

## Key Accomplishments

- Built a working lab domain with a dedicated domain controller.
- Established a clear four-department OU and security group structure.
- Provisioned and documented all 15 employee identities.
- Resolved both the incorrect OU placement and incorrect departmental membership in the Jane Cooper scenario.
- Reconciled the original Day 3 roster with the corrected Day 4 state: HR increased from three to four users, and Operations decreased from four to three.
- Verified account attributes, OU placement, and departmental memberships directly in the running VM.


## Video Walkthrough

**Walkthrough link: coming soon.** The video has not been recorded or published yet.

