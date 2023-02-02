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
    
    ![image](https://user-images.githubusercontent.com/66848339/216410744-7014a844-fbc0-4e6c-928a-bed694893667.png)
    
    ![image](https://user-images.githubusercontent.com/66848339/216410817-e0ad9ad3-08c5-4d3b-93a6-fbc66ebbcec9.png)

    
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
    
    [Kubernetes Documentation](https://kubernetes.io/docs/home/)
