

# Sample Maven Project

- sample github repository : https://github.com/jenkins-docs/simple-java-maven-app.git
- This build required maven version 3.8.6 and above
- delete existing maven from system : sudo apt-get purge maven
  
```
wget <take latest build from official page>
tar -xvf apacheXXXX.tar.gz
sudo mv apacheXXXX /usr/share/maven
echo 'export PATH="$PATH:/usr/share/maven"' >> ~/.bashrc
echo 'export PATH="$PATH:/usr/share/maven/bin"' >> ~/.bashrc
source ~/.bashrc
On Jenkins - ManageJenkins - Tools - maven - install automatically - 3.9.3 vrsion
create new job - maven_project
       - Source code: git : <provide above sample repo>
       - Build steps : Shell : echo "Maven build"   and java -version
       - Add Build steps: Invoke top-level Maven targets - Goals - clean install


```
  
# Parameterized Job

 Create a freestyle job using build parameters - string,multi-line string, password, choice, credentials,Boolean, file parameters
 
 - This project is parameterized
 - string parameter : Project  default value : Moodys
 - Choice parameter: Shift_days  Mon, Tue, Wed
 - Multi-line String Parameter  About
 - Boolean Parameter : status
 - File Parameter  : path
 - Credentials Parameter : credentials
 - Password Parameter : password
 - Build step : Execute Windows batch command
   
 ```
   echo %Project
   echo %Browser%
  echo %About%
  echo %status%
  echo %path%
  echo %password%
  echo %credentials%

```

# Build Trigger

- Trigger builds remotely (e.g., from scripts) :https://www.devopsschool.com/blog/how-to-trigger-builds-remotely-in-jenkins/
  
            - Go to configuration of loggend in user- Ex.admin
            - Create new API token, save it on notepad
            - Go to job configuration - Build trigger- Trigger builds remotely (e.g., from scripts)
            - Authentication Token  : provide any random value and save job
            - Open Git Bash - and execute
            - curl -X POST http://admin:115c8edaf670ddb9d4e104c9e47c9765d5@localhost:8080/job/first/build?token=abc123

- Build after other projects are built
            
            - Check -Build after other projects are built
            - Add job name

- Build periodically

            - */2 * * * *

 - WebHook (This will not work on jenkins on local machine, need to use jenkins on aws cloud instance)

            - Go to your GitHub repository and click on ‘Settings’.
            - Click on Webhooks and then click on ‘Add webhook’
            - In the ‘Payload URL’ field, paste your Jenkins environment URL. At the end of this URL add /github-webhook/. In the ‘Content type’ select: ‘application/json’ and leave the ‘Secret’ field empty.
            - In the page ‘Which events would you like to trigger this webhook?’ choose ‘Let me select individual events.’ Then, check ‘Pull Requests’ and ‘Pushes’. At the end of this option, make sure that the ‘Active’ option is checked and click on ‘Add webhook’.
            - In Jenkins Jobs - Build trigger - GitHub hook trigger for GITScm polling

