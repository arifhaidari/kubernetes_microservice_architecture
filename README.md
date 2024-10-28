# Kubernetes Microservice Architecture

This project is built on Kubernetes and designed to understand and implement a microservice architecture. It leverages various Kubernetes concepts, tools, and best practices to create a local development environment on Minikube. The primary goal is to enable the deployment, scaling, and management of services, with a focus on learning and future reference.

## Table of Contents

1. [Project Overview](#project-overview)
2. [Technologies and Tools](#technologies-and-tools)
3. [Setup and Installation](#setup-and-installation)
   - Minikube
   - HyperKit
   - kubectl CLI
4. [Microservices](#microservices)
   - MongoDB and Mongo Express
5. [Key Kubernetes Concepts](#key-kubernetes-concepts)
   - Namespaces
   - Pods and Deployments
   - Volumes and Persistent Storage
6. [Kubernetes Networking](#kubernetes-networking)
   - Services
   - Ingress and NGINX Ingress Controller
7. [Helm Package Manager](#helm-package-manager)
8. [Useful Tips and Tricks](#useful-tips-and-tricks)

---

## Project Overview

This project simulates a microservice architecture using Kubernetes, offering a hands-on approach to managing and deploying containerized services. It’s configured to run locally using Minikube, enabling a lightweight and straightforward Kubernetes cluster. The project showcases key components of Kubernetes, such as namespace isolation, service exposure, persistent storage, and ingress management.

## Technologies and Tools

This section lists the core tools and technologies used to build and manage the Kubernetes microservices.

- **Minikube**: A lightweight Kubernetes implementation that runs a local cluster with a single node. Minikube is ideal for development and testing in a controlled environment.
- **HyperKit**: A hypervisor framework for macOS, allowing Minikube to run on top of virtualized infrastructure without needing third-party VMs like VirtualBox.
- **kubectl**: The command-line tool for interacting with Kubernetes clusters, used for deploying applications, inspecting and managing cluster resources, and monitoring deployments.
- **kubectx and kubens**: Helper tools to manage multiple Kubernetes clusters and namespaces, simplifying context switching in complex environments.

## Setup and Installation

### Minikube

Minikube creates a single-node Kubernetes cluster on your local machine, ideal for learning and experimentation. Minikube requires a virtualization driver, which can be set up with HyperKit on macOS.

To install and start Minikube:

```bash
brew install minikube
minikube start --driver=hyperkit
```

Minikube CLI commands allow you to start, stop, and delete the cluster:

```bash
minikube start
minikube stop
minikube delete
```

### HyperKit

HyperKit is used as a lightweight VM solution on macOS. It runs entirely in userspace and minimizes dependencies, allowing Minikube to operate without additional VM software. If Docker is already installed, HyperKit may be preconfigured.

### kubectl CLI

The `kubectl` command-line tool enables communication between the Kubernetes API server and your local setup. It manages applications and resources within your cluster. Commands include deployment, scaling, and inspection:

```bash
# To deploy an application
kubectl apply -f <file.yaml>

# To manage and inspect resources
kubectl get pods
kubectl get services
kubectl describe pod <pod-name>
```

## Microservices

This project includes a MongoDB database paired with Mongo Express, providing a simple microservice to manage a database and a web-based admin interface.

- **MongoDB**: A NoSQL, document-oriented database that uses JSON-like schemas for storing data.
- **Mongo Express**: A web-based admin interface for MongoDB built using Node.js and Express.js, making it easy to manage and visualize MongoDB data.

**Tip**: To secure MongoDB passwords, encode them with base64 to avoid plaintext storage:

```bash
echo -n 'your_username_or_password' | base64
```

## Key Kubernetes Concepts

### Namespaces

Namespaces partition resources within a single cluster, allowing isolated environments in larger clusters. Resource names must be unique only within their namespace, which makes namespaces a valuable tool for organizing resources in complex projects.

### Pods and Deployments

- **Pod**: The smallest deployable unit in Kubernetes, representing one or more containers that share storage and network resources.
- **Deployment**: An abstraction over Pods, managing their creation, scaling, and updating. Deployments ensure that the desired number of Pod replicas are running and provide rollback capabilities.

### Volumes and Persistent Storage

Volumes provide persistent storage to containers, allowing data to persist beyond the lifecycle of a Pod. Kubernetes offers various types of storage:

- **Persistent Volume (PV)**: Persistent storage that is independent of any specific Pod, designed for durable, reusable storage.
- **StorageClass**: Specifies the type of storage needed, dynamically provisioning PVs for different workloads.
- **NFS (Network File System)**: Enables distributed storage, allowing files to be accessed over a network as if they were local.

Example NFS setup:

```yaml
apiVersion: v1
kind: PersistentVolume
metadata:
  name: pv-nfs
spec:
  storageClassName: "nfs"
  capacity:
    storage: 1Gi
  accessModes:
    - ReadWriteMany
  nfs:
    path: /path/to/share
    server: nfs-server.local
```

## Kubernetes Networking

### Services

A Service in Kubernetes abstracts access to a group of Pods, assigning them a stable IP address (clusterIP) for consistent communication. This enables load balancing and networking between Pods, even when Pod IPs change over time.

Types of Services:

- **ClusterIP**: Exposes the Service on a cluster-internal IP.
- **NodePort**: Exposes the Service on a specific port of each Node in the cluster.
- **LoadBalancer**: Exposes the Service externally using a cloud provider’s load balancer.

### Ingress and NGINX Ingress Controller

**Ingress** resources manage external access to services within a Kubernetes cluster. Ingress routes traffic from outside the cluster to the correct internal services, based on path rules.

- **NGINX Ingress Controller**: Acts as a reverse proxy and load balancer for HTTP(S) traffic. The controller is installed via Minikube to manage Ingress on a local cluster.

To enable NGINX Ingress on Minikube:

```bash
minikube addons enable ingress
```

## Helm Package Manager

Helm simplifies the management of Kubernetes applications by packaging them into Helm Charts. Charts bundle YAML files and configurations to define an application, allowing for easy versioning, deployment, and upgrades.

- **Helm Chart**: A collection of files that describe a Kubernetes application, including all required resources (pods, services, deployments, etc.).

To install Helm and deploy a chart:

```bash
brew install helm
helm install <chart-name> <repository/chart>
```

## Useful Tips and Tricks

- **kubectx and kubens**: These tools simplify switching between multiple clusters and namespaces, making it easier to manage complex Kubernetes environments.

  Install with:

  ```bash
  brew install kubectx
  ```

- **Password Management**: Use base64 encoding for secure password handling:
  ```bash
  echo -n 'your_password' | base64
  ```
