# K8s Microservices Monitoring Project

## 📌 Project Overview
This project is a **scalable microservices architecture** built using **Python (Flask)**, containerized with **Docker**, orchestrated with **Kubernetes (K8s)**, and monitored using **Prometheus and Grafana**. It demonstrates how to deploy microservices efficiently and observe system metrics in a cloud-native environment.

## 🏗 Architecture
The application consists of multiple **Flask-based microservices** running inside **Kubernetes pods**, with the following components:

### 🔹 Microservices
1. **User Service** - Handles user authentication and management.
2. **Order Service** - Manages customer orders.
3. **Payment Service** - Processes payments securely.

Each microservice exposes RESTful APIs and communicates via internal **Kubernetes services**.

### 🔹 Infrastructure & Deployment
- **Docker**: Each microservice is packaged into a separate Docker container.
- **Kubernetes**: Manages containerized microservices with separate pods.
- **Helm Charts**: Simplifies deployment and configuration.
- **Service Mesh (Optional)**: Istio/Linkerd for enhanced observability and security.

### 🔹 Monitoring Stack
- **Prometheus**: Collects application and system metrics.
- **Grafana**: Provides a dashboard for visualization.
- **Node Exporter**: Captures host-level metrics.
- **Kube State Metrics**: Exposes Kubernetes resource metrics.

## 🚀 Installation & Setup
### Prerequisites:
- Install **Docker** and **Minikube**
- Install **kubectl** and **Helm**

### Steps to Deploy:
1. **Clone the Repository**
   ```sh
   git clone https://github.com/Saahiti402/k8s-monitoring.git
   cd k8s-monitoring
   ```

2. **Build and Push Docker Images**
   ```sh
   docker build -t user-service ./user-service
   docker build -t order-service ./order-service
   docker build -t payment-service ./payment-service
   ```

3. **Start Minikube & Deploy Services**
   ```sh
   minikube start
   kubectl apply -f k8s/
   ```

4. **Deploy Monitoring Stack with Helm**
   ```sh
   helm install prometheus prometheus-community/kube-prometheus-stack -n monitoring --create-namespace
   helm install grafana grafana/grafana -n monitoring
   ```

5. **Port Forward Grafana Dashboard**
   ```sh
   kubectl port-forward svc/grafana -n monitoring 3000:3000
   ```
   Open Grafana at: [http://localhost:3000](http://localhost:3000)

## 📊 Observability & Alerts
- Pre-configured **Grafana dashboards** to visualize API response times, request rates, and CPU/memory usage.
- **Prometheus alerts** configured to trigger when resource limits exceed thresholds.
