AWS EBS





AWS EBS Service

Elastic Block Store



AWS EBS is a cloud-based storage service that provides durable high-performance block storage for use with Amazon EC2 instances.



It works like a virtual hard drive, allowing you to store and access data even when your EC2 instances are stopped or terminated.





Use case :

For example if you are hosting a MySQL or PostgreSQL database, you need reliable high-performance storage to handle frequent read/write operations.



EBS provides persistent fast storage that ensures your data is saved even if the EC2 instance is stopped or restarted, making it ideal for database workloads.





Important points about EBS :

* Region and Availability Zone specific
* Built-in redundancy: EBS volumes are automatically replicated within the same availability zone to prevent data loss due to hardware failures.
* Different volume types:

\- GP2/3

\- I/O1/2

\- ST1

\- SC1

* Allow encryption and snapshot for backup.
* Scalable (Volume can be resized)

\- No data loss will occur during resizing.

\- No need to restart the EC2 instance during the process.

