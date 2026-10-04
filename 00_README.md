# kubernetes-manifests

**Status:** Production-Ready | **Tier:** 3 | **Category:** Infrastructure & Deployment

## Overview

Helm charts and Kubernetes deployment configuration

**Domain:** https://0-1.gg/api-oss/kubernetes-manifests  
**Repository:** github.com/0-1-gg/api-oss-fixed  
**License:** Commercial with open governance

---

## Architecture & Components

### Core Components
- Helm charts
- service manifests
- ingress config
- StatefulSet

### Specifications

Helm: v3+; Services: 15+; Replicas: Auto-scaling 2-10; Resources: CPU/memory limits; Namespace: Multi-tenancy

---

## Deployment Scenarios

### Local Development (docker-compose)
\\\ash
docker-compose up kubernetes-manifests
\\\

### Kubernetes (High Availability)
\\\ash
kubectl apply -f kubernetes-manifests/kubernetes-manifests/
\\\

### Terraform AWS
\\\ash
terraform apply -var="service=kubernetes-manifests"
\\\

---

## Integration Points

See APPENDIX files for detailed integration information:
- 05_PLAYS_WELL_WITH.md — Complementary projects
- 06_System_Integration_Glimpses.md — Real deployment scenarios
- 07_Web_of_Relativity_This_Project.md — Service relationships

---

## Security & Compliance

- **Authentication:** api-oss-security (API Key, OAuth 2.0, JWT)
- **Rate Limiting:** Configurable (default 1000 req/min)
- **Encryption:** TLS 1.3 in transit, AES-256 at rest
- **Audit:** Immutable logging via api-oss-logging
- **Compliance:** HIPAA, GDPR, FedRAMP ready

---

**Last updated:** 2026-09-28
