---
title: Business Events
version: 1.0
status: Approved
owner: Enterprise Architecture
category: Business
last_updated: 2026-07-29
---

# Business Events

## Purpose

This document defines the significant business events that occur within SmartField.

Business events represent meaningful changes in the state of the business. They are triggered by business processes and actors, and they provide the foundation for business traceability, domain modeling, and future event-driven integrations.

Business events describe **what happened from the business perspective**, independently of how the software processes or stores the event.

---

# Scope

This document defines:

- Business events
- Event triggers
- Business outcomes
- Originating actors
- Affected business capabilities

It does not define:

- Domain Events
- Integration Events
- Message Brokers
- Event Streaming
- Technical implementation

---

# Business Event Overview

| Event | Triggered By | Business Capability |
|--------|--------------|---------------------|
| Company Registered | Company Administrator | Company Management |
| Employee Registered | Company Administrator | Workforce Management |
| Employee Updated | Company Administrator | Workforce Management |
| Project Created | Company Administrator | Project Management |
| Project Updated | Supervisor | Project Management |
| Employee Assigned | Supervisor | Assignment Management |
| Assignment Removed | Supervisor | Assignment Management |
| User Authenticated | User | Identity & Access Management |
| User Logged Out | User | Identity & Access Management |

---

# Company Registered

## Description

Occurs when a new organization is successfully registered in SmartField.

### Triggered By

Company Administrator

### Business Outcome

A new company becomes available for operational management.

### Affected Capability

Company Management

---

# Employee Registered

## Description

Occurs when a new employee is incorporated into the organization.

### Triggered By

Company Administrator

### Business Outcome

The employee becomes part of the company's workforce.

### Affected Capability

Workforce Management

---

# Employee Updated

## Description

Occurs when employee information changes.

### Triggered By

Company Administrator

### Business Outcome

The workforce information remains accurate and up to date.

### Affected Capability

Workforce Management

---

# Project Created

## Description

Occurs when a new operational project is created.

### Triggered By

Company Administrator

### Business Outcome

A new project becomes available for planning and execution.

### Affected Capability

Project Management

---

# Project Updated

## Description

Occurs when project information or status changes.

### Triggered By

Supervisor

### Business Outcome

Project information remains aligned with current operations.

### Affected Capability

Project Management

---

# Employee Assigned

## Description

Occurs when an employee is assigned to a project.

### Triggered By

Supervisor

### Business Outcome

The employee becomes an active participant in the selected project.

### Affected Capability

Assignment Management

---

# Assignment Removed

## Description

Occurs when an employee is removed from a project assignment.

### Triggered By

Supervisor

### Business Outcome

The employee is no longer assigned to the selected project.

### Affected Capability

Assignment Management

---

# User Authenticated

## Description

Occurs when a user successfully authenticates into SmartField.

### Triggered By

User

### Business Outcome

The user gains access to authorized business capabilities.

### Affected Capability

Identity & Access Management

---

# User Logged Out

## Description

Occurs when a user terminates an authenticated session.

### Triggered By

User

### Business Outcome

The authenticated session ends.

### Affected Capability

Identity & Access Management

---

# Event Lifecycle

Business events follow a common lifecycle:

```
Business Action
        │
        ▼
Business Event
        │
        ▼
Business State Changes
        │
        ▼
Business Process Continues
```

Events describe **facts** that have already occurred.

---

# Event Principles

Business events follow these principles:

- Events describe completed business facts.
- Events are immutable.
- Every event has a clear business meaning.
- Events originate from a business action.
- Events may affect one or more business capabilities.

---

# Related Documentation

- 02-Business-Processes.md
- 03-Business-Capabilities.md
- 05-Business-Rules.md
- ../domain/01-Domain-Overview.md
- ../domain/05-Domain-Events.md

---

# Revision History

| Version | Date | Description |
|----------|------|-------------|
| 1.0 | 2026-07-29 | Initial version. |