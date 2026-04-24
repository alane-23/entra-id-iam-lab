# Phase 3 — User Lifecycle Management

## Overview

This phase simulates the complete identity lifecycle for a user at Lane Technologies — 
from initial onboarding through formal offboarding. The workflow reflects real-world 
enterprise provisioning and deprovisioning practices, with each step ordered deliberately 
to minimize access risk at every stage of the process.

---

## Objectives

- Simulate structured onboarding of a new employee including attribute population and group assignment
- Demonstrate a security-conscious offboarding sequence that immediately terminates access
- Document the reasoning behind each step in the offboarding process
- Establish a repeatable lifecycle workflow aligned to least privilege principles

---

## Onboarding

New Hire was provisioned in Phase 1 without attributes, reflecting a pre-onboarding 
state. During onboarding, the account was completed with full identity attributes and 
assigned appropriate group membership based on job function.

### Identity Attributes Assigned

| Field | Value |
|---|---|
| Job Title | Marketing Coordinator |
| Department | Marketing |
| Company | Lane Technologies |
| Manager | Sarah Chen |

### Group Assignment

New Hire was added to GRP-All-Employees only — no elevated group membership or 
directory roles were assigned, reflecting least privilege access for a standard 
employee joining outside of IT or administrative functions.

![Onboarding](../../screenshots/project1/phase3/Phase%203%20-%20Onboarding.png)

![New Hire Added to All Employees Group](../../screenshots/project1/phase3/Phase%203%20-%20New%20Hire%20Added%20to%20All%20Employees%20Group.png)

---

## Offboarding

The offboarding sequence was executed in a deliberate order designed to eliminate 
access immediately and create a clear audit trail. Each step builds on the last 
to ensure no residual access remains after the process is complete.

### Offboarding Sequence

| Step | Action | Security Reasoning |
|---|---|---|
| 1 | Password reset | Immediately prevents re-authentication even if sessions persist |
| 2 | Remove from all groups | Eliminates access to all group-based resources |
| 3 | Disable account | Blocks all future sign-in attempts |
| 4 | Label account | Creates audit trail with disable date for compliance purposes |

> **Note:** In a live production environment, the first step would be revoking active 
> sessions to immediately terminate any existing access tokens before proceeding with 
> the remaining steps. This was not applicable in the lab environment as the test 
> account had no active sessions.

### Account Disabled Status
![Offboarding Account Status](../../screenshots/project1/phase3/Phase%203%20-%20Offboarding-Account%20Status.png)

### Account Labeled with Disable Date
![Offboarding Account Disabled Title](../../screenshots/project1/phase3/Phase%203%20-%20Offboarding-Account%20Disabled%20Title.png)

---

## Key Decisions

- **Password reset before group removal** — ensures the account cannot be used 
even if group removal is delayed or partially completed
- **Account labeled with disable date** — supports compliance auditing and ensures 
any administrator reviewing the directory can immediately identify the account status 
without additional investigation
- **Least privilege maintained throughout onboarding** — New Hire received only 
standard employee group membership with no directory roles, consistent with the 
principle that access should be granted based on demonstrated need

---

[← Phase 2 — RBAC](phase2-rbac.md) | [Phase 4 — Conditional Access →](phase4-conditional-access.md)
