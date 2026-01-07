# Kubernetes Commands Used (Rancher Desktop / K3s)

## Cluster / Context
- kubectl config current-context
- kubectl config set-context --current --namespace=linkding
- kubectl config set-context --current --namespace=default

## Namespaces
- kubectl create namespace linkding
- kubectl get namespace linkding

## Deployments / Pods
- kubectl create deployment my-app --image=nginx --replicas=3
- kubectl get deployment my-app
- kubectl get pods
- kubectl get pods -o wide
- kubectl delete pod <pod-name>
- kubectl rollout restart deployment/linkding

## Services
- kubectl expose deployment my-app --port=80 --target-port=80
- kubectl get services
- kubectl describe service my-app

## Port Forwarding
- kubectl port-forward service/my-app 8080:80
- kubectl port-forward service/linkding 8080:9090

## YAML Apply/Delete
- kubectl apply -f deployment.yaml
- kubectl apply -f app.yaml
- kubectl delete -f deployment.yaml
- kubectl delete -f linkding.yaml
- kubectl apply -f linkding-with-storage.yaml

## Generate YAML (dry-run)
- kubectl create deployment test --image=nginx --replicas=2 --dry-run=client -o yaml
- kubectl create deployment test --image=nginx --replicas=2 --dry-run=client -o yaml > test.yaml
- kubectl create service clusterip test --tcp=80:80 --dry-run=client -o yaml

## Storage (PVC/PV)
- kubectl get storageclass
- kubectl get pvc
- kubectl describe pvc linkding-data
- kubectl get pv
- kubectl exec -it deployment/linkding -- /bin/sh
- ls -la /etc/linkding/data
