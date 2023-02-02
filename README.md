# Learn_Kubernetes_with_Project
In this repository you are going to learn about Kubernetes :- What is Kubernetes? ,Why do we use Kubernetes?, Architecture,Node vs Pod,Setup,&amp; Kubernetes Notes in Detail and a Job Ready Project !!!!!  

# Kubernetes

- What is Kubernetes?
    
    Open source Container Orchestration tool By Google used to Multi Environment, Multi Container Deployment 
    
- Why do we use Kubernetes?
    
    For production ready deployment of Micro-services and small apps
    
    Having less failures and Downtimes
    
    Backups and restores
    
- Architecture
    
    
    ![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/26cb95e0-2fbe-4010-b145-f145fc249ef4/Untitled.png)
    
    ![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/877b5694-9a17-4c6f-9784-86de123bea97/Untitled.png)
    
- Node vs Pod
    
    Node is a server or virtual Machine
    
    Pod is the smallest unit in Kubernetes which gives an abstraction over docker container
    
- Setup
    
    Need to visit [https://minikube.sigs.k8s.io/docs/start/](https://minikube.sigs.k8s.io/docs/start/)
    
    curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64
    
    sudo install minikube-linux-amd64 /usr/local/bin/minikube
    
    Install docker
    
    docker system prune
    
    minikube delete
    
    minikube start --driver=docker
    
    sudo usermod -aG docker $USER && newgrp docker
    
    kubectl get po -A
    sudo snap install kubectl
    sudo snap install kubectl --classic
    kubectl get po -A
    minikube status
    kubectl get node
    
- Kubernetes Notes in Detail
    
    [Kubernetes in Detail](https://www.notion.so/Kubernetes-in-Detail-cacca2743a8d497bbfed811fc95fac9e)
