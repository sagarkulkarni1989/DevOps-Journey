# Deploy Microservices into EKS cluster using Helm and Jenkins Pipeline #
We are going to learn how to automate build and deployment of Springboot Microservices Docker Container into Elastic Kubernetes Cluster(EKS) using Helm and Jenkins pipeline.

**Pre-requisite**
 - AWS account
 - Ubunu Instance - 20.04, default VPC,subnet, keypair , security group- create new with all traffic(not recommended in best practice), RAM - 25GB
 - Install Jenkins
 - Git Code - https://github.com/sagarkulkarni1989/docker-spring-boot.git

##Installation steps :## 

 **- AWS CLI**
```
curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip" 
sudo apt install unzip
sudo unzip awscliv2.zip  
sudo ./aws/install
aws --version
```

**- Helm**
```
curl -fsSL -o get_helm.sh https://raw.githubusercontent.com/helm/helm/master/scripts/get-helm-3
sudo chmod 700 get_helm.sh
sudo ./get_helm.sh
helm version --client
```
**- kubectl**
```
curl -s https://packages.cloud.google.com/apt/doc/apt-key.gpg | sudo apt-key add -
sudo touch /etc/apt/sources.list.d/kubernetes.list
echo "deb http://apt.kubernetes.io/ kubernetes-xenial main" | sudo tee -a /etc/apt/sources.list.d/kubernetes.list
sudo apt-get update
sudo apt-get install -y kubectl
kubectl version --client
```
**- eksctl**
```
curl --silent --location "https://github.com/weaveworks/eksctl/releases/latest/download/eksctl_$(uname -s)_amd64.tar.gz" | tar xz -C /tmp
sudo mv /tmp/eksctl /usr/local/bin
eksctl version
```
**-Docker**
```
sudo apt install docker.io -y
sudo systemctl start docker
sudo systemctl enable docker
sudo systemctl status docker
```
**- Jenkins and Jenkins have proper permission to perform Docker builds**

```
Now Login to Jenkins EC2 instance, execute below commands:
Download Jenkins plugins for docker and docker pipeline

Add jenkins user to Docker group
sudo usermod -a -G docker jenkins

Restart Jenkins service
sudo service jenkins restart

Reload system daemon files
sudo systemctl daemon-reload

Restart Docker service as well

sudo service docker stop
sudo service docker start
```

**Create ECR repo in AWS**
```
GO to AWS console nd search for ECR
click on create repository
Entername for your repo- all lower case and click reate repository 
Note the URL from step # 3 below, this will be used for tagging and pushing docker images into ECR.
```
**Create Maven3 variable under Global tool configuration in Jenkins**

Make sure you create Maven3 variable under Global tool configuration. 

![maven3](https://github.com/sagarkulkarni1989/DevOps-Journey/assets/46215433/6fc734df-0518-4436-ae57-04699d3fe91e)


**- EKS Cluster setup**
- Create a IAM Role with Administrator Access
  
    - Go to AWS Console -IAM - Roles - create role -select EC2 server and click on Next Permissions
    - Now search for AdministratorAccess policy and click
- Assign the role to EC2 instance
    - Go to AWS console, click on EC2, select EC2 instance, Choose Security. Click on Modify IAM Role
    - Choose the role you have created from the dropdown. Select the role and click on Apply.
- Switch to Jenkins user :  sudo su - jenkins
- Create EKS Cluster with two worker nodes using eksctl
  ```
  eksctl create cluster --name demo-eks --region us-east-1 --nodegroup-name my-nodes --node-type t3.small --managed --nodes 2        #change region name as per your requirement
  ```

  - the above command should create a EKS cluster in AWS, it might take 15 to 20 mins. The eksctl tool uses CloudFormation under the hood, creating one stack for the EKS master control plane and another stack for the worker nodes.
  - kubeconfig file be updated under /var/lib/jenkins/.kube folder. cat  /var/lib/jenkins/.kube/config
  - Connect to EKS cluster using kubectl commands
  - To view the list of worker nodes as part of EKS cluster.  :  kubectl get nodes

**Steps**
- Clone git repository : git clone https://github.com/sagarkulkarni1989/docker-spring-boot.git
- Create Helm chart using helm command Go to your root of repo where you have source code for your springboot application. Create helm chart by executing below command:
```
helm create mychart
tree mychart
```
- Add Docker image details to download from ECR before deploying to EKS cluster
open mychart/values.yaml.

![Screenshot 2023-05-13 at 4 21 27 PM](https://github.com/sagarkulkarni1989/DevOps-Journey/assets/46215433/05ea4d27-a72b-4224-aba6-08c96d0d6abf)

- Enter service type as LoadBalancer And also open mychart/templates/deployment.yaml and change containerPort to 8080

  ![Screenshot 2023-04-30 at 12 06 47 AM](https://github.com/sagarkulkarni1989/DevOps-Journey/assets/46215433/74c16706-bb56-40d1-94a7-9dad71f707b4)

- Save the files, commit and push into repo
- Create a namespace in EKS : kubectl create ns helm-deployment
- Create a pipeline in Jenkins



  
