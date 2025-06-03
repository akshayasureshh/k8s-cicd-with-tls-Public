# app Application Deployment and Containerization

## Overview
This project demonstrates the **containerization** of the mookube application and its **deployment on Kubernetes** using a **CI/CD pipeline** through GitHub Actions. The end goal is to have an automated system that builds the Docker image, pushes it to a container registry, and deploys it to Kubernetes.


### 1. **Dockerization**
- Created a `Dockerfile` to containerize the app application.
- The Dockerfile defines the necessary steps to package the app into a Docker image, including setting up dependencies and copying source files into the container.

### 2. **Kubernetes Deployment**
- Created the necessary Kubernetes manifest files to deploy the application, including:
  - `deployment.yaml` 
  - `service.yaml`
  - `ingress.yaml`

### 3. **CI/CD Pipeline Implementation (GitHub Actions)**
- Set up a **GitHub Actions** workflow that automatically:
  - Builds the Docker image for the mookube app.
  - Pushes the Docker image to **Docker Hub** for accessibility.
  
  The **continuous deployment (CD)** portion, which would automatically deploy the app to Kubernetes after the Docker image is pushed, has been omitted for this workflow due to the use of **Minikube**.

### 4. **TLS Implementation (Optional Challenge Goal)**
- For security, the application is configured to run with **TLS communication**. This includes using secure protocols for any web traffic.

---

## TLS Configuration for Secure Communication

The **mookube Application** is secured with **TLS** (HTTPS) using a **self-signed certificate**. This allows for encrypted traffic to the application during local development.

###  How TLS is Set Up

- A self-signed certificate (`tls.crt` and `tls.key`) was manually generated.
- A Kubernetes TLS secret (`mookube-tls`) was created using these files:


  ```bash
  kubectl create secret tls mookube-tls --key tls.key --cert tls.crt