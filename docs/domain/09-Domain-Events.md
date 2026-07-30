---
title: Domain Events
version: 1.0
status: Approved
owner: Software Architecture
category: Domain
last_updated: 2026-07-29
---

# Domain Events

## Purpose

This document defines the Domain Events that represent significant business occurrences within the SmartField domain.

Domain Events capture facts that have already happened in the business and communicate meaningful changes between different parts of the domain while preserving loose coupling.

---

# Scope

This document defines:

- Domain Events
- Business significance
- Event ownership
- Event consumers
- Business consequences

It does not define:

- Message brokers
- Event buses
- Kafka topics
- Integration events
- Event serialization

Those implementation details belong to the Architecture and Infrastructure documentation.

---

# What is a Domain Event?

A Domain Event represents a business fact that has already occurred.

A Domain Event:

- Is immutable.
- Represents something that happened.
- Uses past tense.
- Belongs to the Domain.
- Has business meaning.

Examples include:

- Company Registered
- Employee Created
- Project Completed
- Assignment Cancelled

---

# Event Catalog

| Domain Event | Produced By |
|--------------|-------------|
| Company Registered | Company Aggregate |
| Company Deactivated | Company Aggregate |
| User Registered | User Aggregate |
| Employee Registered | Employee Aggregate |
| Employee Updated | Employee Aggregate |
| Project Created | Project Aggregate |
| Project Completed | Project Aggregate |
| Employee Assigned | Assignment Aggregate |
| Assignment Cancelled | Assignment Aggregate |
| Role Assigned | User Aggregate |

---

# Domain Event Definitions

## Company Registered

### Description

Occurs when a new company becomes part of SmartField.

### Produced By

Company Aggregate

### Business Consequences

- Company becomes operational.
- Users can be registered.
- Projects can be created.

---

## Company Deactivated

### Description

Occurs when a company is no longer active.

### Produced By

Company Aggregate

### Business Consequences

- Business operations stop.
- Access restrictions may apply.

---

## User Registered

### Description

Occurs when a new authenticated user is created.

### Produced By

User Aggregate

### Business Consequences

- User may authenticate.
- Authorization policies become applicable.

---

## Employee Registered

### Description

Occurs when an employee is added to a company.

### Produced By

Employee Aggregate

### Business Consequences

- Employee becomes available for assignments.

---

## Employee Updated

### Description

Occurs when significant employee information changes.

### Produced By

Employee Aggregate

### Business Consequences

- Related business processes may react.

---

## Project Created

### Description

Occurs when a new project is created.

### Produced By

Project Aggregate

### Business Consequences

- Employees may be assigned.

---

## Project Completed

### Description

Occurs when a project reaches completion.

### Produced By

Project Aggregate

### Business Consequences

- No further assignments should be created.
- Existing assignments may be finalized.

---

## Employee Assigned

### Description

Occurs when an employee is assigned to a project.

### Produced By

Assignment Aggregate

### Business Consequences

- Assignment becomes active.
- Employee participation begins.

---

## Assignment Cancelled

### Description

Occurs when an assignment is cancelled.

### Produced By

Assignment Aggregate

### Business Consequences

- Employee participation ends.
- Assignment history is preserved.

---

## Role Assigned

### Description

Occurs when a role is granted to a user.

### Produced By

User Aggregate

### Business Consequences

- User permissions change.

---

# Event Characteristics

All Domain Events should:

- Represent completed business facts.
- Be immutable.
- Use business terminology.
- Be expressed in past tense.
- Be independent of technology.

---

# Event Lifecycle

```
Business Action
        │
        ▼
Business Rule Executed
        │
        ▼
Domain State Changes
        │
        ▼
Domain Event Raised
        │
        ▼
Interested Components React
```

The event is raised only after the business state has changed successfully.

---

# Event Ownership

Every Domain Event has exactly one producer.

Only the Aggregate that owns the business state may publish the corresponding Domain Event.

This ensures a clear source of truth for business facts.

---

# Domain Events vs Integration Events

| Domain Event | Integration Event |
|--------------|-------------------|
| Business concept | Technical communication |
| Lives inside the Domain | Lives outside the Domain |
| Technology independent | Technology dependent |
| Expresses business facts | Exchanges information between systems |
| Used by the domain model | Used by external integrations |

A Domain Event may eventually result in an Integration Event, but they are not the same concept.

---

# Design Principles

Domain Events should:

- Represent meaningful business occurrences.
- Avoid technical details.
- Preserve business terminology.
- Be immutable.
- Have a single business meaning.
- Be easy to understand by both business and technical stakeholders.

---

# Related Documentation

- 07-Aggregates.md
- 08-Domain-Services.md
- 10-Repositories.md
- 11-Domain-Rules.md
- ../architecture/03-Architectural-Decisions.md

---

# Revision History

| Version | Date | Description |
|----------|------|-------------|
| 1.0 | 2026-07-29 | Initial version. |