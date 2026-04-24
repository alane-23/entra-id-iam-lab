# Phase 2 — Role Based Access Control

## Overview

This phase implements role-based access control across the Lane Technologies tenant 
using least privilege principles. Directory roles were assigned based strictly on 
job function — no user holds more access than their role requires, and non-administrative 
users hold zero directory roles by design.

---

## Objectives

- Assign Entra ID directory roles aligned to each user's job function
- Demonstrate least privilege enforcement across all user accounts
- Establish a clear separation between privileged and non-privileged accounts
- Document intentional zero-role assignments as evidence of least privilege

---

## Role Assignments

Roles were assigned individually rather than through broad group-based role assignment, 
ensuring each user's access reflects their specific responsibilities.

| User | Assigned Roles | Justification |
|---|---|---|
| Alexis Lane | Global Administrator, User Administrator | Primary IAM administrator — owns identity lifecycle and tenant configuration |
| Alex Turner | Helpdesk Administrator, Groups Administrator | IT support scope — manages group membership and basic user support tasks |
| Sarah Chen | Security Reader, Guest Inviter | HR scope — read access to security info for compliance, manages external invitations |
| Marcus Webb | None | Financial Analyst — no directory role required, access managed through group membership |
| Jamie Reyes | None | Contractor — no directory role required, access isolated to contractor group only |
| New Hire | None | Pre-onboarding state — no access assigned prior to formal onboarding |

---

## Least Privilege Evidence

The absence of directory roles for Marcus Webb and Jamie Reyes is intentional and 
represents a core least privilege decision. Access to resources for these users is 
managed exclusively through group membership, not directory roles — ensuring no 
unnecessary elevation of privilege exists in the tenant.

### Alex Turner — Helpdesk Administrator & Groups Administrator
![Alex Turner Roles](../../screenshots/project1/phase2/Phase%202%20-%20Alex%20Turner%20Roles.png)

### Sarah Chen — Security Reader & Guest Inviter
![Sarah Chen Roles](../../screenshots/project1/phase2/Phase%202%20-%20Sarah%20Chen%20Roles.png)

### Jamie Reyes — No Directory Roles Assigned
![Jamie Reyes Roles](../../screenshots/project1/phase2/Phase%202%20-%20Jamie%20Reyes%20Roles.png)

---

## Key Decisions

- **Helpdesk Administrator scoped to Alex Turner** — provides password reset and 
basic support capabilities without Global Administrator exposure
- **Security Reader assigned to Sarah Chen** — HR requires visibility into security 
posture for compliance purposes without the ability to modify security configurations
- **Guest Inviter assigned to Sarah Chen** — HR owns the external collaboration 
process, controlling who gets invited into the tenant as a guest
- **Zero roles for Finance and Contractors** — neither role requires directory-level 
access; resource access is controlled entirely through group membership, maintaining 
strict least privilege

---

[← Phase 1 — Foundation](phase1-foundation.md) | [Phase 3 — User Lifecycle →](phase3-lifecycle.md)
