# Jenkins Pipeline 

Jenkins offers various types of jobs or project types that cater to different needs in the software development and automation process.

- **Freestyle** Project: This is a general-purpose job type that allows you to define a series of build steps and configuration options. It's flexible and can be used for a wide range of tasks.
- **Pipeline:** Jenkins provides a powerful feature called "Pipeline" that allows you to define your build, test, and deployment steps in code using a domain-specific language called Groovy. This is often used for complex and automated workflows.
- **Multi-Configuration Project:** Also known as matrix jobs, these allow you to run the same set of build steps with different configurations, such as different operating systems or environments.
- **Multibranch Pipeline:** This job type is used for managing multiple branches of a codebase, each with its own automated pipeline.

**Different between Freestyle and Pipeline**

**Freestyle Projects**
- Configuration is done through a user-friendly interface,
- Supports integration with a wide range of Jenkins plugins to extend functionality.
- Each build step, such as compilation, testing, and deployment, needs to be configured individually.
- Ideal for simple build and deployment processes that don't involve complex branching, conditional logic, or intricate workflows.

**Pipeline :**
- Pipeline jobs use code to define the build, test, and deployment pipeline. This code can be versioned and stored in source control, providing better traceability and change management.
- There are two syntax options for defining pipeline jobs: Scripted and Declarative. The Declarative syntax aims to provide a more structured and readable way to define pipelines, while Scripted syntax allows for more customization and flexibility.
- Pipeline jobs are designed to handle complex workflows, including conditional logic, parallel stages, dynamic branching, and more.
- The pipeline script is stored in source control, allowing for versioning, collaboration, and code reviews.
- Reusability: Pipeline scripts can be reused across different jobs

**Syntax for Scripted Pipeline**
```
node {
    // Define environment variables or tools here
    
    stage('Stage 1') {
        // Actions for Stage 1
    }
    
    stage('Stage 2') {
        // Actions for Stage 2
    }
    
    // More stages and actions as needed
}

```
**Syntax for Declarative Pipeline**

```
pipeline {
    agent any
    
    environment {
        // Define environment variables
    }
    
    stages {
        stage('Stage 1') {
            steps {
                // Actions for Stage 1
            }
        }
        
        stage('Stage 2') {
            steps {
                // Actions for Stage 2
            }
        }
        
        // More stages as needed
    }
    
    post {
        // Post-build actions
    }
}

```
