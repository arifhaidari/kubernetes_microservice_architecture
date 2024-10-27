# Kubernetes Microservice Architecture (Under Development)

Technologies Used:

Minikube:
Minikube is a lightweight Kubernetes implementation that creates a VM on your local machine and deploys a simple cluster containing only one node.
and Minikube needs a virtualization as it runs on virtualbox or hypervisor and for that we need Hyperkit

Hyperkit:
HyperKit is a hypervisor built on top of the Hypervisor. framework in macOS. It runs entirely in userspace and has no other dependencies. We use HyperKit to eliminate the need for other VM products, such as Oracle VirtualBox or VMWare Fusion.
if we have the docker already installed then we already have it on our machine

kubectl:
kubectl is a command line tool that enables communications between the Kubernetes API and the control plane. kubectl allows application deployment, cluster resource management, and resource monitoring.

kubectl cli for configuring the minikube cluster
minikube cli for start and deleting the cluster

Pod is the smallest unit but deployment is abstraction over pods (which creates them)
Pod is the abstraction of a container

Demo Project:
Mongo Express
mongo-express is a web-based MongoDB admin interface written in Node. js, Express. js, and Bootstrap3.

MongoDB:
MongoDB is a source-available, cross-platform, document-oriented database program. Classified as a NoSQL database product, MongoDB utilizes JSON-like documents with optional schemas.

while storing the password for mongodb, do not use the plain text instead:
in terminal (or some other ways):
echo -n 'username or password goes here' | base64

---

Namespace:
namespaces provide a mechanism for isolating groups of resources within a single cluster. Names of resources need to be unique within a namespace, but not across namespaces. Namespace-based scoping is applicable only for namespaced objects (e.g. Deployments, Services, etc.)
