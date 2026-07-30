---
title: Use Cases
version: 1.0
status: Approved
owner: Software Architecture
category: Application
last_updated: 2026-07-29
---

# Use Cases

## Purpose

This document defines the business use cases supported by the SmartField application.

A use case represents a complete business capability exposed by the Application Layer.

Each use case coordinates one or more domain operations to accomplish a specific business objective.

---

# Scope

This document defines:

- Business use cases
- Application capabilities
- Primary actors
- Business objectives
- Domain collaboration

It does not define:

- Workflow implementation
- REST endpoints
- Commands
- Queries
- User interface behavior

These concerns are documented separately.

---

# What is a Use Case?

A Use Case represents a business interaction between an actor and the application.

Each use case:

- Has a clear business objective.
- Produces a meaningful business outcome.
- Is coordinated by an Application Service.
- Delegates business rules to the Domain Layer.

A Use Case does not contain business logic.

---

# Use Case Categories

SmartField groups its use cases into the following business domains:

- Authentication
- Company Management
- Employee Management
- Project Management
- Assignment Management
- Authorization
- Audit

---

# Use Case Catalog

| Use Case | Primary Actor | Business Objective |
|-----------|---------------|--------------------|
| Register Company | Administrator | Create a new company. |
| Register User | Administrator | Create a new application user. |
| Authenticate User | User | Access the application. |
| Register Employee | Administrator | Add an employee to a company. |
| Update Employee Information | Administrator | Maintain employee information. |
| Create Project | Project Manager | Register a new project. |
| Complete Project | Project Manager | Finish a project lifecycle. |
| Assign Employee to Project | Project Manager | Allocate an employee to a project. |
| Cancel Assignment | Project Manager | End an employee assignment. |
| Assign Role to User | Administrator | Grant business permissions. |
| View Audit History | Auditor | Review business activity. |

---

# Use Case Definitions

## Register Company

### Objective

Create a new company within SmartField.

### Primary Actor

Administrator

### Collaborates With

- Company Aggregate

### Business Outcome

A new company becomes available for operation.

---

## Register User

### Objective

Create a new authenticated user.

### Primary Actor

Administrator

### Collaborates With

- User Aggregate

### Business Outcome

A user account becomes available.

---

## Authenticate User

### Objective

Authenticate an existing user.

### Primary Actor

User

### Collaborates With

- User Aggregate

### Business Outcome

The user gains access according to assigned permissions.

---

## Register Employee

### Objective

Register a new employee.

### Primary Actor

Administrator

### Collaborates With

- Employee Aggregate

### Business Outcome

The employee becomes available for future assignments.

---

## Update Employee Information

### Objective

Maintain employee information.

### Primary Actor

Administrator

### Collaborates With

- Employee Aggregate

### Business Outcome

Employee information remains current.

---

## Create Project

### Objective

Create a new project.

### Primary Actor

Project Manager

### Collaborates With

- Project Aggregate

### Business Outcome

A project becomes available.

---

## Complete Project

### Objective

Complete a project lifecycle.

### Primary Actor

Project Manager

### Collaborates With

- Project Aggregate

### Business Outcome

The project is closed for future work.

---

## Assign Employee to Project

### Objective

Assign an employee to a project.

### Primary Actor

Project Manager

### Collaborates With

- Assignment Aggregate
- Employee Aggregate
- Project Aggregate
- Assignment Validation Service

### Business Outcome

An active assignment is created.

---

## Cancel Assignment

### Objective

Terminate an employee assignment.

### Primary Actor

Project Manager

### Collaborates With

- Assignment Aggregate

### Business Outcome

The assignment is closed while preserving its history.

---

## Assign Role to User

### Objective

Grant a business role to a user.

### Primary Actor

Administrator

### Collaborates With

- User Aggregate

### Business Outcome

The user's authorization changes.

---

## View Audit History

### Objective

Review business activity.

### Primary Actor

Auditor

### Collaborates With

- Audit Repository

### Business Outcome

Audit records are available for inspection.

---

# Use Case Characteristics

Every use case should:

- Represent a business capability.
- Have one primary objective.
- Produce one meaningful business outcome.
- Coordinate domain behavior.
- Remain independent of technology.

---

# Application Collaboration

```
Actor
   │
   ▼
Use Case
   │
   ▼
Application Service
   │
   ▼
Domain
```

The Application Layer coordinates execution while the Domain Layer evaluates business behavior.

---

# Design Principles

Use Cases should:

- Be expressed using business language.
- Represent complete business goals.
- Avoid technical terminology.
- Remain stable even if technology changes.
- Be independent of user interface design.

---

# Related Documentation

- 03-Application-Services.md
- 04-Commands.md
- 05-Queries.md
- 08-Application-Workflows.md
- ../domain/

---

# Revision History

| Version | Date | Description |
|----------|------|-------------|
| 1.0 | 2026-07-29 | Initial version. |