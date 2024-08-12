# Kubernetes Deployment of TestHello Application

This project demonstrates the deployment of a Spring Boot application named `testhello` on a Kubernetes cluster using YAML configuration files. The application is containerized using Docker and exposed through a Kubernetes Service.

## Prerequisites

- Kubernetes Cluster (Minikube)
- kubectl installed and configured
- Docker installed and DockerHub account
- The `hello` namespace exists in your Kubernetes cluster (create if necessary)

## Steps to Deploy

### 1. Build and Push Docker Image

First, build the Docker image for the Spring Boot application and push it to DockerHub.

``
docker build -t pramila188/testhello .
docker push pramila188/testhello

### 2. Create namespace
kubectl create namespace hello

### 3.Create deployment.yaml and service.yaml file and  Deploy the application
 kubectl apply -f deployment.yaml -n hello
 kubectl apply -f service.yaml -n hello

 ### 4. verify the deployment 
 kubectl get pods -n hello
 kubectl get services -n hello

 ### 3. check the output
 minikube dashboard
 



