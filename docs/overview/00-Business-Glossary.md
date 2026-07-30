---
title: Business Glossary
version: 1.0
status: Draft
owner: Software Architecture
category: Overview
---

# Business Glossary

## Purpose

The Business Glossary establishes the official business vocabulary used throughout the SmartField project.

Its purpose is to ensure that all stakeholders—including business users, developers, architects, QA engineers, DevOps engineers, and AI assistants—share the same understanding of business concepts.

Every document in this repository must use the terminology defined here.

---

# Scope

This glossary defines business terminology only.

It does not describe:

- Technical implementation
- Database tables
- Java classes
- API resources
- Software architecture

Technical terminology is documented in the Domain and Architecture sections.

---

# Naming Principles

The glossary follows these principles:

- One business concept = One official term.
- Avoid synonyms whenever possible.
- Business terminology has priority over technical terminology.
- Terms must remain stable over time.
- Every definition should be understandable without technical knowledge.

---

# Business Terms

| Term | Definition | Notes |
|------|------------|-------|
| Company | A customer organization that uses SmartField to manage its field operations. | Primary business entity. |
| Employee | A person employed by a company who performs operational or administrative activities within SmartField. | Includes supervisors and field workers. |
| Field Worker | An employee assigned to perform activities outside the office. | Specialized employee role. |
| Supervisor | Employee responsible for coordinating projects and field workers. | May supervise multiple projects. |
| Project | A work initiative executed by a company for a client or internal purpose. | Groups assignments and field activities. |
| Assignment | The allocation of one employee to a project. | Represents participation, not employment. |
| User | A digital identity used to authenticate into SmartField. | Different from Employee. |
| Role | A collection of permissions assigned to a user. | Used for authorization. |
| Permission | A specific action that a user is allowed to perform. | Business authorization concept. |
| Authentication | Process used to verify a user's identity. | Business concept, not implementation. |
| Session | Authenticated interaction between a user and the platform. | Ends after logout or expiration. |
| Business Capability | A high-level business function provided by SmartField. | Used in capability mapping. |
| Field Operation | Any activity executed outside the office by field personnel. | Core business concept. |

---

# Abbreviations

| Abbreviation | Meaning |
|-------------|---------|
| MVP | Minimum Viable Product |
| SaaS | Software as a Service |
| RBAC | Role-Based Access Control |
| API | Application Programming Interface |

---

# Forbidden Terms

The following expressions should be avoided in business documentation:

| Avoid | Use Instead |
|--------|-------------|
| Client User | Employee |
| Worker Account | User |
| Job | Project |
| Task Owner | Supervisor |

---

# Related Documentation

- 01-System-Overview.md
- 03-Core-Capabilities.md
- ../business/01-Business-Architecture.md
- ../domain/03-Domain-Glossary.md

---

# Maintenance

The Business Glossary should only be updated when:

- A new business concept is introduced.
- A business definition changes.
- New terminology becomes part of the official language.

Terminology must remain stable to preserve consistency across the project.