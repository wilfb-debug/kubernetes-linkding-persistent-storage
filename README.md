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
