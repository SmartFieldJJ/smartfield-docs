---
title: Business Rules
version: 1.0
status: Approved
owner: Product Management
category: Business
last_updated: 2026-07-29
---

# Business Rules

## Purpose

This document defines the business rules governing each business capability within SmartField.

Unlike the global business rules documented in the Overview section, these rules describe the operational constraints and policies specific to each business domain.

These rules ensure consistent business behavior regardless of the application's technical implementation.

---

# Scope

This document defines:

- Capability-specific business rules
- Operational constraints
- Ownership rules
- Assignment rules
- Access policies

It does not define:

- Input validation
- Database constraints
- Technical authorization
- API behavior
- User interface validation

---

# Identity & Access Management

## IAM-BR-001 — Unique User Identity

Each user account represents a unique digital identity.

Duplicate identities are not permitted.

---

## IAM-BR-002 — Authenticated Access

Business operations requiring system interaction must be performed by authenticated users.

---

## IAM-BR-003 — Role-Based Authorization

Users may only perform operations permitted by their assigned roles.

---

## IAM-BR-004 — Session Integrity

Only valid authenticated sessions may access protected resources.

---

# Company Management

## COM-BR-001 — Company Ownership

Every business resource belongs to one company.

Ownership cannot be shared between companies.

---

## COM-BR-002 — Organizational Isolation

Companies operate independently.

Business information from one company must not be visible to another.

---

## COM-BR-003 — Company Lifecycle

A company must exist before employees, projects, or assignments can be created.

---

# Workforce Management

## WFM-BR-001 — Employee Ownership

Every employee belongs to exactly one company.

---

## WFM-BR-002 — Employment Status

Only active employees may participate in operational activities.

---

## WFM-BR-003 — Supervisor Eligibility

Only employees designated as supervisors may coordinate projects.

---

## WFM-BR-004 — Workforce Consistency

Employee information must accurately reflect the organization's workforce.

---

# Project Management

## PRJ-BR-001 — Company Ownership

Every project belongs to one company.

---

## PRJ-BR-002 — Active Project

Only active projects may receive new employee assignments.

---

## PRJ-BR-003 — Supervisor Assignment

Every project should have one designated supervisor responsible for operational coordination.

---

# Assignment Management

## ASN-BR-001 — Company Consistency

Employees may only be assigned to projects belonging to their own company.

---

## ASN-BR-002 — Assignment Validity

Assignments require both an active employee and an active project.

---

## ASN-BR-003 — Assignment Uniqueness

An employee cannot have duplicate active assignments for the same project.

---

## ASN-BR-004 — Assignment History

Completed or removed assignments should remain historically traceable.

---

# Mobile Operations

## MOB-BR-001 — Authorized Access

Only authenticated employees may access the mobile application.

---

## MOB-BR-002 — Personal Information

Employees may access only information relevant to their own assignments.

---

## MOB-BR-003 — Operational Visibility

Field workers may only consult operational information they are authorized to view.

---

# Audit & Traceability

## AUD-BR-001 — Auditability

Critical business operations shall generate audit records.

---

## AUD-BR-002 — Historical Integrity

Audit information must accurately represent completed business operations.

---

## AUD-BR-003 — Immutability

Audit records shall not be modified once created.

---

# Rule Classification

| Category | Prefix |
|----------|--------|
| Identity & Access Management | IAM |
| Company Management | COM |
| Workforce Management | WFM |
| Project Management | PRJ |
| Assignment Management | ASN |
| Mobile Operations | MOB |
| Audit & Traceability | AUD |

---

# Rule Governance

Business rules are owned by the business capability they affect.

Any modification to an existing rule must be evaluated for its impact on:

- Business Processes
- Business Events
- Domain Model
- Application Use Cases
- Existing Integrations

---

# Related Documentation

- 01-Business-Architecture.md
- 02-Business-Processes.md
- 03-Business-Capabilities.md
- 04-Business-Events.md
- ../overview/05-Business-Rules.md
- ../domain/01-Domain-Overview.md

---

# Revision History

| Version | Date | Description |
|----------|------|-------------|
| 1.0 | 2026-07-29 | Initial version. |