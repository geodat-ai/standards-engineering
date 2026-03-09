# GeoDat AI Security and Secrets Management

This document defines how sensitive information is handled within the GeoDat AI GitHub organisation.

The primary rule is:

> Secrets must never be committed to Git repositories.

---

# What Counts as a Secret

Secrets include any information that could allow access to infrastructure, data, or services.

Examples:

- database passwords
- API keys
- OAuth tokens
- private certificates
- SSH private keys
- service account credentials
- encryption keys

These must never appear in:

- Git commits
- configuration files
- documentation
- screenshots

---

# Secret Management Platform

GeoDat AI uses **Azure Key Vault** for secure storage of secrets.

Key Vault is used to store:

- database credentials
- API tokens
- TLS certificates
- application secrets
- service account credentials

Applications and services retrieve secrets securely at runtime.

---

# Infrastructure Integration

Secrets should be referenced by infrastructure tools rather than stored in code.

Examples:

- Terraform referencing Azure Key Vault secrets
- applications retrieving secrets via environment variables
- runtime services accessing secrets through managed identities

---

# Local Development

For local development:

- use `.env` files for environment variables
- `.env` files must be excluded using `.gitignore`
- example files such as `.env.example` may be committed

Example:

DB_HOST=localhost
DB_USER=dev_user
DB_PASSWORD=your_password_here


---

# GitHub Rules

Repositories must not contain:

- `.env` files with real credentials
- configuration files containing passwords
- exported secret files

Instead include:

- `.env.example`
- documentation explaining required variables

---

# Access Control

Access to secrets should follow the principle of:

**least privilege**

Only systems or users that require access should receive it.

Examples:

- services accessing only the secrets they need
- client environments separated from internal infrastructure

---

# Incident Response

If a secret is accidentally committed:

1. immediately revoke the secret
2. rotate credentials
3. remove the secret from repository history
4. investigate potential exposure

---

# Guiding Principle

Secrets should be stored securely, accessed only when required, and never embedded in source code.
