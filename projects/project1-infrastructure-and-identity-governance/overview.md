# Project 1 — Infrastructure & Identity Governance

## Overview

This project establishes the core identity infrastructure for Lane Technologies, a simulated enterprise environment built in Microsoft Entra ID. It covers the foundational components of an enterprise IAM program — from tenant configuration and user lifecycle management to privileged access controls and identity governance.

The project is structured across six phases, each building on the last to simulate the end-to-end identity program an IAM analyst or engineer would design and manage in a production environment.

---

## Phases

| Phase | Description |
|---|---|
| [Phase 1 — Foundation](phase1-foundation.md) | Tenant setup, user provisioning, group structure, and org hierarchy |
| [Phase 2 — RBAC](phase2-rbac.md) | Role-based access control using least privilege principles |
| [Phase 3 — User Lifecycle](phase3-lifecycle.md) | End-to-end onboarding and offboarding workflows |
| [Phase 4 — Conditional Access](phase4-conditional-access.md) | Zero trust access policies enforcing MFA, location, and device compliance |
| [Phase 5 — Privileged Identity Management](phase5-pim.md) | Just-in-time privileged access with justification and auto-expiration |
| [Phase 6 — Access Reviews](phase6-access-reviews.md) | Recurring access certifications for groups, contractors, and applications |

---

## Environment

| Setting | Value |
|---|---|
| Organization | Lane Technologies |
| Platform | Microsoft Entra ID |
| License | Microsoft Entra ID P2 + Identity Governance |
| Users | 6 simulated enterprise users across IT, HR, Finance, and External |
| Groups | 5 security groups aligned to departments and access tiers |

---

## Key Concepts Demonstrated

- Identity lifecycle management — provisioning and deprovisioning
- Least privilege access control across users and roles
- Zero trust conditional access policy design
- Just-in-time privileged access via PIM
- Compliance-driven access governance through recurring reviews
- Contractor access isolation and risk-based policy enforcement
