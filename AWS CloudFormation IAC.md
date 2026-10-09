AWS CloudFormation IAC 





AWS CloudFormation is an infrastructure as code service that lets you define, provision, and manage AWS resources in a declarative template-based format. 





1\. Create or use an existing template.

2\. Save locally or in an S3 bucket.

3\. Use AWS CloudFormation to create a stack based on your template. It constructs and configures your stack resources.





* Code in YAML, yet another markup language, or JSON, JavaScript object notation directly, or use sample templates
* upload local files or from an S3 bucket
* create stack using API via AWS cloud formation. 
* Stacks and resources are provisioned as a running environment.





It provides :

* consistency : defines infrastructure in code
* automation : reduces manual work
* Repeatable : replicates the environment easily. 





* Infrastructure as code (IAC) tool : automates the creation, management, and operation of AWS infrastructure.
* Declarative language : users define desired end states for resources and cloudFormation handles provisioning. 
* Template-based : uses YAML or JSON templates to specify AWS resources and configurations. 
* AWS native : exclusively supports AWS resources, fully integrated with AWS services.
* State management : manages state internally, eliminating the need for separate state files. 
* Stacks and Stack Sets : organize resources in stacks for easier management and allow for multi-account and region deployments with Stack Sets.
* Cost-free tool : CloudFormation itself is free. You only pay for the AWS resources created.
* DRIFT DETECTION : identifies and reports on resource changes made outside of cloud formation to ensure resources stay aligned with the template.  





&#x20;Use Cases:

1\. Create EC2 instances with Security Groups and Elastic IPs

2\. Provision S3 buckets with HTTP endpoints

3\. Set up VPCs with subnets and route tables

4\. Create RDS databases with automatic backups

5\. Deploy Lambda functions with API Gateway integrations

6\. Set up Elastic Load Balancers and Autoscaling for web applications

7\. Deploy IAM roles, policies, and user access management

## Remember stacks as managed desired state

CloudFormation takes a declarative template and tries to make the account match it. The stack records ownership and dependency relationships so that a reviewed update can change several resources as one operation. Events tell you what happened; outputs expose values that other people or systems may need.

The safest learning habit is **read → validate → preview → apply → inspect**. A change set is the preview: pay special attention to replacements and deletions. Keep secrets out of templates and parameters that may be logged. Manually changing a stack-owned resource creates drift, so make durable changes through the template where practical.

**Recall check:** A stack update says a database will be replaced. What do you inspect before executing it? Data retention, snapshot/backup, replacement behavior, dependencies, and the change set.

**Console practice:** [CloudFormation walkthrough](guides/aws-console/cloudformation.md)











































