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

- Kubernetes is an open-source container management tool that automates container deployment, scaling & load balancing.
- It schedules, runs, and manages isolated containers that are running on virtual/physical/cloud machines.
- All top cloud providers support Kubernetes.
- One popular name for Kubernetes is K8s.

**⬤ History**

- Google developed an internal system called ‘borg’ (later named Omega) to deploy and manage thousands of google applications and services on their cluster.
- In 2014, google introduced Kubernetes an open-source platform written in ‘Golang’ and later donated to CNCF (Cloud Native Computing Foundation).

**⬤ Online platform for K8s**

- Kubernetes playground
- play with K8s
- Play with Kubernetes classroom

**⬤ Cloud-based K8s services**

- GKE [Google Kubernetes Engine]
- AKS [Azure Kubernetes Service]
- Amazon EKS [Amazon Elastic Kubernetes Service]

**⬤ Features of Kubernetes**

- Orchestration (clustering of any number of containers running on a different network).
- Autoscaling (Vertical & Horizontal)
- Auto Healing
- Load Balancing
- Platform Independent (Cloud/Virtual/Physical)
- Fault Tolerance (Node/POD/Failure)
- Rollback (Going back to the previous version)
- Health monitoring of containers
- Batch Execution (One time, Sequential, Parallel)
**Working with Kubernetes**

- We create a Manifest (.yml) file
- Apply those to cluster (to master) to bring it into the desired state.
- POD runs on a node, which is controlled by the master.

**⬤ Role of Master Node**

- Kubernetes cluster contains containers running or Bare Metal / VM instances/cloud instances/ all mix.
- Kubernetes designates one or more of these as masters and all others as workers.
- The master is now going to run a set of K8s processes. These processes will ensure the smooth functioning of the cluster. These processes are called the ‘Control Plane.
- Can be Multi-Master for high availability.
- Master runs control plane to run cluster smoothly.

**⬤ Components of Control Plane**

**◼ Kube-api-server → (For all communications)**

- This api-server interacts directly with the user (i.e we apply .yml or .json manifest to kube-api-server)
- This kube-api-server is meant to scale automatically as per load.
- Kube-api-server is the front end of the control plane.

**◼ etcd**

- Stores metadata and status of the cluster.
- etcd is a consistent and high-available store (key-value-store)
- Source of touch for cluster state (info about the state of the cluster)

***→ etcd has the following features***

1. Fully Replicated → The entire state is available on every node in the cluster.
2. Secure → Implements automatic TLS with optional client-certificate authentication.
3. Fast → Benchmarked at 10,000 writes per second.

**◼ Kube-schedular (action)**

- When users request the creation & management of Pods, Kube-scheduler is going to take action on these requests.
- Handles POD creation and Management.
- Kube-scheduler match/assign any node to create and run pods.
- A scheduler watches for newly created pods that have no node assigned. For every pod that the scheduler discovers, the scheduler becomes responsible for finding the best node for that pod to run.
- The scheduler gets the information for hardware configuration from configuration files and schedules the Pods on nodes accordingly.

**◼ Controller-Manager**

- Make sure the actual state of the cluster matches the desired state.

→ Two possible choices for controller manager —

1. If K8s is on the cloud, then it will be a cloud controller manager.
2. If K8s is on non-cloud, then it will be kube-controller-manager.

**◼ Components on the master that runs the controller**

**Node Controller →** For checking the cloud provider to determine if a node has been detected in the cloud after it stops responding.

**Route-Controller →** Responsible for setting up a network, and routes on your cloud.

**Service-Controller →** Responsible for load Balancers on your cloud against services of type Load Balancer.

**Volume-Controller →** For creating, attaching, and mounting volumes and interacting with the cloud provider to orchestrate volume.

**◼ Nodes (Kubelet and Container Engine)**

- Node is going to run 3 important pieces of software/process.

**Kubelet**

- The agent running on the node.
- Listens to Kubernetes master (eg- Pod creation request).
- Use port 10255.
- Send success/Fail reports to master.

**Container Engine**

- Works with kubelet
- Pulling images
- Start/Stop Containers
- Exposing containers on ports specified in the manifest.

**Kube-Proxy**

- Assign IP to each pod.
- It is required to assign IP addresses to Pods (dynamic)
- Kube-proxy runs on each node & this makes sure that each pod will get its unique IP Address.
- These 3 components collectively consist of ‘node’.

---

**⬤ POD**

- The smallest unit in Kubernetes.
- POD is a group of one or more containers that are deployed together on the same host.
- A cluster is a group of nodes.
- A cluster has at least one worker node and a master node.
- In Kubernetes, the control unit is the POD, not the containers.
- Consist of one or more tightly coupled containers.
- POD runs on a node, which is controlled by the master.
- Kubernetes only knows about PODs (Does not know about individual containers).
- Cannot start containers without a POD.
- One POD usually contains One Container.

◼ Multi Container PODs →

- Share access to memory space.
- Connect using Localhost <Container-Port>
- Share access to the Same Volume.
- Containers within POD are deployed in an all-or-nothing manner.
- The entire POD is hosted on the same node (Scheduler will decide which node).
- There is no auto-healing or scaling by default.

**⬤ Higher-level Kubernetes Objects**

- **Replication Set →** Auto scaling and auto-healing.
- **Deployment →** Versioning and Rollback.
- **Service →** Static (Non-ephemeral) IP and Networking.
- **Volume →** Non-ephemeral storage [Ephemeral → Storage outside the node]
    
    [Kubernetes Documentation](https://kubernetes.io/docs/home/)
    
    
# Kubernetes Project : 
# Project - Automated CI/CD Pipeline for Django and React Application.
# Project Description - 
  Build Kubernetes Cluster on AWS from Scratch with Minikube ; Setup and Managed Docker Containers for Django and React Application into Kubernetes Pods, Managed Deployment, Replication, Auto Healing, Auto Scaling for Kubernetes Cluster; Managed network and Services with Host IP allocation.
  
 # Step 1 :   Build Kubernetes Cluster on AWS from Scratch with Minikube
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
 
 # Step 2 : Setup and Managed Docker Containers for Django and React Application into Kubernetes Pods
 
 - Create a SSH for the instance which you have created in Amazon EC2
 - Clone the django todo app
 ```
    git clone 
 ```
 - Go to the docker file directory and then type 
 ```
 docker build -t <dockerhub_id>/<image_name>:latest
 ```
 - Now create a container of the image which you have just created
 ```
 docker run -d -p 8000:8000 <dockerhub_id>/<image_name>:latest
 
 ```
 Here you are doing "port-binding" put the 'exposed' port number
 
 - To check it is working or not. Copy the IP address from Amaxon EC2, and type the command :
 ```
 curl -L http://<ip_address>
 ```
 
 - Now, we will create a Kubernetes Pods : 
 - Now we will create a new folder. I have used k8s

 ```
 mkdir k8s
 ```
 ```
 cd k8s/
 ```
 ```
 ls
 ```
 - Now we will write a pod file.
 - Generally when we create file we pull image form Docker Hub. 
 
 ```
 docker push <dockerhub_id>/<image_name>
 ```
 - Here your created image went to DockerHub and when the kubernetes pod will be created it will get automatically gets pulled. 
 - Creating Pod
 ```
 vim pod.yaml 
 ```
 
-- Then copy this file and do necessary changes. 

```
apiVersion: v1

kind: Pod

metadata:

  name: <give a name as you like>

spec:

  containers:

  - name: <container name as you like>

    image: <dockerhub_id>/<image_name>:latest

    ports:

    - containerPort: 8000


 (esc :wq to exit)
 
 ```
 - Now kill the ports after writing 'docker ps' from the SSH Terminal 
 ```
 docker kill <FIRST_PORTS_NAME_AFTER_RUNNING_ABOVE_COMMAND>
```
- Command to create the pod 
```
kubectl apply -f pod.yaml
```
- Congrats Step 2 Done

# Step 3 : Managed Deployment, Replication, Auto Healing, Auto Scaling for Kubernetes Cluster.

- Create a deployment deployment.yaml 

- Now copy the piece of code to the deployment.yaml

```
apiVersion: apps/v1

kind: Deployment

metadata:

  name: todo-deployment

  labels:

    app: todo-app

spec:

  replicas: 3

  selector:

    matchLabels:

      app: todo-app 

  template:

    metadata:

      labels:

        app: todo-app 

    spec:

      containers:

      - name: todo-app 

        image: <imagename>

        ports:

        - containerPort: 8000
```
- After saving the file 

```
kubectl apply -f deployment.yaml 
```
- To check everying is working fine or not
```
kubectl get deployments
```
- Now you will see the replicas and no of replicals is equal to number of pods 
- No of replicas is there for the Auto-Scaling Process 
- To see pods
```
kubectl get pods 
```
- Now to delete pods
```
kubectl delete pods <pod_name>
```
- Now try to delete any deployment pod, and recheck to see. Here you able to see the deployment pod once again as this process is Auto-Healing. 

# Managed network and Services with Host IP allocation.

- To do this you face a problem follow to this steps to understand:

- Command : To see IP 
```
kubectl get pods -o wide
```
```
curl -L http://<IP>
```
- But here you will not able to see the pod because there is no route. This pod is running inside Minikube Kubernetes Cluster
- Now you need a service.yaml file to Managed network and Services.
```
vim service.yaml
```
```
apiVersion: v1
kind: Service
metadata:
  name: todo-service
spec:
  type: NodePort
  selector:
    app: todo-app
  ports:
      # By default and for convenience, the `targetPort` is set to the same value as the `port` field.
    - port: 80
      targetPort: 8000
      # Optional field
      # By default and for convenience, the Kubernetes control plane will allocate a port from a range (default: 30000-32767)
      nodePort: 30005
      
 ```
 
 - Now you need to apply the file. 
 ```
 kubectl apply -f service.yaml
 ```
 - To check 
 ```
 kubectl get svc
 ```
    
 - You will not get the external IP therefore need to go to the minikube service 
 
 ```
 minikube service todo-service --url 
 ```
    
 - Now
 ```
 curl -L <http_link>
 ```
 - Now we will give the IP name 
 - Here we will get all the IPs
 ```
 sudo vim /etc/hosts 
 ```
 - Now enter the previous IP which you want to customize
 - Now bind xxx.xxx.xx.x <any name.com>
 -NOW
 ```
 curl -L <any name.com>:30005
 ```
 
 #Achievement 
 - Reduce Downtime by 75% on Production Environments. 
 - Coz, If you delete the pod also, It will be Up Again. Therefore you have reduced downtime. 25% were being kept for scheduled maintainance in website down. 
 
 -Congratulation🥳🥳🥳 and  Happy Coding🪷👩‍💻🧑‍💻!!!
 
 
