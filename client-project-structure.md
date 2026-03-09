# GeoDat AI Client Project Structure

Client repositories represent individual engagements.

They contain client-specific work only.

Reusable platform components should be stored in shared repositories.

---

# Naming Convention

client-

Examples:

client-council-transport-review  
client-nhs-accessibility-analysis

---

# Typical Structure

docs/  
analysis/  
sql/  
api/  
frontend/  
config/  
deliverables/

---

# Frontend Technologies

Frontend applications may use:

HTMX  
SvelteKit  
React  
Vue  
Shiny dashboards

HTMX is recommended for lightweight applications and form-based tools.

---

# API Integration

Client repositories may integrate with shared services such as:

api-routing-go  
api-auth-go  
api-reporting-python

These services should be consumed through APIs.

---

# Container Usage

Client APIs and services should normally run as containers.

Containerisation ensures consistent deployment across environments.

---

# Security Rules

Client repositories must not contain:

real credentials  
private keys  
sensitive datasets

Use Azure Key Vault for secrets.

---

# Workflow

Client repositories follow the standard development workflow:

main branch for stable code  
feature branches for development  
pull requests for major changes

---

# Guiding Principle

Client repositories should remain focused on the client engagement and not become platform repositories.
