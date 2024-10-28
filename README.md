# Kubernetes Microservice Architecture (Under Development)

This project explores a microservice architecture using Kubernetes, allowing for learning and future reference. The setup is designed for local development on Minikube, leveraging various Kubernetes resources, tools, and best practices for a scalable microservice deployment.

## Table of Contents

1. [Technologies Used](#technologies-used)
2. [Setup](#setup)
   - Minikube
   - kubectl CLI
3. [Demo Project: Mongo Express and MongoDB](#demo-project-mongo-express-and-mongodb)
4. [Kubernetes Concepts](#kubernetes-concepts)
   - Namespaces
   - Helm and Helm Charts
   - Volumes and Persistent Volumes
5. [Networking](#networking)
   - Services
   - Ingress and NGINX Ingress Controller

## Technologies Used

### Minikube

Minikube is a lightweight Kubernetes implementation that creates a VM on your local machine and deploys a simple, single-node cluster. Minikube can run on virtual environments like VirtualBox or HyperKit. When Docker is installed, HyperKit is automatically available for use as the VM driver.

### HyperKit

HyperKit is a lightweight hypervisor framework for macOS, designed to run entirely in userspace. This eliminates the need for third-party VM products, streamlining Kubernetes deployments on local machines.

### kubectl

`kubectl` is a command-line tool that enables interaction between the Kubernetes API and the control plane. It allows for application deployment, resource management, and monitoring of cluster resources.

### kubectx and kubens

- **kubectx**: A CLI tool to switch easily between Kubernetes clusters.
- **kubens**: A CLI tool for switching between namespaces within a Kubernetes cluster.

Install using:

```bash
brew install kubectx
```

## Setup

### Minikube CLI

The `minikube` CLI is used to start, stop, and delete the Kubernetes cluster.

### kubectl CLI

Use the `kubectl` CLI to configure and manage the Minikube cluster, including deployment of applications and resources.

## Demo Project: Mongo Express and MongoDB

This demo utilizes MongoDB as a NoSQL database and Mongo Express as a web-based MongoDB admin interface.

- **MongoDB**: A document-oriented, NoSQL database that stores data in JSON-like documents.
- **Mongo Express**: An admin interface for MongoDB, built using Node.js, Express, and Bootstrap.

**Tip**: For added security, avoid storing plain text passwords. Use base64 encoding:

```bash
echo -n 'your_username_or_password' | base64
```

## Kubernetes Concepts

### Namespaces

Namespaces provide a mechanism for isolating resources within a Kubernetes cluster. Resource names need to be unique only within a namespace, allowing for better resource organization in large clusters.

### Helm and Helm Charts

- **Helm**: A tool to define, install, and upgrade Kubernetes applications. Helm Charts bundle Kubernetes resource definitions, allowing for easy versioning and sharing.
- **Helm Charts**: Collections of Kubernetes files that package an application into a single deployable unit.

### Volumes and Persistent Volumes

- **Volumes**: Directories accessible to containers within a pod, allowing for data persistence.
- **Persistent Volumes (PV)**: Provide storage that persists beyond the lifecycle of individual pods.
- **StorageClass**: Enables dynamic provisioning of PVs by defining storage characteristics that pods can request based on their requirements.

Example of using **NFS** (Network File System) for shared storage across pods, which allows remote access to files as if they were on local storage.

## Networking

### Kubernetes Services

A Kubernetes Service is a logical abstraction that groups a set of pods, allowing for stable networking and load balancing between ephemeral pods.

### Ingress and NGINX Ingress Controller

**Ingress** resources manage external access to services within a Kubernetes cluster. It acts as a unified entry point, routing traffic to the appropriate services based on defined rules.

**NGINX Ingress Controller** provides public access to internal services using the NGINX web server as a proxy.

To enable the NGINX Ingress Controller in Minikube:

```bash
minikube addons enable ingress
```
