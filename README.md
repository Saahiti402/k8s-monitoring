# Kubernetes Microservices Monitoring with Prometheus & Grafana

## 📌 Project Overview
This project demonstrates a **scalable microservices architecture** deployed on **Kubernetes** with monitoring capabilities powered by **Prometheus** and **Grafana**. The system ensures observability by collecting and visualizing metrics from various microservices.

## 🏗 Architecture
The project follows a **microservices architecture** where different services communicate through REST APIs. Monitoring is set up to track resource usage, service health, and performance trends.

### Key Components:
1. **Microservices**: Multiple containerized services running independently.
2. **API Gateway**: Handles routing, authentication, and load balancing.
3. **Kubernetes Cluster**: Manages deployment, scaling, and networking.
4. **Prometheus**: Collects and stores metrics from microservices.
5. **Grafana**: Visualizes data from Prometheus using dashboards.
6. **Node Exporter**: Provides system-level metrics.
7. **Kube State Metrics**: Collects Kubernetes resource metrics.

## 🛠 Tech Stack
- **Backend**: Python (FastAPI / Flask)
- **Containerization**: Docker
- **Orchestration**: Kubernetes (Minikube / K3s / Cloud Kubernetes Service)
- **Monitoring**: Prometheus, Grafana, Node Exporter
- **Storage**: Persistent Volumes (for Grafana dashboards)
- **Messaging Queue (Optional)**: Redis + BullMQ

## 🚀 Setup Instructions
### 1️⃣ Prerequisites
- Install **Docker** and **Kubernetes (Minikube / Kind)**
- Install **Helm** (for Prometheus & Grafana deployment)
- Install **kubectl** for managing Kubernetes cluster

### 2️⃣ Clone the Repository
```bash
git clone https://github.com/your-username/microservices-monitoring.git
cd microservices-monitoring
```

### 3️⃣ Deploy Microservices
Deploy your microservices using Kubernetes manifests:
```bash
kubectl apply -f k8s/
```

### 4️⃣ Deploy Monitoring Stack
Use **Helm** to install Prometheus and Grafana:
```bash
helm repo add prometheus-community https://prometheus-community.github.io/helm-charts
helm repo update
helm install prometheus prometheus-community/kube-prometheus-stack --namespace monitoring --create-namespace
```

### 5️⃣ Access Grafana Dashboard
#### **Find Grafana Service Details**
```bash
kubectl get svc -n monitoring
```
Check for **NodePort** and access Grafana via:
```
http://localhost:<NodePort>
```
#### **Retrieve Grafana Admin Password**
```bash
kubectl get secret --namespace monitoring grafana-admin -o jsonpath="{.data.admin-password}" | base64 --decode ; echo
```
Login with **admin** and the retrieved password.

### 6️⃣ Configure Dashboards
- Import **predefined Grafana dashboards** for Kubernetes & Prometheus.
- Set **Prometheus** as the data source in Grafana.

## 📊 Monitoring Setup
- **Prometheus** scrapes metrics from microservices and Kubernetes nodes.
- **Grafana** visualizes CPU, Memory, Requests, and more.
- Alerts can be set up in Prometheus Alertmanager for **incident detection**.

## 🔥 Future Enhancements
- **Service Mesh Integration** (Istio / Linkerd for better traffic control)
- **Logging with ELK Stack** (Elasticsearch, Logstash, Kibana)
- **Auto-Scaling** based on Prometheus metrics

---
### 🎯 Conclusion
This project showcases how to **deploy, monitor, and scale microservices** using **Kubernetes, Prometheus, and Grafana**. With observability in place, maintaining system health and debugging issues becomes significantly easier.


