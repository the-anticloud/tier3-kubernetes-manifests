# L5 Narrow / L2 General Classification — kubernetes-manifests
**Platform:** Anticloud | **PAX:** 27B | **IP:** USPTO pending 2026, Anticloud FZ LLE
**Domain:** Sovereign Kubernetes deployment: air-gapped K8s manifests for Anticloud

## L5 Narrow
kubernetes-manifests specializes in sovereign kubernetes deployment: air-gapped k8s manifests for anticloud within the Anticloud sovereign deployment boundary. All operations stay local — no cloud services, no external APIs, no data exfiltration. The narrow scope ensures deterministic, auditable behavior that PAX 27B can reason about precisely.

## L2 General
L2 General means kubernetes-manifests is available to all 9 Anticloud tiers without per-tier configuration. The same API serves hospital, defense, robotics, and research deployments.

## PAX Integration
PAX 27B validates K8s manifests for sovereign compliance: no external LoadBalancer services, all PVCs use encrypted storage, RBAC is least-privilege, NetworkPolicies block external egress.

## AIOSS Audit Relevance
Every K8s event (manifest hash + applied resources + RBAC policy hash + network policy hash) is AIOSS-chained: H_n = SHA3-256(H_{n-1} || entry_hash_n || timestamp_n).
Tamper-evident, offline-verifiable, zero cloud dependency.

## Regulatory / Compliance
NIST SP 800-190 (container security), CIS Kubernetes Benchmark, NSA/CISA K8s hardening
