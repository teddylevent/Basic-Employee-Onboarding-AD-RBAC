# Role-Based Access Control (RBAC) Structure

This lab uses a flat departmental model: each employee has one organizational location and a separately assigned departmental security group. The following map reflects the verified state after ticket `NMG-0047`.

| Department | Organizational unit | Global security group | Assigned users | Intended resource scope |
| --- | --- | --- | --- | --- |
| Finance | `OU=Finance,DC=NMG,DC=com` | `Finance-Users` | `dchen`, `kmills`, `rhayes`, `lpark` | Finance documents, accounting work, and finance departmental shares |
| HR | `OU=HR,DC=NMG,DC=com` | `HR-Users` | `storres`, `jwhitfield`, `mgrant`, `jcooper` | HR records, benefits, onboarding, and HR payroll resources |
| IT | `OU=IT,DC=NMG,DC=com` | `IT-Users` | `mjohnson`, `ppatel`, `tbrooks`, `acoleman` | IT support and systems resources, with privileged access separately authorized |
| Operations | `OU=Operations,DC=NMG,DC=com` | `Operations-Users` | `bfoster`, `crivera`, `nross` | Facilities, scheduling, and operations departmental resources |

**Implementation boundary:** The OUs, groups, and employee memberships are implemented and verified. The resource scopes are design intentions. No particular read, write, administrative, or application permission is claimed without a corresponding resource configuration and access test.

## Access Model

```text
Employee identity
      │ explicit membership (implemented)
      ▼
Departmental security group
      │ permission assignment (not demonstrated in this lab)
      ▼
Departmental resource
```

`IT-Users` is not a built-in administrative role. The group's name does not grant domain administration. Similarly, Finance or HR membership alone does not establish access to a payroll application.

## Applying Least Privilege in the Incident

Jane's correction required removing her old Operations membership as well as adding HR membership. Leaving both would retain an unnecessary departmental assignment. The directory fix changed both her organizational location and her membership, then verified the final state.

A future extension could implement a test share, assign precise group permissions, and verify both permitted and denied access with ordinary employee accounts. Those access tests are outside the completed scope documented here.
