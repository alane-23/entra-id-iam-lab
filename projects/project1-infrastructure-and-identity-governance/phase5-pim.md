# Phase 5 — Privileged Identity Management

## Overview

This phase implements Privileged Identity Management (PIM) across the Lane Technologies 
tenant, eliminating standing privileged access entirely. Rather than holding administrative 
roles permanently, eligible users must request elevation, provide justification, and 
complete MFA before access is granted — with all activations automatically expiring 
after a defined window.

---

## Objectives

- Eliminate permanent standing access for privileged roles
- Configure just-in-time role activation with justification and MFA requirements
- Demonstrate the full activation workflow from eligible assignment to active access
- Establish automatic expiration to ensure privileged access is time-bound

---

## PIM Configuration

### Roles Configured

Two high-value roles were placed under PIM control, removing them from permanent 
assignment and requiring on-demand activation for all use.

| Role | Activation Duration | MFA Required | Justification Required | Approval Required |
|---|---|---|---|---|
| Security Administrator | 4 hours | Yes | Yes | No |
| User Administrator | 4 hours | Yes | Yes | No |

A 4-hour maximum activation window was selected to provide sufficient time for 
administrative tasks while ensuring access does not persist beyond the immediate 
need. Approval was not required in the lab environment for simplicity, though 
in a production environment dual-approval workflows would be appropriate for 
Security Administrator activations.

---

## Eligible Assignment

A dedicated privileged account — Alexis Lane (Admin) — was created and assigned 
as eligible for both roles. Eligible assignment means the account can request 
activation at any time but holds no standing access until an activation is 
explicitly requested and approved.

This separation between the standard user account (Alexis Lane) and the 
administrative account (Alexis Lane Admin) reflects enterprise best practice — 
day-to-day work is performed under a standard account, and privileged access 
is only elevated when explicitly required.

![PIM Eligible Assignments](../../screenshots/project1/phase5/Phase%205%20-%20PIM%20Eligible%20Assignments.png)

---

## Activation Workflow

The full activation workflow was demonstrated by signing in as Alexis Lane (Admin) 
and requesting elevation to Security Administrator through the PIM My Roles interface.

### Activation Request

Justification was provided as required by the role configuration, simulating a 
real-world scenario where an administrator documents the reason for elevation 
before access is granted.

**Justification provided:** `Investigating suspicious authentication activity in tenant`

![Activation Request & Reasoning](../../screenshots/project1/phase5/Phase%205%20-%20Activation%20Request%20%26%20Reasoning.png)

### Active Assignment

Following successful activation and MFA completion, the Security Administrator 
role moved from Eligible to Active status with a 2-hour expiration window — 
demonstrating that privileged access is time-bound and self-terminating.

![PIM Security Admin Active](../../screenshots/project1/phase5/Phase%205%20-%20PIM%20Security%20Admin%20Active.png)

---

## Key Decisions

- **Dedicated admin account created** — separates privileged identity from 
standard user identity, ensuring administrative actions are always performed 
under a distinct account that can be independently monitored and audited
- **4-hour maximum activation window** — balances operational practicality 
with security; long enough for legitimate administrative work, short enough 
to limit exposure from a compromised elevation
- **Justification required on every activation** — creates an audit trail 
for all privileged access, supporting compliance requirements and enabling 
investigation of any activation that cannot be correlated to a known change or incident
- **MFA required on activation** — ensures that even if an eligible account's 
password is compromised, privileged access cannot be obtained without the 
second factor

---

[← Phase 4 — Conditional Access](phase4-conditional-access.md) | [Phase 6 — Access Reviews →](phase6-access-reviews.md)
