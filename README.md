# Kubernetes

Kubernetes (K8s) is an open-source container orchestration system for automating deployment, scaling, and management of containerized applications.

## Key Concepts

* **Pod**: The smallest deployable unit in Kubernetes, containing one or more containers sharing network and storage.
* **Service**: An abstract way to expose an application running on a set of Pods as a network service.
* **Deployment**: Provides declarative updates for Pods and ReplicaSets.
* **ConfigMap / Secret**: Objects used to store non-sensitive and sensitive configuration data respectively.
* **Ingress**: Manages external access to services in a cluster, typically HTTP/HTTPS routing.

## Container Health Probes

* **Liveness Probe**: Determines if the container needs to be restarted. If it fails, `kubelet` kills the container and applies its restart policy.
* **Readiness Probe**: Determines if a container is ready to accept traffic. If it fails, the endpoints controller removes the Pod's IP from matching Services.
* **Startup Probe**: Indicates whether the application inside the container has started. Disables liveness and readiness checks until startup succeeds, useful for slow-starting legacy workloads.

## Control Plane Components

* `kube-apiserver`: Core API server exposing the Kubernetes REST API.
* `etcd`: Consistent and highly-available key-value store for cluster data.
* `kube-scheduler`: Assigns newly created Pods to optimal nodes.
* `kube-controller-manager`: Runs controller processes (Node, Replication, Endpoints controllers).