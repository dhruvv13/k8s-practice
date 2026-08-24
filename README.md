# Kubernetes Practice & Projects Portfolio 

This repository contains hands-on Kubernetes projects following the **Tech World with Nana** DevOps Roadmap.

‚ Projects Directory

### 1. [01-Basic K8s Practice](./01-basic-k8s-practice)
- Foundational Kubernetes manifests, Pods, Deployments, and Service configurations.

### 2. [02-Microservices Architecture Project](./02-microservices-project)
- Multi-environment isolation (`dev`/`prod` namespaces).
- Stateful workloads with MySQL StatefulSets, PersistentVolumeClaims, Secrets, and ConfigMaps.

### 3. [03-Helm MongoDB Ingress Project](./03-helm-mongodb-ingress-project)
- Production-grade deployment packaged as a Helm Chart.
- Replicated MongoDB cluster with Mongo-Express UI and NGINX Ingress host routing.

### 4. [04-K8s Operators, RBAC & Prometheus Monitoring](./04-k8s-operators-rbac-prometheus)
- Operators pattern with Custom Resource Definitions (CRDs).
- Enterprise RBAC model (Users, Groups, ServiceAccounts, Roles, and ClusterRoles).
- Full monitoring stack with Prometheus TSDB, Alertmanager, Grafana, Node Exporter, and dynamic ServiceMonitors.

5. [05-Helmfile Microservices (Google Online Boutique)](./05-helmfile-microservices)
   * Deploys a complex, 11-tier microservices application using advanced Helm concepts and **Helmfile**.
   * Utilized the **DRY (Don't Repeat Yourself)** principle to create a single generic Helm template and dynamically injected values.
   * **Key Concepts Mastered:**
     * **Helmfile & Generic Charts:** Dynamic value injection for multiple releases.
     * **Microservices Architecture:** Managing dependencies between 11 interconnected services (Go, Java, Node.js, Python).
     * **Stateful K8s Deployments:** Configured Redis with `emptyDir` volumes for cart caching.
   * **Real-World Troubleshooting & Problem Solving:**
     * Fixed Helmfile version compatibility (`unknown flag: --client`).
     * Resolved CPU starvation & CrashLoopBackOff for slow-booting Node.js services via probe tuning.
     * Debugged and fixed 500 Internal Server Errors by dynamically injecting missing `PORT` environment variables.
     * Handled K8s resource exhaustion limits during Istio Service Mesh sidecar injection.
**To deploy this project:**
```bash
cd 05-helmfile-microservices
helmfile sync
