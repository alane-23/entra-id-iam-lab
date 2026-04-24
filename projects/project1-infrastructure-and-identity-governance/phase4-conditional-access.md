# Phase 4 — Conditional Access

## Overview

This phase implements a layered Conditional Access policy framework for Lane Technologies, 
applying Zero Trust principles across all users, resources, and access scenarios. Three 
policies were designed to address distinct risk categories — universal MFA enforcement, 
contractor location-based restrictions, and privileged device compliance requirements.

---

## Objectives

- Enforce MFA for all users across all cloud applications
- Restrict contractor access to approved geographic locations
- Require device compliance for IT administrators accessing cloud resources
- Demonstrate production-safe policy deployment using Report Only mode

---

## Named Location Configuration

Prior to policy creation, a named location was configured to define the approved 
geographic boundary for access control purposes. This location is referenced 
directly in the contractor access policy.

| Setting | Value |
|---|---|
| Name | Approved Countries - US Only |
| Type | Countries Location |
| Countries | United States |

![Named Location US Only](../../screenshots/project1/phase4/Phase%204%20-%20Named%20Location%20US%20Only.png)

---

## Policies

### CA001 — Require MFA for All Users

The foundational access policy enforcing MFA across the entire tenant. No user 
can authenticate to any cloud application without completing a second factor, 
regardless of location, device, or role.

| Setting | Value |
|---|---|
| Users | All Users |
| Target Resources | All Cloud Apps |
| Grant Control | Require Multifactor Authentication |
| Policy State | Report Only |

### CA002 — Block Contractor Access Outside US

A location-based restriction policy targeting the GRP-Contractors group. Any 
authentication attempt originating outside the United States is blocked, 
reflecting the elevated risk profile of external contractor accounts and 
limiting the blast radius of a compromised contractor credential.

| Setting | Value |
|---|---|
| Users | GRP-Contractors |
| Target Resources | All Cloud Apps |
| Locations — Include | Any Location |
| Locations — Exclude | Approved Countries - US Only |
| Grant Control | Block Access |
| Policy State | Report Only |

![Contractor Location Block Policy](../../screenshots/project1/phase4/Phase%204%20-%20Contractor%20Location%20Block%20Policy.png)

### CA003 — Require Compliant Device for IT Admins

A device compliance policy targeting GRP-IT-Admins, ensuring administrative 
access is only permitted from managed, compliant devices. This policy enforces 
the Zero Trust principle that device health is a prerequisite for privileged access — 
not just user identity.

| Setting | Value |
|---|---|
| Users | GRP-IT-Admins |
| Target Resources | All Cloud Apps |
| Grant Control | Require device to be marked as compliant |
| Policy State | Report Only |

---

## Policy Overview

All three policies are visible in the Conditional Access overview, providing 
a complete picture of the access control framework applied across the tenant.

![All Conditional Access Policies](../../screenshots/project1/phase4/Phase%204%20-%20All%20Conditional%20Access%20Policies.png)

---

## Report Only Mode

All policies were deployed in Report Only mode following production best practices. 
Enabling Conditional Access policies directly against all users in a production 
environment without prior validation risks locking legitimate users — including 
administrators — out of the tenant.

Report Only mode allows the full impact of each policy to be assessed against 
real sign-in activity before enforcement, ensuring no unintended access disruption 
occurs. In a production environment, policies would be validated against a pilot 
group before being moved to Enabled.

---

## Key Decisions

- **CA002 scoped to GRP-Contractors specifically** — contractors represent a higher 
risk access category than standard employees; location restriction limits exposure 
from compromised external credentials without impacting the broader workforce
- **CA003 targets IT Admins exclusively** — privileged accounts have the highest 
blast radius if compromised; requiring device compliance ensures administrative 
actions can only be performed from known, managed endpoints
- **Report Only for all policies** — reflects production operational maturity; 
no policy was enabled without impact assessment, consistent with enterprise 
change management practices

---

[← Phase 3 — User Lifecycle](phase3-lifecycle.md) | [Phase 5 — Privileged Identity Management →](phase5-pim.md)
