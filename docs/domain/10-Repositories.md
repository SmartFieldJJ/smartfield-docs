---
title: Repositories
version: 1.0
status: Approved
owner: Software Architecture
category: Domain
last_updated: 2026-07-29
---

# Repositories

## Purpose

This document defines the Repository contracts used by the SmartField domain.

Repositories provide the domain with a mechanism to retrieve and persist Aggregate Roots while keeping the domain independent of persistence technologies.

A Repository represents a domain abstraction rather than a database implementation.

---

# Scope

This document defines:

- Repository contracts
- Aggregate ownership
- Repository responsibilities
- Repository principles

It does not define:

- Database access
- SQL queries
- ORM mappings
- Spring Data repositories
- Persistence implementation

These implementation details belong to the Infrastructure documentation.

---

# What is a Repository?

A Repository provides access to Aggregate Roots.

From the perspective of the domain, a Repository behaves like an in-memory collection of Aggregates.

Repositories hide all persistence concerns and expose only operations that are meaningful to the business.

---

# Repository Principles

Repositories should:

- Work only with Aggregate Roots.
- Hide persistence details.
- Expose business-oriented operations.
- Return domain objects.
- Preserve Aggregate boundaries.
- Remain technology independent.

Repositories should never expose database concepts.

---

# Repository Catalog

| Repository | Aggregate |
|------------|-----------|
| Company Repository | Company |
| User Repository | User |
| Employee Repository | Employee |
| Project Repository | Project |
| Assignment Repository | Assignment |
| Audit Repository | Audit Record |

---

# Repository Definitions

## Company Repository

### Aggregate

Company

### Responsibilities

- Retrieve companies.
- Persist company changes.
- Verify company existence.

Typical business operations include:

- Find by identifier.
- Find by business criteria.
- Save company.

---

## User Repository

### Aggregate

User

### Responsibilities

- Retrieve users.
- Persist user changes.
- Verify user existence.

Typical business operations include:

- Find by identifier.
- Find by username or email.
- Save user.

---

## Employee Repository

### Aggregate

Employee

### Responsibilities

- Retrieve employees.
- Persist employee changes.
- Search employees.

Typical business operations include:

- Find by identifier.
- Find employees by company.
- Save employee.

---

## Project Repository

### Aggregate

Project

### Responsibilities

- Retrieve projects.
- Persist project changes.

Typical business operations include:

- Find by identifier.
- Find active projects.
- Save project.

---

## Assignment Repository

### Aggregate

Assignment

### Responsibilities

- Retrieve assignments.
- Persist assignment changes.

Typical business operations include:

- Find by identifier.
- Find assignments by employee.
- Find assignments by project.
- Save assignment.

---

## Audit Repository

### Aggregate

Audit Record

### Responsibilities

- Store audit history.
- Retrieve audit records.

Typical business operations include:

- Save audit record.
- Find audit history.

---

# Aggregate Ownership

Each Aggregate has exactly one Repository.

```
Company
      │
      ▼
Company Repository

Employee
      │
      ▼
Employee Repository

Project
      │
      ▼
Project Repository

Assignment
      │
      ▼
Assignment Repository

User
      │
      ▼
User Repository
```

Repositories never manage multiple Aggregate Roots.

---

# Repository Usage

Repositories are typically used by:

- Application Services
- Domain Services (when appropriate)

Entities and Value Objects should not depend directly on Repositories.

---

# Repository Design Guidelines

Repositories should expose operations using domain terminology.

Examples include:

- FindEmployeeById
- FindProjectsByCompany
- ExistsCompany
- SaveAssignment

Avoid exposing persistence-specific concepts such as:

- SQL statements
- Pagination frameworks
- ORM sessions
- Database transactions

---

# Repository vs DAO

| Repository | DAO |
|------------|-----|
| Domain abstraction | Data access abstraction |
| Business-oriented | Persistence-oriented |
| Returns Aggregates | Returns persistence models |
| Lives in the Domain | Lives in Infrastructure |
| Technology independent | Technology dependent |

A Repository models the needs of the domain, whereas a DAO focuses on data storage concerns.

---

# Implementation Responsibility

Repository interfaces belong to the Domain Layer.

Their implementations belong to the Infrastructure Layer.

This separation preserves the independence of the domain model and allows persistence technologies to change without affecting business logic.

---

# Related Documentation

- 07-Aggregates.md
- 08-Domain-Services.md
- 11-Domain-Rules.md
- ../architecture/05-Layered-Architecture.md
- ../infrastructure/

---

# Revision History

| Version | Date | Description |
|----------|------|-------------|
| 1.0 | 2026-07-29 | Initial version. |