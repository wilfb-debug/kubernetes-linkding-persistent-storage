# Kubernetes Linkding with Persistent Storage

## Overview
This project deploys **Linkding**, a self-hosted bookmark manager, on Kubernetes using:
- Namespaces
- Deployments
- Services
- PersistentVolumeClaims
- Dynamic storage provisioning

The application is deployed on a local Kubernetes cluster (Rancher Desktop / K3s) and uses persistent storage to ensure 
data survives pod restarts.

---

## Architecture
- **Namespace:** linkding
- **Deployment:** linkding (1 replica)
- **Service:** ClusterIP
- **Storage:** PersistentVolumeClaim (1Gi, local-path)
- **Database:** SQLite (mounted at `/etc/linkding/data`)

---

## Key Kubernetes Concepts Demonstrated
- Declarative YAML manifests
- Multi-resource YAML files
- Namespace isolation
- Service discovery via labels
- Persistent storage using PVCs
- Volume mounting inside containers
- Pod lifecycle and data persistence

---

## How to Deploy

```bash
kubectl apply -f manifests/linkding/linkding-with-storage.yaml
