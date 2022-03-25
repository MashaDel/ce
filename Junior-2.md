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
 | [text](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/Stop_Start.html)
<details><summary>Show details</summary>

* **Details**
  * To start instance use AWS Console
* **What we have as a result (to check/validate)**
  * Ability to execute commands remotely (via SSH) in shell of the instance created in the previous section 
</details> 
Start the EC2 instance stopped in the previous section and connect to it via SSH as default user
 | [text](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/Stop_Start.html)
<details><summary>Show details</summary>

* **Details**
  * To start instance use AWS Console
* **What we have as a result (to check/validate)**
  * Ability to execute commands remotely (via SSH) in shell of the instance created in the previous section 
</details> 



