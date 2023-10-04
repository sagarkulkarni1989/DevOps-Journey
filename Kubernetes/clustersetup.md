## Cluster Setup 

**Pre-requesite**
- ubuntu - t2.medium , 15GB RAM Default VPC, security group - all traffic 

## Minikube

Minikube is a lightweight Kubernetes implementation that creates a VM on your local machine and deploys a simple cluster containing only one node. Minikube is available for Linux, macOS, and Windows systems

**Docker Installation**

```
sudo apt update -y
sudo apt upgrade -y
sudo reboot
sudo apt install apt-transport-https ca-certificates curl software-properties-common
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu focal stable"
apt-cache policy docker-ce
sudo apt install docker-ce
sudo systemctl status docker

```
**Minikube instalation steps** 

```
sudo apt install -y curl wget apt-transport-https
curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64
sudo install minikube-linux-amd64 /usr/local/bin/minikube
minikube version
curl -LO https://storage.googleapis.com/kubernetes-release/release/`curl -s https://storage.googleapis.com/kubernetes-release/release/stable.txt`/bin/linux/amd64/kubectl
chmod +x kubectl
sudo mv kubectl /usr/local/bin
kubectl version -o yaml
minikube start --driver=docker --force
In case you want to start minikube with customize resources and want installer to automatically select the driver then you can run following command,
minikube start --addons=ingress --cpus=2 --cni=flannel --install-addons=true --kubernetes-version=stable --memory=6g
minikube status
kubectl cluster-info
kubectl get nodes

```

**KOPS**

kOps, also known as Kubernetes operations, is an open-source project which helps you create, destroy, upgrade, and maintain a highly available, production-grade Kubernetes cluster. Depending on the requirement, kOps can also provision cloud infrastructure. kOps is mostly used in deploying AWS and GCE Kubernetes clusters. But officially, the tool only supports AWS.

Benefits of kOps

- Supports rolling cluster updates
- Manages cluster add-ons
- Supports state-sync model for dry-runs and automatic idempotency
  

```
curl -LO https://github.com/kubernetes/kops/releases/download/$(curl -s https://api.github.com/repos/kubernetes/kops/releases/latest | grep tag_name | cut -d '"' -f 4)/kops-linux-amd64
sudo chmod +x kops-linux-amd64
mv kops-linux-amd64 /usr/local/bin/kops
sudo curl -LO https://storage.googleapis.com/kubernetes-release/release/$(curl -s https://storage.googleapis.com/kubernetes-release/release/stable.txt)/bin/linux/amd64/kubectl
chmod +x kubectl
sudo mv kubectl /usr/local/bin
kubectl version -o yaml
sudo apt-get update
sudo apt-get install python3-pip
apt install awscli
```
Create a new AWS User 

```
aws configure
access key
secret key
region
```

Create a new S3 bucket : kops-statets
Generate SSH Key
ssh-keygen

Create Cluster 
For Non DNS Base Cluster, work with .k8s.local

```
kops create cluster --yes --state=s3://kops-statets --zones=ap-south-1a,ap-south-1b --node-count=2 --node-size=t2.micro --master-size=t2.micro --name=test.k8s.local
kubectl get nodes --show-labels
kops validate cluster --state=s3://S3-bucket-name
kops delete cluster --state=s3://kops-statets --name=test.k8s.local --yes
```

## Kind 

Kind is an open-source tool for running a Kubernetes cluster locally, using Docker containers as cluster nodes.While its primary purpose is enabling users to test Kubernetes on a single machine, developers also use Kind for local development and Continuous Integration (CI).

```
apt-get update
apt install docker.io -y
curl -s https://packages.cloud.google.com/apt/doc/apt-key.gpg | sudo apt-key add -
echo "deb https://apt.kubernetes.io/ kubernetes-xenial main" | sudo tee -a /etc/apt/sources.list.d/kubernetes.list
sudo apt-get update
sudo apt-get install -y kubectl
curl -Lo ./kind https://kind.sigs.k8s.io/dl/v0.11.1/kind-linux-amd64
chmod +x ./kind
mv ./kind /usr/local/bin/kind
kind version
kind create cluster
docker ps
kind get clusters
kubectl get nodes
kubectl cluster-info --context kind-kind
Delete cluster : kind delete cluster
```

## EKS cluster setup using eksctl

Amazon EKS is a fully managed container orchestration service. EKS allows you to quickly deploy a production ready Kubernetes cluster in AWS, deploy and manage containerized applications more easily with a fully managed Kubernetes service.
EKS takes care of master node/control plane. We need to create worker nodes.

EKS cluster can be created in following ways:

1. AWS console
2. AWS CLI
3. eksctl command
4. using Terraform

We will create EKS cluster using eksctl command line tool.

**Pre-requisites:**

- Install AWS CLI : Command line tools for working with AWS services, including Amazon EKS.

```
curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"
sudo apt install unzip
sudo unzip awscliv2.zip
sudo ./aws/install
aws --version
```
- Install eksctl – A command line tool for working with EKS clusters that automates many individual tasks.

```
curl --silent --location "https://github.com/weaveworks/eksctl/releases/latest/download/eksctl_$(uname -s)_amd64.tar.gz" | tar xz -C /tmp
sudo mv /tmp/eksctl /usr/local/bin/
eksctl version
```

- Install kubectl  – A command line tool for working with Kubernetes clusters.

```
sudo curl --silent --location -o /usr/local/bin/kubectl   https://s3.us-west-2.amazonaws.com/amazon-eks/1.22.6/2022-03-09/bin/linux/amd64/kubectl
sudo chmod +x /usr/local/bin/kubectl
kubectl version --short --client
```

- Create IAM Role with Administrator Access : ou need to create an IAM role with AdministratorAccess policy.
Go to AWS console, IAM, click on Roles. create a role

- Select AWS services, Click EC2, Click on Next permissions.
- Now search for AdministratorAccess policy and click
- Now give a role name and create it.
- Assign the role to EC2 instance
- Go to AWS console, click on EC2, select EC2 instance, Choose Security. Click on Modify IAM Role
- create new user : adduser jenkins
- Switch to Jenkins user : sudo su - jenkins
- Create EKS Cluster with two worker nodes using eksctl

```
eksctl create cluster --name demo-eks --region ap-south-1 --nodegroup-name my-nodes --node-type t3.small --managed --nodes 2     # change region based on your requirement
```
- the above command should create a EKS cluster in AWS, it might take 15 to 20 mins. The eksctl tool uses CloudFormation under the hood, creating one stack for the EKS master control plane and another stack for the worker nodes.
- eksctl get cluster --name demo-eks --region ap-south-1
- This should confirm that EKS cluster is up and running.
- Connect to EKS cluster using kubectl commands kubectl get nodes , kubectl get ns
- Deploy Nginx on a Kubernetes Cluster  : kubectl create deployment nginx --image=nginx
- View Deployments  : kubectl get deployments
- Delete EKS Cluster using eksctl :  eksctl delete cluster --name demo-eks --region us-east-1    #delete cluster after your practical
