# Deploy Microservices into EKS cluster using Helm and Jenkins Pipeline #
We are going to learn how to automate build and deployment of Springboot Microservices Docker Container into Elastic Kubernetes Cluster(EKS) using Helm and Jenkins pipeline.

**Pre-requisite**
 - AWS account
 - Ubunu Instance - 20.04, default VPC,subnet, keypair , security group- create new with all traffic(not recommended in best practice), RAM - 25GB
 - Install Jenkins

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

**- EKS Cluster setup**
- Create a IAM Role with Administrator Access
  
    - Go to AWS Console -IAM - Roles - create role -select EC2 server and click on Next Permissions
    - Now search for AdministratorAccess policy and click
- Assign the role to EC2 instance
    - Go to AWS console, click on EC2, select EC2 instance, Choose Security. Click on Modify IAM Role
    - Choose the role you have created from the dropdown. Select the role and click on Apply.
