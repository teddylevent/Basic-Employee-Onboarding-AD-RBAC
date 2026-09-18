# User List Documentation

**Employee accounts:** 15

**Day 3 provisioning completed:** September 15, 2026

**Final state verified:** September 18, 2026, after the Day 4 correction

Names, usernames, UPNs, departments, job titles, OU placement, and departmental group memberships below were checked directly in Active Directory on `NMG-DC01`. All identities are fictional lab accounts. Built-in accounts are excluded from the employee count.

## Naming Convention

- Username (`sAMAccountName`): lowercase first initial followed by surname.
- UPN: `username@NMG.com`.
- Department values: `Finance`, `HR`, `IT`, or `Operations`.
- UPNs are sign-in identifiers; this inventory does not assert that mailboxes exist.

## Final Inventory

| Employee | Username | UPN | Department / OU | Job title | Departmental security group |
| --- | --- | --- | --- | --- | --- |
| David Chen | `dchen` | `dchen@NMG.com` | Finance | Finance Manager | `Finance-Users` |
| Karen Mills | `kmills` | `kmills@NMG.com` | Finance | Finance Analyst | `Finance-Users` |
| Robert Hayes | `rhayes` | `rhayes@NMG.com` | Finance | Payroll Specialist | `Finance-Users` |
| Lisa Park | `lpark` | `lpark@NMG.com` | Finance | Accounts Payable | `Finance-Users` |
| Sandra Torres | `storres` | `storres@NMG.com` | HR | HR Manager | `HR-Users` |
| James Whitfield | `jwhitfield` | `jwhitfield@NMG.com` | HR | HR Recruiter | `HR-Users` |
| Michelle Grant | `mgrant` | `mgrant@NMG.com` | HR | Benefits Coordinator | `HR-Users` |
| Jane Cooper | `jcooper` | `jcooper@NMG.com` | HR | HR Payroll Specialist | `HR-Users` |
| Marcus Johnson | `mjohnson` | `mjohnson@NMG.com` | IT | IT Administrator | `IT-Users` |
| Priya Patel | `ppatel` | `ppatel@NMG.com` | IT | Security Analyst | `IT-Users` |
| Tyler Brooks | `tbrooks` | `tbrooks@NMG.com` | IT | Help Desk Technician | `IT-Users` |
| Aisha Coleman | `acoleman` | `acoleman@NMG.com` | IT | Systems Engineer | `IT-Users` |
| Brian Foster | `bfoster` | `bfoster@NMG.com` | Operations | Operations Manager | `Operations-Users` |
| Carlos Rivera | `crivera` | `crivera@NMG.com` | Operations | Facilities Supervisor | `Operations-Users` |
| Natalie Ross | `nross` | `nross@NMG.com` | Operations | Scheduling Coordinator | `Operations-Users` |

## Day 3 to Day 4 Change

The original Day 3 notes recorded Finance 4, HR 3, IT 4, and Operations 4. Jane was initially created in Operations for the incident exercise. The final inventory above places her in HR after the correction, yielding Finance 4, HR 4, IT 4, and Operations 3. The total remains 15.

Jane's manager is `Sandra Torres`, verified as `CN=Sandra Torres,OU=HR,DC=NMG,DC=com`. Her corrected company field was shown as `NMG` in the retained local evidence.

The table lists departmental groups. It is not a full effective-access report and does not replace review of primary groups, nested groups, resource ACLs, or application roles. No credentials are published.
