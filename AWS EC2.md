AWS EC2



Elastic Cloud Compute
AWS EC2 (Amazon Elastic Compute Cloud) is a cloud service that provides resizable virtual servers called instances, which you can run applications on.

* Instead of buying and managing physical servers, AWS EC2 lets you rent virtual servers in the cloud. These virtual servers are called instances.

You can configure several options :

* Which operating system
* How much RAM
* Which CPU
* Cores
* Disk space
* Network
* Firewall
* How to access the machine

Instance type : Select the hardware capacity, Example: CPU, memory
AMI (Amazon machine image) : Choose the operating system and software: Linux, Mac, Windows
Storage: configure the type and size of storage (example: EBS volume)
Security groups: set up firewall rules to control inbound and outbound traffic
Key pair: create or use an existing key pair for SSH access
Network settings: configure VPC, subnet, and assign public or private IP addresses.
Attach an IAM role for permissions to access other AWS resources.
User data: scripts to be executed when the instance starts.
Elastic IP: optionally associate a static IP address for consistent public access.

Security groups :- network firewall rules that control inbound and outbound traffic for instances

Important points about security groups :

* Region-specific
* only allow rule but no deny rule.
* All inbound traffic blocked and outbound allowed by default.
* You defined rules for specific :
protocols like HTTP/HTTPS, SSH etc
port numbers (example port 80 for HTTP, port 22 for SSH)
IP addresses or range. Allow traffic only from a specific IP or range of IPs.
* If you allow incoming traffic on a specific port (example port 80 for HTTP), the outgoing response traffic is automatically allowed without an explicit outbound rule.





HTTP (port 80) - unencrypted web traffic
HTTPS (port 443) - encrypted web traffic, SSL/TLS
SSH (port 22) - secure remote access to servers (Linux/Unix)
FTP (port 21) - file transfer protocol (Unsecured)
SFTP (port 22) - secure file transfer protocol
SMTP (port 25) - simple mail transfer protocol, email sending
RDP (port 3389): remote desktop protocol, Windows remote access
MySQL (port 3306) - MySQL database connections
PostgreSQL (port 5432) - PostgreSQL database connections
DNS (port 53) - domain name system, converts domain names into IP addresses

SSL: Secure Sockets Layer
TLS: Transport Layer Security







How to SSH into EC2 instance?
SSH allows you to control/access a remote machine



1. Case 1: Small website/blog
suitable type : t3.micro or t3.small for the general purpose.
2. Case 2: E-commerce application
suitable type : m5.large or m5.xlarge for the general purpose.
3. Case 3: Real-time video rendering and streaming (accelerated computing)
instance type: g5.12xlarge or g5.24xlarge.
4. Case 4: in-Memory Database for Real-Time Analytics (Memory Optimized)
r6g.16xlarge or x2idn.32xlarge (Memory Optimized).

## Remember an EC2 launch as five choices

An instance needs an **image** (AMI), a **shape** (instance type), a **home** (VPC/subnet), an **identity** (instance role), and **storage** (EBS or instance store). A security group filters network access; it does not log you in. A key pair or Systems Manager access method handles administration, while the IAM role authorizes AWS API calls from the workload.

Running instances can incur compute charges even when idle. Stopping an EBS-backed instance pauses its compute billing, but storage and attached resources may still cost money. Termination can delete attached volumes according to their delete-on-termination settings, so check backups first.

**Recall check:** An app on EC2 cannot read S3. Where should you first check? The instance profile/role and its permission policy, then connectivity if the call still fails.

**Console practice:** [EC2 walkthrough](guides/aws-console/amazon-ec2.md) · [AMI walkthrough](guides/aws-console/ami-image-builder.md)

