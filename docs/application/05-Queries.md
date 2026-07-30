---
title: Queries
version: 1.0
status: Approved
owner: Software Architecture
category: Application
last_updated: 2026-07-29
---

# Queries

## Purpose

This document defines the Queries used by the SmartField Application Layer.

Queries represent explicit requests to retrieve information from the application without modifying the state of the domain.

A Query carries the information required to obtain application data while remaining independent of business logic and infrastructure technologies.

---

# Scope

This document defines:

- Query responsibilities
- Query characteristics
- Query catalog
- Query lifecycle

It does not define:

- Business rules
- Database queries
- Repository implementations
- REST endpoints
- Query handlers

These concerns are documented elsewhere.

---

# What is a Query?

A Query represents an intention to retrieve information from the application.

Queries are immutable application messages that describe what information is requested rather than how it is obtained.

Executing a Query must never change the state of the domain.

---

# Query Characteristics

All Queries should:

- Represent an information request.
- Be immutable.
- Contain only retrieval criteria.
- Be technology independent.
- Produce no side effects.
- Not contain business logic.

Queries must never modify business state.

---

# Query Catalog

| Query | Purpose |
|---------|---------|
| GetCompanyDetailsQuery | Retrieve company information. |
| SearchCompaniesQuery | Search companies using business criteria. |
| GetUserDetailsQuery | Retrieve user information. |
| SearchUsersQuery | Search users. |
| GetEmployeeDetailsQuery | Retrieve employee information. |
| SearchEmployeesQuery | Search employees. |
| GetProjectDetailsQuery | Retrieve project information. |
| SearchProjectsQuery | Search projects. |
| GetAssignmentDetailsQuery | Retrieve assignment information. |
| SearchAssignmentsQuery | Search assignments. |
| GetAuditHistoryQuery | Retrieve audit records. |
| GetDashboardSummaryQuery | Retrieve dashboard information. |

---

# Query Definitions

## GetCompanyDetailsQuery

### Purpose

Retrieve detailed information for a specific company.

### Consumed By

Company Application Service

---

## SearchCompaniesQuery

### Purpose

Retrieve companies matching business search criteria.

### Consumed By

Company Application Service

---

## GetUserDetailsQuery

### Purpose

Retrieve detailed information for a specific user.

### Consumed By

User Application Service

---

## SearchUsersQuery

### Purpose

Retrieve users matching business criteria.

### Consumed By

User Application Service

---

## GetEmployeeDetailsQuery

### Purpose

Retrieve detailed information for a specific employee.

### Consumed By

Employee Application Service

---

## SearchEmployeesQuery

### Purpose

Retrieve employees according to business filters.

### Consumed By

Employee Application Service

---

## GetProjectDetailsQuery

### Purpose

Retrieve project information.

### Consumed By

Project Application Service

---

## SearchProjectsQuery

### Purpose

Retrieve projects matching search criteria.

### Consumed By

Project Application Service

---

## GetAssignmentDetailsQuery

### Purpose

Retrieve assignment information.

### Consumed By

Assignment Application Service

---

## SearchAssignmentsQuery

### Purpose

Retrieve assignments.

### Consumed By

Assignment Application Service

---

## GetAuditHistoryQuery

### Purpose

Retrieve audit history.

### Consumed By

Audit Application Service

---

## GetDashboardSummaryQuery

### Purpose

Retrieve summarized operational information for the application's dashboard.

### Consumed By

Dashboard Application Service

---

# Query Lifecycle

A Query follows the execution flow below:

```
Client Request
      │
      ▼
Query Created
      │
      ▼
Structural Validation
      │
      ▼
Application Service
      │
      ▼
Read Model
      │
      ▼
Application Response
```

The Query only carries the criteria required to retrieve information.

---

# Structural Validation

Queries may perform structural validation before execution.

Examples include:

- Required parameters.
- Identifier format.
- Pagination values.
- Sorting options.
- Filter consistency.

Business validation remains the responsibility of the Domain Layer when required.

---

# Query vs Command

| Query | Command |
|--------|---------|
| Retrieves information. | Changes business state. |
| Produces no side effects. | May produce side effects. |
| Never publishes Domain Events. | May publish Domain Events. |
| Represents an information request. | Represents a business intention. |

---

# Query vs Repository

| Query | Repository |
|--------|------------|
| Application message. | Domain abstraction. |
| Expresses retrieval intent. | Retrieves Aggregate Roots. |
| Lives in the Application Layer. | Lives in the Domain Layer. |
| Technology independent. | Technology independent. |

A Query requests information; a Repository provides access to Aggregate Roots.

---

# Design Principles

Queries should:

- Use business terminology.
- Represent information needs.
- Remain immutable.
- Avoid technical details.
- Be independent of transport protocols.
- Never modify domain state.

---

# Related Documentation

- 02-Use-Cases.md
- 03-Application-Services.md
- 04-Commands.md
- 06-Ports.md
- 08-Application-Workflows.md
- ../domain/10-Repositories.md

---

# Revision History

| Version | Date | Description |
|----------|------|-------------|
| 1.0 | 2026-07-29 | Initial version. |