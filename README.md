# Geodat AI Engineering Standards and Architecture

This repository defines the engineering standards, architecture principles, and development practices used across Geodat AI systems.

The documents in this repository act as the **engineering handbook** for the platform.

They describe how infrastructure, services, applications, and client projects should be organised and deployed.


## Contents

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

# Platform Architecture

The GeoDat AI platform follows a layered architecture designed for containerised services, geospatial analytics, and cloud-native deployment.

See:

platform-architecture.md

This document describes the full system architecture including:

- Azure infrastructure
- container runtime
- APIs and services
- AI services
- geospatial systems
- frontend applications
- client delivery projects

---

# Engineering Standards

The following documents define how the platform is built and maintained.

## Repository Structure

repo-structure.md

Defines how repositories are organised across the GitHub organisation.

Covers:

- infrastructure repositories
- APIs and services
- applications
- shared libraries
- analysis projects
- client repositories

---

## Development Workflow

development-workflow.md

Defines the development workflow including:

- branching strategy
- pull request workflow
- commit conventions
- container development practices

---

## Infrastructure Architecture

infrastructure.md

Defines how infrastructure is managed using Infrastructure-as-Code.

Covers:

- Azure infrastructure
- container runtime
- Terraform and Bicep
- runtime configuration

---

## Container Standards

container-standards.md

Defines how containerised services should be built and deployed.

Includes:

- Dockerfile standards
- container repository structure
- container registry usage
- CI/CD container builds
- runtime configuration

---

## Security and Secrets

security-and-secrets.md

Defines security standards.

Covers:

- Azure Key Vault
- secret management
- environment configuration
- incident response

---

## AI Services

ai-services.md

Defines how AI capabilities are integrated into the platform.

Covers:

- Azure AI Services
- AI agents
- AI service APIs
- integration patterns

---

## Client Project Structure

client-project-structure.md

Defines how client repositories should be organised.

Includes:

- repository layout
- frontend technologies
- API integration
- container usage
- client deliverables

---

# Platform Technologies

Typical technologies used across GeoDat AI systems include:

Backend services:
- Go
- Python
- R

Frontend applications:
- HTMX
- SvelteKit
- React
- Vue
- Shiny

Geospatial systems:
- PostGIS
- GeoServer
- OpenTripPlanner

Cloud infrastructure:
- Microsoft Azure
- Azure Container Apps
- Azure Container Registry
- Azure Database for PostgreSQL
- Azure Blob Storage
- Azure Key Vault

AI capabilities:
- Azure AI Services
- Azure OpenAI

---

# Guiding Principles

GeoDat AI systems follow several core principles:

- use containerised services
- separate infrastructure from application code
- design APIs as reusable services
- store secrets securely
- maintain clear boundaries between platform services and client work
- prioritise simplicity and maintainability

---

# Purpose

This repository exists to ensure that Geodat AI systems remain:

- consistent
- maintainable
- secure
- scalable

## Additional documentation

- [Engineering principles](engineering-principles.md)
