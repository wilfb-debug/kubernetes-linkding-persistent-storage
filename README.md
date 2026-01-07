# Kubernetes Linkding with Persistent Storage

## Overview
This project demonstrates how to deploy a **stateful application** on Kubernetes using
**PersistentVolumeClaims (PVCs)** to ensure data durability across pod restarts.

The application used is **Linkding**, a self-hosted bookmark manager, deployed into its own
namespace with persistent SQLite storage.

This lab was built and tested locally using **Rancher Desktop (K3s)**, following production-grade Kubernetes storage patterns.

---

## Architecture Summary

- **Namespace isolation** (`linkding`)
- **Deployment** for application lifecycle management
- **Service** for internal access
- **PersistentVolumeClaim (PVC)** for durable storage
- **StorageClass**: `local-path` (dynamic provisioning)
---

## Key Kubernetes Concepts Demonstrated

### 1. Stateless vs Stateful Containers
- Containers are ephemeral by default
- Application data is lost when pods restart unless persisted externally

### 2. PersistentVolumeClaim (PVC)
- Requests storage independently of pod lifecycle
- Automatically provisioned via StorageClass
- Bound to a PersistentVolume (PV)

### 3. Volume Mounting
- PVC mounted into container at `/etc/linkding/data`
- SQLite database persists across pod restarts

---

## Repository Structure

```text
.
├── manifests/
│   ├── linkding/
│   │   ├── linkding.yaml                # Deployment + Service (no storage)
│   │   └── linkding-with-storage.yaml   # PVC + Deployment + Service
│   └── nginx/                           # Earlier learning artifacts
├── screenshots/
│   ├── 01-pods-running.png
│   ├── 02-pvc-bound.png
│   ├── 02-describe-pvc.png
│   ├── 03-container-data-dir.png
│   ├── 03-sqlite-data-persisted.png
│   └── 04-linkding-ui.png
└── README.md
