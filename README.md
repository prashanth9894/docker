# Node.js Kubernetes Deployment 🚀

This repository contains the Kubernetes manifests to deploy a scalable Node.js application. It is configured with an automated scaling mechanism to handle variable traffic loads effectively.

## Architecture Overview 🏗️

The setup is composed of three primary Kubernetes resources:
- **Deployment**: Runs the Node.js application (`paulbouwer/hello-kubernetes`) starting with **3 replicas**. It specifies CPU and Memory limits/requests.
- **Service**: Exposes the application over a standard TCP connection on Port 80, routing to the containers on port 8080.
- **Horizontal Pod Autoscaler (HPA)**: Monitors CPU utilization and automatically scales the number of pods between 3 and 10 based on a 50% CPU target threshold.

## Files Description 📂
- `nodejs-k8s-manifests.yaml`: The unified resource file containing the defining code for the Deployment, Service, and HPA.

## Usage Instructions ⚙️

### Prerequisites
- A working Kubernetes cluster (Minikube, EKS, GKE, etc.)
- Metrics Server installed (required for the Horizontal Pod Autoscaler to read CPU metrics).

### Deployment
To apply these configurations to your cluster, run:
```bash
kubectl apply -f nodejs-k8s-manifests.yaml
```

### Monitoring
To watch the status of the deployed pods and the autoscaler, use:
```bash
kubectl get pods
kubectl get hpa
```

## Clean Up 🧹
To remove all resources created by this manifest:
```bash
kubectl delete -f nodejs-k8s-manifests.yaml
```
