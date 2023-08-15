# Jenkins Master Slave architecture #

Jenkins has powerful feature of master slave architecture which enables distributed builds. This article we will learn how to establish slave nodes on Ubuntu machines and integrate with Jenkins Master.

different ways to configure the Master-Slave setup in Jenkins
  - Permanent Agent (JNLP Slave)
    
    This is the traditional method of setting up Jenkins slaves. Agents are launched via Java Web Start (JNLP) from the Jenkins master. They establish a connection to the master, which allows the master to send build jobs to them.
   -  SSH Agent
     
In this configuration, Jenkins slaves connect to the master using SSH. SSH agents provide a more secure way of communication compared to JNLP slaves, as the connection is encrypted. SSH agents are useful when there 
  is a need for enhanced security and the ability to work across different networks.
    


![MAster slave](https://github.com/sagarkulkarni1989/DevOps-Journey/assets/46215433/542f5857-d2dd-4132-948d-9688e035e969)

**Jenkins Master**

Your main Jenkins server is the Master. The Master’s job is to handle:
 - Scheduling build jobs.
 - Dispatching builds to the slaves for the actual execution.
 - Monitor the slaves (possibly taking them online and offline as required).
 - A Master instance of Jenkins can also execute build jobs directly.

**Jenkins Slave**

A Slave is a Java executable that runs on a remote machine. Following are the characteristics of Jenkins Slaves:
 - It hears requests from the Jenkins Master instance.
 - Slaves can run on a variety of operating systems.
 - The job of a Slave is to do as they are told to, which involves executing build jobs dispatched by the Master.
 - You can configure a project to always run on a particular Slave machine, or a particular type of Slave machine, or simply let Jenkins pick the next available Slave.

**LAB Setup**

**Pre-requisite**

- Launch three EC2 Instances - Jenkins master, Slave1, Slave2 and ocker Host(For docker host you can create new VM or use existing)
- AMI - Ubuntu 20.04 , Instance type - t2.micro , Generate new keypair
- Network Settings - default VPC, Security group - Create new with inbound rules - OPen all traffic (Not recommented in best practice but its only for practical purpose)
- Configure storage - 15GB and Launch

**Procedure** 

* Install Java on all the Machines

  ```
  sudo su -
  sudo apt update
  sudo apt install openjdk-11-jdk
  java --version
  
  ```
* Install Jenkins on master Machine

  ```
  wget -p -O - https://pkg.jenkins.io/debian/jenkins.io.key | sudo apt-key add –
  sudo sh -c 'echo deb http://pkg.jenkins.io/debian-stable binary/ > /etc/apt/sources.list.d/jenkins.list'
  sudo apt update
  sudo apt install Jenkins
  sudo systemctl start Jenkins
  sudo systemctl status Jenkins
  Access Jenkins from Browser : http://your_server_ip_or_domain:8080
  
  
  ```
  
**Slave1 Node Configuration Launch Method - SSH Agent**

Maven Install

```
sudo apt install maven -y
```

Create User as Jenkins

```
sudo useradd -m jenkins
sudo -u jenkins mkdir /home/jenkins/.ssh
```
**Now Login to Jenkins Master**

Create SSH keys by executing below command:
```
ssh-keygen
```

Copy SSH Keys from Master to Slave 

Execute the below command in Jenkins master EC2.
```
sudo cat ~/.ssh/id_rsa.pub
```
Copy the output of the above command

Now Login to Slave node and execute the below command
```
sudo -u jenkins vi /home/jenkins/.ssh/authorized_keys
```

This will be empty file, now copy the public keys from master into above file. Once you pasted the public keys in the above file in Slave, come out of the file by entering :wq!

Now go into master node
```
ssh jenkins@slave_node_ip
```

this is to make sure master is able to connect slave node.

**Register slave node in Jenkins:**

- Now to go Jenkins Master, manage jenkins, manage nodes.
- Click on new node. give name and check permanent agent.
- give name and no of executors as 1. enter /home/jenkins as remote directory.
- select launch method as Launch slaves nodes via SSH.
- enter Slave node ip address as Host.
- click on credentials. Enter user name as jenkins. Make jenkins as lowercase as it is shown.
- Kind as SSH username with private key. enter private key of master node directly by executing below command:
```
sudo cat ~/.ssh/id_rsa
```
- select Host key verification strategy as "manually trusted key verification strategy".
- Click on launch agent..make sure it connects to agent node

**PRACTICAL**

*Create a new freestyle job  and select Restrict where this project can be run - use newly created slave agent**
*Note: Sample repositry : https://github.com/kishancs2020/webAppExample*

**Slave2 Node Configuration - Launch Method - JNLP**

 - On Jenkins dashbord - Manage Jenkins - Manage Nodes and Clouds - New Node
 - Add the node name as Permanent Agent
 - Name: uniquely identifies an agent within this Jenkins installation  . Description : anything
 - Number of executors: 2
 - Remote root directory: /opt/build
 - Labels: Labels (or tags) are used to group multiple agents into one logical group.
 - Usage:Use this node as much as possible
 - Launch method:Launch agent via execution of command on the controller
 - Custom WorkDir path: If you keep blank it will automatically refer root directory custom Remoting work directory will be used instead of the Agent Root Directory
 - Availability:Keep this agent online as much as possible
 - Once you save above configuration you will get a command which should be executed in the agent. it contains agent.jar, a secret-file, and a jnlp file
 - Change IP address before executing below command - IP address of master machine
 - Once connected you can create or edit a job to chose this option in the Restrict where this project can be run


  ```
   curl -sO http://54.84.175.179:8080/jnlpJars/agent.jar
   java -jar agent.jar -jnlpUrl http://54.84.175.179:8080/computer/java%2Dnode/jenkins-agent.jnlp -secret 048ad980b94153362fedfb85123e72c0f0093f53b8fec44849f5848ddf29b2b0 -workDir "/opt/build"
  ```

**Docker Slave - Dynamic slave provisioning**
