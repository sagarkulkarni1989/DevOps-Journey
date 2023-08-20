# Jenkins Integration with LDAP
Integrating Jenkins with LDAP (Lightweight Directory Access Protocol) is important for several reasons, especially in larger organizations or enterprises where user management and access control are crucial.

Pre-requisite 
Amazon Ubuntu 20.04 Machine 

**Process of Integration**

**Open LDAP setup**

```
sudo apt update
hostname -f
vim cat /etc/hostname
add : server1
save and close 
vim /etc/hosts  (update fqdn)
<IP addres> <domain> <hostname>
43.204.141.158 server1.hg.local server1
save and close
sudo apt install apache2 php php-cgi libapache2-mod-php php-mbstring php-common php-pear -y 
sudo apt-get install slapd ldap-utils -y 
sudo slapcat
sudo apt install ldap-account-manager -y 
sudo a2enconf php*-cgi
sudo a2enconf php*-cgi
sudo systemctl restart apache2
sudo systemctl enable apache2
sudo systemctl status apache2

```
For configuration follow instruction : https://www.youtube.com/watch?v=LzRK_8zwqxY

Create user and group in LDAP 

![image](https://github.com/sagarkulkarni1989/DevOps-Journey/assets/46215433/5202c165-738b-4c98-ac38-315db4dcc08d)


**Jenkins installation**
Follow Instruction : 

**Integration with LDAP Configuration**

- Manage Jenkins -security - Security Realm - LDAP
- Server: <VM Private IP Address>
- Advanced server configuration
- root DN: dc=hg,dc=local
- Manager DN: cn=admin,dc=hg,dc=local
- Test LDAP settings - provide any created user in LDAP server

![image](https://github.com/sagarkulkarni1989/DevOps-Journey/assets/46215433/7e7eaa13-8751-4507-b5f8-0fd4d2764b76)

Access Jenkins using ldap user 




