# GeoDat AI Container Standards

This document defines the containerisation standards used across GeoDat AI services and applications.

All deployable services should normally run as containers to ensure consistent environments across development, testing, and production.

---

# Objectives

Containerisation provides:

- reproducible environments
- consistent deployments
- portable services
- simplified scaling
- easier automation

All services deployed to the GeoDat AI platform should follow these standards.

---

# Runtime Platform

The primary runtime platform is:

Azure Container Apps

Supporting components include:

Azure Container Registry  
Azure Key Vault  
Azure Monitor  

Containers are built from repository source code and deployed automatically through CI/CD pipelines.

---

# Container Registry

All container images should be stored in:

Azure Container Registry

Typical workflow:

GitHub repository  
↓  
CI/CD builds container image  
↓  
Image pushed to Azure Container Registry  
↓  
Azure Container Apps pulls container image

Images should never be deployed directly from local developer machines.

---

# Container Image Naming

Images should follow a predictable naming convention.

Example format:

geodatai/<service-name>

Examples:

geodatai/api-routing  
geodatai/api-auth  
geodatai/service-data-ingestion  
geodatai/service-ai-agent

Version tags should normally follow semantic versioning.

Examples:

v1.0.0  
v1.1.0  
v2.0.0

Development environments may use tags such as:

dev  
latest

---

# Container Repository Structure

Containerised service repositories should normally follow this structure:

cmd/  
internal/  
config/  
Dockerfile  
README.md  
.env.example  

Example structure for a Go service:

cmd/api/main.go  
internal/service/  
internal/database/  
Dockerfile  

Example structure for a Python service:

app/  
services/  
Dockerfile  
requirements.txt  

---

# Dockerfile Standards

Each deployable service must include a Dockerfile.

Dockerfiles should:

- use minimal base images
- install only required dependencies
- avoid unnecessary packages
- minimise final image size

Example base images:

golang:alpine  
python:slim  

Multi-stage builds should be used where possible.

Example pattern:

builder stage  
runtime stage

This reduces container size and attack surface.

---

# Environment Configuration

Containers must use environment variables for configuration.

Typical environment variables:

DATABASE_URL  
API_PORT  
LOG_LEVEL  
SERVICE_NAME

Environment variables should be injected by the runtime platform.

Configuration should not be hard-coded.

---

# Secrets Management

Secrets must never be stored in container images or repositories.

Secrets should be retrieved from:

Azure Key Vault

Applications should access secrets using:

environment variables  
managed identities  

Examples of secrets:

database credentials  
API tokens  
AI service keys  
storage account keys  

---

# Local Development

Containers should support local development.

Developers may use:

Docker  
Docker Compose  

Example development workflow:

1. run PostgreSQL locally
2. build container
3. run container locally
4. test API endpoints

Local `.env` files may be used but must not be committed.

---

# Container Logging

Containers should write logs to stdout/stderr.

The runtime platform captures logs and sends them to:

Azure Monitor  
Application Insights  

Logging should include:

service start events  
API requests  
errors  
important system events

---

# Health Checks

Containers should expose health endpoints.

Example:

/health  
/status  

These endpoints allow the runtime platform to detect unhealthy containers.

---

# Container Scaling

Scaling should be handled by the runtime platform.

Azure Container Apps supports:

HTTP request scaling  
event-driven scaling  
background job scaling  

Services should be designed to scale horizontally where possible.

---

# Service Isolation

Each service should run in its own container.

Examples:

api-routing-go  
api-auth-go  
service-data-ingestion  

Avoid combining unrelated services into a single container.

---

# AI Services Containers

AI services should run as containerised APIs.

Examples:

service-ai-agent  
api-ai-assistant-python  

These services may call:

Azure OpenAI  
Azure AI Services  

Secrets must be retrieved via Key Vault.

---

# Frontend Containers

Frontend applications may also run as containers.

Examples:

HTMX applications  
SvelteKit apps  
React applications  

For lightweight systems, frontend code may also run inside backend services.

---

# Data Processing Containers

Data processing services may use:

Python  
R  

Examples:

service-analysis-worker  
service-ml-training  

These services should run as batch or background containers.

---

# CI/CD Pipeline

Container builds should be automated.

Typical workflow:

Git push  
↓  
CI pipeline builds container  
↓  
image pushed to container registry  
↓  
deployment to runtime platform

Containers must not be manually built for production.

---

# Security Practices

Containers should follow basic security practices.

Examples:

use minimal base images  
remove unnecessary packages  
avoid running as root  
keep images updated  

---

# Observability

Containerised services should support observability.

This includes:

logging  
metrics  
health checks  

Azure Monitor and Application Insights should be used for runtime monitoring.

---

# Guiding Principle

Containers should be small, secure, reproducible, and easy to deploy.
