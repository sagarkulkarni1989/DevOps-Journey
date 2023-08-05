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

# Build Trigger 

**Trigger builds remotely (e.g., from scripts)**

Jenkins can be triggered remotely by sending an HTTP POST request to a specific URL endpoint. This can be useful for integrating Jenkins with other tools or services.

**Build after other projects are built**

To set up a Jenkins job to build after other projects are built, you can use the "Build after other projects are built" trigger. This trigger allows you to specify one or more projects that need to complete successfully before the current job starts its execution.
 
**Build periodically**

In Jenkins, the "Build periodically" trigger allows you to schedule builds based on a cron expression. This means you can set up a specific time interval for your Jenkins job to run automatically.

```
* * * * * *
| | | | | |
| | | | | +-- Year (optional) (1970–2099)
| | | | +---- Day of the Week (0–7) (Sunday is both 0 and 7)
| | | +------ Month (1–12)
| | +-------- Day of the Month (1–31)
| +---------- Hour (0–23)
+------------ Minute (0–59)
```
- An asterisk (*) represents all possible values for that field.
- A hyphen (-) denotes a range of values. For example, 1-5 means from 1 to 5.
- A comma (,) allows you to specify a list of values. For example, 1,3,5 means 1, 3, and 5.
- A forward slash (/) allows you to define a step value. For example, */5 in the minute field means every 5 minutes.
Examples:

- Run a task every minute: * * * * *
- Run a task every day at 3:30 PM: 30 15 * * *
- Every 2 min */2 * * * *
- Every saturday and sunday 17.00PM 0 17 * * 6,7

**GitHub hook trigger for GITScm polling**

Jenkins can listen for incoming HTTP requests (webhooks) from external services, such as version control systems or issue trackers. When a webhook event occurs (e.g., code push, pull request created), Jenkins triggers a build.
   
 **Poll SCM**

 This trigger checks the version control system (e.g., Git, Subversion) for changes at a specified interval. If there are new changes, it triggers a build.


# How to deploy war file in Tomcat using Jenkins? 
https://www.youtube.com/watch?v=KHnQ0n4deqI

# jenkins email notification configuration 
https://www.youtube.com/watch?v=MFgbp00hbVI

# Master Slave configuration
  
# Freestyle and Jenkins Pipeline
In Jenkins, there are two primary types of jobs used for build automation and continuous integration: Freestyle projects and Pipeline projects (also known as Jenkins Pipeline). Each type of job has its own approach to defining and configuring the build process.
   
    
**Freestyle Projects**

   Freestyle projects are the traditional and simpler form of Jenkins jobs. They provide a user-friendly web interface to configure the build process using a series of build steps and configurations.

**Features:**

**Easy Configuration:** Freestyle projects have a straightforward web-based UI, making it easy to configure build steps, triggers, and post-build actions.

**GUI-based:** Configurations are done through a graphical user interface, and no scripting is required.

**Limited Reusability:** Build steps are specific to each project, and it is challenging to reuse configurations across multiple projects without duplication.

**Lack of Version Control:** Freestyle jobs don't store their configuration as code, making it harder to track changes and manage job configurations using version control systems.

**Pipeline Projects (Jenkins Pipeline):**

Jenkins Pipeline is a more advanced and flexible way to define the build process as code. It allows you to create complex build pipelines using a domain-specific language (DSL) based on Groovy scripting.

**Features:**

**Scripted Pipelines:** Pipeline jobs are defined using a script written in Groovy DSL, providing a high degree of flexibility and reusability.

**Code as Configuration:** Pipeline configurations are versioned along with the source code in the project's version control system, enabling better traceability and reproducibility of build processes.

**Extensibility:** Jenkins Pipeline supports defining custom functions, libraries, and shared pipelines, making it easier to reuse code across multiple projects.

**Continuous Delivery:** Pipelines can model entire continuous delivery workflows, including build, test, deployment, and manual approvals.

# Dashboard

**Types of Jobs**

Jenkins offers several types of items (projects) that you can create when setting up a new job. These job types allow you to implement various build and automation workflows based on your project's requirements.

**Freestyle project:**
This is the traditional type of job in Jenkins, where you can configure the build steps, triggers, and post-build actions using a graphical user interface. It is suitable for simple and straightforward build processes.

**Pipeline:**
Jenkins Pipeline allows you to define your build process as code using a domain-specific language (DSL) based on Groovy. With pipelines, you can model complex build, test, and deployment workflows, as well as integrate with version control systems.

**Multi-branch pipeline:**
This type of job is an extension of the Pipeline project, optimized for multi-branch development workflows. It automatically detects branches in your version control repository and creates individual pipelines for each branch, making it ideal for continuous integration with multiple branches.

**Folder:**
A folder is a way to organize jobs hierarchically within Jenkins. You can create folders to group related jobs together, providing better organization and management of projects.

**Multi-configuration project**

A Multi-configuration project, also known as a Matrix project, is a type of item in Jenkins that allows you to perform a build or test in multiple configurations simultaneously. It is useful when you need to test your application or code against different combinations of platforms, operating systems, environments, or parameters.

**General**
In Jenkins, the "General" options refer to the basic settings and configurations that apply to a Jenkins job (item) regardless of its type.

**- Discard Old Builds:**
This option allows you to control the number of builds to keep. You can specify the maximum number of builds to retain, the maximum number of days to keep builds, or both. Older builds beyond the specified limits will be automatically deleted to save disk space.

**- GitHub Project:**
If your Jenkins job is associated with a GitHub repository, you can specify the GitHub project's URL in this option. It helps Jenkins display build status and links back to GitHub.

- This project is parameterized:
When enabled, this option allows you to add parameters to the job, enabling you to customize the build based on user input or other dynamic values.
    - Jenkins supports several parameter types, including:
    - String Parameter: Allows you to define a simple text parameter.
    - Choice Parameter: Presents a dropdown menu with predefined choices.
    - Boolean Parameter: Represents a true/false or yes/no parameter.
    - File Parameter: Enables users to upload a file when triggering the job.

**- Throttle builds**
   Throttle Builds is a Jenkins plugin that allows you to limit the number of concurrent builds for specific jobs or for jobs within certain categories. This plugin is particularly useful when you have limited resources, such as build agents or hardware capacity, and you want to control how many builds of a particular job or group of jobs can run simultaneously.
  
**- Concurrent Build:**
By default, Jenkins allows concurrent builds of the same job. You can set the maximum number of concurrent builds to control how many simultaneous builds are allowed.

**- Quiet Period:**
The quiet period is the time delay between the moment Jenkins is triggered and when the build actually starts. It helps avoid excessive builds triggered by multiple changes in quick succession.

**Build Triggers**

Build Triggers in Jenkins are mechanisms that define when and how a Jenkins job (or pipeline) should be triggered to start a build. Jenkins provides various build triggers to accommodate different use cases and automation scenarios.

**- Trigger builds remotely (e.g., from scripts)**
  In Jenkins, you can trigger builds remotely using various methods, such as API calls, scripts, or URL-based triggers. This feature allows you to automate the build process and initiate builds programmatically from external systems, scripts, or other tools.
  
         - Using Jenkins Remote API (Jenkins REST API):
         
Jenkins provides a RESTful API that allows you to interact with Jenkins programmatically. You can trigger a build remotely by making an HTTP POST request to the Jenkins API 
         - Using Jenkins CLI (Command Line Interface):
         
Jenkins CLI is a command-line tool that allows you to interact with Jenkins from the command line. You can trigger a build using the build command of the Jenkins CLI.

- Build after other projects are built
- Build periodically
- GitHub hook trigger for GITScm polling
- Poll SCM

**Post-build Actions**

