# Geodat AI Repository Structure

This document defines how repositories are organised within the GeoDat AI GitHub organisation.

Repositories represent deployable services, reusable platform components, analytical projects, or client engagements.

The goal is to maintain a clear separation between infrastructure, services, applications, data systems, and client delivery work.

---

# Platform Architecture

Geodat AI follows a layered platform architecture.

Infrastructure Layer  
Azure cloud resources defined using Infrastructure-as-Code.

Runtime Layer  
Managed container runtime responsible for executing containerised services.

Service Layer  
Containerised APIs and processing services.

Application Layer  
User-facing applications and dashboards.

Client Layer  
Client-specific integrations and delivery work.

---

# Repository Categories

Repositories are organised by **function**, not programming language.

---

## Infrastructure

Repositories that define and manage cloud infrastructure.

Examples:

infra-core  
infra-runtime

Typical contents:

Terraform  
Bicep  
network definitions  
database infrastructure  
container environment configuration  
deployment pipelines

These repositories define what infrastructure exists and how it is deployed.

---

## APIs

Reusable backend APIs shared across applications or client projects.

Examples:

api-routing-go  
api-auth-go  
api-reporting-python  
api-geospatial-go

Typical contents:

service source code  
Dockerfile  
API documentation  
container configuration  
deployment instructions

These services normally run as **containerised APIs**.

---

## Services

Background services and processing systems.

Examples:

service-otp-runner  
service-data-ingestion  
service-analysis-worker

Typical responsibilities:

data ingestion  
batch processing  
scheduled jobs  
analytics pipelines

Services are usually deployed as containers.

---

## Interface and access patterns

Repositories should also be clear about how a system is accessed.

Common patterns include:

- API services: accessed over HTTP by applications or other services.
- UI applications: accessed by end users through a browser-based interface.
- CLI tools: accessed through command-line commands by developers or operators.
- Worker services: run in the background and are not directly accessed by end users.
- Shared libraries: imported by other repositories and not deployed directly.

A repository should have one primary access pattern. Mixed-purpose repositories should be avoided unless there is a strong reason for combining them.


---


## Databases

Repositories containing database schema and SQL assets.

Examples:

db-postgres-core  
db-postgis-tools

Contents may include:

schema definitions  
migration scripts  
views  
functions  
index configuration  
database documentation

---

## Shared Libraries

Reusable internal packages.

Examples:

pkg-geodatutils  
pkg-go-spatial  
pkg-python-geo

These contain:

utility functions  
internal SDKs  
shared modules

These libraries are imported by other repositories.

---

## Applications

User-facing systems.

Examples:

app-accessibility-portal  
app-admin-dashboard  
app-journey-planner

Applications may include frontend frameworks such as:

HTMX  
SvelteKit  
React  
Vue  
Shiny

Applications normally interact with APIs and services rather than accessing databases directly.

---

## Analysis Projects

Research or analytical work.

Examples:

analysis-powys-bus-access  
analysis-topic-modelling-gis

These repositories may include:

R scripts  
Python notebooks  
SQL analysis  
data processing pipelines  
reproducible research projects

---

## Client Projects

Repositories dedicated to individual engagements.

Examples:

client-council-transport-review  
client-nhs-accessibility-analysis

These repositories contain:

documentation  
integration code  
client-specific configuration  
deliverables

Client repositories should not contain reusable platform services.

---

# Naming Conventions

| Prefix | Purpose |
|------|------|
| infra- | Infrastructure |
| api- | APIs |
| service- | Background services |
| db- | Database schema |
| analysis- | Analytical projects |
| client- | Client work |
| pkg- | Shared libraries |
| app- | Applications |

---

# Guiding Principle

Repositories should represent deployable systems, reusable platform components, or clearly scoped projects.

