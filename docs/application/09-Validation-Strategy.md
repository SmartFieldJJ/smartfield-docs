---
title: Validation Strategy
version: 1.0
status: Approved
owner: Software Architecture
category: Application
last_updated: 2026-07-29
---

# Validation Strategy

## Purpose

This document defines the validation strategy used throughout the SmartField Application Layer.

Validation is performed at different architectural layers, each responsible for enforcing a specific category of rules.

The objective is to ensure data quality, preserve business consistency, and maintain a clear separation of responsibilities.

---

# Scope

This document defines:

- Validation categories
- Validation responsibilities
- Validation flow
- Layer responsibilities

It does not define:

- Business rules
- Database constraints
- Framework validation annotations

These concerns belong to other architectural components.

---

# Validation Principles

Validation should:

- Occur as early as possible.
- Be performed only by the responsible layer.
- Avoid duplicated rules.
- Produce meaningful errors.
- Preserve domain consistency.

Every validation belongs to exactly one architectural responsibility.

---

# Validation Categories

SmartField classifies validation into three categories.

| Validation Type | Responsibility |
|-----------------|----------------|
| Structural Validation | Verify request structure. |
| Domain Validation | Verify business rules. |
| Infrastructure Validation | Verify technical capabilities. |

---

# Structural Validation

Structural Validation ensures that incoming application requests are well-formed.

Typical responsibilities include:

- Required fields.
- Identifier format.
- Email format.
- String length.
- Numeric range.
- Enumeration values.
- Collection size.

Structural Validation occurs before business execution begins.

---

# Domain Validation

Domain Validation verifies whether a requested business operation is permitted.

Examples include:

- Employee belongs to the Company.
- Employee is active.
- Project accepts assignments.
- Assignment period is valid.
- User has required business permissions.

These validations are performed by:

- Entities
- Value Objects
- Aggregates
- Domain Services

Business validation never belongs to the Application Layer.

---

# Infrastructure Validation

Infrastructure Validation verifies technical dependencies required by the application.

Examples include:

- Storage availability.
- External identity provider availability.
- Notification service availability.
- Messaging infrastructure readiness.

These validations are performed by Infrastructure adapters.

---

# Validation Flow

The validation process follows this sequence:

```
Client Request
       │
       ▼
Structural Validation
       │
       ▼
Application Service
       │
       ▼
Domain Validation
       │
       ▼
Infrastructure Interaction
       │
       ▼
Application Response
```

Each layer validates only its own responsibilities.

---

# Validation Responsibilities

| Layer | Responsibility |
|--------|----------------|
| API | Request parsing and transport validation. |
| Application | Structural validation and orchestration. |
| Domain | Business validation. |
| Infrastructure | Technical validation. |

Each validation rule exists in only one layer.

---

# Validation Failure

When validation fails:

- Execution stops.
- No unnecessary work is performed.
- No inconsistent state is produced.
- The caller receives a meaningful error.

Business failures never result in partial state changes.

---

# Validation vs Business Rules

| Validation | Business Rule |
|------------|---------------|
| Verifies input correctness. | Defines business behavior. |
| Prevents invalid requests. | Protects business consistency. |
| May occur before execution. | Occurs during domain execution. |
| Focuses on request integrity. | Focuses on business integrity. |

Not every validation is a business rule.

Not every business rule is a validation.

---

# Design Principles

Validation should:

- Be explicit.
- Be deterministic.
- Be easy to maintain.
- Avoid duplication.
- Preserve separation of concerns.
- Remain independent of frameworks.

---

# Related Documentation

- 04-Commands.md
- 07-Transactions.md
- 10-Error-Handling.md
- ../domain/11-Domain-Rules.md
- ../api/

---

# Revision History

| Version | Date | Description |
|----------|------|-------------|
| 1.0 | 2026-07-29 | Initial version. |