# Geodat AI Platform Architecture

The Geodat AI platform is built around a cloud-native architecture for scalable geospatial analytics and data services.

## Core components

Client applications
↓
Web applications (Leaflet / Shiny / dashboards)
↓
API services (Go microservices)
↓
Data processing pipelines (Python / R)
↓
Spatial database (PostgreSQL + PostGIS)
↓
Cloud infrastructure (Azure)

## Infrastructure layer

- Azure Container Apps for service deployment
- Docker containers for reproducible environments
- Azure Blob Storage for large datasets
- Azure networking and identity management

## Development and deployment

- GitHub for version control
- CI/CD pipelines for automated builds
- Infrastructure-as-code for platform management
