# Security Group Doc

**Domain:** `NMG.com`

**Day 2 completed:** September 14, 2026

**Current configuration checked:** September 18, 2026

## Departmental Organization

| Department / OU | Purpose | Security group | Scope | Category | Final employee count |
| --- | --- | --- | --- | --- | --- |
| Finance | Organizes finance, payroll, and accounts payable identities | `Finance-Users` | Global | Security | 4 |
| HR | Organizes HR, recruiting, benefits, and HR payroll identities | `HR-Users` | Global | Security | 4 |
| IT | Organizes IT administration, support, security, and systems identities | `IT-Users` | Global | Security | 4 |
| Operations | Organizes facilities, scheduling, and operations identities | `Operations-Users` | Global | Security | 3 |

Each group resides in its matching departmental OU. The final counts reflect Jane Cooper's correction from Operations to HR on Day 4.

## Why OUs and Groups Are Separate

OUs organize directory objects and provide boundaries for delegated administration and linked Group Policy. Security groups collect identities to which resource permissions can be assigned. Placing a user in an OU does not automatically add the user to the similarly named group, and moving an account does not automatically remove an old group membership.

For example, a Finance employee belongs in the Finance OU for the departmental structure and in `Finance-Users` for the intended access model. A Finance share would need an explicit permission assignment to the appropriate group. Managing those assignments through groups makes membership changes easier to review than a collection of individual user grants.

The lab verifies the group objects and memberships. It does not establish that departmental shares or application permissions have been configured. See the [RBAC map](RBAC-Structure.md) for the intended resource categories and the [verification record](Verification.md) for the observed results.
