
**Different between Linux and UNIX**

![image](https://github.com/sagarkulkarni1989/DevOps-Journey/assets/46215433/13202a6d-eb29-4085-a3fd-5399adad52d5)

**Linux Architecture**

![image](https://github.com/sagarkulkarni1989/DevOps-Journey/assets/46215433/abaa25ac-dc40-43fb-bac5-139627d2d01f)

**How many types of Shells are there in Linux?**

- Bourne Shell (sh)
- C Shell (csh)
- Korn Shell (ksh)
- Bourne Again Shell (bash) – default
- Z Shell (zsh)

**Check shells**

- echo $SHELL - This command will print the path to the shell that you are currently using.
- cat /etc/shells - This command will list all of the shells that are installed on the system.

**Linux Directory structure** 

- / (root filesystem): It is the top-level filesystem directory. It must include every file needed to boot the Linux system before another filesystem is mounted. /boot: It includes the static kernel and bootloader configuration and executable files needed to start a Linux computer.
- /bin: This directory includes user executable files.
- /dev: It includes the device file for all hardware devices connected to the system.
- /etc: It includes the local system configuration files for the host system.
- /lib: It includes shared library files that are needed to start the system.
- /home: The home directory storage is available for user files. All users have a subdirectory inside /home.
- /mnt: It is a temporary mount point for basic filesystems that can be used at the time when the administrator is working or repairing a filesystem.
- /media: A place for mounting external removable media devices like USB thumb drives that might be linked to the host.
- /opt: It contains optional files like vendor supplied application programs that must be placed here.
- /root: It's the home directory for a root user. Keep in mind that it's not the '/' (root) file system.
- /tmp: It is a temporary directory used by the OS and several programs for storing temporary files.
- /sbin: These are system binary files. They are executables utilized for system administration.
- /usr: They are read-only and shareable files, including executable libraries and binaries, man files, and several documentation types.
- /var: Here, variable data files are saved. It can contain things such as MySQL, log files, other database files, email inboxes, web server data files, and much more.

**File Permissions:**

All the three owners (user owner, group, others) in the Linux system have three types of permissions defined. Read(r), Write (w), Execute(x)

```
$ ls -l drwxr-xr-x. 4 root root 68 Jun 13 20:25 tuned
```
- File type: -
- Permission settings: rw-r--r--
- Extended attributes: dot (.)
- User owner: root
- Group owner: root
- r (read): 4
- w (write): 2
- x (execute): 1

**How do you modify Linux file permissions?**

chmod ug+rwx example.txt $ chmod o+r example2.txt

- This grants read, write, and execute for the user and group, and only read for others. In symbolic mode, chmod u represents permissions for the user owner, chmod g represents other users in the file's group, chmod o represents other users not in the file's group. For all users, use chmod a.

- Chown change the user owner itself
- Chgrp can be used to change the group ownership of a file.
- change both the owner and the group to bin by executing
- chown bin sampsoft
- chgrp bin sampsoft
- Default file permission is 644 and directory 755 

Important troubleshooting commands 

**check Disk usage**
```
df –h
df -h /path/to/directory
```
**ping**
- The ping utility helps you identify the availability of a network and host. It checks if the host is reachable or if a service is running.
- ping 8.8.8.8

**What are the ways to check CPU usage**

- top Command: The top command provides real-time monitoring of system processes, including CPU usage.
- ps Command: The ps command can also be used to check CPU usage. By using the -eo option with specific format specifiers, you can customize the output to display CPU-related information.
- mpstat Command: The mpstat command provides detailed information about CPU usage, including average CPU utilization, individual CPU core utilization, and statistics for specific intervals. You can run mpstat -P ALL to display CPU usage for each core separately

**What is SSH ? How you generate SSH-keys**

- SSH (Secure Shell) is a cryptographic network protocol used for secure remote access and secure file transfer over an insecure network. It provides a secure channel between two systems, allowing secure authentication and encrypted communication.
- SSH uses public-key cryptography to authenticate and establish a secure connection. Here's a general process for generating SSH keys:
- Open a terminal or command prompt on your local system.
- Use the ssh-keygen command to generate the SSH key pair. By default, this command generates a 2048-bit RSA key pair. You can specify a different key type (e.g., ED25519) and key size if desired. For example:
- ssh-keygen -t rsa -b 2048
- The command will prompt you to choose a location to save the generated keys. Press Enter to accept the default location (~/.ssh/id_rsa) or provide a custom path.
- Next, you'll be prompted to enter a passphrase for the key pair. A passphrase adds an extra layer of security by encrypting the private key with a password. You can choose to use a passphrase or leave it empty for a passphrase-less key. It is generally recommended to use a passphrase.
- The ssh-keygen command will generate two files: a private key file (typically named id_rsa) and a public key file (typically named id_rsa.pub).
- The private key (id_rsa) must be kept secure and should not be shared with anyone. It is used for authentication when connecting to remote systems.
- The public key (id_rsa.pub) can be shared with remote systems to which you want to authenticate. It is added to the ~/.ssh/authorized_keys file on the remote system.
- To use the generated SSH key pair, you can either manually copy the public key to the remote system or use the ssh-copy-id command. For example:
- ssh-copy-id user@remote_host

**What is Private & public key ? How they authenticate**

- Private and public keys are a fundamental component of public-key cryptography, which is used in various security protocols, including SSH.
- Public Key: A public key is derived from a private key and is meant to be shared freely with others. It is used for encryption and authentication. The public key is typically made available to anyone who wants to communicate with the owner of the corresponding private key.
- Private Key: A private key is kept secret and known only to its owner. It is used for decryption and digital signatures. The private key should be securely stored and not shared with others. The security of the private key is crucial as it allows access to resources or data encrypted using the corresponding public key.

**Port no of HTTP, FTP, SSH, HTTPS**

Here are the standard port numbers for commonly used protocols:

- HTTP (Hypertext Transfer Protocol): Port 80 is the default port for HTTP. It is used for unencrypted web traffic.
- FTP (File Transfer Protocol): Port 21 is the default port for FTP. It is used for transferring files between a client and a server.
- SSH (Secure Shell): Port 22 is the default port for SSH. It is used for secure remote login and encrypted communication between systems.
- HTTPS (Hypertext Transfer Protocol Secure): Port 443 is the default port for HTTPS. It is used for secure, encrypted web traffic.

