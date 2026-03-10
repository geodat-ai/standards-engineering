# Geodat AI Engineering Standards and Architecture

This repository defines the engineering standards, architecture principles, and development practices used across Geodat AI systems.

The documents in this repository act as the **engineering handbook** for the Geodat AI platform.

They describe how infrastructure, services, applications, analytical workflows, and client projects should be organised and deployed.

The goal is to ensure Geodat AI systems remain:

- consistent  
- maintainable  
- secure  
- scalable  

---

# Contents

- [Engineering principles](engineering-principles.md)
- [Development workflow](development-workflow.md)
- [Container standards](container-standards.md)
- [Platform architecture](platform-architecture.md)
- [Infrastructure](infrastructure.md)
- [Repository structure](repo-structure.md)
- [AI services](ai-services.md)
- [Security and secrets management](security-and-secrets.md)
- [Client project structure](client-project-structure.md)

---


## Documentation

| Document | Description |
|--------|--------|
| [Engineering principles](engineering-principles.md) | Core engineering principles |
| [Development workflow](development-workflow.md) | Branching, commits, pull requests |
| [Container standards](container-standards.md) | Docker and container practices |
| [Platform architecture](platform-architecture.md) | Overall system architecture |
| [Infrastructure](infrastructure.md) | Infrastructure-as-code and Azure setup |
| [Repository structure](repo-structure.md) | Organisation of repositories |
| [AI services](ai-services.md) | AI integration architecture |
| [Security and secrets management](security-and-secrets.md) | Key Vault and secret handling |
| [Client project structure](client-project-structure.md) | Structure of client repositories |





# Platform Architecture

Geodat AI follows a layered architecture designed for:

- containerised services
- geospatial analytics
- scalable cloud deployment

The architecture combines:

- Azure infrastructure
- containerised APIs and services
- spatial databases
- analytical pipelines
- AI capabilities
- web applications and dashboards

See:

`platform-architecture.md`

---

# Engineering Standards

The following documents define how the platform is built and maintained.

## Engineering principles

`engineering-principles.md`

Defines the core engineering principles guiding Geodat AI system design.

Includes:

- reproducible analytics
- cloud-native architecture
- open geospatial standards
- spatial data integrity
- scalable spatial processing
- secure infrastructure

---

## Development workflow

`development-workflow.md`

Defines the development workflow used across Geodat AI repositories.

Includes:

- branching strategy
- pull request workflow
- commit conventions
- container development practices

---

## Container standards

`container-standards.md`

Defines how containerised services should be built and deployed.

Includes:

- Dockerfile standards
- container repository structure
- container registry usage
- CI/CD container builds
- runtime configuration

---

## Infrastructure architecture

`infrastructure.md`

Defines how cloud infrastructure is managed using Infrastructure-as-Code.

Includes:

- Azure infrastructure resources
- Terraform and Bicep configuration
- runtime container environments
- infrastructure deployment practices

---

## Repository structure

`repo-structure.md`

Defines how repositories are organised across the Geodat AI GitHub organisation.

Includes:

- infrastructure repositories
- APIs and services
- applications
- shared libraries
- analytical projects
- client repositories

---

## AI services

`ai-services.md`

Defines how AI capabilities are integrated into the Geodat AI platform.

Includes:

- Azure AI Services
- Azure OpenAI
- AI agents
- document analysis
- AI service APIs

---

## Security and secrets

`security-and-secrets.md`

Defines security standards and credential management.

Includes:

- Azure Key Vault
- secret management
- runtime configuration
- incident response

---

## Client project structure

`client-project-structure.md`

Defines how repositories for client engagements should be organised.

Includes:

- repository layout
- frontend technologies
- API integration
- container usage
- client deliverables

---

# Platform Technologies

Typical technologies used across Geodat AI systems include:

### Backend services

- Go
- Python
- R

### Frontend applications

- HTMX
- SvelteKit
- React
- Vue
- Shiny

### Geospatial systems

- PostGIS
- GeoServer
- OpenTripPlanner

### Cloud infrastructure

- Microsoft Azure
- Azure Container Apps
- Azure Container Registry
- Azure Database for PostgreSQL
- Azure Blob Storage
- Azure Key Vault

### AI capabilities

- Azure AI Services
- Azure OpenAI

---

# Design Principles

Geodat AI systems follow several core principles:

- use containerised services
- separate infrastructure from application code
- design APIs as reusable services
- store secrets securely
- maintain clear boundaries between platform services and client work
- prioritise simplicity and maintainability

---

# Purpose

This repository exists to ensure Geodat AI systems remain:

- consistent
- maintainable
- secure
- scalable

It serves as the engineering handbook for the Geodat AI platform.
