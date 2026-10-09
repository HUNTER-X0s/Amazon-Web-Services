AWS IAM


Aws Identity and Access Management
- IAM is a service that helps you securely control access to AWS resources.
- It allows you to manage users, roles, and permissions to define who can access what within your AWS environment. 
- Free service : IAM is offered at no additional cost. 
- Global Service 
- Root account created by default should not be used or shared. 

- Create users : You can create individual user accounts for people who need access to your AWS resources.
- Assign permissions : You can assign specific permissions to users, groups, or roles to control what actions they can perform on AWS services.
- Create groups : You can group users together and assign permissions to the group, making management easier for multiple users.
- Create roles to assign temporary permissions to AWS services or users, especially useful for securely managing permissions across different AWS resources.
- Define policies. You can create and attach custom policies to define fine-grained permissions for controlling access to AWS resources.
- Manage federated access. I allow integrating with external identity providers like Active Directory for centralized management of user access across AWS.

AWS IAM - MFA (Multi-Factor Authentication) :
MFA is an extra layer of security that requires users to provide two or more forms of verification, like a password and a code from their phone, to access their accounts.  


- AWS Management Console provides a graphical web-based approach.
- The AWS CLI provides a command-line scripting approach.
- AWS SDKs and APIs offer programmatic, code-based access, allowing users to integrate AWS directly into their applications.


AWS IAM Best Practices :
1. Avoid using root account except for account setup.
2. Add user to a group and assign permission to the group.
3. Use password policy or MFA.
4. Use access keys for CLI/SDK.
5. Never share access keys or passwords.
6. Audit the permission using the IAM credential report.

## Remember IAM with “who, what, and where”

An identity policy says what a principal may do; a trust policy says who may assume a role; a resource policy can say which principals may reach a particular resource. A request succeeds only when the relevant policies and account controls permit it and no applicable explicit deny blocks it.

For humans, use your organization's federation or IAM Identity Center where available. For software running on AWS, attach a role to the service instead of distributing long-lived keys. Give the role only the actions and resource ARNs needed, then check CloudTrail when troubleshooting access.

**Recall check:** EC2 needs to read one S3 bucket. What is the safer credential pattern? An EC2 instance role with narrowly scoped S3 read permission—not an access key in the app.

**Console practice:** [IAM walkthrough](guides/aws-console/iam.md)




