# Geodat AI Platform Architecture

This document describes the high-level architecture used across GeoDat AI systems.

The platform combines modern cloud infrastructure, containerised services, geospatial databases, analytical tooling, and AI capabilities to support consultancy work, research projects, and production applications.

---

# Architecture Overview

Geodat AI systems follow a layered architecture.

Infrastructure Layer  
Cloud infrastructure and networking.

Runtime Layer  
Container execution environment.

Service Layer  
Containerised APIs and processing services.

Application Layer  
User-facing applications and dashboards.

Client Layer  
Client-specific integrations and delivery work.

---

# Infrastructure Layer

Infrastructure is hosted on Microsoft Azure.

Core components include:

- Azure Virtual Networks
- Azure Container Apps
- Azure Container Registry
- Azure Database for PostgreSQL
- Azure Blob Storage
- Azure Key Vault
- Azure Monitor

Infrastructure is defined using Infrastructure-as-Code tools such as:

- Terraform
- Bicep

Infrastructure repositories include:

- infra-core
- infra-runtime

---

# Runtime Layer

The runtime layer is responsible for running containerised applications.

Primary runtime platform:

- Azure Container Apps

Responsibilities include:

- container hosting
- service scaling
- environment configuration
- secret injection
- network routing
- service health monitoring

Container images are stored in:

- Azure Container Registry

---

# Service Layer

The service layer contains containerised APIs and backend services.

Services are typically implemented using:

- Go
- Python
- R

Examples of services:

- api-routing-go
- api-auth-go
- api-reporting-python
- service-data-ingestion
- service-otp-runner
- service-analysis-worker

Services provide functionality such as:

- geospatial APIs
- data processing pipelines
- analytics services
- AI integration services
- routing services

Services normally communicate using HTTP APIs.

---

# AI Services

GeoDat AI integrates artificial intelligence capabilities using Azure AI Services.

Examples include:

- Azure OpenAI
- AI agents
- chatbots
- document analysis
- language models

AI services are normally implemented as containerised APIs.

Examples:

- service-ai-agent
- api-ai-assistant-python

Applications interact with AI services through APIs.

Credentials and API keys are stored in Azure Key Vault.

---

# Spatial Services

Geodat AI platforms may include geospatial services such as:

- GeoServer for OGC-compliant map services
- PostGIS for spatial analysis
- OpenTripPlanner for routing and accessibility analysis

These services may run as containerised services.

---

# Data Layer

The data layer stores operational and analytical data.

Primary database:

- Azure Database for PostgreSQL

Spatial functionality is provided by:

- PostGIS

These systems support:

- spatial analysis
- routing models
- operational application data
- analytical datasets

Additional storage is provided by:

- Azure Blob Storage

Blob storage may store:

- uploaded images
- files
- exports
- analytical outputs
- large datasets

---

# Data Science and Analytics

Geodat AI supports advanced analytics using:

- R
- Python
- SQL

These tools support:

- spatial statistics
- modelling
- machine learning
- data pipelines
- geospatial analysis

Processing services may run as containerised workers.

Examples:

- service-analysis-worker
- service-ml-training

---

# Application Layer

The application layer contains user-facing systems.

Examples include:

- dashboards
- web applications
- data entry tools
- analytics portals

Frontend technologies may include:

- HTMX
- SvelteKit
- React
- Vue
- Shiny

Applications typically interact with backend APIs rather than accessing databases directly.

---

# Client Layer

Client repositories represent specific engagements.

Examples:

- client-council-transport-review
- client-nhs-accessibility-analysis

Client repositories may contain:

- documentation
- analysis scripts
- integration code
- frontend applications
- project deliverables

Reusable services should be moved into shared repositories.

---

# Container Architecture

Deployable services normally run as containers.

Containerisation provides:

- reproducible environments
- consistent deployments
- simplified scaling
- isolated services

Containers are deployed using Azure Container Apps.

Container images are stored in Azure Container Registry.

---

# Security Architecture

Security is implemented using several Azure components.

Azure Virtual Networks provide network isolation.

Azure Key Vault stores:

- database credentials
- API tokens
- service credentials
- application secrets

Applications retrieve secrets at runtime.

Secrets must never be stored in source code repositories.

---

# Observability and Monitoring

Monitoring and logging are provided by:

- Azure Monitor
- Application Insights

These systems capture:

- service logs
- performance metrics
- error reporting

Observability helps maintain system reliability.

---

# Development Workflow

Development occurs through GitHub repositories.

Typical workflow:

1. developer commits code
2. CI builds container image
3. image pushed to container registry
4. runtime platform deploys container

Infrastructure and application code are fully version controlled.

---

# Design Principles

GeoDat AI systems follow several principles:

- use containers for deployable services
- separate infrastructure from application code
- connect systems through APIs
- store secrets securely
- design services to be modular and reusable
- keep client work separate from platform services

---

Geodat AI systems may expose functionality through different interface types:

- APIs for machine-to-machine communication.
- Web applications and dashboards for end users.
- CLI tools for developer and operator workflows.
- Background workers for scheduled or event-driven processing.

These access patterns should be explicit in repository documentation and deployment design.


# Guiding Principle

The Geodat AI platform should remain modular, scalable, and flexible while remaining simple enough to support both small consultancy projects and larger analytical systems.
