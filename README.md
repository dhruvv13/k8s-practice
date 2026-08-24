# Kubernetes Practice & Projects Portfolio 🚀

This repository contains hands-on Kubernetes projects following the **Tech World with Nana** DevOps Roadmap.

## 📂 Projects Directory

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
## 📁 05-helmfile-microservices (Google Online Boutique)

This project deploys a complex, 11-tier microservices application (Google's Online Boutique) using advanced Helm concepts and **Helmfile**. Instead of creating 11 separate charts, I utilized the **DRY (Don't Repeat Yourself)** principle to create a single generic Helm template and dynamically injected values using Helmfile.

### 🛠️ Key Concepts Mastered:
*   **Helmfile & Generic Charts:** Dynamic value injection for multiple releases.
*   **Microservices Architecture:** Managing dependencies between 11 interconnected services (Go, Java, Node.js, Python).
*   **Stateful K8s Deployments:** Configured Redis with `emptyDir` volumes for cart caching.

### � Real-World Troubleshooting & Problem Solving:
During deployment, I encountered and resolved several production-grade issues:
1.  **Helmfile Version Compatibility (`unknown flag: --client`):** The default Helmfile version was incompatible with Helm v3.15+. Fixed by explicitly upgrading Helmfile to `v1.7.4`.
2.  **CPU Starvation & CrashLoopBackOff:** Slow-booting Node.js services (`currencyservice`, `paymentservice`) were being killed by K8s probes prematurely. Resolved by tuning Probes (`initialDelaySeconds: 60`).
3.  **Missing Environment Variables (500 Internal Server Error):** Services crashed due to missing binding ports. Fixed by dynamically injecting the `PORT` env variable via the generic Helm template.
4.  **Resource Exhaustion (Pending Pods via Istio):** Attempted to inject Istio Service Mesh, but K8s nodes hit the 4GB RAM limit, causing pods to stay in the `0/2 Pending` state. Successfully debugged the resource limit and safely rolled back the Istio sidecar injection to restore the application state.

**To deploy this project:**
```bash
cd 05-helmfile-microservices
helmfile sync
