AWS : 

- AWS offers a vast range of services, including compute power, storage solutions, networking, databases, and much more. 
- It offers a pay as you go model , allowing you to pay only for what you use, which is ideal for optimizing costs.
- scalability, global reach, reliability, security


AWS IAM
Aws Identity and Access Management
- IAM is a service that helps you securely control access to AWS resources.
- It allows you to manage users, roles, and permissions to define who can access what within your AWS environment. 
- Free service : IAM is offered at no additional cost. 
- Global Service 
- Root account created by default should not be used or shared.

## Keep the AWS mental model connected

Most applications combine a few service roles: **identity** decides who may act (IAM), **networking** decides where traffic can travel (VPC), **compute** runs code (EC2/ECS/Lambda), and **storage/data** keeps files or records (S3/RDS/DynamoDB). Route 53, CloudFront, and load balancing guide user traffic; CloudWatch and CloudTrail help operate and audit the system.

AWS is a collection of services with separate configuration, permissions, and billing—not one automatically secure “cloud server.” Learn the boundary for each service, then trace a simple request through the parts.

**Recall check:** An EC2 workload needs to read a private S3 object. Name the two main controls: its IAM role permissions and the bucket/resource policy, plus KMS permission if the object uses a customer-managed key.
