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
