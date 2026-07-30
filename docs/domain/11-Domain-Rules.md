---
title: Domain Rules
version: 1.0
status: Approved
owner: Software Architecture
category: Domain
last_updated: 2026-07-29
---

# Domain Rules

## Purpose

This document defines the business rules enforced by the SmartField domain model.

Domain Rules represent the invariants, constraints, and validations that must always hold true regardless of how the system is accessed.

These rules preserve business consistency and are enforced by Entities, Value Objects, Aggregates, and Domain Services.

---

# Scope

This document defines:

- Domain invariants
- Aggregate consistency rules
- Validation rules
- Cross-aggregate business constraints

It does not define:

- UI validation
- API validation
- Database constraints
- Infrastructure policies

Those concerns belong to other architectural layers.

---

# Domain Rule Categories

Domain Rules are organized into the following categories:

- Company Rules
- User Rules
- Employee Rules
- Project Rules
- Assignment Rules
- Authorization Rules
- Audit Rules

---

# Company Rules

## DR-COM-001

A Company must have a valid business name.

---

## DR-COM-002

Every Company is uniquely identified by a CompanyId.

---

## DR-COM-003

A Company owns its Employees, Projects, and Users.

Ownership cannot be transferred.

---

# User Rules

## DR-USR-001

Every User belongs to exactly one Company.

---

## DR-USR-002

Only active Users may authenticate.

---

## DR-USR-003

A User performs operations according to the Permissions granted through assigned Roles.

---

# Employee Rules

## DR-EMP-001

Every Employee belongs to exactly one Company.

---

## DR-EMP-002

An Employee cannot exist without an owning Company.

---

## DR-EMP-003

An inactive Employee cannot receive new Assignments.

---

# Project Rules

## DR-PRJ-001

Every Project belongs to exactly one Company.

---

## DR-PRJ-002

Only active Projects may receive new Assignments.

---

## DR-PRJ-003

Completed Projects cannot be modified in ways that violate their completed state.

---

# Assignment Rules

## DR-ASN-001

Every Assignment references one Employee and one Project.

---

## DR-ASN-002

Employee and Project must belong to the same Company.

---

## DR-ASN-003

Assignment periods must define a valid time interval.

---

## DR-ASN-004

An Assignment cannot be created for an inactive Employee or an inactive Project.

---

# Authorization Rules

## DR-AUTH-001

Every protected business operation requires an authenticated User.

---

## DR-AUTH-002

Authorization is determined through Roles and Permissions.

---

## DR-AUTH-003

Business authorization rules must be evaluated before modifying domain state.

---

# Audit Rules

## DR-AUD-001

Significant business operations must produce an Audit Record.

---

## DR-AUD-002

Audit Records are immutable after creation.

---

## DR-AUD-003

Audit history must preserve chronological order.

---

# Rule Enforcement

Domain Rules are enforced by the appropriate building blocks:

| Rule Type | Primary Responsibility |
|------------|------------------------|
| Entity invariants | Entities |
| Value validation | Value Objects |
| Consistency boundaries | Aggregates |
| Cross-aggregate rules | Domain Services |
| Business facts | Domain Events |

The Application Layer coordinates execution but does not own these rules.

---

# Rule Evolution

When business requirements change:

1. Review the affected Domain Rule.
2. Evaluate its impact on the Domain Model.
3. Update related Aggregates and Domain Services.
4. Review Domain Events if business behavior changes.
5. Keep the Domain Model consistent.

Domain Rules should evolve with the business while preserving conceptual integrity.

---

# Related Documentation

- 05-Entities.md
- 06-Value-Objects.md
- 07-Aggregates.md
- 08-Domain-Services.md
- 09-Domain-Events.md
- 10-Repositories.md
- ../business/05-Business-Rules.md

---

# Revision History

| Version | Date | Description |
|----------|------|-------------|
| 1.0 | 2026-07-29 | Initial version. |