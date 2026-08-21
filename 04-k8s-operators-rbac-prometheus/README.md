# Project 04: Kubernetes Operators, RBAC & Prometheus Monitoring Stack 📊

## 📌 Architecture Overview

### 1. Prometheus Server Architecture
- **Data Retrieval Worker**: Pulls metrics data on defined scrape intervals.
- **TSDB (Time Series Database)**: Stores all persistent telemetry data.
- **HTTP Server**: Accepts PromQL queries for dashboard clients like Grafana.
- **Alertmanager**: Receives alert triggers and forwards to channels (Slack, Email).

### 2. Enterprise RBAC Model
- **Role & RoleBinding**: Namespace-scoped authorization (`pods`, `secrets`).
- **ClusterRole & ClusterRoleBinding**: Cluster-wide administrative permissions (`namespaces`).
- **Identity Types**: Bound to `Users` (`CN=jane`), `Groups` (`O=devops-admins`), and in-cluster `ServiceAccounts`.

### 3. Monitoring Components Breakdown
- **Prometheus & Alertmanager**: Deployed as **StatefulSets**.
- **Node Exporter**: Deployed as a **DaemonSet** across all cluster nodes.
- **Kube-State-Metrics & Grafana**: Deployed as **Deployments**.
- **ServiceMonitor CRD**: Managed by the Prometheus Operator for zero-config metric discovery.
