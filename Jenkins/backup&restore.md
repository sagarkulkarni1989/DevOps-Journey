# Jenkins Backup and Restore

Backing up Jenkins is essential to ensure the safety and availability of your Jenkins server and its configurations.

Backing up and restoring Jenkins is essential for several important reasons:
   - Data Recovery
   - Minimizing Downtime
   - Configuration Consistency
   - Disaster Recovery
   - Business Continuity
**Method #1 : Backup and Restore Jenkins Server**

**Pre-requsite**

  - Two AWS Ubuntu Machine - T2.micro, default vpc, security group(open traffic)
  - Install Jenkins on first machine with all plugins and create some test jobs
  - On Second VM- install jenkins only and do not do any steps just wait on default password page  
  - install aws-cli on both machine
  - create one S3 bucket
  - create IAM Role with - IAM - Roles - provide any name - Policy - AmazonS3FullAccess
  - Add Newly created role to VM

  **Backup**
   - On VM#1 - Login to VM
   - Stop jenkins
     ```
     systemctl status jenkins
     systemctl stop jenkins
     aws s3 cp <backup_file_name.tar.gz> s3://<Bucket_name>/<store_file_name>.tar.gz
     aws s3 cp jenkins-backup.tar.gz s3://jenkins12345/jenkins-backup.tar.gz
     ```
  **Restore**
  
  - on VM#2 - Login to VM
    
   ```
   systemctl status jenkins
   systemctl stop jenkins
   Copy baakcup from s3 : aws s3 cp s3://jenkins12345/jenkins-backup.tar.gz jenkins-backup.tar.gz
   Remove existing jenkins home directory : rm -rf /var/lib/jenkins/
   tar -zxvf jenkins-backup.tar.gz -C /
   systemctl start jenkins
   open Jenkins - http://<IP_address>:8080
   you will see all jobs/configurations are copied from VM#1

   ```
**Backup using Plugins - ThinBackup and Periodic Backup**

**ThinBackup**


