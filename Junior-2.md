# Cloud-simply Engineering Curriculum
Level: `Junior 2` | `Basic`

---
### Exercise 1
Create first Linux EC2 Instance 
  | [text](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/EC2_GetStarted.html)
<details><summary>Show details</summary>  

* **Details**
  * Use AWS Console
  * Use any of the created IAM admin users 
  * Use AWS Region: `Europe (Frankfurt) eu-central-1` 
    | [text](https://docs.aws.amazon.com/awsconsolehelpdocs/latest/gsg/select-region.html)
  * Use the following EC2 instance settings (pre selected as default when applicable) 
     * Amazon Machine Image: `Amazon Linux 2 AMI (HVM), SSD Volume Type`
     * Instance type: `t2.micro` 
     * Security group name (wizard created): `launch-wizard-1` 
       * **Create a new key pair** as wizard prompted and download the private key file        
         * Key pair type: `RSA` 
         * Key pair name: `launch-wizard-1`
         * Downloaded private key file name: `launch-wizard-1.pem`
* **What we have as a result (to check/validate)**
  * **Running** Amazon Linux 2 EC2 instance (created within AWS account) in `eu-central-1` region, SSH RSA private key (downloaded) 
</details>

Connect to the created Linux EC2 instance using SSH
  | [text](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/AccessingInstancesLinux.html)<details><summary>Show details</summary>

* **Details**
  * Use corresponding user name and the instance public DNS name (or IP address)
    | [text](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/connection-prereqs.html)
  * Use the downloaded private key 
    | [text](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/connection-prereqs.html)
  * Use terminal of local Linux/MacOS workplace
    * Make sure local Linux/MacOS workplace has `ssh` program installed
  * Use terminal of the created AWS Cloud9 IDE environment
* **What we have as a result (to check/validate)**
  * SSH session (to the created EC2 instance) established (with the ability to execute commands remotely)
</details>

Transfer a file from the created Linux EC2 instance to local Linux/MacOS host using SCP
<details><summary>Show details</summary>

* **Details**
  * Make sure local Linux/MacOS workplace has scp program installed
  * Use the same command parameters as ones used to connect to the instance via SSH above
  * Use the following file paths:
    * Remote file: `/etc/ssh/ssh_host_ecdsa_key.pub`
    * Local file: `~/.ssh/ssh_host_ecdsa_key.pub`
* **What we have as a result (to check/validate)**
  * ~/.ssh/ssh_host_ecdsa_key.pub file presence (on the filesystem of local Linux/MacOS host) 
</details>

Clean up (terminate) the created instance
<details><summary>Show details</summary>

* **What we have as a result (to check/validate)**
  * No instance exists in AWS account (the created EC2 instance is terminated)
</details>  

---
### Exercise 2
Repeat the part of the above exercise creating a Linux EC2 Instance and connecting to it via SSH
<details><summary>Show details</summary>

* **Details**
  * To connect to the instance via SSH use **default user** name (user which is default for the Amazon Machine Image used to launch the instance) and the downloaded private key
* **What we have as a result (to check/validate)**
  * Ability to execute commands in shell of the created instance remotely via SSH
</details>

Configure SSH daemon of the created Linux EC2 Instance (remotely via SSH) to be more secure 
  | [text](https://aws.amazon.com/ru/premiumsupport/knowledge-center/ec2-ssh-best-practices/)
<details><summary>Show details</summary>

* **Details**
  * Disallow SSH access for Linux `root` user
    * Backup Linux `root` user public key authentication settings
      | [text](https://man.openbsd.org/sshd.8)
    * Setup public key authentication for Linux `root` user **to allow** to use the same public key as used for **default user** 
    * Try to connect to the instance via SSH with root user using public key of **default user**
    * Configure SSH daemon to **deny**  <span style="color:red">connecing</span> for Linux `root` user
      | [text](https://man.openbsd.org/sshd_config.5)
    * Make sure it is not possible to connect to the instance via SSH for Linux `root` user
    * Restore Linux `root` user public key authentication settings from the backup
  * Disallow SSH access using passwords
    * Setup password for the **default user** in the Linux instance
      | passwd(1)
    * Try to connect to the instance via SSH with **default user** using password
    * Configure SSH daemon to **allow** connecting with password
      | [text](https://man.openbsd.org/sshd_config.5)
    * Try to connect to the instance via SSH with **default user** using password
    * Configure SSH daemon to **deny** connecing with password
    * Make sure it is **not possible** to connect to the instance via SSH using password
  * Install `fail2ban` utility and enable and start it as a service  
     * fail2ban monitors log files and blocks consecutive unsuccessful access attempts
     * Update the EC2 instance software (all packages)
       | [text](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/install-updates.html)
     * Try to find `fail2ban` software package
       | [text](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/find-software.html)
     * Add EPEL repository for the EC2 instance running Amazon Linux 2
       | [text](https://aws.amazon.com/ru/premiumsupport/knowledge-center/ec2-enable-epel/)
       | [text](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/add-repositories.html)
     * Try to find `fail2ban` software package again
     * Install `fail2ban` software package
       | [text](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/install-software.html)
     * Enable and start `fail2ban` service
       | [text](https://www.redhat.com/sysadmin/getting-started-systemctl)
     * Leave the `fail2ban` utility configured by default
* **What we have as a result (to check/validate)**
  * SSH daemon is configured according to best practices for keeping Linux instance secure
</details>

Stop the created instance
 | [text](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/Stop_Start.html)
<details><summary>Show details</summary>

* **Details**
  * Use AWS Console
* **What we have as a result (to check/validate)**
  * Linux EC2 instance in **Stopped** state in AWS account in `eu-central-1` region
</details> 

Start the EC2 instance stopped in the previous section and connect to it via SSH as **default user**
  | [text](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/Stop_Start.html)(*)
<details><summary>Show details</summary>

* **Details**
  * To start instance use AWS Console
  * Install `nginx` package on the EC2 Instance (remotely via SSH) and configure `http` access to it
  * Install `nginx` software package by repeating the same step for `nginx` package as for installing `fail2ban` utility in the previous section 
    * Update the EC2 instance software (all packages)
      | [text](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/install-updates.html)(*)
    * Make sure EPEL repository is added
      | [text](https://aws.amazon.com/ru/premiumsupport/knowledge-center/ec2-enable-epel/)(*)
      | [text](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/add-repositories.html)(*) 
    * Find `nginx` software package
      | [text](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/find-software.html)(*) 
    * Install `nginx` software package
      | [text](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/install-software.html)(*)
    * Enable and start `nginx` service
      | [text](https://www.redhat.com/sysadmin/getting-started-systemctl)(*)
   * Use the following commands to configure Amazon Linux 2 OS firewall to allow ingress `http` traffic
     * `sudo firewall-cmd --zone=public --add-service=http --permanent`
     * `sudo firewall-cmd --reload`
   * If it is required use the following commands to configure Amazon Linux 2 OS firewall to allow ingress traffic on specific `<port>/<protocol>` (for example `8080/tcp`)
     * `sudo firewall-cmd --zone=public --add-port=<port>/<protocol> --permanent`
     * `sudo firewall-cmd --reload`
   * Allow `http` traffic to access `nginx` service running on TCP port `80`
     | [text](https://aws.amazon.com/ru/premiumsupport/knowledge-center/connect-http-https-ec2/)
     * Use AWS Console
     * Configure the security group of the EC2 instance to allow `http` traffic by adding an inbound rule on TCP port `80` from the source address `0.0.0.0/0`
       | [text](https://docs.aws.amazon.com/vpc/latest/userguide/VPC_SecurityGroups.html)
       | [video](https://www.youtube.com/watch?v=UQLWYy-EpCg)  
* **What we have as a result (to check/validate)**
  * Ability to execute commands remotely (via SSH) in shell of the instance created in the previous section 
</details>
  
Stop the EC2 instance
<details><summary>Show details</summary>

* **Details**
  * Use AWS Console
* **What we have as a result (to check/validate)**
  * Linux EC2 instance in **Stopped** state in AWS account in `eu-central-1` region
</details> 
  
Start the EC2 instance stopped in the previous section and access it via SSH
<details><summary>Show details</summary>

* **Details**
  * See the previous section
* **What we have as a result (to check/validate)**
  * See the previous section
</details>   
    
Start the EC2 instance stopped in the previous section and access it via SSH
  | [text](https://aws.amazon.com/ru/premiumsupport/knowledge-center/new-user-accounts-linux-instance/)
  | [video](https://www.youtube.com/watch?v=khPGZYh73fo)
<details><summary>Show details</summary>

* **Details**
  * Use the following Linux OS user settings
    | adduser(8)
    * Username: `tutor-a`
    * Public key: `ssh-ed25519 AAAAC3NzaC1lZDI1NTE5AAAAIChvBKAJbIt0H0O26DbZnu2I0kHG+OJBEvR0UkgqWwFb tutor-a`
  * Provide user `tutor-a` with instance administrative privileges via `sudo`
    | [text](https://developers.redhat.com/blog/2018/08/15/how-to-enable-sudo-on-rhel)
    * Add user `tutor-a` to the group: `wheel`
      | usermod(8)
    * Use `visudo` command (which safely edits `/etc/sudoers` file with `vi` editor) to enable all users in group `wheel` to run any command with `sudo` **without a password**
      | visudo(8)
* **What we have as a result (to check/validate)**
  * User `tutor-a` has SSH access to the Linux EC2 instance (using its private key) with instance administrative privileges via `sudo`
</details>   
  
Stop the EC2 instance
<details><summary>Show details</summary>

* **Details**
  * See the previous section
* **What we have as a result (to check/validate)**
  * **Stopped** Linux EC2 instance in `eu-central-1` region configured according to the following
    * Amazon Linux 2 OS installed
    * SSH daemon configured according to best practices
    * Web server `nginx` installed and accessible via `http` on TCP port `80`
    * User `tutor-a` created and provided SSH access (using its private key) with instance administrative privileges via `sudo`  
</details>   
  
Create custom EC2 key pair using Amazon EC2
  | [text](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ec2-key-pairs.html)(Console)
<details><summary>Show details</summary>

* **Details**
  * Use AWS Console
  * Use any of the created IAM admin users
  * Use AWS Region: `Europe (Frankfurt) eu-central-1`
  * Use the following EC2 key pair settings
    * Key pair name: `student-rsa`
    * Key pair type: `RSA`
    * Private key file format: `.pem`
  * Save downloaded private key file (`student-rsa.pem`) as `~/.ssh/id_student_rsa` (in local Linux/MacOS workplace) and make appropriate permission changes
* **What we have as a result (to check/validate)**
  * EC2 key pair `student-rsa` in `eu-central-1` region, private key file `~/.ssh/id_student_rsa`
</details>   
  
Create custom EC2 key pair using Amazon EC2
  | [text](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ec2-key-pairs.html)(AWS CLI)
<details><summary>Show details</summary>

* **Details**
  * Use AWS CLI
  * Use any of the created IAM admin users
  * Use AWS Region: `Europe (Frankfurt) eu-central-1`
  * Use the following EC2 key pair settings
    * Key pair name: `student-ed25519`
    * Key pair type: `ED25519`
    * Private key file format: `.pem`
  * Save private key file as `~/.ssh/id_student_ed25519` (in local Linux/MacOS workplace) and make appropriate permission changes
* **What we have as a result (to check/validate)**
  * EC2 key pair `student-ed25519` in `eu-central-1` region, private key file `~/.ssh/id_student_ed25519`
</details>   
  
Create custom EC2 security group
  | [text](Create custom EC2 security group)
<details><summary>Show details</summary>

* **Details**
  * Use AWS Console
    | [text](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/working-with-security-groups.html)(New console) 
  * Use any of the created IAM admin users
  * Use AWS Region: `Europe (Frankfurt) eu-central-1`
  * Use the following security group settings
    * Security group name: `public-ssh-and-http`
    * Description: `Allow SSH and HTTP access from the World`
    * VPC: use `default` VPC (the only VPC ID available at this stage)
    * Allow ingress `http` traffic on TCP port `80` from the source address `0.0.0.0/0`	
      | [text](https://developers.redhat.com/blog/2018/08/15/how-to-enable-sudo-on-rhel)(New console) 
    * Allow ingress `ssh` traffic on TCP port `22` from the source address `0.0.0.0/0`
    * Allow all egress traffic to the destination address `0.0.0.0/0`     
* **What we have as a result (to check/validate)**
  * EC2 security group `public-ssh-and-http in eu-central-1` region allowing SSH and HTTP access from the World
</details>   
  
Create custom EC2 security group
<details><summary>Show details</summary>

* **Details**
  * Use AWS CLI
    | [text](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/working-with-security-groups.html)(Command line) 
  * Use any of the created IAM admin users
  * Use AWS Region: `Europe (Frankfurt) eu-central-1`
  * Use the following security group settings
    * Security group name: `public-ssh-http-81`
    * Description: `Allow SSH, HTTP and 81/TCP access from the World`
    * VPC: use `default` VPC (the only VPC ID available at this stage)
    * Allow ingress `http` traffic on TCP port 80 from the source address `0.0.0.0/0`
      | [text](https://developers.redhat.com/blog/2018/08/15/how-to-enable-sudo-on-rhel)(Command line) 
    * Allow ingress traffic on TCP port `81` from the source address `0.0.0.0/0`  
    * Allow ingress `ssh` traffic on TCP port `22` from the source address `0.0.0.0/0`
    * Allow all egress traffic to the destination address `0.0.0.0/0`       
* **What we have as a result (to check/validate)**
  * EC2 security group `public-ssh-http-81`  in `eu-central-1` region allowing SSH, HTTP, and TCP on port `81` access from the World
</details>   
   
Create Ubuntu EC2 Instance with custom EC2 security group and EC2 key pair
  | [text](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/get-set-up-for-amazon-ec2.html)
<details><summary>Show details</summary>

* **Details**
  * Use AWS Console 
  * Use any of the created IAM admin users
  * Use AWS Region: `Europe (Frankfurt) eu-central-1`
  * Use the following EC2 instance settings (all set as default with the exception of the specified)
    | [text](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/launching-instance.html)
    * Amazon Machine Image: `Ubuntu Server 20.04 LTS (HVM), SSD Volume Type`(Free tier eligible)
    * Instance type: `t2.micro` (Free tier eligible)
    * Instance tag key-value: `Name: ubuntu-console`
    * Security group name: `public-ssh-and-http`
    * **Choose an existing key pair** as wizard prompted
      * Select a key pair: `student-rsa|RSA` 
* **What we have as a result (to check/validate)**
  * **Running** Ubuntu EC2 instance (`ubuntu-console`) in `eu-central-1` region
</details>   
  
Connect to the created instance via SSH using **default user**
  | [text](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/connection-prereqs.html)(*)
<details><summary>Show details</summary>
  
* **What we have as a result (to check/validate)**
  * Ability to execute commands in shell of the created instance remotely via SSH
</details>   
  
Configure SSH daemon of the created instance to be more secure 
  | [text](https://aws.amazon.com/ru/premiumsupport/knowledge-center/ec2-ssh-best-practices/)(*)
<details><summary>Show details</summary>

* **Details**
  * Make sure that SSH access for Linux `root` user is prohibited
  * Make sure that SSH access using passwords is prohibited
  * Make sure that SSH access using passwords is prohibited
* **What we have as a result (to check/validate)**
  * SSH daemon is configured according to best practices
</details>   
  
Install `nginx` web server and set up a basic website (custom static page) over `http` on TCP port `81` — according to the referenced [tutorial](https://ubuntu.com/tutorials/install-and-configure-nginx#1-overview)(*)
  | [text](https://ubuntu.com/tutorials/install-and-configure-nginx#1-overview)
<details><summary>Show details</summary>

* **Details**
  * Make sure both default `nginx` welcome page (*Welcome to nginx*) and basic website (*Hello, Nginx!*) are accessible from all over the world  
* **What we have as a result (to check/validate)**
  * http request to TCP port 80 to public IP address or DNS name of the EC2 instance returns default nginx welcome page of Ubuntu AMI (*Welcome to nginx!*); http request to TCP port 81 to public IP address or DNS name of the EC2 instance returns custom static page (*Hello, Nginx!*)
</details>   
  
Add OS user to the Linux instance and provide it with SSH access (using its private key) with instance administrative privileges via `sudo`  
  | [text](https://aws.amazon.com/ru/premiumsupport/knowledge-center/new-user-accounts-linux-instance/)(*)
<details><summary>Show details</summary>
 
* **Details**
  * Use the following Linux OS user settings
    | [adduser(8)](http://manpages.ubuntu.com/manpages/trusty/man8/adduser.8.html) 
    * Username: `tutor-a`
    * Public key: `ssh-ed25519 AAAAC3NzaC1lZDI1NTE5AAAAIChvBKAJbIt0H0O26DbZnu2I0kHG+OJBEvR0UkgqWwFb tutor-a`
  * Provide user `tutor-a` with instance administrative privileges via `sudo`
    | [text](https://www.digitalocean.com/community/tutorials/how-to-edit-the-sudoers-file)(add) 
    * Add user `tutor-a` to the group: `sudo`
    * Use `visudo` command to enable all users in group `sudo` to run **any command as any user or member of any group** with `sudo` **without a password**
* **What we have as a result (to check/validate)**
  * User `tutor-a` has SSH access to the Linux EC2 instance (using its private key); user `tutor-a` is a member of  `sudo` group; members of group `sudo` can run any command as any user or member of any group with `sudo` without a password
</details>  
  
Stop the created EC2 instance
<details><summary>Show details</summary>
 
* **What we have as a result (to check/validate)**
  * **Stopped** Linux EC2 instance in `eu-central-1` region configured according to the following
    * Ubuntu Server 20.04 LTS OS installed
    * SSH daemon configured according to best practices
    * Web server `nginx` installed and accessible via `http` on TCP ports `80` and `81`
    * Members of the group `sudo` can run any command as any user or member of any group with `sudo` without a password
    * User `tutor-a` created and provided SSH access (using its private key) with instance administrative privileges via the group `sudo` membership  
</details>   
  
Start (just before the check) the created above (and now stopped) Amazon Linux 2 and Ubuntu instances and provide their public **IP addresses** (or DNS names) 
  | [text](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/connection-prereqs.html)(*)
<details><summary>Show details</summary>
 
* **What we have as a result (to check/validate)**
  * **Checkpoint**(01): please, **stop here** to check the results of your work before moving on
</details>  
  
  
  
  
  
