---
title: Resource Model
version: 1.0
status: Approved
owner: Software Architecture
category: API
last_updated: 2026-07-29
---

# Resource Model

## Purpose

This document defines the public resources exposed by the SmartField API.

Resources represent the business concepts that external consumers interact with through the public API. They provide a stable abstraction over the internal domain model and serve as the foundation for all API operations.

The Resource Model describes **what** the API exposes, not **how** those resources are manipulated.

---

# Scope

This document defines:

- Public API resources
- Resource responsibilities
- Resource relationships
- Resource hierarchy
- Resource design principles

It does not define:

- HTTP methods
- URI operations
- Request or response payloads
- Domain entities
- Database tables

These concerns are documented separately.

---

# What is a Resource?

A Resource is a publicly identifiable business concept exposed through the API.

A Resource represents information that external consumers can discover, retrieve, create, update, or remove through standardized API operations.

Resources are independent of internal implementation details.

---

# Resource Catalog

| Resource | Description |
|----------|-------------|
| Companies | Organizations managed by SmartField. |
| Users | Identities authorized to access the platform. |
| Employees | Members of a company workforce. |
| Projects | Business initiatives managed by a company. |
| Assignments | Relationships between employees and projects. |
| Audit Records | Historical records of business activities. |

---

# Resource Responsibilities

## Companies

Represents an organization using SmartField.

Typical information includes:

- Company identity
- Business information
- Operational status

---

## Users

Represents an authenticated identity within the platform.

Typical information includes:

- User profile
- Assigned roles
- Business permissions

---

## Employees

Represents an employee belonging to a company.

Typical information includes:

- Personal information
- Employment details
- Organizational relationship

---

## Projects

Represents a business project managed within a company.

Typical information includes:

- Project information
- Status
- Planning data

---

## Assignments

Represents the relationship between an Employee and a Project.

Typical information includes:

- Assigned employee
- Assigned project
- Assignment period
- Assignment status

---

## Audit Records

Represents historical information describing relevant business events.

Typical information includes:

- Event description
- Timestamp
- Responsible user
- Affected resource

---

# Resource Relationships

The public Resource Model can be represented conceptually as:

```
Company
│
├── Users
├── Employees
├── Projects
│       │
│       └── Assignments
│
└── Audit Records
```

The hierarchy expresses business relationships visible to API consumers rather than internal implementation details.

---

# Resource Characteristics

All Resources should:

- Represent meaningful business concepts.
- Have a stable identity.
- Remain independent of implementation technologies.
- Be understandable to external consumers.
- Support long-term evolution.

Resources should never expose internal architectural structures.

---

# Resource Representations

A single Resource may have multiple representations depending on the client need.

Examples include:

- Summary representation
- Detailed representation
- Collection representation
- Reference representation

Different representations describe the same Resource while exposing different levels of detail.

---

# Resource Design Principles

Resources should:

- Use business terminology.
- Be stable over time.
- Avoid technical naming.
- Represent concepts meaningful to clients.
- Preserve backward compatibility.
- Remain independent of internal domain structures.

---

# Resource vs Domain Entity

| Resource | Domain Entity |
|----------|---------------|
| Public API abstraction | Internal business model |
| Designed for external consumers | Designed for business behavior |
| Defines communication contracts | Defines business rules |
| May aggregate multiple domain concepts | Represents a single domain concept |

A Resource is not required to map one-to-one with a Domain Entity.

---

# Resource Lifecycle

A Resource typically follows this conceptual lifecycle:

```
Resource Created
        │
        ▼
Resource Retrieved
        │
        ▼
Resource Updated
        │
        ▼
Resource Archived or Removed
```

The lifecycle is conceptual and independent of specific HTTP operations.

---

# Related Documentation

- README.md
- 01-API-Overview.md
- 02-API-Design-Principles.md
- 04-Request-Response-Model.md
- 05-Resource-Operations.md
- ../domain/04-Domain-Model.md
- ../application/02-Use-Cases.md

---

# Revision History

| Version | Date | Description |
|----------|------|-------------|
| 1.0 | 2026-07-29 | Initial version. |