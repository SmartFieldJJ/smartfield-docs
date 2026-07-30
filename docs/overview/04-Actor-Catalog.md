---
title: Actor Catalog
version: 1.0
status: Approved
owner: Product Management
category: Overview
last_updated: 2026-07-29
---

# Actor Catalog

## Purpose

This document identifies the primary actors that interact with SmartField from a business perspective.

Actors represent roles that participate in business processes and system interactions. They are independent of technical implementation and authentication mechanisms.

This catalog provides a common reference for business analysis, use cases, and system design.

---

# Scope

This document describes:

- Business actors
- Their responsibilities
- Their primary objectives
- Their interactions with the platform

It does not define:

- Permissions
- Security roles
- Authentication mechanisms
- Technical implementation

These topics are documented separately.

---

# Actor Overview

| Actor | Description |
|--------|-------------|
| Company Administrator | Manages the organization and its operational information. |
| Supervisor | Coordinates projects and oversees field workers. |
| Field Worker | Executes operational activities assigned through the platform. |
| System Administrator | Maintains the platform and its operational integrity. |

---

# Company Administrator

## Description

Represents the person responsible for configuring and managing a company's information within SmartField.

## Responsibilities

- Manage company information.
- Register employees.
- Manage users.
- Create projects.
- Assign supervisors.
- Monitor organizational activity.

## Primary Goals

- Maintain an accurate organizational structure.
- Ensure operational continuity.
- Keep company information up to date.

---

# Supervisor

## Description

Coordinates operational activities and supervises field workers assigned to projects.

## Responsibilities

- Monitor project execution.
- Coordinate field personnel.
- Review assignments.
- Track operational progress.

## Primary Goals

- Ensure projects are executed efficiently.
- Coordinate available resources.
- Improve operational visibility.

---

# Field Worker

## Description

Represents employees who perform operational activities outside the office.

## Responsibilities

- Access assigned projects.
- Review personal assignments.
- Consult operational information.
- Keep informed about assigned work.

## Primary Goals

- Access relevant information quickly.
- Stay informed about current assignments.
- Support efficient field operations.

---

# System Administrator

## Description

Responsible for maintaining the technical operation of the SmartField platform.

## Responsibilities

- Maintain platform availability.
- Support operational continuity.
- Monitor system health.
- Manage platform configuration.

## Primary Goals

- Ensure system stability.
- Maintain secure operation.
- Support reliable platform performance.

---

# Actor Relationships

```
                    SmartField

        +-------------------------------+
        |                               |
        |  Company Administrator        |
        |                               |
        +---------------+---------------+
                        |
                        |
                        v
                 Company Management
                        |
        +---------------+---------------+
        |                               |
        v                               v
 Supervisor                  Field Worker
        |
        v
 Project Coordination

        System Administrator
                |
                v
        Platform Operation
```

---

# Future Actors

As SmartField evolves, additional actors may be introduced, including:

- Client Representative
- External Auditor
- Third-Party Integration
- Automated Services
- Artificial Intelligence Assistant

These actors are outside the scope of the MVP.

---

# Related Documentation

- 01-System-Overview.md
- 03-Core-Capabilities.md
- 05-Business-Rules.md
- ../business/02-Business-Processes.md
- ../application/01-Application-Overview.md

---

# Revision History

| Version | Date | Description |
|----------|------|-------------|
| 1.0 | 2026-07-29 | Initial version. |