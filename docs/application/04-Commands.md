---
title: Commands
version: 1.0
status: Approved
owner: Software Architecture
category: Application
last_updated: 2026-07-29
---

# Commands

## Purpose

This document defines the Commands used by the SmartField Application Layer.

Commands represent explicit requests to perform business operations that modify the state of the domain.

A Command carries the information required to execute a business use case without containing business logic or technical implementation details.

---

# Scope

This document defines:

- Command responsibilities
- Command characteristics
- Command catalog
- Command lifecycle

It does not define:

- Business rules
- Validation logic
- REST requests
- DTO mappings
- Command handlers

These concerns belong to other architectural components.

---

# What is a Command?

A Command represents an intention to change the state of the business.

Commands are immutable application messages that describe **what** the application should do, not **how** it should do it.

Each Command is processed by exactly one Application Service during the execution of a business use case.

---

# Command Characteristics

All Commands should:

- Represent a business intention.
- Be immutable.
- Contain only required input data.
- Be technology independent.
- Be validated structurally before execution.
- Not contain business logic.

Commands should never make business decisions.

---

# Command Catalog

| Command | Purpose |
|----------|---------|
| RegisterCompanyCommand | Register a new company. |
| RegisterUserCommand | Register a new user. |
| AuthenticateUserCommand | Authenticate a user. |
| RegisterEmployeeCommand | Register a new employee. |
| UpdateEmployeeInformationCommand | Update employee information. |
| CreateProjectCommand | Create a project. |
| CompleteProjectCommand | Complete a project. |
| AssignEmployeeToProjectCommand | Assign an employee to a project. |
| CancelAssignmentCommand | Cancel an assignment. |
| AssignRoleToUserCommand | Grant a role to a user. |

---

# Command Definitions

## RegisterCompanyCommand

### Purpose

Request the registration of a new company.

### Consumed By

Company Application Service

---

## RegisterUserCommand

### Purpose

Request the creation of a new user.

### Consumed By

User Application Service

---

## AuthenticateUserCommand

### Purpose

Request user authentication.

### Consumed By

Authentication Application Service

---

## RegisterEmployeeCommand

### Purpose

Request the registration of a new employee.

### Consumed By

Employee Application Service

---

## UpdateEmployeeInformationCommand

### Purpose

Request the update of employee information.

### Consumed By

Employee Application Service

---

## CreateProjectCommand

### Purpose

Request the creation of a new project.

### Consumed By

Project Application Service

---

## CompleteProjectCommand

### Purpose

Request completion of a project.

### Consumed By

Project Application Service

---

## AssignEmployeeToProjectCommand

### Purpose

Request the assignment of an employee to a project.

### Consumed By

Assignment Application Service

---

## CancelAssignmentCommand

### Purpose

Request cancellation of an assignment.

### Consumed By

Assignment Application Service

---

## AssignRoleToUserCommand

### Purpose

Request assigning a business role to a user.

### Consumed By

Authorization Application Service

---

# Command Lifecycle

A Command follows the execution flow below:

```
Client Request
      │
      ▼
Command Created
      │
      ▼
Structural Validation
      │
      ▼
Application Service
      │
      ▼
Domain Execution
      │
      ▼
Command Completed
```

The Command is only a carrier of information throughout the execution.

---

# Structural Validation

Commands may perform structural validation before reaching the Domain Layer.

Examples include:

- Required fields.
- Data format.
- Length restrictions.
- Data type consistency.

Business validation belongs exclusively to the Domain Layer.

---

# Command vs Use Case

| Use Case | Command |
|-----------|---------|
| Business capability. | Business request. |
| Represents a business objective. | Represents an execution request. |
| Executed by an Application Service. | Consumed by an Application Service. |
| May involve multiple Commands in complex workflows. | Represents one application message. |

---

# Command vs Query

| Command | Query |
|----------|-------|
| Changes business state. | Reads business state. |
| May trigger Domain Events. | Never changes state. |
| Produces side effects. | Has no side effects. |
| Represents an intention. | Represents an information request. |

---

# Design Principles

Commands should:

- Be named using business language.
- Express an explicit intention.
- Be immutable.
- Remain independent of transport protocols.
- Avoid technical terminology.
- Be easy to understand by both technical and business stakeholders.

---

# Related Documentation

- 02-Use-Cases.md
- 03-Application-Services.md
- 05-Queries.md
- 07-Transactions.md
- ../domain/

---

# Revision History

| Version | Date | Description |
|----------|------|-------------|
| 1.0 | 2026-07-29 | Initial version. |