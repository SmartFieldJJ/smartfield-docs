---
title: Ubiquitous Language
version: 1.0
status: Approved
owner: Software Architecture
category: Domain
last_updated: 2026-07-29
---

# Ubiquitous Language

## Purpose

This document defines the Ubiquitous Language used throughout the SmartField domain.

The Ubiquitous Language establishes a shared vocabulary between business stakeholders, domain experts, architects, developers, testers, and technical documentation.

Its purpose is to ensure that every business concept is expressed consistently across discussions, documentation, APIs, and source code.

---

# Scope

This document defines:

- Official domain terminology
- Naming conventions
- Domain vocabulary
- Language consistency guidelines

It does not define:

- Business definitions
- Technical implementation
- Database naming
- API specifications

Business terminology is documented in the Business Glossary.

---

# Principles

The SmartField Ubiquitous Language follows these principles:

- Every business concept has a single official name.
- The same concept must never have multiple names.
- Technical names must reflect business terminology.
- Documentation, APIs, and source code use the same vocabulary.
- Business language has priority over technical jargon.

---

# Naming Rules

The following rules apply throughout the project:

- Use business terminology instead of technical abbreviations.
- Prefer complete words over acronyms.
- Avoid synonyms for the same concept.
- Names should be descriptive and unambiguous.
- Use English consistently throughout the codebase and documentation.

---

# Core Domain Vocabulary

| Term | Meaning |
|------|---------|
| Company | Organization that owns employees, projects, and business operations. |
| User | Authenticated identity that accesses SmartField. |
| Employee | Worker employed by a company. |
| Project | Business initiative managed by a company. |
| Assignment | Allocation of an employee to a project. |
| Role | Collection of permissions assigned to a user. |
| Permission | Authorization to perform a specific action. |
| Audit Record | Historical record of a business action. |
| Authentication | Process of verifying a user's identity. |
| Authorization | Process of determining what a user is allowed to do. |

---

# Preferred Terminology

The following terms should always be used:

| Preferred | Avoid |
|-----------|-------|
| Company | Organization |
| Employee | Worker, Staff |
| Assignment | Allocation, Link |
| Project | Job, Work |
| User | Account |
| Role | Profile |
| Permission | Privilege |
| Audit Record | Log |

---

# Naming Consistency

The same terminology should be used consistently across all project artifacts.

| Artifact | Example |
|----------|---------|
| Documentation | Employee |
| Source Code | Employee |
| REST API | Employee |
| Database | Employee |
| Tests | Employee |

The terminology should not change depending on the context.

---

# Language Evolution

The Ubiquitous Language evolves together with the business.

When introducing a new business concept:

1. Define its meaning.
2. Select a single official term.
3. Update this document.
4. Use the new term consistently across the project.

Existing terms should not be renamed without evaluating the impact on the documentation, APIs, and source code.

---

# Related Documentation

- 01-Domain-Overview.md
- 03-Bounded-Contexts.md
- 12-Domain-Glossary.md
- ../overview/00-Business-Glossary.md

---

# Revision History

| Version | Date | Description |
|----------|------|-------------|
| 1.0 | 2026-07-29 | Initial version. |