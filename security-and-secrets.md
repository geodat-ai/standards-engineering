# GeoDat AI Security and Secrets Management

Sensitive credentials must never be stored in source code repositories.

---

# What Counts as a Secret

Examples include:

database passwords  
API tokens  
private certificates  
access keys  
encryption keys

---

# Secret Management Platform

GeoDat AI uses Azure Key Vault.

Key Vault stores:

database credentials  
API tokens  
storage keys  
TLS certificates  
application secrets

Applications retrieve secrets securely at runtime.

---

# Infrastructure Integration

Infrastructure tools should reference secrets stored in Key Vault.

Applications should access secrets using:

environment variables  
managed identities  
secure configuration injection

---

# Local Development

Use `.env` files for local development.

`.env` files must be excluded from Git.

Repositories should include `.env.example` files.

---

# Access Control

Secrets should follow least privilege.

Only systems requiring access should receive it.

---

# Incident Response

If a secret is exposed:

1 revoke the credential  
2 rotate the secret  
3 remove the secret from Git history  
4 investigate exposure

---

# Guiding Principle

Secrets must always remain outside source code.
