## Deploying a Containerized Node.js App on Kubernetes
This guide will walk you through deploying a simple **Node.js + Express** app onto a **Kubernetes cluster** using **Docker** and `kubectl`.

## Purpose

The goal of this project is to:
- Containerize a Node.js application using Docker
- Deploy the app to a Kubernetes cluster using a Deployment
- Expose the app to the browser using a Kubernetes Service

### Required tools
- Git
- Visual Studio code
- Node.js
- Docker
- Kubernetes
- Kubernetes CLI
- Docker CLI

### Installation
1. Clone the repository:
```
git clone https://github.com/lswitlearning/sit737-2025-prac6c.git
```

2. Install required dependencies:
```
npm install
```

### Instructions

1. Setup the Kubernetes Cluster (Docker Desktop (local K8s))
    Enter Docker Desktop setting, enable Kubernetes  

    To check the currently active context: `kubectl config current-context`  
&nbsp;
2. Build the Docker Image
 -`docker build -t myapp-k8s .`
&nbsp;
3. Create Kubernetes Deployment
 -create deployment.yaml file  
 -Apply the file `kubectl apply -f deployment.yaml`  
 -Check pods: `kubectl get pods`
 &nbsp;
4. Create Kubernetes Service
 -create service.yaml file
 -Apply the file : `kubectl apply -f service.yaml`
 -Verify service: `kubectl get svc`
 &nbsp;

5. Use the kubectl port-forward command to forward traffic from a local port to the Kubernetes service.
`kubectl port-forward service/myapp-service 8888:80 `
 &nbsp;
6. Access the Application
 http://localhost:8888
 &nbsp;
7. Updating the application (modifying the code)
 &nbsp;
8. Build a new Docker Image witha a new version tag
 -`docker build -t myapp-k8s:v2 .`
 &nbsp;
9. Update the deployment yaml
change the Image: From `myapp-k8s` -> `myapp-k8s:v2`
 &nbsp;
10. Reapply the deployment to trigger an update
 -`kubectl apply -f deployment.yaml`
 &nbsp;
11. Forward traffic to local port 8888, verify the Application  
 http://localhost:8888

