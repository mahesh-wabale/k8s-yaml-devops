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

 ### 5. check the output
 minikube dashboard
--------------------------------------------------------------------------------------------------------------------------------------------------------

# Tomcat Deployment on Kubernetes

This repository contains the Kubernetes configuration files for deploying a Tomcat server with a custom web application. Follow the instructions below to set up and manage the Tomcat deployment in a Kubernetes cluster.

## Prerequisites

- Kubernetes cluster
- `kubectl` command-line tool
- Docker (for building and pushing images)
- DockerHub account (if using a private image repository)

## Directory Structure

/tomcat
├── tomcat-deployment.yaml
├── Dockerfile
├── your-application.war
└── README.md

###  Build and Push Docker Image

First, build the Docker image for the tomcat application and push it to DockerHub.

``
docker build -t pramila188/tomcat1 .
docker push pramila188/tomcat1

###  create namespace
kubectl create namespace tomcat


### 1. kubernetes deployment
   create tomcat-deployment.yaml and applying the configuration
## Kubernetes Resources

### 2. ResourceQuota

The `ResourceQuota` limits the resources that the Tomcat application can use in the `tomcat1` namespace.

- **File:** `tomcat-resource-quota.yaml`
- **Quota Summary:**
  - CPU Requests: 1 core
  - Memory Requests: 2Gi
  - CPU Limits: 2 cores
  - Memory Limits: 4Gi
  - Pods: 10
  - Services: 5
  - ConfigMaps: 10
  - Secrets: 10

### 3. Ingress

The `Ingress` resource provides external access to the Tomcat application.

- **File:** `tomcat-ingress.yaml`
- **Host:** `tomcat.example.com`
- **TLS Secret:** `tomcat-tls`

### 4. Secrets

The `Secrets` resource stores sensitive data, such as credentials for the Tomcat admin interface.

- **File:** `tomcat-secret.yaml`
- **Data Stored:**
  - `username` (Base64 encoded)
  - `password` (Base64 encoded)

### 5. ConfigMap

The `ConfigMap` contains configuration data for the Tomcat application, such as `server.xml` and `logging.properties`.

- **File:** `tomcat-configmap.yaml`
- **Config Files:**
  - `server.xml`
  - `logging.properties`

### 6. ServiceAccount

The `ServiceAccount` provides an identity for processes running in the Tomcat pod.

- **File:** `tomcat-service-account.yaml`

## Deployment
kubectl apply -f tomcat-resource-quota.yaml
Apply the deployment and service:
kubectl apply -f tomcat-deployment.yaml -n tomcat
kubectl apply -f tomcat-service-account.yaml
kubectl apply -f tomcat-configmap.yaml
kubectl apply -f tomcat-secret.yaml
kubectl apply -f tomcat-ingress.yaml


Verify the status of the pods and service:
kubectl get pods -n tomcat
kubectl get services -n tomcat

###  check output
minikube dashboard





