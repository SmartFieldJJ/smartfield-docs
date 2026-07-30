\---

title: Aggregates

version: 1.0

status: Approved

owner: Software Architecture

category: Domain

last\_updated: 2026-07-29

\---



\# Aggregates



\## Purpose



This document defines the Aggregates that compose the SmartField domain model.



Aggregates establish consistency boundaries by grouping related domain objects under a single Aggregate Root.



Every modification to business data must occur through an Aggregate Root to ensure that domain invariants are preserved.



\---



\# Scope



This document defines:



\- Aggregate Roots

\- Aggregate boundaries

\- Business consistency rules

\- Ownership of entities and value objects



It does not define:



\- Database transactions

\- Persistence implementation

\- Repository implementation

\- Object mapping



These topics are documented elsewhere.



\---



\# What is an Aggregate?



An Aggregate is a cluster of related domain objects treated as a single unit for consistency.



Every Aggregate:



\- Has exactly one Aggregate Root.

\- Defines a transactional consistency boundary.

\- Protects business invariants.

\- Controls access to internal objects.



External objects interact only with the Aggregate Root.



\---



\# Aggregate Catalog



| Aggregate | Aggregate Root | Purpose |

|-----------|----------------|---------|

| Company | Company | Manages organizational information. |

| User Management | User | Manages authentication identity and access. |

| Employee | Employee | Manages employee information. |

| Project | Project | Manages project lifecycle. |

| Assignment | Assignment | Manages employee participation in projects. |



\---



\# Aggregate Definitions



\## Company Aggregate



\### Aggregate Root



Company



\### Responsibilities



\- Manage company information.

\- Protect organizational boundaries.

\- Ensure company consistency.



\### Contains



\- Company

\- Company Name

\- Address



\### Business Invariants



\- A Company always has a valid name.

\- Company information remains internally consistent.



\---



\## User Management Aggregate



\### Aggregate Root



User



\### Responsibilities



\- Manage authentication identity.

\- Maintain authorization assignments.

\- Protect access rules.



\### Contains



\- User

\- Role References

\- Permission References



\### Business Invariants



\- Every User belongs to exactly one Company.

\- Every User has a valid authentication status.



\---



\## Employee Aggregate



\### Aggregate Root



Employee



\### Responsibilities



\- Manage employee lifecycle.

\- Protect employee information.

\- Maintain employment consistency.



\### Contains



\- Employee

\- Employee Name

\- Email Address

\- Phone Number



\### Business Invariants



\- Every Employee belongs to exactly one Company.

\- Employee information must remain valid.



\---



\## Project Aggregate



\### Aggregate Root



Project



\### Responsibilities



\- Manage project lifecycle.

\- Protect project consistency.



\### Contains



\- Project

\- Project Name



\### Business Invariants



\- Every Project belongs to exactly one Company.

\- Project status follows the defined lifecycle.



\---



\## Assignment Aggregate



\### Aggregate Root



Assignment



\### Responsibilities



\- Manage employee participation.

\- Preserve assignment history.



\### Contains



\- Assignment

\- Assignment Period



\### Business Invariants



\- Every Assignment references one Employee.

\- Every Assignment references one Project.

\- Assignment dates must define a valid period.



\---



\# Aggregate Relationships



Aggregates reference each other through identifiers rather than direct object references.



```

CompanyId

&#x20;    │

&#x20;    ▼

Employee



CompanyId

&#x20;    │

&#x20;    ▼

Project



EmployeeId

&#x20;     │

&#x20;     ▼

&#x20;Assignment

&#x20;     ▲

&#x20;     │

ProjectId

```



Each Aggregate owns its own consistency boundary.



\---



\# Consistency Boundaries



Business rules inside an Aggregate must always remain consistent after every operation.



Changes involving multiple Aggregates should be coordinated by the Application Layer.



Aggregates should never directly modify another Aggregate.



\---



\# Aggregate Design Principles



Aggregates should:



\- Represent a single business consistency boundary.

\- Have one Aggregate Root.

\- Be as small as possible.

\- Protect business invariants.

\- Avoid unnecessary dependencies.

\- Expose meaningful business operations.



\---



\# Aggregate Collaboration



Aggregates collaborate through:



\- Aggregate identifiers

\- Domain Services

\- Domain Events

\- Application orchestration



Direct manipulation of another Aggregate's internal state is prohibited.



\---



\# Transactional Consistency



Operations affecting a single Aggregate should complete within a single business transaction.



Operations involving multiple Aggregates should preserve business consistency through coordinated application workflows rather than by expanding Aggregate boundaries.



\---



\# Related Documentation



\- 05-Entities.md

\- 06-Value-Objects.md

\- 08-Domain-Services.md

\- 09-Domain-Events.md

\- 10-Repositories.md



\---



\# Revision History



| Version | Date | Description |

|----------|------|-------------|

| 1.0 | 2026-07-29 | Initial version. |

