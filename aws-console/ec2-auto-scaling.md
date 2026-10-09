# Amazon EC2 Auto Scaling: Console Walkthrough

**Mental model:** A launch template is the recipe; an Auto Scaling group is the manager that keeps the desired number of healthy instances across chosen subnets. Scaling policies change desired capacity inside the minimum/maximum guardrails.

Related note: [AWS ELB.md](../../AWS%20ELB.md)

## Create the launch template

1. In [EC2](https://console.aws.amazon.com/ec2/), choose **Launch templates → Create launch template**.
2. Name the template; choose a maintained AMI, compatible instance type, IAM instance profile, encrypted root-volume settings, and a security group.
3. Add only required user data. Do not put credentials in user data because instance metadata/logs may expose it.
4. Review public-IP assignment, key access, tags, and **Auto Scaling guidance**, then create the template.

## Create an Auto Scaling group

1. Choose **Auto Scaling groups → Create Auto Scaling group**, choose the launch template and version, and continue.
2. Select the VPC and subnets in multiple AZs. Choose private subnets for app instances behind a load balancer where possible.
3. Set minimum, desired, and maximum capacity deliberately. A nonzero desired capacity launches billable compute.
4. Optionally attach a target group. Configure health checks and a suitable grace period.
5. Add a target-tracking scaling policy based on a meaningful metric only after setting sensible min/max limits. Add tags and review the summary before creating.

## Verify behavior

Check **Activity**, **Instance management**, and target health. Confirm the group replaces an unhealthy instance only in a disposable sandbox; do not terminate production instances to test it. Review scaling activity and CloudWatch metrics.

## Clean up

Delete the Auto Scaling group with desired capacity allowed to reach zero, then remove the launch template, load balancer/target group, and related resources only if unused. A running desired capacity keeps EC2 charges accruing.

**Remember:** **template defines what launches; group defines how many stay healthy**.

**Official reference:** [Create your first Auto Scaling group](https://docs.aws.amazon.com/autoscaling/ec2/userguide/create-your-first-auto-scaling-group.html)
