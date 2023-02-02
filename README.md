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
    
    
# Kubernetes Project : 
# Project - Automated CI/CD Pipeline for Django and React Application.
# Project Description - 
  Build Kubernetes Cluster on AWS from Scratch with Minukube , Setup and Managed Docker Containers for Django and React Application into Kubernetes Pods, Managed Deployment, Replication, Auto Healing, Auto Scaling for Kubernetes Cluster, Managed network and Services with Host IP allocation through Proxy on AWS EC2 and Route53.
  
 # Step 1 :   Build Kubernetes Cluster on AWS from Scratch with Minukube
 -  Head to AWS EC2
 -  Launch an Instance and Create a Server Name 
    ```
    'Create a Server Name of your wish' I have used 'kubernetes-tut' as a server name 
    ```
 -  Select the Applications and OS Images(Amazon Machine Image). Take any OS which you prefer. I have used 'ubuntu'
    
 -   Now change the instance type to t2.medium coz we require 2 CPU for the processing.(This is not included in Free Tier)
    
 - Then add a Key Pair 
    ```
    TWS-Key
    ```
  - Finally, Click on Create Instance 

  - Select the instance and Click on Connect 
  - Copy the SSH Client
  - Head to your Terminal and type Sudo and Paste the Link 
  - Instal Docker 
  ```
  https://docs.docker.com/get-docker/
  ```
  - Install Minukube
 ```
 https://minikube.sigs.k8s.io/docs/start/
 ```
 - After installing type --> sudo usermod -aG docker $USER && newgrp docker 
 - Then type -->  minikube start --driver=docker 
 - Now to communicate with the master and the node you need to install the kubctl tool 
 ```
 sudo snap install kubectl
 ```
 
