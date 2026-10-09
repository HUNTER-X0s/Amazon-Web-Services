# AWS Elastic Beanstalk: Console Walkthrough

**Mental model:** An Elastic Beanstalk application holds versions; an environment runs one version on a set of AWS resources. Beanstalk handles provisioning and deployment, while you still own application security, configuration, and cost review.

Related note: [Cloud Computing.md](../../Cloud%20Computing.md)

## Launch a sample environment

1. Open [Elastic Beanstalk](https://console.aws.amazon.com/elasticbeanstalk/), choose the Region, and select **Create application**.
2. Enter a neutral application name. Choose a supported platform and a sample application for a first deployment.
3. Name the environment. Choose **Single instance** only for a disposable learning exercise; a load-balanced production environment provisions more resources and costs more.
4. Review service role, EC2 instance profile, VPC/subnets, instance type, key access, security groups, health reporting, and environment variables. Keep secrets out of plain environment settings where possible.
5. Choose **Create app** and follow **Events** until environment health is **Ok**. Open **Go to environment** and confirm the sample page is reachable.

## Deploy an app version

Upload a valid source bundle or connect the documented deployment workflow. Create a named application version, deploy it to the intended environment, and monitor events/health. Use a separate environment for risky changes and understand rollback behavior.

## Clean up

Terminate the environment from the Elastic Beanstalk console and wait until its underlying resources are removed. Then review the related CloudFormation stack, S3 source bucket, logs, load balancers, EC2 volumes, and Elastic IPs for leftovers. Elastic Beanstalk itself has no separate environment fee, but its created resources do.

**Remember:** **application → version → environment → health**.

**Official reference:** [Elastic Beanstalk getting started](https://docs.aws.amazon.com/elasticbeanstalk/latest/dg/GettingStarted.html)
