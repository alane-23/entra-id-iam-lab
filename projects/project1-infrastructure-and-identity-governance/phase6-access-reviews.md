# Phase 6 — Access Reviews

## Overview

This phase establishes a recurring access certification program for Lane Technologies, 
ensuring that access across groups, contractor accounts, and applications is periodically 
reviewed and validated. Access Reviews enforce the principle that access should not 
persist indefinitely — it must be actively certified or it is revoked automatically.

---

## Objectives

- Implement recurring access reviews across high-risk and standard access categories
- Apply risk-based review frequency — higher risk access is reviewed more frequently
- Configure auto-remediation to remove uncertified access without manual intervention
- Demonstrate compliance-driven governance aligned to regulated industry standards

---

## Access Reviews Configured

Three access reviews were created, each targeting a distinct access category with 
review frequency aligned to the risk level of the access being certified.

| Review | Target | Reviewer | Frequency | If No Response |
|---|---|---|---|---|
| QR001 - IT Admin Group Access Review | GRP-IT-Admins | Sarah Chen | Quarterly | Remove Access |
| QR002 - Contractor Access Review | GRP-Contractors | Alexis Lane | Monthly | Remove Access |
| QR003 - Application Access Review | Salesforce | Alexis Lane | Quarterly | Remove Access |

---

## Review Design Decisions

### Risk-Based Review Frequency

Contractor access is reviewed monthly while employee and application access 
is reviewed quarterly. This reflects a deliberate risk-based approach — 
external contractor accounts represent a higher risk category than standard 
employee access due to their limited organizational accountability and 
typically broader access scope relative to their tenure.

### Cross-Functional Reviewer Assignment

QR001 targets IT Admin group membership but is reviewed by Sarah Chen in HR 
rather than an IT administrator. This cross-functional assignment reflects 
a real-world governance pattern where access certification is performed by 
someone outside the team being reviewed, reducing the risk of rubber-stamp 
approvals and ensuring independent validation of access necessity.

### Auto-Remediation Configuration

All three reviews are configured to automatically remove access if a reviewer 
does not respond within the review period. This secure-by-default configuration 
ensures that inaction results in access removal rather than access preservation — 
a critical distinction in regulated environments where access persistence without 
active certification represents a compliance risk.

### Justification Required

All reviews require written justification for access approval decisions, 
creating an auditable record of every certification decision. In a regulated 
healthcare environment, this justification trail directly supports compliance 
requirements around access governance and periodic access certification.

---

## Access Reviews Overview

![All Access Reviews](../../screenshots/project1/phase6/Phase%206%20-%20All%20Access%20Reviews.png)

## Review Details

![Access Review Details](../../screenshots/project1/phase6/Phase%206%20-%20Access%20Review%20Details.png)

---

## Key Decisions

- **Monthly contractor reviews** — contractor access is the highest risk 
category in the tenant; monthly certification ensures access is continuously 
validated and cannot persist unnoticed beyond a 30-day window
- **Auto-remove on non-response** — access is denied by default when reviewers 
do not act; this is the security-conscious configuration choice and directly 
contrasts with the alternative of preserving access on non-response
- **Justification required on all reviews** — supports audit trail requirements 
and ensures reviewers actively consider access necessity rather than approving 
by default
- **Cross-functional reviewer for IT Admin group** — HR reviewing IT access 
provides independent oversight and mirrors enterprise governance structures 
where segregation of duties is applied to access certification

---

[← Phase 5 — Privileged Identity Management](phase5-pim.md) | [↑ Back to Project 1 Overview](overview.md)
