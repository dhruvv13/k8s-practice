# Kubernetes Demo Microservices Project

This repository contains the declarative Kubernetes manifests for a multi-environment microservice architecture setup, following the **Tech World with Nana** DevOps Roadmap.

## 🚀 Architecture Highlights
- **Environment Isolation:** Separate `dev` and `prod` namespaces.
- **Database & Persistence:** MySQL deployed using `StatefulSet` with dynamic `PVC` provisioning.
- **Security:** Sensitive data managed via Kubernetes `Secrets` and `ConfigMaps`.
- **Microservices Layer:** Stateless frontend web app with `ClusterIP` Services.
- **Traffic Routing:** `Ingress Controller` configured for domain routing (`dev.myapp.com` / `prod.myapp.com`).

## 🛠️ How to Deploy
1. Create namespaces:
   ```bash
   kubectl create ns dev
   kubectl create ns prod
   ```
2. Apply Dev environment manifests:
   ```bash
   kubectl apply -f dev-environment.yaml
   ```
