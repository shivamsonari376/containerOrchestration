# containerOrchestration
# README - MERN Stack Deployment with Kubernetes, Helm, and Jenkins

## Directory Structure
```
mern-k8s-deployment/
├── kubernetes/
│   ├── backend-deployment.yaml
│   ├── backend-service.yaml
│   ├── frontend-deployment.yaml
│   ├── frontend-service.yaml
│   ├── mongodb-deployment.yaml
│   ├── mongodb-service.yaml
│   ├── mongodb-pv.yaml
│   ├── mongodb-pvc.yaml
│   ├── ingress.yaml
├── helm/
│   ├── Chart.yaml
│   ├── values.yaml
│   ├── templates/
│   │   ├── backend-deployment.yaml
│   │   ├── backend-service.yaml
│   │   ├── frontend-deployment.yaml
│   │   ├── frontend-service.yaml
│   │   ├── mongodb-deployment.yaml
│   │   ├── mongodb-service.yaml
│   │   ├── mongodb-pv.yaml
│   │   ├── mongodb-pvc.yaml
│   │   ├── ingress.yaml
├── jenkins/
│   ├── Jenkinsfile
```

---

## 1. Kubernetes Deployment

### 1.1 Backend Deployment (`backend-deployment.yaml`)
Deploys the Node.js backend application with environment variables for MongoDB connection.

### 1.2 Backend Service (`backend-service.yaml`)
Exposes the backend using a ClusterIP service for internal communication.

### 1.3 Frontend Deployment (`frontend-deployment.yaml`)
Deploys the React.js frontend application and connects it to the backend.

### 1.4 Frontend Service (`frontend-service.yaml`)
Exposes the frontend via NodePort.

### 1.5 MongoDB Deployment (`mongodb-deployment.yaml`)
Deploys MongoDB with PersistentVolume and PersistentVolumeClaim for data storage.

### 1.6 MongoDB Service (`mongodb-service.yaml`)
Exposes MongoDB via ClusterIP.

### 1.7 MongoDB Persistent Volume (`mongodb-pv.yaml`)
Defines the storage for MongoDB.

### 1.8 MongoDB Persistent Volume Claim (`mongodb-pvc.yaml`)
Claims storage for MongoDB.

### 1.9 Ingress (`ingress.yaml`)
Defines routing rules for frontend and backend.

---

## 2. Helm Chart

### 2.1 `Chart.yaml`
Metadata for Helm chart.

### 2.2 `values.yaml`
Defines configurable values for Helm deployment.

### 2.3 `templates/`
Contains Helm templates for all Kubernetes resources.

#### Helm Commands:
```sh
# Install Helm Chart
helm install mern-app helm/

# Upgrade Helm Chart
helm upgrade mern-app helm/

# Uninstall Helm Chart
helm uninstall mern-app
```

---

## 3. Jenkins CI/CD Pipeline

### 3.1 `Jenkinsfile`
Automates build and deployment.

#### Stages:
1. **Clone Repository**: Fetches frontend & backend repos.
2. **Build Docker Images**: Builds & pushes images to Docker Hub.
3. **Deploy to Minikube**: Connects to Minikube and applies Kubernetes manifests.

#### Jenkins Commands:
```sh
kubectl config view --raw > ~/.kube/config
scp ~/.kube/config ubuntu@YOUR_EC2_IP:~/.kube/config
```

