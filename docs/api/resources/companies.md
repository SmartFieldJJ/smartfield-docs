---
title: Companies Resource
version: 1.0
status: Approved
owner: Software Architecture
category: API Resource
last_updated: 2026-07-29
---

# Companies Resource

## Purpose

This document defines the public contract for the Companies resource exposed by the SmartField API.

It describes the operations available to API consumers, the resource representations, and the rules governing interaction with companies.

---

# Resource Overview

The Companies resource represents organizations managed within SmartField.

A company is the top-level organizational unit that owns users, employees, projects, and other business resources.

---

# Supported Operations

| Operation | Description |
|----------|-------------|
| Create Company | Register a new company. |
| Get Company | Retrieve a specific company. |
| List Companies | Retrieve a collection of companies. |
| Update Company | Modify company information. |

---

# Resource Representations

The Companies resource may use the following representations:

| Representation | Purpose |
|---------------|---------|
| Company Summary | Compact representation used in collections. |
| Company Detail | Complete representation of a company. |
| Company Create Request | Data required to create a company. |
| Company Update Request | Data used to modify an existing company. |

---

# Resource Relationships

A Company may be associated with:

- Users
- Employees
- Projects
- Audit Records

These relationships represent business associations and do not imply nested API structures.

---

# Common Operations

## Create Company

Creates a new company.

---

## Get Company

Retrieves a company by its unique identifier.

---

## List Companies

Returns a paginated collection of companies.

Supports filtering and sorting when applicable.

---

## Update Company

Updates the information of an existing company.

---

# Security

Access to the Companies resource requires authentication.

Authorization requirements depend on the operation being executed.

---

# Error Responses

Typical error responses include:

- Validation Error
- Authentication Error
- Authorization Error
- Resource Not Found
- Business Conflict
- Internal Server Error

---

# Related Documentation

- ../05-Resource-Operations.md
- ../04-Request-Response-Model.md
- ../06-Authentication-and-Authorization.md
- ../08-Error-Responses.md

---

# Revision History

| Version | Date | Description |
|----------|------|-------------|
| 1.0 | 2026-07-29 | Initial version. |