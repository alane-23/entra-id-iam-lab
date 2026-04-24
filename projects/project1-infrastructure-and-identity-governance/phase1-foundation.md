# Phase 1 — Foundation

## Overview

The foundation phase establishes the core identity infrastructure for Lane Technologies. 
This includes tenant configuration, organizational hierarchy, user provisioning, and 
security group structure — the building blocks that all subsequent phases depend on.

---

## Objectives

- Configure the Entra ID tenant to represent a structured enterprise organization
- Provision users with complete identity attributes aligned to their role and department
- Establish a security group structure that supports least privilege access control
- Define a management hierarchy to support access review delegation in later phases

---

## Tenant Configuration

The Microsoft Entra ID tenant was configured to represent Lane Technologies as the 
organizational identity boundary. All users, groups, roles, and policies exist within 
this tenant, reflecting how an enterprise directory is structured in production.

![Tenant Name](../../screenshots/project1/phase1/Phase%201%20-%20Tenant%20Name.png)

---

## User Provisioning

Six users were provisioned across four departments, each assigned structured identity 
attributes including job title, department, company name, and manager. Populating these 
fields intentionally — rather than leaving them blank — supports dynamic group eligibility, 
access review delegation, and accurate reporting throughout the identity lifecycle.

| User | Title | Department |
|---|---|---|
| Alexis Lane | IT Analyst | IT |
| Alex Turner | IT Administrator | IT |
| Sarah Chen | HR Manager | HR |
| Marcus Webb | Financial Analyst | Finance |
| Jamie Reyes | Contractor | External |
| New Hire | — | — |

New Hire was provisioned without attributes intentionally, reflecting a pre-onboarding 
state that would be completed as part of the formal onboarding process in Phase 3.

![Users](../../screenshots/project1/phase1/Phase%201%20-%20Users.png)

---

## Security Group Structure

Five security groups were created to support department-based access control and 
contractor isolation. Membership type was set to Assigned for all groups, with 
Dynamic membership considered for future phases based on department attributes.

| Group | Purpose |
|---|---|
| GRP-IT-Admins | IT department administrators |
| GRP-HR | Human Resources staff |
| GRP-Finance | Finance department staff |
| GRP-Contractors | External contractors — isolated from employee groups |
| GRP-All-Employees | All full-time employees — explicitly excludes contractors |

The deliberate exclusion of Jamie Reyes from GRP-All-Employees reflects a core 
identity governance principle — contractor access is a separate risk category that 
requires distinct controls and review cycles from standard employee access.

![Groups](../../screenshots/project1/phase1/Phase%201%20-%20Groups.png)

---

## Key Decisions

- **Manager hierarchy established** — enables manager-based access review delegation 
in Phase 6 without additional configuration
- **Contractor group isolation** — separates external access from internal employee 
access at the group level, enforcing least privilege by default
- **Complete identity attributes** — all users provisioned with full profile data 
rather than minimum required fields, reflecting enterprise provisioning standards

---

[← Back to Project 1 Overview](overview.md) | [Phase 2 — RBAC →](phase2-rbac.md)
