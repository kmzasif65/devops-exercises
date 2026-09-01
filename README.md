# Kubernetes Exercises & Questions

Kubernetes (K8s) is an open-source container orchestration platform for automating deployment, scaling, and management of containerized applications.

## Key Concepts

- **Pod**: The smallest deployable unit created and managed by Kubernetes.
- **Service**: An abstract way to expose an application running on a set of Pods as a network service.
- **Deployment**: Provides declarative updates for Pods and ReplicaSets.
- **Ingress**: An API object that manages external access to the services in a cluster, typically HTTP.
- **ConfigMap & Secret**: Objects used to store non-confidential and confidential data in key-value pairs.

## Exercises

### 1. Pods & Deployments
- How do you create a pod using `kubectl` imperatively?
  - `kubectl run nginx --image=nginx`
- How do you scale a deployment to 5 replicas?
  - `kubectl scale deployment/nginx-deployment --replicas=5`

### 2. Probes & Health Checks
- What is the difference between `livenessProbe`, `readinessProbe`, and `startupProbe`?
  - **Liveness probe**: Indicates whether the container is running; if it fails, kubelet kills the container and subjects it to restart policy.
  - **Readiness probe**: Indicates whether the container is ready to serve network traffic.
  - **Startup probe**: Disables liveness and readiness checks until the startup probe succeeds, useful for slow-starting containers.

### 3. Troubleshooting
- How do you inspect events related to a failing pod?
  - `kubectl describe pod <pod-name>`
  - `kubectl get events --sort-by='.metadata.creationTimestamp'`