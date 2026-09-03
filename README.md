# Kubernetes Exercises & Notes

Kubernetes (K8s) is an open-source container orchestration platform for automating deployment, scaling, and management of containerized applications.

## Core Concepts

- **Pod**: The smallest deployable unit in Kubernetes, containing one or more containers.
- **Service**: An abstract way to expose an application running on a set of Pods as a network service.
- **Deployment**: Provides declarative updates for Pods and ReplicaSets.
- **Ingress**: Manages external access to services in a cluster (typically HTTP/HTTPS).
- **ConfigMap & Secret**: Used to store non-confidential and confidential key-value data.

## Quick kubectl Reference

```bash
# Get cluster status
kubectl cluster-info

# List all pods in all namespaces
kubectl get pods -A

# View logs for a specific pod
kubectl logs -f <pod-name>

# Describe pod details and events
kubectl describe pod <pod-name>

# Apply configuration manifest
kubectl apply -f manifest.yaml

# Port-forward to local machine
kubectl port-forward svc/<service-name> 8080:80
```

## Recommended Ecosystem Tools

- `k9s`: Terminal-based UI for managing Kubernetes clusters.
- `helm`: Package manager for Kubernetes.
- `kind` / `minikube`: Local Kubernetes clusters for development.