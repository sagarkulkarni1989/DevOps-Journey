# Jenkins Shared Library

In Jenkins, a shared library is a way to store commonly used code(reusable code), such as scripts or functions, that can be used by different Jenkins pipelines.
Instead of writing the same code again and again in multiple pipelines, you can create a shared library and use it in all the pipelines that need it. This can make your code more organized and easier to maintain.

**Advantages**

 - Standarization of Pipelines
 - Reduce duplication of code
 - Easy onboarding of new applications, projects or teams
 - One place to fix issues with the shared or common code
 - Code Maintainence
 - Reduce the risk of errors

**Here's a simple step-by-step guide on how to create and use a Jenkins shared library:**

 - Create the Shared Library Repository
   
   Start by creating a Git repository to store your shared library code. This repository will contain your Groovy scripts that define reusable functions, classes, and other pipeline components.
   
 - Define the Directory Structure
   
    ```
     <repository-root>
     |-- src/
     |    |-- org/
     |       |-- mylibrary/
     |           |-- MyFunctions.groovy
     |-- vars/
     |   |-- myCustomStep.groovy
     |-- resources/
     |   |-- myResource.txt
     |-- README.md
    
    ```
    
       src/: This directory is used for storing Groovy classes that can be used within the pipeline.
       vars/: This directory is used for defining custom steps that can be directly used in Jenkins pipelines.
       resources/: You can place any resources (like text files) that your library might need here.

   - Write the Shared Library Code

      Write your reusable pipeline logic in the appropriate Groovy files within the src/ and vars/ directories. 

   - Configure Jenkins
  
        - Go to "Manage Jenkins" > "Configure System."
        - Under the "Global Pipeline Libraries" section, add your shared library:
        - Name: Give your library a name.
        - Default Version: Specify the default version of your library.
        - Retrieval Method: Choose "Modern SCM" and provide your Git repository URL.
        - Load implicitly: Enable this option if you want pipelines to automatically use the library without explicitly importing it.

   - Use the Shared Library in Pipelines:
