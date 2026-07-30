\---

title: Value Objects

version: 1.0

status: Approved

owner: Software Architecture

category: Domain

last\_updated: 2026-07-29

\---



\# Value Objects



\## Purpose



This document defines the Value Objects used throughout the SmartField domain.



Value Objects represent immutable business concepts that are identified by their attributes rather than by a unique identity.



They improve the expressiveness of the domain model by encapsulating validation rules, business meaning, and domain behavior.



\---



\# Scope



This document defines:



\- Domain Value Objects

\- Business meaning

\- Validation rules

\- Equality semantics

\- Usage guidelines



It does not define:



\- Entities

\- Database mappings

\- DTOs

\- Framework-specific classes



These topics are documented elsewhere.



\---



\# What is a Value Object?



A Value Object is a domain concept that is defined entirely by its values.



Unlike an Entity, a Value Object:



\- Has no identity.

\- Is immutable.

\- Is compared by value.

\- Represents a business concept.

\- Encapsulates validation and business rules.



If two Value Objects contain the same values, they are considered equal.



\---



\# Value Object Catalog



| Value Object | Description |

|--------------|-------------|

| Company Name | Legal or business name of a company. |

| Employee Name | Full name of an employee. |

| Project Name | Business name of a project. |

| Email Address | Email used for authentication and communication. |

| Phone Number | Business contact number. |

| Address | Physical location information. |

| Assignment Period | Time interval during which an assignment is active. |

| Password | Encapsulates password validation requirements. |



\---



\# Value Object Definitions



\## Company Name



\### Purpose



Represents the official name of a company.



\### Characteristics



\- Immutable

\- Cannot be empty

\- Compared by value



\---



\## Employee Name



\### Purpose



Represents the full name of an employee.



\### Characteristics



\- Immutable

\- Human-readable

\- Compared by value



\---



\## Project Name



\### Purpose



Represents the official business name of a project.



\### Characteristics



\- Immutable

\- Unique within the company's business context

\- Compared by value



\---



\## Email Address



\### Purpose



Represents a valid business email address.



\### Responsibilities



\- Validate email format

\- Normalize value when appropriate

\- Ensure consistent comparisons



\### Characteristics



\- Immutable

\- Compared by value



\---



\## Phone Number



\### Purpose



Represents a business contact number.



\### Characteristics



\- Immutable

\- Valid format

\- Compared by value



\---



\## Address



\### Purpose



Represents a physical business location.



\### Characteristics



\- Immutable

\- Composed of multiple attributes

\- Compared by value



\---



\## Assignment Period



\### Purpose



Represents the period during which an employee participates in a project.



\### Characteristics



\- Immutable

\- Defines a valid time range

\- Compared by value



\---



\## Password



\### Purpose



Represents a validated password value within the domain.



The Value Object encapsulates password validation rules.



It does not define how passwords are stored or encrypted.



\### Characteristics



\- Immutable

\- Validated

\- Compared by value



\---



\# Equality



Value Objects are equal when all of their attributes are equal.



```

Email("john@company.com")

==

Email("john@company.com")

```



```

ProjectName("Warehouse Upgrade")

==

ProjectName("Warehouse Upgrade")

```



Identity is never considered.



\---



\# Immutability



All Value Objects must be immutable.



Once created:



\- Their state cannot change.

\- Updates require creating a new instance.

\- Internal consistency is preserved.



Immutability simplifies reasoning about the domain and reduces unintended side effects.



\---



\# Validation



Validation belongs inside the Value Object.



Examples include:



\- Email format

\- Required fields

\- Maximum length

\- Allowed character sets

\- Date range consistency



Creating an invalid Value Object should not be possible.



\---



\# Design Principles



Value Objects should:



\- Represent meaningful business concepts.

\- Encapsulate validation logic.

\- Be immutable.

\- Avoid primitive obsession.

\- Improve readability of the domain model.



They should not expose setters or mutable state.



\---



\# Relationship with Entities



Entities own Value Objects.



Examples:



```

Company

&#x20;├── Company Name

&#x20;└── Address



Employee

&#x20;├── Employee Name

&#x20;├── Email Address

&#x20;└── Phone Number



Project

&#x20;├── Project Name

&#x20;└── Assignment Period

```



Value Objects never own Entities.



\---



\# Related Documentation



\- 04-Domain-Model.md

\- 05-Entities.md

\- 07-Aggregates.md

\- 11-Domain-Rules.md



\---



\# Revision History



| Version | Date | Description |

|----------|------|-------------|

| 1.0 | 2026-07-29 | Initial version. |

