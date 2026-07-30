\---

title: Dependency Rules

version: 1.0

status: Approved

owner: Software Architecture

category: Architecture

last\_updated: 2026-07-29

\---



\# Dependency Rules



\## Purpose



This document defines the dependency rules that govern interactions between architectural layers and application modules in SmartField.



These rules preserve architectural integrity, prevent unintended coupling, and ensure that dependencies always flow toward the business core.



\---



\# Scope



This document defines:



\- Layer dependency rules

\- Module dependency rules

\- Allowed dependencies

\- Forbidden dependencies

\- Dependency governance



It does not define:



\- Package organization

\- Business rules

\- Application workflows

\- Infrastructure configuration



\---



\# Dependency Principles



All dependencies must follow these principles:



\- Dependencies point toward the business core.

\- Business modules remain independent whenever possible.

\- Communication occurs through explicit contracts.

\- Internal implementations remain private.

\- Circular dependencies are prohibited.



\---



\# Layer Dependency Rules



The following dependency flow is mandatory.



```

Presentation

&#x20;     │

&#x20;     ▼

Application

&#x20;     │

&#x20;     ▼

Domain

&#x20;     ▲

&#x20;     │

Infrastructure

```



No layer may violate this dependency direction.



\---



\# Allowed Layer Dependencies



| From | To | Allowed |

|------|----|----------|

| Presentation | Application | ✅ |

| Application | Domain | ✅ |

| Infrastructure | Domain | ✅ |

| Infrastructure | External Systems | ✅ |



\---



\# Forbidden Layer Dependencies



| From | To | Reason |

|------|----|--------|

| Domain | Infrastructure | Domain must remain technology independent. |

| Domain | Presentation | Domain cannot know how it is exposed. |

| Domain | Application | Business rules must not depend on orchestration. |

| Application | Presentation | Prevents inverted dependencies. |

| Presentation | Infrastructure | Controllers must not bypass use cases. |



\---



\# Module Dependency Rules



Modules collaborate only through their public interfaces.



A module may expose:



\- Application services

\- Commands

\- Queries

\- Events

\- Public contracts



A module must never expose:



\- Internal entities

\- Repository implementations

\- Internal services

\- Database models

\- Internal package structure



\---



\# Allowed Module Dependencies



```

Authentication

&#x20;       │

&#x20;       ▼

Company

&#x20;  ┌────┴────┐

&#x20;  ▼         ▼

Employee   Project

&#x20;     └─────┬─────┘

&#x20;           ▼

&#x20;     Assignment



Audit

&#x20; │

&#x20; └────────► Observes all modules

```



Dependencies should always reflect business relationships.



\---



\# Forbidden Module Dependencies



The following practices are prohibited:



\- Circular module dependencies

\- Direct database access across modules

\- Access to another module's internal classes

\- Shared mutable business state

\- Business logic duplicated across modules



\---



\# Shared Module Rules



The Shared module contains only reusable technical components.



Examples include:



\- Common exceptions

\- Utility classes

\- Shared value objects

\- Constants

\- Validation helpers



The Shared module must never contain:



\- Business rules

\- Business services

\- Domain entities

\- Business workflows



\---



\# Dependency Validation



Architectural compliance should be verified during development.



Recommended validation includes:



\- Code reviews

\- Static analysis

\- Architectural tests

\- Continuous Integration checks



Any dependency violation should be corrected before merging changes.



\---



\# Dependency Evolution



When introducing new modules or dependencies:



1\. Verify that a business relationship exists.

2\. Prefer collaboration through interfaces.

3\. Minimize coupling.

4\. Avoid introducing cyclic dependencies.

5\. Update this document if architectural rules change.



\---



\# Related Documentation



\- 02-Architectural-Principles.md

\- 04-Module-Architecture.md

\- 05-Layered-Architecture.md

\- 07-Architecture-Views.md

\- ../application/



\---



\# Revision History



| Version | Date | Description |

|----------|------|-------------|

| 1.0 | 2026-07-29 | Initial version. |

