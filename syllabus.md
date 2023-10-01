## DevOps Syllabus ##

## Introduction to DevOps ##

- Let’s Understand about Software Development Model
- Overview of Waterfall Development Model
- What is DevOps?
- Waterfall -> Agile -> CI/CD -> DevOps -> DevSecOps
- What is DevSecOps, SRE?
- Microservices Fundamentals
- API Fundamental
- Tools used in DevOps
- Essentials of Cloud Computing
- Cloud Providers
- containerization vs virtualization

## Platform - OS

- Different between Linux and Unix, Windows OS
- Different flavors of Unix, Linux
- Basic commands
- Managing users, groups and permissions
- Filter commands
- start/stop services, installing packages using RPM/YUM
- Find/kill process, vi editor shortcuts

## GIT

- About Version Control System and Types
- Difference between CVCS and DVCS
- GIT Basics
- GIT command line
- installation of GIT- windows and Linux
- Initial setup
- GIT Essentials
- Clone, check-in and commiting
- Fetch, pull and remote
- Branching
- Creating the Branches, switching the branches, merging the branches
- Merge/Rebase

## MAVEN

- Build tool - maven
- Build lifecycle
- introduction of POM.xml

## Cloud - AWS 

- Creating AWS account
- Understanding AWS Regions and availability zones
- EC2 ( Elastic Cloud Comput)
- About EC2 and types , Pricing
- Launch Linux Instances, connecting to
  
  ***To be continue ....***

## Introduction to CI/CD 

- Understanding continuous integration
- Introduction about Jenkins
- Jenkins Architecture
- Installation
- Exploring Jenkins Dashboard
- Different types of Job
- Adding plugins
- Build triggers
- Security In Jenkins
- Pipeline - Declarative vs Scripted
- Master/Slave configuration
- Shared library

## Project - Deploy sample applicaction on Tomcat using Jenkins, Maven, Git 

## Artifact Repository 

- About Nexus
- Integration with Jenkins

## project : Build Sample application and upload to Nexus - deploy on tomcat

## Docker - Containers 

- Introuction
- What is a Docker
- Use case of Docker
- Platforms for Docker
- Dockers vs. Virtualization
- Architecture
- Docker Architecture.
- Understanding the Docker components
- Installing Docker on Linux
- Some Docker commands
- Docker Hub
- Downloading Docker images.
- Uploading the images in Docker Registry and AWS ECS
- Understanding the containers
- Running commands in container.
- Running multiple containers.
- Custom images
- Running a container from the custom image
- Publishing the custom image
- Docker Networking
- Exposing container ports
- Docker Compose
- Multistage container
- Build word press site using Docker compose

## Project : Build Sample application, containarize it and upload it Image on DockerHub 

## Cloud - AWS 

## Ansible

**Ansible - Introduction, features, Architecture**

- Introduction To Ansible
- Features Of Ansible
- Use Cases Of Ansible
- What Can Do In Production Environment
- Ansible Documentation
- How Ansible Is Different From Configuration Management Tools
- Ansible Architecture
  
**Ansible - Workflow, Terminologies, Installation** 

- Ansible Workflow
- Ansible Terminologies
- Ansible Lab-setup
- Ansible Control Machine Requirements
- Ansible Control Machine on RHEL
- Verify Ansible installation and version
- Verify Ansible Playbook version
- Locate Ansible configuration file

**Ansible-Yaml, Inventory, Groups** 

- Representation Of Dictionary In Yaml
- Non-group Inventory File
- Group Inventory File
- Ansible Inventory Parameters
- Use Case Of - Ansible_host
- Use Case Of - Ansible_port
- Use Case Of - Ansible_connection
- Use Case Of - Ansible_user
- Use Case Of - Ansible_ssh_pass
- Use Case Of - Ansible_password
- Ansible Exercise - To Setup Inventory File And Perform Ping Test
- Case Study On Ping Test Error Message :
- Ansible Inventory Exercise 1- Create A Inventory File
- Ansible Inventory Exercise 2 : To Create A Group
- Ansible Inventory Exercise 3 : To Create Nested Groups (Parent_group)

**Ansible- Modules, Ad Hoc, Playbooks** 

- Ansible Playbooks
- Sample Ansible Playbook
- Ansible Playbook Format
- Ansible Modules
- Ansible Tasks
- How To Run A Playbooks
- How to check syntax of a Playbook
- How to Run a playbook on multiple hosts
- How to Run a playbook on target hosts
- Ansible Run Command Methods
- Ansible Playbook Exercise 1: Perform Ping Test On All Hosts Of Inventory File
- Ansible Playbook Exercise 2: To Install Git On All Hosts using script module
- Ansible Playbook Exercise 3: To Install A Web Server httpd using yum module
- Ansible Playbook Exercise 4: To start a httpd service using service module
- References On Playbook And Modules

**Ansible - Variables, Conditions, Loops, Roles, Galaxy** 

- Ansible Variables
- How To Define A Variable In Ansible Playbook
- Ansible Variable Exercise
- Ansible Conditions
- Ansible Loops
- Ansible Vaults
- How To Limit The Execute Of Ansible On Single Hosts Or Desired Hosts
- How To Check Ansible Playbook Syntax
- Ansible Roles
- Use Case Of Roles
- Ansible Include Statement
- Ansible Patterns
- Use Case Of Patterns
- Ansible vault

## Kubernetes 

**Introduction to Kubernetes**

- Understanding Containerization and Orchestration
- Kubernetes Overview and Architecture
- Installation Methods (Minikube, kubeadm, cloud-managed clusters)
- Basic Cluster Management (kubectl, kubeconfig)

**Kubernetes Pods and Containers**

- Pod Networking and Storage
- Container Lifecycles
- Creating and Managing Pods
- Deployments vs. ReplicaSets
- Scaling Applications
- Rolling Updates and Rollbacks
- Strategies for High Availability

**Services and Networking**

- Service Types (ClusterIP, NodePort, LoadBalancer)
- Ingress Controllers
- DNS in Kubernetes
- Network Policies for Security

**Configuration and Secrets Management**

- ConfigMaps and Secrets
- Environment Variables and Configurations
- Managing Sensitive Data
- Helm: Kubernetes Package Manager
  
**Persistent Storage**

- Persistent Volumes (PVs) and Persistent Volume Claims (PVCs)
- Storage Classes
- StatefulSets for Stateful Applications
- Data Backup and Recovery

**Kubernetes Security**

- Securing the Kubernetes API
- RBAC (Role-Based Access Control)
- Pod Security Policies
- Image Scanning and Security Best Practices

**Advanced Topics**

- Custom Resource Definitions (CRDs)
- Operators for Automating Operations
- Multi-Cluster Management
- Cost Optimization and Resource Efficiency



## Monitoring - Prometheus and Grafana
