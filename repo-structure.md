# GeoDat AI Repository Structure

This document defines how repositories are organised within the GeoDat AI GitHub organisation.

The aim is to maintain a clear separation between infrastructure, services, databases, analysis projects, and client work.

---

## Repository Categories

Repositories are organised by **function**, not by programming language.

### Infrastructure

Repositories that define and manage cloud resources.

Examples:

- infra-core
- infra-runtime

Contents may include:

- Terraform
- Bicep
- deployment scripts
- Docker configuration
- infrastructure documentation

---

### APIs and Services

Repositories that contain deployable services.

Examples:

- api-routing-go
- service-data-ingestion
- service-otp-runner

These repos normally include:

- service source code
- configuration templates
- deployment instructions

---

### Databases

Repositories containing database schema and SQL assets.

Examples:

- db-postgres-core
- db-postgis-tools

Contents may include:

- migrations
- functions
- views
- indexes
- database documentation

---

### Analysis Projects

Repositories containing analytical or modelling work.

Examples:

- analysis-powys-bus-access
- analysis-topic-modelling-gis

These may include:

- R projects
- Python notebooks
- SQL queries
- data processing scripts

---

### Client Projects

Repositories dedicated to specific client engagements.

Examples:

- client-council-transport-review
- client-nhs-accessibility-analysis

Access to these repositories should be restricted where required.

---

### Shared Libraries

Reusable internal packages or libraries.

Examples:

- pkg-geodatutils
- pkg-spatial-tools

These should contain reusable code used across multiple projects.

---

## Naming Conventions

Repositories should follow predictable prefixes:

| Prefix | Purpose |
|------|------|
| infra- | Infrastructure configuration |
| api- | Backend APIs |
| service- | Background services |
| db- | Database schema and SQL |
| analysis- | Research or analytical projects |
| client- | Client-specific work |
| pkg- | Shared libraries |

---

## Guiding Principle

Repositories should represent **deployable systems, reusable components, or clearly scoped projects**, rather than arbitrary collections of code.
