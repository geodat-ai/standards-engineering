# Geodat AI Infrastructure Architecture

Infrastructure is defined using Infrastructure-as-Code.

The authoritative IaC language for GeoDat AI is **Bicep** (Azure-native).

Infrastructure should be reproducible, version controlled, and auditable.

---

# Infrastructure Repositories

Two main repositories manage infrastructure.

---

## infra-core

Defines cloud infrastructure resources.

Examples:

Azure Virtual Network  
Azure Container Apps environment  
Azure PostgreSQL servers  
Azure Blob Storage  
Azure Key Vault  
Azure Container Registry

Tools used:

Bicep (primary)  
Terraform (if multi-cloud portability becomes a requirement)

---

## infra-runtime

Defines how services run on the infrastructure.

Examples:

container deployment configuration  
container app definitions  
reverse proxy configuration  
service configuration  
monitoring setup

---

# Bicep Folder Structure

The canonical Bicep folder structure for Geodat AI infrastructure is:

```
infra/
  main.bicep
  main.parameters.dev.json
  modules/
    network.bicep
    storage.bicep
    keyvault.bicep
    postgres.bicep
    compute.bicep
```

---

## main.bicep

The root orchestrator template.

Responsibilities:

- calls all child modules
- wires outputs between modules (e.g. passing Key Vault reference to compute)
- sets top-level resource group scope

---

## main.parameters.dev.json

Environment-specific parameter file for the development environment.

Additional parameter files should be added as environments are introduced:

```
main.parameters.dev.json
main.parameters.test.json
main.parameters.prod.json
```

Parameter files control environment-specific values such as:

- SKU sizes
- replica counts
- environment names
- network address spaces

---

## modules/network.bicep

Defines Azure networking resources.

Includes:

- Virtual Network
- Subnets (app, data, management)
- Network Security Groups
- Route tables
- Private DNS zones
- Private endpoints for data services

This module should be deployed first as other modules depend on subnet references.

---

## modules/storage.bicep

Defines Azure storage resources.

Includes:

- Azure Blob Storage accounts
- PMTiles and static asset hosting
- GeoServer data directory storage (Azure Files if required)
- Lifecycle management policies

---

## modules/keyvault.bicep

Defines Azure Key Vault.

Includes:

- Key Vault resource
- Access policies or RBAC assignments
- Secret placeholders (values injected separately, never in templates)

Key Vault should be deployed before compute so that Container Apps can reference secrets at startup.

---

## modules/postgres.bicep

Defines Azure Database for PostgreSQL Flexible Server.

Includes:

- PostgreSQL Flexible Server
- Database configuration
- Private endpoint or VNet integration
- Firewall rules (private access only)
- Extensions note: PostGIS and pgRouting must be enabled post-provision

---

## modules/compute.bicep

Defines Azure Container Apps environment and individual container app definitions.

Includes:

- Container Apps environment
- Individual Container Apps (auth, API, Shiny, Python jobs)
- Azure Container Registry reference
- Managed identity assignments
- Ingress configuration

As the number of services grows, this module may be split into:

```
modules/
  container-env.bicep       ← ACA environment
  container-apps.bicep      ← individual app definitions
  registry.bicep            ← Azure Container Registry
```

---

# Deployment Order

Modules should be deployed in dependency order:

1. network.bicep
2. keyvault.bicep
3. storage.bicep
4. postgres.bicep
5. compute.bicep

---

# Runtime Layer

The runtime layer runs containerised services.

Responsibilities include:

container hosting  
environment configuration  
service scaling  
network routing  
secret injection

Primary runtime platform:

Azure Container Apps

---

# Container Architecture

Applications and services are deployed as containers.

Typical container workloads:

Go APIs  
Python APIs  
data processing services  
frontend applications  
analytics pipelines

Containers allow reproducible and portable deployments.

---

# Azure Services

Core Azure infrastructure typically includes:

Azure Container Apps  
Azure Container Registry  
Azure Database for PostgreSQL  
Azure Blob Storage  
Azure Virtual Networks  
Azure Key Vault  
Azure Monitor

---

# Bicep State

Bicep is declarative and does not maintain state files.

Deployments are idempotent by design.

Deployment history is tracked in Azure Resource Manager and should be treated as the audit trail.

---

# Guiding Principle

Infrastructure should be reproducible and controlled through versioned Bicep code.

All infrastructure changes must flow through version-controlled templates.

Manual changes to production infrastructure are not permitted.

