# kubernetes-linkding-persistent-storage
Deployed Linkding on local Kubernetes (Rancher Desktop/K3s) using namespaces, YAML manifests, Services, and PersistentVolumeClaims to persist SQLite data across pod restarts.

# Linkding on Kubernetes (Rancher Desktop/K3s) — Stateful App with Persistent Storage

## What this project proves
- Deployed workloads using Kubernetes YAML manifests (Deployment + Service)
- Used namespaces to isolate applications
- Exposed services and accessed them via port-forwarding
- Implemented persistence using PersistentVolumeClaim (PVC) and verified PV binding
- Verified data survival across pod restarts (stateful workload)

## Tech stack
- Rancher Desktop (K3s)
- kubectl
- Docker image: sissbruecker/linkding
- StorageClass: local-path

## Architecture (high level)
- Namespace: `linkding`
- Deployment: `linkding` (1 replica)
- Service: `linkding` (ClusterIP)
- PVC: `linkding-data` mounted to `/etc/linkding/data`

## How to run (quickstart)
### 1) Create namespace
```bash
kubectl create namespace linkding
kubectl config set-context --current --namespace=linkding
