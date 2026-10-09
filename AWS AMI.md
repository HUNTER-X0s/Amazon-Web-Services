AWS AMI


AWS AMI Service
Amazon Machine Image

An Amazon machine image (AMI) is a pre-configured template that provides the necessary information to launch an EC2 instance in AWS.
It includes:
- operating system (example: Windows, Linux)
- applications (example: Apache, Nginx)
- pre-installed software and configurations


- With an AMI you can launch new EC2 instances with a consistent predefined configuration. 

- You can also create custom AMIs to include specific software or settings, allowing for quick replication of environments. 


Types of AWS AMIs :- 
- public AMIs : available to all AWS users. useful for basic use cases like popular operating systems for example Ubuntu, CentOS 
- private AMIs : Created by a user and only available within that account or shared with specific accounts  
- paid AMIs / marketplace AMIs : provided by third parties through AWS marketplace offering software like databases, web servers or pre-configured environments


Use case of paid AMI's benefits:
- Rapid deployment: the LAMP stack is pre-configured, eliminating the need to manually install and configure Apache, MySQL, and PHP.
- Scalability and load balancing: running on AWS enables quick scaling to match website traffic while Elastic Load Balancer helps in distributing requests.
- Cost efficiency : you only pay for the infrastructure and software according to your usage.




Run Cleanup Script :

#!/bin/bash

# 1. Stop logging services
sudo systemctl stop rsyslog
sudo systemctl stop auditd

# 2. Purge and clear all system logs
sudo logrotate -f /etc/logrotate.conf
sudo rm -f /var/log/*-???????? /var/log/*.gz
sudo find /var/log -type f -exec truncate -s 0 {} \;

# 3. Wipe temporary folders and caches
sudo rm -rf /tmp/* /var/tmp/*
sudo yum clean all || sudo dnf clean all

# 4. Remove network persistent rules
sudo rm -f /etc/udev/rules.d/70-persistent-net.rules

# 5. Remove unique SSH server host keys
sudo rm -f /etc/ssh/ssh_host_*

# 6. Remove authorized SSH keys and credentials
rm -rf ~/.ssh/authorized_keys
sudo rm -rf /root/.ssh/authorized_keys
sudo passwd -l root

# 7. Remove non-default user accounts
for user in $(awk -F: '$3 >= 1000 && $1 != "ec2-user" {print $1}' /etc/passwd); do sudo userdel -r "$user"; done
sudo find /etc/sudoers.d/ -type f ! -name "90-cloud-init-users" -exec rm -f {} \;

# 8. Reset system configuration files
sudo sed -i '/^HOSTNAME=/d' /etc/sysconfig/network
sudo rm -f /etc/hostname
sudo rm -rf /var/lib/cloud/instances/*

# 9. Clean up Vim history and file swaps
rm -rf ~/.viminfo ~/.lesshst
sudo rm -rf /root/.viminfo /root/.lesshst
sudo find /home /root -name ".viminfo" -o -name "*.swp" -o -name "*.swo" -exec rm -f {} \;

# 10. Clear user terminal command histories
cat /dev/null > ~/.bash_history
sudo cat /dev/null > /root/.bash_history
history -c



| Feature / Category   		| Create Image (AMI)                             		     | Create Launch Template                                            |
|----------------------------|-------------------------------------------------- |-----------------------------------------------------|
| **What it is**     		        | Complete snapshot of your server's data.           | Configuration blueprint specifying how to build.   |
| **What it stores**    		| Operating system, files, and application data.    | Instance type, security groups, and key pairs.         |
| **Relationship**      		| It acts as a virtual hard drive disk image.              | It references an AMI inside its configurations.	       |
| **Mutability**        		| Immutable. Cannot be edited once created.      | Versioned. Supports editing as v2, v3, etc.               |
| **Primary Use Case**  	| Freezing a sanitized system before scaling.        | Powering Auto Scaling Groups and architectures.  |
| **Billing Impact**    		| Incurs monthly charges for storage used (GB).   | Completely free to create and store templates.      |



Summary :
- Yes all installed applications, configuration settings, environment variables, network configurations, DNS settings, users, and firewall settings will be included in the AMI.
- An AMI is essentially a complete snapshot of the instance at the point in time you created the image, allowing you to replicate the exact state of that server, including all software configuration and operating system-level changes.
- When you create an EC2 instance from this AMI, it will go top as if it were an exact clone of the original, with all installed software and settings in fact. 


EC2 Image Builder  :
- Automate VM or image creation
Creation, testing, and deployment of AMIs. 
- can be configured to run at regular intervals (example: daily, weekly, or monthly). 
- free. 

