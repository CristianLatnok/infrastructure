# Kubernetes Local Cluster Setup 

## Overview

This project demonstrates the setup of a local Kubernetes cluster with the following services:

1. Three pods with a proxy allowing internet access, accessible only through a load balancer with authentication.
2. A load balancer pod with authentication for HTTP and HTTPS traffic.
3. A client pod making requests to different websites through the load balancer.
4. A monitoring pod to track the resources used by other pods.

## Prerequisites

- [Docker](https://www.docker.com/get-started)
- [kubectl](https://kubernetes.io/docs/tasks/tools/install-kubectl/)
- [Minikube](https://minikube.sigs.k8s.io/docs/start/)

## Setup Instructions

1. Clone this repository:

    ```bash
    git clone <repository-url>
    cd <repository-directory>
    ```

2. Start Minikube cluster:

    ```bash
    minikube start
    ```

3. Deploy the Kubernetes manifests:

    ```bash
    kubectl apply -f manifests/
    ```

4. Verify the deployment:

    ```bash
    kubectl get pods
    ```

## Usage

1. Access the load balancer service:

    ```bash
    minikube service load-balancer-service
    ```

    This will open the load balancer service in your default browser.

2. Make requests from the client pod:

    ```bash
    kubectl exec -it client-pod -- /bin/sh
    ```

    Inside the pod, use tools like `curl` or `wget` to make requests to other services:

    ```bash
    curl http://load-balancer-service
    ```

## Cleaning Up

To clean up the resources created by this project, run:

```bash
kubectl delete -f manifests/
minikube stop
minikube delete
