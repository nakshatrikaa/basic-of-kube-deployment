# Kube Learn

A Kubernetes learning project featuring basic Kubernetes concepts and a complete voting application demo.

## Project Structure

- **pods/**: Basic pod definitions for learning
- **replicasets/**: ReplicaSet examples
- **deployments/**: Deployment configurations
- **service/**: Service definitions (NodePort and ClusterIP)
- **voting-app-demo/**: Complete voting application with multiple microservices

## Prerequisites

Before deploying this project, ensure you have the following installed:

1. **Minikube** - Local Kubernetes cluster
2. **kubectl** - Kubernetes command-line tool
3. **Docker** (optional, if you want to build custom images)

## Installing Minikube

Minikube is a tool that runs a single-node Kubernetes cluster locally. Follow the official installation guide:

[Minikube Installation Guide](https://minikube.sigs.k8s.io/docs/start/)

### Quick Setup (Windows/Mac/Linux)

```bash
# Start minikube
minikube start

# Check status
minikube status

# View cluster info
kubectl cluster-info
```

## Deploying on Minikube

### 1. Start Minikube

```bash
minikube start
```

### 2. Deploy Basic Examples

Navigate to the project and apply basic Kubernetes resources:

```bash
# Deploy pods
kubectl apply -f pods/

# Deploy replicasets
kubectl apply -f replicasets/

# Deploy deployments
kubectl apply -f deployments/

# Deploy services
kubectl apply -f service/
```

### 3. Deploy the Voting App Demo

```bash
# Deploy all voting app resources
kubectl apply -f voting-app-demo/deployments/

# Or deploy pods version
kubectl apply -f voting-app-demo/pods/
```

### 4. Access the Application

The voting app uses services to expose applications. To access them:

```bash
# For NodePort services, get the service URL
minikube service vote-service --url
minikube service result-service --url

# Or open directly in browser
minikube service vote-service
minikube service result-service
```

## Monitoring and Managing

```bash
# View all resources
kubectl get all

# View pods
kubectl get pods

# View deployments
kubectl get deployments

# View services
kubectl get services

# View logs
kubectl logs <pod-name>

# Describe a resource
kubectl describe pod <pod-name>
```

## Cleanup

To stop and remove resources:

```bash
# Delete all resources
kubectl delete -f voting-app-demo/deployments/

# Stop minikube
minikube stop

# Delete the cluster
minikube delete
```

## Learning Resources

This project covers:

- Basic Pod definitions
- ReplicaSets for managing multiple pod replicas
- Deployments for managing application updates
- Services for exposing applications (ClusterIP, NodePort)
- Multi-tier application architecture with microservices

## Voting App Architecture

The voting app demo includes:

- **Vote**: Web UI for voting
- **Redis**: In-memory data store for vote caching
- **Worker**: Background process for storing votes in database
- **Database**: PostgreSQL for persistent storage
- **Result**: Web UI for displaying results

Each component is deployed as a separate microservice with its own deployment and service configuration.

---

> **Note**: This README was created by an LLM (Claude). Please verify the instructions match your specific environment and update as needed.
