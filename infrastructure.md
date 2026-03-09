# GeoDat AI Infrastructure Architecture

This document defines how infrastructure is managed within the GeoDat AI GitHub organisation.

Infrastructure is managed using **Infrastructure as Code (IaC)** to ensure systems are reproducible, version controlled, and auditable.

---

# Infrastructure Repositories

Infrastructure is separated into two main repository types.

## infra-core

This repository defines the **cloud infrastructure itself**.

Examples:

- Azure resource groups
- virtual machines
- networking
- PostgreSQL databases
- storage accounts
- identity and access configuration

Typical tools used:

- Terraform
- Bicep
- infrastructure documentation

This repository answers the question:

> What infrastructure exists?

---

## infra-runtime

This repository defines **how applications and services run on that infrastructure**.

Examples:

- Docker Compose
- service deployment scripts
- reverse proxy configuration
- SSL configuration
- runtime environment setup
- monitoring configuration

This repository answers the question:

> How do services run on the infrastructure?

---

# Infrastructure Principles

Infrastructure should be:

- reproducible
- version controlled
- documented
- separated from application code

Infrastructure definitions should **not be embedded inside application repositories** unless they are extremely small project-specific deployments.

---

# Terraform / Bicep Usage

Infrastructure should be defined using Infrastructure-as-Code tools such as:

- Terraform
- Bicep

Typical components managed via IaC include:

- networks
- virtual machines
- container hosts
- PostgreSQL servers
- storage
- security policies

IaC ensures that environments can be rebuilt consistently.

---

# State Management

When using Terraform:

- remote state storage should be used
- state files must not be committed to Git
- sensitive information must not be stored in repositories

---

# Secrets Management

Secrets must **never be committed to Git repositories**.

Examples of secrets:

- database passwords
- API keys
- private certificates
- access tokens

Instead use:

- environment variables
- secure secret storage
- platform secret managers

---

# Infrastructure Lifecycle

Typical workflow:

1. Define infrastructure changes in `infra-core`
2. Review and commit changes
3. Apply changes via Terraform or Bicep
4. Deploy services using `infra-runtime`

---

# Guiding Principle

Infrastructure should be predictable, secure, and fully reproducible from version-controlled code.
