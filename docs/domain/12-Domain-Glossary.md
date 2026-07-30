---
title: Domain Glossary
version: 1.0
status: Approved
owner: Software Architecture
category: Domain
last_updated: 2026-07-29
---

# Domain Glossary

## Purpose

This glossary provides a consolidated reference of the concepts used throughout the SmartField domain model.

Its objective is to establish a consistent vocabulary for architects, developers, testers, and technical stakeholders working with the Domain Layer.

Unlike the Business Glossary, this document focuses on concepts that are relevant to the software domain model.

---

# Scope

This glossary includes:

- Domain concepts
- DDD terminology
- Aggregate names
- Domain building blocks
- Business concepts represented inside the software

It does not define:

- Technical frameworks
- Infrastructure technologies
- API terminology

---

# Domain Concepts

## Aggregate

A consistency boundary that groups related domain objects under a single Aggregate Root.

Only the Aggregate Root may be accessed from outside the Aggregate.

---

## Aggregate Root

The primary Entity responsible for protecting the consistency of an Aggregate.

---

## Assignment

Represents the participation of an Employee in a Project during a defined period.

---

## Assignment Period

A Value Object representing the time interval during which an Assignment remains valid.

---

## Audit Record

An immutable record describing a significant business action performed within the system.

---

## Company

Represents an organization that owns users, employees, and projects within SmartField.

---

## CompanyId

Unique identifier of a Company.

---

## Domain Event

A business fact that has already occurred and may be observed by other parts of the domain.

---

## Domain Service

A stateless domain component that encapsulates business logic spanning multiple Aggregates.

---

## Employee

A person who belongs to a Company and may participate in one or more Projects.

---

## Entity

A domain object identified by a stable identity throughout its lifecycle.

---

## Permission

Represents a business capability that may be granted to a User through one or more Roles.

---

## Project

Represents a business initiative managed by a Company.

---

## Repository

A domain abstraction responsible for retrieving and persisting Aggregate Roots.

---

## Role

Represents a collection of Permissions assigned to Users.

---

## User

Represents an authenticated identity that accesses SmartField.

---

## Value Object

An immutable domain object defined entirely by its values rather than by an identity.

---

# DDD Terminology

## Bounded Context

A conceptual boundary within which a specific domain model is valid.

---

## Consistency Boundary

The transactional boundary protected by an Aggregate.

---

## Invariant

A business rule that must always remain true.

---

## Ubiquitous Language

The shared language used by business experts and software professionals to describe the domain.

---

# Relationships

```
Company
 ├── Users
 ├── Employees
 └── Projects

Employee
      │
      ▼
 Assignment
      ▲
      │
Project
```

---

# Naming Conventions

Domain terminology should:

- Use business language.
- Be technology independent.
- Be explicit.
- Avoid abbreviations.
- Remain consistent across documentation and source code.

---

# Usage Guidelines

Every new domain concept introduced into SmartField should:

1. Be documented in this glossary.
2. Follow the Ubiquitous Language.
3. Be referenced consistently throughout the documentation.
4. Preserve existing terminology whenever possible.

---

# Related Documentation

- 01-Domain-Overview.md
- 02-Ubiquitous-Language.md
- 03-Bounded-Contexts.md
- 04-Domain-Model.md
- 05-Entities.md
- 06-Value-Objects.md
- 07-Aggregates.md
- 08-Domain-Services.md
- 09-Domain-Events.md
- 10-Repositories.md
- 11-Domain-Rules.md
- ../overview/00-Business-Glossary.md

---

# Revision History

| Version | Date | Description |
|----------|------|-------------|
| 1.0 | 2026-07-29 | Initial version. |