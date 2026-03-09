# Geodat AI Services Architecture

Geodat AI integrates artificial intelligence capabilities using Azure AI Services.

These services may include:

Azure OpenAI  
AI agents  
chatbots  
document analysis  
language models

---

# AI Service Repositories

AI capabilities may be implemented as containerised services.

Examples:

api-ai-assistant-python  
service-document-analysis  
service-ai-agents

These services expose APIs that applications can call.

---

# Integration Patterns

AI services may support:

analysis assistants  
client chat interfaces  
automated reporting  
document classification  
geospatial analytics

---

# Deployment

AI services should normally run as containerised APIs.

Applications should interact with AI services through APIs rather than embedding AI logic directly.

---

# Security

AI service credentials must be stored in Azure Key Vault.

---

# Guiding Principle

AI capabilities should remain modular, containerised, and reusable across applications.
