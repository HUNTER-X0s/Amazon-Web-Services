1. What is Cloud Computing?

Cloud computing is the on-demand delivery of computing resources over the internet, such as:

Servers
Storage
Databases
Networking
Software
Security
Analytics
AI/ML services

Instead of buying and maintaining physical infrastructure yourself, you use infrastructure provided by a cloud provider and generally pay according to usage.

Example

Instead of buying:

Physical server → RAM → CPU → HDD → Networking → Power → Cooling → Maintenance

You can rent:

AWS EC2 → configure CPU/RAM → deploy application


2. Why Cloud Computing?

Know these advantages very well.

Scalability

Ability to increase or decrease resources according to demand.

Example:

10 users → 1 server
10,000 users → multiple servers

Elasticity

Resources automatically expand and shrink according to workload.

Scalability: ability to scale.

Elasticity: ability to dynamically scale based on demand.

Availability

System remains operational and accessible.

Reliability

System consistently performs correctly.

Cost efficiency

No need to purchase large amounts of hardware upfront.

Global reach

Applications can be deployed close to users around the world.

Agility

Resources can be provisioned quickly.

Disaster recovery

Cloud infrastructure can replicate data and services across locations.

3. Traditional Computing vs Cloud Computing
Traditional	Cloud
Buy hardware	Rent resources
Large upfront investment	Pay-as-you-go
Manual scaling	Easy/automatic scaling
Physical maintenance	Provider handles infrastructure
Limited capacity	Highly scalable
Longer deployment	Fast provisioning
Interview question

Why do companies use cloud computing?

Good answer:

Companies use cloud computing because it provides scalable, flexible and highly available infrastructure without requiring them to purchase and maintain large amounts of physical hardware.

4. Cloud Computing Characteristics

The classic characteristics are important.

On-demand self-service

Users can provision resources whenever required.

Broad network access

Resources are accessible through networks/internet.

Resource pooling

Cloud providers share physical infrastructure among multiple customers.

Rapid elasticity

Resources can scale rapidly.

Measured service

Usage is monitored and billed accordingly.

These five are commonly associated with the NIST definition.

5. Cloud Service Models

One of the most important interview topics.

IaaS — Infrastructure as a Service

You manage:

OS
Applications
Runtime
Data

Provider manages:

Physical hardware
Networking
Data center
Virtualization

Examples:

AWS EC2
Azure Virtual Machines
Google Compute Engine
Example

Renting an empty apartment.

You manage the inside.

6. PaaS — Platform as a Service

Provider manages more infrastructure.

You primarily manage:

Application
Data

Examples:

AWS Elastic Beanstalk
Azure App Service
Google App Engine
Example

Renting a furnished apartment.

7. SaaS — Software as a Service

You simply use the software.

Examples:

Gmail
Microsoft 365
Salesforce
Google Docs

Provider manages almost everything.

Example

Staying in a hotel.

8. IaaS vs PaaS vs SaaS

Remember this hierarchy:

IaaS → More control, more responsibility

PaaS → Less infrastructure management

SaaS → Almost everything managed by provider

9. FaaS / Serverless

FaaS = Function as a Service

You write functions and the cloud provider executes them when needed.

Example:

AWS Lambda

Other examples:

Azure Functions
Google Cloud Functions

You don't manage traditional servers directly.

Important

Serverless does NOT mean servers don't exist.

Servers still exist.

The provider manages them for you.

10. Cloud Deployment Models

Another very common interview topic.

Public Cloud

Infrastructure is provided by cloud providers to multiple customers.

Examples:

AWS
Microsoft Azure
Google Cloud
Private Cloud

Cloud infrastructure dedicated to one organization.

Useful when organizations require:

High control
Specific compliance
Custom security
Hybrid Cloud

Combination of:

Private Cloud + Public Cloud

Example:

Sensitive data → private infrastructure

Public website → AWS

Multi-Cloud

Using multiple cloud providers.

Example:

AWS + Azure + GCP

Important distinction:

Hybrid cloud ≠ multi-cloud

Hybrid:

public + private

Multi-cloud:

multiple cloud providers

11. Cloud Provider Basics

The three major providers:

AWS

Amazon Web Services

Azure

Microsoft Azure

GCP

Google Cloud Platform

For a fresher, understand their equivalent services.

Category	AWS	Azure	GCP
VM	EC2	Virtual Machines	Compute Engine
Object Storage	S3	Blob Storage	Cloud Storage
Database	RDS	Azure SQL	Cloud SQL
Serverless	Lambda	Functions	Cloud Functions
Kubernetes	EKS	AKS	GKE
Monitoring	CloudWatch	Azure Monitor	Cloud Monitoring
12. Region

A Region is a geographic area containing cloud infrastructure.

Examples:

Mumbai
Singapore
Frankfurt
Ohio

Different cloud providers use different names and structures internally, but the idea is geographic isolation.

Why regions?
Reduce latency
Data residency
Disaster recovery
Compliance
13. Availability Zone

An Availability Zone, usually called AZ, is an isolated infrastructure location within a region.

Example concept:

Region: Mumbai


    ├── AZ-1
    ├── AZ-2
    └── AZ-3

Using multiple AZs improves availability and fault tolerance.

14. Region vs Availability Zone

This is frequently asked.

Region:

Geographic area

Availability Zone:

Isolated location inside a region

15. Edge Location

Edge locations are locations closer to users where content can be cached or delivered.

Used heavily by services such as:

CDN

AWS example:

CloudFront

Purpose:

Reduce latency and improve content delivery speed.

16. Latency

Latency is the time taken for data/request to travel between source and destination.

Lower latency generally means faster response.

Example:

Indian user:

India server → lower latency

Indian user:

US server → potentially higher latency

17. Bandwidth

Bandwidth means the amount of data that can be transferred over a network in a given period.

Example:

1 Gbps connection

18. Scalability Types
Vertical Scaling

Increase resources of one machine.

Example:

4 CPU / 8 GB RAM
        ↓
8 CPU / 16 GB RAM

Also called:

Scale Up

Horizontal Scaling

Add more machines.

1 Server
   ↓
3 Servers
   ↓
10 Servers

Also called:

Scale Out

19. Load Balancer

A load balancer distributes incoming traffic across multiple servers.

Example:

             Users
                |
          Load Balancer
          /      |      \
      Server1 Server2 Server3

Benefits:

High availability
Traffic distribution
Scalability
Fault tolerance

AWS examples:

ALB
NLB
GWLB

For fresher interviews, knowing the concept is more important than memorizing every type.

20. Auto Scaling

Auto scaling automatically adjusts infrastructure capacity according to workload.

Example:

Normal traffic:

2 servers

Peak traffic:

8 servers

Traffic decreases:

3 servers

AWS:

Auto Scaling Groups

Azure:

Virtual Machine Scale Sets

21. Fault Tolerance

Fault tolerance means the system continues functioning even when some components fail.

Example:

If Server 1 fails:

Load Balancer
     |
 Server 2

continues serving users.

22. High Availability

High availability means minimizing downtime.

Often achieved through:

Multiple servers
Multiple AZs
Load balancers
Replication
Auto scaling
23. Disaster Recovery

Disaster recovery means restoring systems after major failures.

Examples:

Data center failure
Region outage
Hardware failure
Cyberattack
24. Backup vs Disaster Recovery
Backup

Copy of data.

Disaster Recovery

Complete strategy for restoring services/data after failure.

Backup is a component of disaster recovery.

25. RTO and RPO

Very important in cloud interviews.

RTO — Recovery Time Objective

Maximum acceptable time to restore service.

Example:

RTO = 2 hours

Means service should be restored within 2 hours.

RPO — Recovery Point Objective

Maximum acceptable amount of data loss measured in time.

Example:

RPO = 15 minutes

Means organization can tolerate losing approximately 15 minutes of data.

26. Virtualization

Virtualization allows multiple virtual machines to run on one physical machine.

Example:

Physical Server
      |
 Hypervisor
 ┌────┼────┐
VM1  VM2   VM3
27. Hypervisor

Software that creates/manages virtual machines.

Two broad categories:

Type 1

Runs directly on hardware.

Examples:

VMware ESXi
Microsoft Hyper-V
Xen
Type 2

Runs on top of an operating system.

Examples:

VirtualBox
VMware Workstation
28. Virtual Machine

A VM is a software-based computer running on physical infrastructure.

Contains:

CPU allocation
RAM
Disk
Network interface
Operating system

AWS example:

EC2 instance

29. Container

A container packages an application and its dependencies.

Examples:

Docker

Containers are generally lighter than VMs because they share the host OS kernel.

30. VM vs Container
VM	Container
Includes full guest OS	Shares host kernel
Heavier	Lightweight
Slower startup	Fast startup
Stronger isolation traditionally	Process-level isolation
More resource usage	Lower resource usage
31. Docker

Docker is a platform for creating and running containers.

Know these terms:

Image
Container
Dockerfile
Docker Hub
Volume
Network
Image

Blueprint/template.

Container

Running instance of an image.

32. Kubernetes

Kubernetes is a container orchestration platform.

It manages:

Container deployment
Scaling
Networking
Service discovery
Self-healing

AWS:

EKS

Azure:

AKS

GCP:

GKE

For fresher interviews, basic Kubernetes knowledge is enough unless you're targeting DevOps/cloud roles.

33. Storage Types

Very important.

Three major types:

Object Storage

Stores data as objects.

Examples:

AWS S3

Good for:

Images
Videos
Backups
Documents
Logs
Block Storage

Provides storage blocks attached to virtual machines.

Example:

AWS EBS

Good for:

Operating systems
Databases
Applications
File Storage

Provides shared filesystem access.

Examples:

AWS EFS

Multiple systems can access files.

34. Object vs Block vs File Storage
Type	Example	Typical Use
Object	S3	Images, backups
Block	EBS	VM disks
File	EFS	Shared files

This is very frequently asked in AWS interviews.

35. AWS S3

S3 = Simple Storage Service.

Important concepts:

Bucket
Object
Object key
Region
Storage class
Versioning
Lifecycle
Permissions
Bucket

Container for objects.

Object

Actual stored data.

36. S3 Storage Classes

Know the basic idea rather than every exact pricing detail.

Examples:

S3 Standard
S3 Intelligent-Tiering
S3 Standard-IA
S3 One Zone-IA
S3 Glacier
S3 Glacier Deep Archive

General principle:

Frequently accessed → faster/more available storage class

Rarely accessed → lower-cost archival class

37. EBS

EBS = Elastic Block Store.

Used with EC2.

Think:

EC2 = computer

EBS = disk attached to that computer

Common interview question:

Is EBS object storage?

No.

It is block storage.

38. AMI

AMI = Amazon Machine Image

It is a template used to create EC2 instances.

An AMI can contain:

OS
Applications
Configuration
Packages

Think:

AMI = blueprint/image for an EC2 machine

39. EBS vs AMI

This distinction matters.

EBS

Storage volume

AMI

Template used to launch an instance

40. EBS Snapshot

A snapshot is a point-in-time backup of an EBS volume.

Useful for:

Backup
Recovery
Creating new volumes
41. Database Fundamentals

Cloud interviews often ask database basics.

Understand:

SQL database

Structured relational data.

Examples:

MySQL
PostgreSQL
Oracle
SQL Server
NoSQL database

Non-relational data models.

Examples:

MongoDB
DynamoDB
Cassandra
42. SQL vs NoSQL
SQL

Good for:

Structured data
Relationships
Complex queries
Transactions
NoSQL

Good for:

Flexible schemas
Large-scale distributed workloads
High-speed access
Certain unstructured/semi-structured workloads
43. Managed Database

Cloud provider manages much of the infrastructure.

Examples:

AWS:

RDS

You generally don't have to manage:

Physical servers
Hardware maintenance
Many patching operations
Infrastructure provisioning

You still manage database-related configuration and usage.

44. AWS RDS

RDS = Relational Database Service.

Supports engines such as:

MySQL
PostgreSQL
MariaDB
Oracle
SQL Server
45. DynamoDB

AWS managed NoSQL database.

Important characteristics:

Key-value/document model
Highly scalable
Managed service
Low-latency access
46. Database Replication

Replication means maintaining copies of data on multiple systems.

Benefits:

Availability
Failover
Read scaling
Disaster recovery
47. Primary vs Replica

Primary database:

Handles writes

Replica:

Often used for reads / redundancy depending on architecture

48. Networking Fundamentals

You absolutely need basic networking.

Understand:

IP address
IPv4
IPv6
DNS
TCP
UDP
HTTP
HTTPS
Ports
Subnet
Routing
Firewall
49. IP Address

An IP address identifies a device/interface on a network.

Example:

192.168.1.10

50. Public vs Private IP
Public IP

Accessible through the public internet, subject to security controls.

Private IP

Used within private networks.

Private IPv4 ranges include:

10.0.0.0/8

172.16.0.0/12

192.168.0.0/16

51. DNS

DNS = Domain Name System.

It translates domain names into IP addresses.

Example:

google.com
     ↓
IP address

Instead of remembering:

142.x.x.x

you use:

google.com

52. TCP vs UDP
TCP
Connection-oriented
Reliable
Ordered
Error handling

Used by:

HTTP/HTTPS
SSH
FTP
UDP
Connectionless
Faster
No delivery guarantee

Used in workloads such as:

DNS
Streaming
Gaming
VoIP
53. HTTP vs HTTPS

HTTP:

Unencrypted application protocol

HTTPS:

HTTP over TLS encryption

HTTPS provides:

Encryption
Integrity
Authentication of the server via certificates
54. Port

A port identifies a network service/application endpoint.

Common ports:

Port	Protocol
22	SSH
80	HTTP
443	HTTPS
53	DNS
3306	MySQL
5432	PostgreSQL
3389	RDP

Memorize the common ones.

55. VPC

AWS VPC = Virtual Private Cloud

It provides an isolated virtual network for AWS resources.

Within a VPC you configure things such as:

Subnets
Route tables
Internet gateways
NAT gateways
Security groups
Network ACLs

This is one of the most important AWS fundamentals.

56. Subnet

A subnet is a range of IP addresses within a network.

Example:

VPC
 |
 ├── Public Subnet
 └── Private Subnet
57. Public Subnet vs Private Subnet

A subnet is commonly considered public when its route table provides a route to an Internet Gateway.

Private subnet:

No direct route to the internet through an Internet Gateway.

Typical architecture:

Internet
   |
Load Balancer
   |
Public subnet
   |
Private subnet
   |
Database
58. Internet Gateway

Allows resources in a VPC to communicate with the internet when appropriate routing and public addressing/security are configured.

59. NAT Gateway

Allows resources in private subnets to initiate outbound connections to the internet without directly exposing those resources to unsolicited inbound internet traffic.

Example:

Private EC2
    |
 NAT Gateway
    |
 Internet
60. Route Table

A route table determines where network traffic goes.

Example:

0.0.0.0/0 → Internet Gateway

means traffic for other destinations is sent toward the Internet Gateway.

61. Security Group

AWS Security Groups are virtual firewalls associated with supported network interfaces/resources.

Important:

Stateful

If inbound traffic is allowed, the response traffic is automatically allowed.

62. Network ACL

NACL = Network Access Control List.

Operates at subnet level.

Important difference:

Security Group
Instance/network-interface level
Stateful
Allow rules
NACL
Subnet level
Stateless
Supports allow and deny rules

This is a classic AWS interview question.

63. IAM

IAM = Identity and Access Management

Used to control who can access what.

Important concepts:

User
Group
Role
Policy
Permission
Authentication
Authorization
64. Authentication vs Authorization
Authentication

Who are you?

Example:

Username + password

Authorization

What are you allowed to do?

Example:

Can read S3 but cannot delete S3 objects.

65. IAM User

Represents an identity, historically commonly used for a human/application identity.

However, AWS best practices generally favor temporary credentials and IAM roles for workloads over long-lived access keys.

66. IAM Role

A role provides permissions that can be assumed by trusted entities such as:

AWS services
Users
Applications

Example:

EC2 needs S3 access.

Instead of storing AWS access keys inside the application:

Attach an IAM role to EC2.

67. IAM Policy

A policy defines permissions.

Conceptually:

Who → Can perform what → On which resource

Example:

Allow reading objects from a particular S3 bucket.

68. Least Privilege

Give users/applications only the permissions they actually need.

Bad:

Full AdministratorAccess

Better:

Read-only access to a specific bucket.

This concept is extremely important in security interviews.

69. Encryption

Two common forms:

Encryption at Rest

Data stored on disk is encrypted.

Encryption in Transit

Data moving through networks is encrypted.

Examples:

HTTPS / TLS

70. Key Management

Cloud providers provide key-management systems.

AWS:

KMS

KMS is used to create/manage cryptographic keys and support encryption workflows.

71. Secrets Management

Never put passwords/API keys directly in source code.

Use services such as:

AWS Secrets Manager

or equivalent secret-management systems.

72. Monitoring

Monitoring means observing system health and performance.

Metrics can include:

CPU utilization
Memory
Network traffic
Request count
Latency
Error rate

AWS:

CloudWatch

73. Logging

Logs record events.

Examples:

Application errors
User actions
API requests
Authentication attempts
System events

AWS examples:

CloudWatch Logs

CloudTrail

74. CloudTrail

CloudTrail records AWS API activity and account actions.

Example:

Who deleted an S3 bucket?

CloudTrail can help answer:

Which identity made the API call?

Think:

CloudWatch → monitoring

CloudTrail → API/account activity auditing

75. CDN

CDN = Content Delivery Network.

Stores/caches content at locations closer to users.

Example:

AWS CloudFront

Useful for:

Images
Videos
CSS
JS
Static websites

Main benefit:

Reduced latency.

76. Caching

Caching stores frequently requested data temporarily for faster retrieval.

Examples:

Browser cache
CDN cache
Redis
Memcached
77. Message Queue

Queues allow systems to communicate asynchronously.

Example:

Application
     |
    Queue
     |
 Worker

Benefits:

Decoupling
Reliability
Traffic smoothing
Asynchronous processing

AWS:

SQS

78. Pub/Sub

Publish-subscribe architecture allows publishers to send messages to topics and subscribers receive them.

AWS:

SNS

Example:

Publisher
    ↓
 Topic
 /   \
App1 App2
79. SQS vs SNS
SQS

Queue

Typically a consumer processes messages from the queue.

SNS

Publish/Subscribe notification service

One message can be delivered to multiple subscribers.

80. API Gateway

API Gateway manages APIs.

Common responsibilities:

Receiving requests
Routing
Authentication/authorization integration
Throttling
Monitoring

AWS:

API Gateway

81. Microservices

Instead of building one huge application, divide the application into smaller services.

Example:

User Service
Payment Service
Order Service
Notification Service

Benefits:

Independent deployment
Scaling
Fault isolation
Team autonomy

Challenges:

Distributed-system complexity
Network failures
Monitoring
Data consistency
82. Monolith vs Microservices
Monolith

One large application.

Microservices

Multiple independently deployable services.

For fresher interviews, understand both advantages and disadvantages.

83. Serverless Architecture

Example:

User
 ↓
API Gateway
 ↓
Lambda
 ↓
DynamoDB

Advantages:

No traditional server management
Automatic scaling
Pay based on usage
Fast deployment

Disadvantages:

Cold starts
Vendor lock-in
Execution limits
Debugging complexity
84. Cloud Pricing Models

Know these:

Pay-as-you-go

Pay according to usage.

Reserved / commitment-based pricing

Commit to usage for lower rates where applicable.

Spot / interruptible instances

Use spare cloud capacity at reduced cost, but workloads may be interrupted.

AWS example:

EC2 Spot Instances

85. CapEx vs OpEx

Very common conceptual question.

CapEx

Capital expenditure.

Example:

Buying servers for a data center.

OpEx

Operating expenditure.

Example:

Paying cloud bills for infrastructure usage.

Cloud computing often shifts spending from:

CapEx → OpEx

86. Shared Responsibility Model

Extremely important.

The cloud provider is responsible for security of the cloud.

Customer is responsible for security in the cloud, depending on the service.

For example:

AWS handles:

Physical data centers

Customer handles:

IAM permissions

Data

Application security

OS patching for EC2

87. AWS Shared Responsibility Example

With EC2:

AWS:

Physical hardware, data center, virtualization infrastructure

Customer:

Guest OS

Applications

Security configuration

IAM

Data

With managed services, AWS may manage more layers.

88. Data Center

A data center is a physical facility containing:

Servers
Storage
Networking
Power
Cooling
Physical security

Cloud providers operate massive data centers globally.

89. SLA

SLA = Service Level Agreement.

It defines service expectations such as:

Availability
Support
Service commitments

For example:

99.9% availability commitment

Understand that SLA is generally a contractual/service commitment, not a guarantee that outages never happen.

90. Availability Calculation

A common interview concept.

99.9% availability means approximately:

0.1% downtime

99.99% availability:

0.01% downtime

You should understand the basic concept of "nines."

91. Horizontal vs Vertical Scaling

Interview scenario:

Traffic increased suddenly. How would you scale?

Possible solutions:

Horizontal scaling + Load Balancer + Auto Scaling

Vertical scaling:

Increase CPU/RAM of existing instance.

92. Stateless vs Stateful
Stateless

Each request can be handled independently.

Example:

REST API servers

Stateful

Server retains information about previous interactions.

Example:

Some session-based applications

Cloud architectures usually favor stateless application servers because they are easier to scale horizontally.

93. Session Management in Cloud

Instead of storing sessions only on one server, use shared storage such as:

Redis

or other centralized session mechanisms.

This prevents problems when requests move between servers.

94. Elasticity vs Scalability

Interview favorite.

Scalability

Ability to handle increasing workload by adding resources.

Elasticity

Ability to automatically add/remove resources according to workload.

95. Availability vs Durability

Another common question.

Availability

Can I access the service/data?

Durability

Will my data remain intact over time?

For example:

A storage service can have extremely high durability while still experiencing temporary unavailability.

96. Reliability vs Availability
Availability

System is accessible.

Reliability

System consistently performs correctly over time.

97. Idempotency

An operation is idempotent if performing it multiple times has the same intended final effect as performing it once.

Example:

Setting a resource to a particular state.

This is important in distributed systems and cloud APIs.

98. Stateless Architecture

Example:

Users
  |
Load Balancer
 /    |    \
API  API   API
 \    |    /
  Shared DB/Cache

Any API server can handle the request.

This makes scaling easier.

99. Decoupling

Decoupled systems reduce direct dependencies between components.

Example:

Order Service
     |
     ↓
Message Queue
     |
     ↓
Notification Service

Order service does not need notification service to process the request synchronously.

100. Infrastructure as Code

IaC means defining infrastructure using code/configuration.

Tools:

Terraform
AWS CloudFormation
Azure Bicep

Instead of manually creating:

20 servers + networking + databases

you define infrastructure declaratively.

Benefits:

Repeatability
Version control
Automation
Consistency
101. CI/CD

CI = Continuous Integration.

Developers frequently integrate code and run automated tests/builds.

CD can mean:

Continuous Delivery

or

Continuous Deployment

depending on the organization.

Typical pipeline:

Code
 ↓
Git
 ↓
Build
 ↓
Test
 ↓
Deploy
102. DevOps

DevOps combines development and operations practices to improve:

Automation
Collaboration
Deployment speed
Reliability

Cloud is commonly used as infrastructure for DevOps workflows.

103. Git

Know basic Git concepts:

Repository
Commit
Branch
Merge
Pull Request
Push
Pull

Cloud interviews sometimes combine:

Git + CI/CD + cloud deployment.

104. Infrastructure Components You Should Know

For an AWS-oriented fresher, understand this architecture:

                 INTERNET
                    |
                   DNS
                    |
                  CDN
                    |
             Load Balancer
                    |
          -------------------
          |                 |
       EC2/AZ1           EC2/AZ2
          |                 |
          ---------+---------
                   |
                Database
                   |
                 Backup

And networking:

VPC
 |
 ├── Public Subnet
 │     └── Load Balancer
 │
 └── Private Subnet
       ├── Application Servers
       └── Database
105. AWS Core Services You Should Know as a Fresher

Given your goal of getting an IT job, I would prioritize these.

Compute

EC2

Lambda

ECS

EKS — basic awareness

Storage

S3

EBS

EFS

Database

RDS

DynamoDB

Networking

VPC

Subnet

Internet Gateway

NAT Gateway

Route Table

Security Group

NACL

Route 53

CloudFront

Load Balancer

Security

IAM

KMS

Secrets Manager

Monitoring

CloudWatch

CloudTrail

Messaging

SQS

SNS

Scaling

Auto Scaling

Infrastructure

CloudFormation

Containers

Docker

Kubernetes — fundamentals

106. AWS Services You Mentioned Previously

You specifically asked about these services earlier, and yes, they are worth knowing.

EBS

Think:

EC2 disk

AMI

Think:

EC2 machine template

ELB

Think:

Traffic distributor

ASG

Think:

Automatically maintain the number of EC2 instances

Together:

User
 ↓
ELB
 ↓
ASG
 ↓
EC2
 ↓
EBS

AMI:

Used to create EC2 instances.

107. ELB + ASG Interview Scenario

Question:

Website traffic suddenly increases from 1,000 users to 100,000 users. What would you do?

A strong beginner answer:

I would place the application behind a load balancer and use an Auto Scaling Group to automatically increase the number of application instances based on demand. I would distribute instances across multiple Availability Zones for high availability.

That answer demonstrates several cloud concepts simultaneously.

108. Security Fundamentals

You should understand:

Authentication

Who are you?

Authorization

What can you do?

Encryption

Protect data.

Least privilege

Minimum required permissions.

MFA

Additional authentication factor.

Firewall

Controls network traffic.

Secrets management

Protect passwords/API keys.

Logging

Track activity.

Security monitoring

Detect suspicious activity.

109. Zero Trust — Basic Knowledge

Modern security concept:

Never automatically trust a user/device simply because it is inside a network.

Instead:

Verify identity → verify permissions → continuously monitor.

You don't need deep Zero Trust knowledge for most fresher interviews, but understand the principle.

110. Common Cloud Security Mistakes

Interviewers may give scenarios.

Mistake

S3 bucket publicly accessible.

Mistake

AWS access keys committed to GitHub.

Mistake

Allowing SSH from:

0.0.0.0/0

Mistake

Giving every user Administrator privileges.

Mistake

Storing passwords in source code.

Better practices

IAM roles

Least privilege

MFA

Secrets Manager

Restricted Security Groups

Encryption

Logging

111. 3-Tier Architecture

A classic architecture:

Presentation Layer
        ↓
Application Layer
        ↓
Database Layer

Cloud:

Internet
   ↓
Load Balancer
   ↓
Application Servers
   ↓
Database

This is a very common interview topic.

112. Monolithic Cloud Architecture

Example:

User
 ↓
One EC2
 ↓
Database

Simple but may have scaling and fault tolerance limitations.

113. Highly Available Architecture

Better:

                 Load Balancer
                /             \
           AZ-1                AZ-2
            |                    |
          EC2                  EC2
             \                /
               Database

If one AZ has problems, the other can continue handling traffic.

114. Disaster Recovery Strategies

Know the broad categories:

Backup and Restore

Lowest complexity/cost, slower recovery.

Pilot Light

Minimal core infrastructure running.

Warm Standby

Scaled-down copy running.

Multi-site / Active-Active

Multiple environments actively serving workloads.

General rule:

Faster recovery usually costs more.

115. RPO/RTO Scenario

Suppose a company says:

"We can lose at most 5 minutes of data and service must recover within 30 minutes."

Then:

RPO = 5 minutes

RTO = 30 minutes

Memorize this distinction.

116. Cloud Migration

Know the basic migration strategies, often called the 7 Rs:

Retain
Retire
Rehost
Relocate
Repurchase
Replatform
Refactor

For fresher interviews, focus especially on:

Rehost

"Lift and shift."

Move application with minimal changes.

Replatform

Make some optimizations without redesigning everything.

Refactor

Redesign application to take better advantage of cloud-native capabilities.

117. Vendor Lock-in

Vendor lock-in means becoming heavily dependent on one cloud provider's technologies, making migration difficult.

Example:

Using many provider-specific services may make migration from AWS → Azure harder.

118. Multi-Tenant Architecture

Multiple customers share underlying infrastructure while their data/resources remain logically isolated.

Cloud providers commonly use multi-tenancy.

119. Resource Pooling

Cloud providers dynamically allocate pooled infrastructure among customers according to demand.

This enables high utilization and economies of scale.

120. Cloud Native

Cloud-native applications are designed specifically to exploit cloud capabilities.

Common characteristics:

Containers
Microservices
Automation
APIs
Managed services
Elastic scaling
Observability
121. Observability

Modern cloud systems talk about three major signals:

Metrics

Numbers.

Example:

CPU = 72%

Logs

Event records.

Traces

Track a request through distributed services.

Example:

API
 ↓
Auth Service
 ↓
Order Service
 ↓
Payment Service

Tracing helps identify where latency occurs.

122. Health Check

A health check determines whether a service/server is functioning correctly.

Load balancers often use health checks to avoid sending traffic to unhealthy instances.

123. Blue-Green Deployment

Two environments:

Blue = Current
Green = New

Deploy new version to Green.

After testing:

Switch traffic to Green.

Easy rollback by switching traffic back.

124. Canary Deployment

Release a new version to a small percentage of users first.

Example:

5% → 25% → 50% → 100%

Useful for reducing deployment risk.

125. Rolling Deployment

Gradually replace old instances with new instances.

Example:

Old Old Old Old
↓
New Old Old Old
↓
New New Old Old
↓
New New New Old
↓
New New New New
126. Container Registry

Stores container images.

AWS:

ECR

Docker ecosystem:

Docker Hub

127. What Happens When You Open a Website?

This is an excellent interview question.

Suppose you enter:

https://example.com

Basic flow:

Browser
 ↓
DNS lookup
 ↓
IP address
 ↓
TCP connection
 ↓
TLS handshake
 ↓
HTTP request
 ↓
Load Balancer
 ↓
Application Server
 ↓
Database
 ↓
Response
 ↓
Browser

Understanding this flow makes you look much stronger in interviews.

128. Common Cloud Interview Scenarios

Prepare these carefully.

Scenario 1

Your EC2 server is unreachable. What do you check?

Think:

Instance state

Security Group

NACL

Route table

Internet Gateway

Public/private IP

SSH configuration

CPU/memory

Scenario 2

Application is slow. What do you check?

Think:

CPU

Memory

Network

Database performance

Application logs

Latency

Load balancer metrics

CloudWatch

Scenario 3

Traffic suddenly increases.

Think:

Load Balancer + Auto Scaling + multiple AZs

Scenario 4

Database should not be publicly accessible.

Put it in:

Private subnet

and restrict access using security controls.

Scenario 5

EC2 needs S3 access.

Best practice:

IAM Role

Not hard-coded credentials.

129. Most Asked Fresher Cloud Questions

You should be able to answer these without hesitation:

What is cloud computing?
What are the benefits of cloud computing?
What is IaaS?
What is PaaS?
What is SaaS?
What is serverless?
What is virtualization?
What is a hypervisor?
What is a VM?
What is a container?
What is Docker?
What is Kubernetes?
What is a region?
What is an Availability Zone?
What is an edge location?
What is scalability?
What is elasticity?
Vertical vs horizontal scaling?
What is load balancing?
What is auto scaling?
What is high availability?
What is fault tolerance?
What is disaster recovery?
What are RTO and RPO?
What is a VPC?
What is a subnet?
Public vs private subnet?
What is an Internet Gateway?
What is NAT Gateway?
What is a route table?
Security Group vs NACL?
What is IAM?
Authentication vs authorization?
What is least privilege?
What is encryption?
Encryption at rest vs transit?
What is S3?
What is EBS?
What is EFS?
EBS vs S3?
What is AMI?
What is an EBS snapshot?
What is RDS?
SQL vs NoSQL?
What is DynamoDB?
What is DNS?
TCP vs UDP?
HTTP vs HTTPS?
What is CDN?
What is CloudWatch?
What is CloudTrail?
What is SQS?
What is SNS?
What is API Gateway?
What is Lambda?
What is Infrastructure as Code?
What is Terraform?
What is CI/CD?
What is DevOps?
What is cloud migration?
What is vendor lock-in?
What is shared responsibility?
What is multi-cloud?
What is hybrid cloud?
What is cloud-native architecture?
130. What You Should Actually Learn for a Fresher Job

Do not try to memorize 200 AWS services.

Build your knowledge in this order:

Level 1 — Must Know

Cloud fundamentals:

Cloud computing
IaaS/PaaS/SaaS
Public/private/hybrid cloud
Region/AZ
Scalability/elasticity
High availability
Disaster recovery
Virtualization

Level 2 — Networking

IP
DNS
TCP/UDP
HTTP/HTTPS
Ports
VPC
Subnet
Routing
Internet Gateway
NAT
Security Groups
NACL

Level 3 — AWS Core

EC2
S3
EBS
AMI
EBS Snapshot
ELB
Auto Scaling
IAM
RDS
Lambda
CloudWatch
CloudTrail
Route 53
CloudFront

Level 4 — Practical Development/DevOps

Linux basics
Git/GitHub
Docker
CI/CD
Terraform
Basic Kubernetes

Level 5 — Architecture

Learn to design:

3-tier application

Highly available web application

Scalable REST API

Static website

Serverless application

Basic microservices architecture

131. The Most Important AWS Mental Model

Remember this:

                     AWS
                      |
        +-------------+-------------+
        |             |             |
      Compute       Storage       Database
        |             |             |
       EC2           S3            RDS
       Lambda        EBS           DynamoDB
        |
     Networking
        |
       VPC
        |
   +----+----+
   |         |
Subnet     Routing
   |
Security
   |
IAM + SG + NACL

Then add:

        Traffic
           |
      Route 53
           |
       CloudFront
           |
      Load Balancer
           |
      Auto Scaling
           |
          EC2
           |
          RDS

And monitoring:

Everything
    |
CloudWatch
    |
CloudTrail
132. Fresher Interview Depth

For a normal Software Developer / Backend Developer / Cloud Developer fresher, I would target approximately:

Cloud fundamentals: 9/10

AWS core services: 8/10

Networking: 7/10

Linux: 7/10

Docker: 6/10

CI/CD: 5/10

Terraform/IaC: 4–5/10

Kubernetes: 3–5/10

Advanced cloud architecture: 3–4/10

You do not need to be a cloud architect to clear a fresher software interview.

133. One Critical Point for Your Preparation

Since you're targeting IT/software roles, don't study cloud as a list of AWS definitions.

Be able to explain a complete application:

User
 ↓
Route 53
 ↓
CloudFront
 ↓
Load Balancer
 ↓
Auto Scaling Group
 ↓
EC2 instances
 ↓
RDS
 ↓
S3

and explain:

Why each service is there.

For example:

Why Load Balancer?

Distributes traffic.

Why Auto Scaling?

Automatically adjusts instance count.

Why multiple AZs?

Improve availability and fault tolerance.

Why RDS?

Managed relational database.

Why S3?

Object storage for files/backups/static assets.

That is much closer to how interviewers evaluate actual understanding.

Your target

For a fresher AWS/cloud-aware developer, a very strong foundation is:

Cloud fundamentals + Networking + Linux + AWS core services + Git + Docker + basic CI/CD + one deployed project.

With that combination, you are much more interview-ready than someone who simply memorizes 50 AWS services.

## Fast recall framework: explain the job, then the boundary

For any cloud topic, answer four questions: **What problem does it solve? What does it manage for me? What do I still configure? What can fail or cost money?** This turns a memorized definition into an explanation that survives follow-up questions.

Use this architecture spine as a retrieval cue:

`DNS → CDN → load balancer → scalable compute → database/object storage`

Then add identity, network isolation, messaging, monitoring, audit logs, backups, and deployment automation. Each service should have a reason in the design: Route 53 names endpoints, CloudFront caches/delivers, ELB distributes traffic, Auto Scaling adjusts instance count, EC2 runs a server, RDS stores relational data, and S3 stores objects.

When comparing concepts, state the axis explicitly: **availability vs durability; scalability vs elasticity; Multi-AZ vs read replica; EBS vs S3 vs EFS; CloudWatch vs CloudTrail; public vs private subnet**. This makes the contrast memorable and prevents mixing the terms.

**Active-recall drill:** Hide the page and sketch one request path from URL to database. For every arrow, say what it does, which identity is used, and one likely failure. Revisit the answer after a day and a week rather than rereading the whole guide passively.

**Console practice:** Use the dedicated [AWS Console Field Guides](guides/aws-console/README.md) to turn each concept into a small, cleanable exercise.
