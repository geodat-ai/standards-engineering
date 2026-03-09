# Geodat AI Infrastructure Architecture

Infrastructure is defined using Infrastructure-as-Code.

Typical tools:

Terraform  
Bicep

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

Tools typically used:

Terraform  
Bicep

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

# Terraform State

Terraform state should:

use remote storage  
never be committed to Git  
be securely protected

---

# Guiding Principle

Infrastructure should be reproducible and controlled through versioned code.
