---
title: Application Services
version: 1.0
status: Approved
owner: Software Architecture
category: Application
last_updated: 2026-07-29
---

# Application Services

## Purpose

This document defines the Application Services responsible for orchestrating business use cases within SmartField.

Application Services coordinate the execution of application workflows by interacting with the Domain Layer, Repository interfaces, and external ports while ensuring that business operations are executed consistently.

They do not contain business rules.

---

# Scope

This document defines:

- Application Service responsibilities
- Service boundaries
- Use case orchestration
- Collaboration with the Domain Layer

It does not define:

- Business rules
- Infrastructure implementations
- REST Controllers
- Framework-specific services

Those concerns belong to other architectural layers.

---

# What is an Application Service?

An Application Service coordinates the execution of a single business use case.

Its responsibilities include:

- Receiving application requests.
- Loading Aggregates.
- Invoking domain behavior.
- Coordinating Domain Services.
- Persisting Aggregate changes.
- Publishing Domain Events.
- Returning application responses.

Business decisions remain inside the Domain Layer.

---

# Application Service Catalog

| Application Service | Primary Responsibility |
|---------------------|------------------------|
| Company Application Service | Coordinate company operations. |
| User Application Service | Coordinate user lifecycle operations. |
| Authentication Application Service | Coordinate authentication workflows. |
| Employee Application Service | Coordinate employee management. |
| Project Application Service | Coordinate project management. |
| Assignment Application Service | Coordinate assignment workflows. |
| Authorization Application Service | Coordinate authorization operations. |
| Audit Application Service | Coordinate audit retrieval operations. |

---

# Service Definitions

## Company Application Service

### Responsibilities

- Register companies.
- Update company information.
- Coordinate company lifecycle operations.

### Collaborates With

- Company Aggregate
- Company Repository

---

## User Application Service

### Responsibilities

- Register users.
- Update user information.
- Manage user lifecycle.

### Collaborates With

- User Aggregate
- User Repository

---

## Authentication Application Service

### Responsibilities

- Authenticate users.
- Coordinate login workflows.
- Produce authentication results.

### Collaborates With

- User Aggregate
- Authentication Port

---

## Employee Application Service

### Responsibilities

- Register employees.
- Update employee information.
- Coordinate employee workflows.

### Collaborates With

- Employee Aggregate
- Employee Repository

---

## Project Application Service

### Responsibilities

- Create projects.
- Complete projects.
- Coordinate project lifecycle operations.

### Collaborates With

- Project Aggregate
- Project Repository

---

## Assignment Application Service

### Responsibilities

- Assign employees.
- Cancel assignments.
- Coordinate assignment workflows.

### Collaborates With

- Assignment Aggregate
- Assignment Validation Service
- Assignment Repository

---

## Authorization Application Service

### Responsibilities

- Assign roles.
- Evaluate authorization requests.

### Collaborates With

- User Aggregate
- Authorization Policy Service

---

## Audit Application Service

### Responsibilities

- Retrieve audit history.
- Coordinate audit queries.

### Collaborates With

- Audit Repository

---

# Execution Responsibilities

Application Services typically perform the following sequence:

```
Receive Request
       │
       ▼
Validate Input
       │
       ▼
Load Aggregates
       │
       ▼
Invoke Domain
       │
       ▼
Persist Changes
       │
       ▼
Publish Domain Events
       │
       ▼
Return Response
```

Each step contributes to executing the use case without introducing business logic into the Application Layer.

---

# Collaboration Model

```
Presentation
      │
      ▼
Application Service
      │
      ▼
Domain Service
      │
      ▼
Aggregate
```

Repositories and external ports support the orchestration process but do not alter the separation of responsibilities.

---

# Characteristics

Application Services should:

- Be stateless.
- Orchestrate one business use case at a time.
- Depend on abstractions.
- Delegate business rules to the Domain Layer.
- Remain independent of infrastructure technologies.
- Keep workflows explicit and easy to understand.

---

# Application Service vs Domain Service

| Application Service | Domain Service |
|---------------------|----------------|
| Orchestrates a use case. | Encapsulates business behavior. |
| Coordinates workflows. | Evaluates business rules. |
| Uses repositories and ports. | Uses Aggregates and Value Objects. |
| Manages application flow. | Preserves domain consistency. |
| Lives in the Application Layer. | Lives in the Domain Layer. |

---

# Design Principles

Application Services should:

- Represent application capabilities.
- Avoid business decision-making.
- Be cohesive.
- Coordinate, not calculate.
- Keep the Domain Model rich.
- Be independent of frameworks.

---

# Related Documentation

- 02-Use-Cases.md
- 04-Commands.md
- 05-Queries.md
- 06-Ports.md
- 07-Transactions.md
- ../domain/08-Domain-Services.md

---

# Revision History

| Version | Date | Description |
|----------|------|-------------|
| 1.0 | 2026-07-29 | Initial version. |