---
title: Domain Services
version: 1.0
status: Approved
owner: Software Architecture
category: Domain
last_updated: 2026-07-29
---

# Domain Services

## Purpose

This document defines the Domain Services used within the SmartField domain model.

Domain Services encapsulate business operations that cannot be naturally assigned to a single Entity, Value Object, or Aggregate while remaining part of the business domain.

Their purpose is to preserve a rich domain model by keeping business logic close to the domain instead of moving it into application services.

---

# Scope

This document defines:

- Domain Services
- Business responsibilities
- Service boundaries
- Collaboration with Aggregates

It does not define:

- Application Services
- Infrastructure Services
- REST Controllers
- Technical integrations

These topics are documented elsewhere.

---

# What is a Domain Service?

A Domain Service represents a business capability that:

- Belongs to the domain.
- Does not naturally belong to one Aggregate.
- Coordinates business rules across multiple Aggregates.
- Has no persistent identity.
- Is stateless.

Domain Services express business behavior rather than technical operations.

---

# Service Catalog

| Domain Service | Purpose |
|----------------|---------|
| Assignment Validation Service | Validates assignment business rules. |
| Authorization Policy Service | Evaluates domain authorization policies. |
| Project Allocation Service | Coordinates employee allocation decisions. |
| Audit Registration Service | Registers significant domain activities. |

---

# Domain Service Definitions

## Assignment Validation Service

### Purpose

Validates whether an employee can be assigned to a project.

### Collaborates With

- Employee Aggregate
- Project Aggregate
- Assignment Aggregate

### Business Rules

Examples include:

- Employee and Project belong to the same Company.
- Employee is active.
- Project accepts new assignments.
- Assignment period is valid.

The service evaluates business conditions but does not persist data.

---

## Authorization Policy Service

### Purpose

Evaluates domain authorization policies.

### Collaborates With

- User Aggregate
- Role Aggregate
- Permission Aggregate

### Business Rules

Examples include:

- User possesses required permissions.
- User account is active.
- Assigned role grants access.

---

## Project Allocation Service

### Purpose

Coordinates business decisions related to project participation.

### Collaborates With

- Employee Aggregate
- Project Aggregate
- Assignment Aggregate

### Business Rules

Examples include:

- Employee availability.
- Project capacity.
- Assignment compatibility.

---

## Audit Registration Service

### Purpose

Determines which business activities should be recorded for traceability.

### Collaborates With

- Audit Aggregate
- Other business Aggregates

### Business Rules

Examples include:

- Register significant business actions.
- Preserve immutable audit history.

---

# Characteristics

All Domain Services should:

- Be stateless.
- Encapsulate business logic.
- Operate on Aggregates.
- Respect Aggregate boundaries.
- Preserve business invariants.
- Avoid technical responsibilities.

---

# Interaction Model

```
Application Service
        │
        ▼
Domain Service
   │         │
   ▼         ▼
Aggregate   Aggregate
```

The Application Layer coordinates the use case.

The Domain Service evaluates business behavior.

Aggregates protect their own consistency.

---

# Domain Service vs Application Service

| Domain Service | Application Service |
|----------------|---------------------|
| Contains business logic. | Orchestrates use cases. |
| Lives in the Domain Layer. | Lives in the Application Layer. |
| Works with Aggregates. | Coordinates workflows. |
| Technology independent. | May coordinate repositories and external ports. |
| Expresses business behavior. | Expresses application behavior. |

---

# Design Principles

Domain Services should:

- Represent meaningful business capabilities.
- Avoid becoming generic utility classes.
- Be cohesive.
- Be independent of infrastructure.
- Keep business rules inside the Domain.

If business logic belongs to an Entity or Aggregate, it should not be moved to a Domain Service.

---

# Related Documentation

- 05-Entities.md
- 06-Value-Objects.md
- 07-Aggregates.md
- 09-Domain-Events.md
- 11-Domain-Rules.md
- ../application/

---

# Revision History

| Version | Date | Description |
|----------|------|-------------|
| 1.0 | 2026-07-29 | Initial version. |