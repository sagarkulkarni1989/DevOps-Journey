# Access Control #

Access Control is the primary mechanism for securing a Jenkins environment against unauthorized usage. Two facets of configuration are necessary for configuring Access Control in Jenkins

A **Security Realm** which informs the Jenkins environment how and where to pull user (or identity) information from. Also commonly known as "authentication."

   - Jenkins supports 
   - Jenkins own user database
   - Delegate to the servlet container
   - LDAP

**Authorization** configuration which informs the Jenkins environment as to which users and/or groups can access which aspects of Jenkins, and to what extent.
Various ways of authorization include

    - Anyone can do anything
    - Legacy mode
    - Logged-in users can do anything
    - Matrix-based security
    - Project-based Matrix authorization strategy


# Lab Implementation: Jenkins Integration with LDAP

**Pre-requisite**
  - What is LDAP and how it works , its terminology : https://www.youtube.com/watch?v=0FwOcZNjjQA
  - Amazon web service account mandatory
  - One ubuntu 20.04 machine required for lab setup (t2.micro, security group- open all trafic- not recommended , default vpc-subnet, volume 25GB )
  - Jenkins installation : https://www.cherryservers.com/blog/how-to-install-jenkins-on-ubuntu-22-04

Integrating Jenkins with LDAP (Lightweight Directory Access Protocol) is important for several reasons, especially in larger organizations or enterprises where user management and access control are crucial.


**Process of Integration**

**OpenLDAP setup**

```
sudo apt update
hostname -f
sudo hostnamectl set-hostname server-1 - Temparary
For permanant change add here and reboot vim cat /etc/hostname
add : server-1
save and close 
vim /etc/hosts  (update fqdn)
<IP addres> <domain> <hostname>
43.204.141.158 server-1.hg.local server-1
save and close
sudo apt install apache2 php php-cgi libapache2-mod-php php-mbstring php-common php-pear -y 
sudo apt-get install slapd ldap-utils -y   - set admin password - admin
sudo slapcat
sudo apt install ldap-account-manager -y 
sudo a2enconf php*-cgi
sudo a2enconf php*-cgi
sudo systemctl restart apache2
sudo systemctl enable apache2
sudo systemctl status apache2

```
**Post installation steps on LAM (LDAP account Manager)**

- open LAM - http://<machine_IP>/lam 
- click on LAM Configuration - Edit server profiles - initial default credentials - lam/lam
- server settings - Do not changes server address - keep it as default.  tree suffix : **dc=hg,dc=local**
- Language settings - Default language - English and TimeZone : **Asia/kolkata** 
- security settings : List of valid users : **cn=admin,dc=hg,dc=local**
- profile password : Change default password and **save** changes
- Login again http://<machine_IP>/lam - Edit server profiles  with new password
- Acount types - Active account types : user and Group
-  Users : LDAP suffix : ou=Department,dc=hg,dc=local   (No Other changes)
-  Groups:LDAP suffix: ou=Group,dc=hg,dc=local    (No Other changes)
- save changes
  
![image](https://github.com/sagarkulkarni1989/DevOps-Journey/assets/46215433/ce5ca290-8c4e-4418-8713-09cfd8b27bac)

  - Create some dummy groups and users - align users to group

   - Create user and group in LDAP 

![image](https://github.com/sagarkulkarni1989/DevOps-Journey/assets/46215433/5202c165-738b-4c98-ac38-315db4dcc08d)

**Integration with LDAP Configuration**

- Manage Jenkins -security - Security Realm - LDAP
- Server: <VM Private IP Address>
- Advanced server configuration
- root DN: dc=hg,dc=local
- Manager DN: cn=admin,dc=hg,dc=local
- Test LDAP settings - provide any created user in LDAP server

![image](https://github.com/sagarkulkarni1989/DevOps-Journey/assets/46215433/7e7eaa13-8751-4507-b5f8-0fd4d2764b76)

- Access Jenkins using ldap user 


**Reference**
- OpenLDAP setup and configuration : https://www.youtube.com/watch?v=LzRK_8zwqxY
- hostname and FQDN : https://www.youtube.com/watch?v=vjDbVb1Ul44
- Jenkins integration with LDAP : https://www.youtube.com/watch?v=jXrHx7S0vh4
