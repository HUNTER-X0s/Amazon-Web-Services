# AWS IAM: Console Walkthrough

**Mental model:** A role says who may assume it; a permissions policy says what that identity may do; a resource policy can also decide who may access a resource. Effective access is the result of all applicable allows, explicit denies, boundaries, and organization controls.

Related note: [AWS IAM.md](../../AWS%20IAM.md)

## Create a workload role

1. Open [IAM](https://console.aws.amazon.com/iam/). For people, prefer your organization's IAM Identity Center/federation setup. Reserve the root user for account-level tasks and secure it with MFA.
2. Choose **Roles → Create role**. For **Trusted entity type**, select **AWS service** and choose the workload service (for example EC2, Lambda, or ECS task).
3. Attach only the permissions needed for the job. Prefer a customer-managed policy restricted to required actions and resource ARNs. Do not choose broad administrator permissions for an application role.
4. Name and describe the role so its purpose and owner are clear. Add non-sensitive tags, review the trust policy and permissions, then create it.
5. Attach it to the EC2 instance profile, Lambda function, or ECS task definition from that service's console. Test the required operation and inspect CloudTrail/CloudWatch on access denied.

## Review human access

Use IAM Identity Center or your federated identity provider for workforce access. If a legacy IAM user is required, create it only for a defined reason, use console access and MFA as appropriate, grant access through groups, and avoid long-lived access keys. Never place keys in code, README files, shell history, or AMIs.

## Verify and clean up

Open the role's **Trust relationships** and **Permissions** tabs. Use policy simulation/access analyzer where available. Remove test policies and roles only after confirming no service depends on them; deleting a role may break running workloads.

**Remember:** **trust policy = who; permission policy = what**.

**Official references:** [Create a service role](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles_create_for-service.html) · [IAM best practices](https://docs.aws.amazon.com/IAM/latest/UserGuide/best-practices.html)
