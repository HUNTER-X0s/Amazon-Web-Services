AWS RDS





Aws RDS service

Relational database service



AWS RDS is a managed database service that simplifies database setup, operation, and scaling 

The purpose is to handle administrative tasks like backups, patching, monitoring, and scaling. 





RDS Instance :

* Create an RDS MySQL instance. 
* Use free tier. 
* Username will be admin and you can set the password. You can't use a special character. 
* Keep the public access to true to access it from the local or remote server.
* Create a security group and allow 3306 from everywhere. 
* After creating you can find the endpoint host name to connect to this database. 



EC2 instance :

* sudo yum install -y docker
* sudo service docker start
* sudo usermod -aG docker ec2-user
* sudo docker pull philippaul/node-mysql-app:02





sudo docker run --rm -p 80:3000 -e DB\_HOST="database-1.ca5ucsoyqul3.us-east-1.rds.amazonaws.com" -e DB\_USER="admin" -e DB\_PASSWORD="#Hunter0s125" -d philippaul/node-mysql-app:02





sudo docker run -it --rm MySQL -h database-1.ca5ucsoyqul3.us-east-1.rds.amazonaws.com -u admin -p









Aurora offers :

* up to 5x the throughput of MySQL Community Edition and 3x of PostgreSQL.
* Up to 120 TB of auto-scaling SSD storage
* 6-way replication across three availability zones
* Up to 15 read replicas with replica lag under 10-ms
* Automatic monitoring with failover







Benefits of using RDS:

\- High availability and fault tolerance

\- Vertical and horizontal scaling

\- Automated backups and recovery

\- Read replicas for improved read performance

\- Multi-Availability Zones setup for DR (disaster recovery)

\- Cost Effectiveness 











RDS FEATURE: Managed Provisioning \& Scaling

HOW IT WORKS: AWS automatically provisions hardware, installs database software, and scales compute (CPU/RAM) or storage with a few clicks or API calls.

PURPOSE / USE CASE: Eliminates manual server setup, capacity planning, and hardware procurement. 



RDS FEATURE: Automated Backups

HOW IT WORKS: Captures daily volume backups and transaction logs, saving them to Amazon S3 with a configurable retention period.

PURPOSE / USE CASE: Enables Point-in-Time Recovery (PITR) to restore data down to the exact second. 



RDS FEATURE: Multi-AZ Deployment

HOW IT WORKS: Synchronously replicates data to a standby database instance in a different Availability Zone (AZ).

PURPOSE / USE CASE: Provides high availability and automatic failover if the primary instance fails. 



RDS FEATURE: Read Replicas

HOW IT WORKS: Asynchronously replicates data from the primary instance to one or more read-only database copies.

PURPOSE / USE CASE: Offloads heavy read traffic from the primary database to improve application performance. 



RDS FEATURE: Automated Patching

HOW IT WORKS: Automatically applies engine security updates and minor version patches during a user-defined weekly maintenance window.

PURPOSE / USE CASE: Ensures the database remains secure and updated without manual administrator intervention. 



RDS FEATURE: Storage Auto-Scaling

HOW IT WORKS: Monitors actual storage utilization and automatically expands database volume sizes when remaining space falls below thresholds.

PURPOSE / USE CASE: Prevents application downtime caused by storage volume exhaustion. 



RDS FEATURE: Database Monitoring \& Metrics

HOW IT WORKS: Integrates with Amazon CloudWatch and Enhanced Monitoring to track CPU, memory, IOPS, and query execution times.

PURPOSE / USE CASE: Helps developers diagnose performance bottlenecks and optimize slow database queries. 



RDS FEATURE: Security \& Isolation

HOW IT WORKS: Runs inside an Amazon VPC, integrates with IAM for access control, and offers built-in KMS encryption at rest and SSL/TLS in transit.

PURPOSE / USE CASE: Secures sensitive data from unauthorized network access and complies with regulatory standards.







Common use cases for RDS :

* web applications : Relational databases are ideal for web apps requiring structured data
* E-commerce platforms : for handling inventory, customer data, and order transactions
* Business applications : ERP, CRM, and financial applications with strong data integrity needs

## Remember RDS as an operated database, not an automatic application design

RDS manages database infrastructure tasks such as provisioning, patching options, backups, monitoring, and failover. Your application still needs a correct schema, connection pooling, query tuning, access control, and a recovery plan. A Multi-AZ standby is primarily for availability/failover; a read replica is primarily for scaling read traffic. They solve different problems.

Network access is a separate gate from database credentials: put the database in private subnets, allow the database port only from the app tier, and manage credentials securely. Automated backups support recovery within their retention window; a snapshot can outlive the instance and continue to cost money.

Aurora is an AWS relational database engine compatible with MySQL or PostgreSQL protocols. In the RDS console, creating Aurora provisions a DB cluster with a writer and optional readers, cluster endpoints, and storage behavior different from a single-instance RDS engine. Choose it for measured requirements, not simply because “it is newer.”

**Recall check:** The database accepts credentials from an admin laptop, but the app cannot connect. Check VPC/subnet routing and the DB security group's inbound source before changing the password.

**Credential safety:** A password-like literal remains in the original example above to preserve its content. Treat it as exposed, rotate it, and replace it with a placeholder before publishing this repository.

**Console practice:** [RDS walkthrough](guides/aws-console/amazon-rds.md) · [Secrets Manager walkthrough](guides/aws-console/secrets-manager.md)















