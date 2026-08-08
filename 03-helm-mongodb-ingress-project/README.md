# Project 03: Replicated MongoDB with Mongo-Express UI & Ingress 🚀

## 📌 Architecture Overview
This project demonstrates deploying a complete database stack with web interface and ingress routing using **Helm**:
- **Replicated MongoDB**: Multi-replica database setup for scalability.
- **Mongo-Express UI**: Web-based administration tool for MongoDB.
- **NGINX Ingress Controller**: External traffic routing with custom host-header parsing (`mongo.express.com`).
- **Helm Packaging**: Parameterized manifests using `values.yaml`.

## 📂 Directory Structure
```text
03-helm-mongodb-ingress-project/
├── Chart.yaml             # Helm Chart Metadata
├── values.yaml            # Parameterized configurations
├── templates/
│   ├── mongodb.yaml       # MongoDB Deployment & ClusterIP Service
│   ├── mongo-express.yaml # Mongo-Express Deployment & NodePort Service
│   └── ingress.yaml       # Ingress Routing Rules
└── README.md
```

## 🛠️ Deployment Instructions

1. **Deploy using Helm:**
   ```bash
   helm install my-db-release ./03-helm-mongodb-ingress-project
   ```

2. **Verify Pods & Ingress:**
   ```bash
   kubectl get pods
   kubectl get ingress
   ```

3. **Access via Ingress:**
   ```bash
   curl -u admin:pass -H "Host: mongo.express.com" http://localhost:<INGRESS_NODEPORT>
   ```
