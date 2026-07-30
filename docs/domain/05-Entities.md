---
title: Entities
version: 1.0
status: Approved
owner: Software Architecture
category: Domain
last_updated: 2026-07-29
---

# Entities

## Purpose

This document defines the Entities that compose the SmartField domain model.

Entities represent business concepts with a distinct identity and lifecycle. While their attributes may change over time, their identity remains constant throughout their existence.

Entities encapsulate business behavior and enforce the business rules that govern their state.

---

# Scope

This document defines:

- Domain entities
- Entity responsibilities
- Identity
- Lifecycle
- Business invariants
- Relationships

It does not define:

- Database tables
- Persistence mappings
- REST representations
- Framework annotations

These implementation details belong to other sections of the documentation.

---

# What is an Entity?

An Entity is a business object distinguished by its identity rather than by its attributes.

Two Entities may contain identical data while still representing different business objects.

Entities:

- Have a unique identity.
- Have a lifecycle.
- Can change over time.
- Encapsulate business behavior.
- Protect business invariants.

---

# Entity Catalog

| Entity | Context | Identity |
|---------|---------|----------|
| Company | Company | CompanyId |
| User | Authentication | UserId |
| Employee | Workforce | EmployeeId |
| Project | Project | ProjectId |
| Assignment | Assignment | AssignmentId |
| Role | Authentication | RoleId |
| Permission | Authentication | PermissionId |
| Audit Record | Audit | AuditRecordId |

---

# Entity Definitions

## Company

### Purpose

Represents an organization that owns business resources within SmartField.

### Identity

CompanyId

### Responsibilities

- Own employees.
- Own projects.
- Own users.
- Define organizational boundaries.

### Lifecycle

Created → Active → Inactive → Archived

---

## User

### Purpose

Represents an authenticated identity.

### Identity

UserId

### Responsibilities

- Authenticate.
- Access protected resources.
- Perform authorized business operations.

### Lifecycle

Registered → Active → Suspended → Disabled

---

## Employee

### Purpose

Represents a worker employed by a company.

### Identity

EmployeeId

### Responsibilities

- Participate in projects.
- Maintain employment information.
- Receive project assignments.

### Lifecycle

Registered → Active → Inactive → Archived

---

## Project

### Purpose

Represents work managed by a company.

### Identity

ProjectId

### Responsibilities

- Organize work.
- Receive assignments.
- Track business progress.

### Lifecycle

Created → Active → Completed → Archived

---

## Assignment

### Purpose

Represents the participation of an Employee in a Project.

### Identity

AssignmentId

### Responsibilities

- Associate employees with projects.
- Track assignment status.
- Preserve assignment history.

### Lifecycle

Created → Active → Completed → Cancelled

---

## Role

### Purpose

Represents a collection of permissions.

### Identity

RoleId

### Responsibilities

- Group permissions.
- Define authorization policies.

### Lifecycle

Created → Active → Deprecated

---

## Permission

### Purpose

Represents authorization for a business operation.

### Identity

PermissionId

### Responsibilities

- Authorize actions.
- Protect business functionality.

### Lifecycle

Created → Active

---

## Audit Record

### Purpose

Represents an immutable record of business activity.

### Identity

AuditRecordId

### Responsibilities

- Preserve history.
- Support traceability.
- Record business events.

### Lifecycle

Created → Retained

Audit Records are immutable once created.

---

# Entity Relationships

```
Company
├── User
├── Employee
└── Project
       │
       ▼
 Assignment
      │
      ▼
 Employee

User
 │
 ▼
Role
 │
 ▼
Permission

Audit Record
     │
     └────► References business activity
```

Relationships represent business associations rather than implementation details.

---

# Business Invariants

All Entities must preserve their business invariants.

Examples include:

- Every Employee belongs to exactly one Company.
- Every Project belongs to one Company.
- Every Assignment references one Employee and one Project.
- Every User belongs to one Company.
- Every Role contains zero or more Permissions.
- Audit Records cannot be modified after creation.

The complete set of business rules is documented in **11-Domain-Rules.md**.

---

# Design Principles

Entities should:

- Encapsulate business behavior.
- Protect business consistency.
- Expose meaningful operations.
- Avoid anemic domain models.
- Remain independent of persistence technologies.

Entities should not become simple data containers.

---

# Related Documentation

- 04-Domain-Model.md
- 06-Value-Objects.md
- 07-Aggregates.md
- 11-Domain-Rules.md

---

# Revision History

| Version | Date | Description |
|----------|------|-------------|
| 1.0 | 2026-07-29 | Initial version. |