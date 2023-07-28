# About Jenkins
Jenkins is an open-source automation server that is widely used for continuous integration (CI) and continuous delivery (CD) in software development. It helps developers automate various aspects of the software development lifecycle, such as building, testing, and deploying code changes to production environments. Jenkins is written in Java and is highly extensible through plugins, making it flexible and customizable for various workflows.

**Key features and concepts of Jenkins include**

**CI/CD Pipelines:** Jenkins enables the creation of CI/CD pipelines, which are sequences of automated steps that define how code changes progress from development to production. Pipelines typically include stages for code compilation, testing, packaging, and deployment.

**Plugins:** Jenkins has a rich ecosystem of plugins that extend its functionality. Plugins cover a wide range of tasks, including integrating with version control systems, building and testing frameworks, notification systems, and cloud providers.

**Freestyle Projects:** Jenkins allows you to create freestyle projects, where you manually configure build and deployment steps. It provides flexibility but might require more manual setup.

**Declarative Pipelines:** Jenkins supports declarative pipelines, where you define the pipeline using a domain-specific language (DSL) in a Jenkinsfile. Declarative pipelines offer a more structured and concise way to define complex workflows.

**Distributed Builds:** Jenkins supports distributed builds, allowing you to distribute build jobs across multiple agents (build nodes) to leverage resources efficiently and reduce build times.

**Integration with Version Control:** Jenkins can integrate with various version control systems like Git, Subversion, and Mercurial. It can automatically trigger builds when code changes are committed.

**Security:** Jenkins provides options for securing access to the server, projects, and plugins. You can set up user authentication, role-based access control (RBAC), and manage permissions for different users and groups.

**Monitoring and Logging:** Jenkins offers built-in monitoring and logging capabilities to help track build status, view build logs, and monitor the performance of Jenkins itself.

# Jenkins Installation
Jenkins is written in Java so java installation is mandatory to run Jenkins.

**Windows**
- Check which Java is running on system: Open command prompt and run : java -version
- If its not present then install Java : Download windows pakcage from https://adoptium.net/  
- Best practice to install package as a administrator. Click n java msi and install it. provide appropriate installation path while installing.
- Follow official page for Jenkins installation: https://www.jenkins.io/doc/book/installing/windows/
- Download Jenkins .msi from above page and start installation. - Select appropriate path for jenkins Home and select Java Home/Bin path(we installed in above step) validate port(Jenkins default port 8080) we can change it here or after installation also.

**Linux**
- Pre-requisite: If you are using Linux/Unix OS on your personal Laptop then well and good, if not then best solution is to get one instance on AWS account.
- Follow steps to get new machine: https://linux.how2shout.com/how-to-create-a-ubuntu-linux-aws-ec2-instance-on-amazon-cloud/
- Check which Java is running on system: Open command prompt and run : java -version
- Follow instruction to install Jenkins along with Java https://www.cherryservers.com/blog/how-to-install-jenkins-on-ubuntu-22-04

# GIT : Source Code Management
Git is a distributed version control system (VCS) widely used in software development to manage and track changes to source code and other files.

**Installation**

**Windows/Linux** 
 - Check which Git is running on system: Open command prompt and run : git --version
 - Installation steps: https://git-scm.com/download/win
 - For Linux: https://www.digitalocean.com/community/tutorials/how-to-install-git-on-ubuntu-20-04

# MAVEN : Build Tool
Maven is a popular build automation and project management tool used primarily for Java projects. It simplifies the process of building, managing dependencies, and packaging Java applications. 
To use Maven, you need to install it on your development machine and have a Java Development Kit (JDK) installed. Once set up, you can navigate to your project directory and run various Maven commands,

**mvn clean:**
This command cleans the project by deleting the target directory, which contains compiled classes, generated files, and other build artifacts. It ensures a clean slate before the next build.

**mvn compile:**
This command compiles the source code in the src/main/java directory and stores the compiled classes in the target/classes directory.

**mvn test:**
This command runs all the unit tests in the src/test/java directory using a testing framework like JUnit. Test results and reports are generated in the target/surefire-reports directory.

**mvn package:**
This command packages the compiled code and resources into a distributable format, such as a JAR, WAR, or EAR file, depending on the project's packaging type.

**mvn install:**
This command compiles, tests, and packages the project and installs the resulting artifact (JAR, WAR, etc.) into the local Maven repository (~/.m2/repository). The installed artifact can then be used as a dependency in other local Maven projects.

**mvn deploy:**
This command deploys the project's artifacts to a remote Maven repository (if specified in the project's POM). It is typically used to deploy artifacts to a remote repository like Nexus or Artifactory for sharing with other developers or projects.

**Intallation**
*Windows& Linux*
- Windows: https://www.javatpoint.com/how-to-install-maven
- Linux: https://linuxhint.com/install_apache_maven_ubuntu/

**Other Tools** 
- Visual Studio Code: https://code.visualstudio.com/download
- Mobaxtream: https://mobaxterm.mobatek.net/download.html  


