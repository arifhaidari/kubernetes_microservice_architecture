# Kubernetes Microservice Architecture (Under Development)

content of the project:

Use Helm for managing Kubernetes applications
Deploy a sample application to a Kubernetes cluster
Extend Kubernetes with custom resources and controllers
Deploy auxiliary tools like Trivy Operator for security and CloudNativePG for database management
Enhance developer experience with tools like Tilt and External Secrets Operator
Debug and troubleshoot Kubernetes applications
Manage deployments across multiple environments using Kustomize, Helm, Kluctl and other tools
Implement a CI/CD pipeline for Kubernetes

for the purpose of demo:
I will use React in the front end. I will use API (Go & Node.js), Python load generator and PostgreSQL database.

Tools to use:

- Docker
- DevBox - it is a wrapper around a technology called Nix. Nix is a package manager and it allows you to use different tools and create a reproducible installation. DevBox will help you create an isolated environment.

install the Devbox:
curl -fsSL https://get.jetify.com/devbox | bash

then I create a devbox.json file and in this json file packages are a bunch of CLI tools.
then I created a devbox.lock and it contains the specific version of the packages and mange the compatibility between the packages
devbox shell in the terminal install everything and pull it out from the package manager
devbox list in terminal list out everything

one of the dependency is go-task - this a task runner program that will store all the commands.
Go-Task is a very simple library that allows you to write simple “task” scripts in Go and run.

KinD:
kind is a tool for running local Kubernetes clusters using Docker container “nodes”. kind was primarily designed for testing Kubernetes itself, but may be used for local development or CI

---

Credit:
a lot of material and approaches are inspired from different sources such as Stackoverflow (stackexchange), Medium, Github, tutorials and also ChatGPT.
