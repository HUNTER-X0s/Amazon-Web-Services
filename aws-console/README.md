# AWS Console Field Guides

Short, practical walkthroughs for building the resources described in this repository. The guides focus on the AWS Management Console and pair each action with the reason for it, a way to verify success, and a cleanup reminder.

> Console labels change over time and can vary by Region, account type, and enabled features. The procedures below follow current AWS documentation checked on 2026-10-09; follow the linked AWS guide if a page looks different.

## Start with the data layer

- [Amazon S3](amazon-s3.md) — create a private bucket, upload and retrieve an object, enable versioning, and clean up.
- [Amazon RDS](amazon-rds.md) — create a private relational database, connect from an app tier, and delete a practice instance safely.
- [Amazon DynamoDB](amazon-dynamodb.md) — create a table, write/read an item, and choose a capacity mode.
- [Amazon EBS](amazon-ebs.md) — create, attach, format/mount, snapshot, and detach a block volume.
- [Amazon EFS](amazon-efs.md) — create a shared Linux file system and connect it to compute in the same VPC.
- [Amazon ElastiCache](elasticache.md) — create a managed cache and connect it privately to an application tier.
- [DynamoDB Accelerator (DAX)](dynamodb-dax.md) — configure a VPC-resident read cache for a DynamoDB workload.
- [AWS Storage Gateway](storage-gateway.md) — understand the console setup path for hybrid storage and its appliance prerequisites.
- [AWS Snow Family](snow-family.md) — prepare and request an offline data-transfer device when the service is available for the use case and Region.

## Run compute and containers

- [Amazon EC2](amazon-ec2.md) — launch, connect to, inspect, stop, and terminate a virtual server.
- [AMI and EC2 Image Builder](ami-image-builder.md) — capture a clean machine image or schedule repeatable image builds.
- [Amazon ECS](amazon-ecs.md) — register a container image, define a task, deploy a service, inspect health, and tear it down.
- [Amazon EKS](amazon-eks.md) — create a managed Kubernetes cluster and node capacity, then verify and delete it.
- [Amazon ECR](amazon-ecr.md) — create a private image repository and use the console's push-command instructions.
- [AWS Lambda](aws-lambda.md) — create and test a function, inspect logs, and connect an event source carefully.
- [Elastic Beanstalk](elastic-beanstalk.md) — deploy a sample web app and monitor its environment.
- [EC2 Spot Instances](ec2-spot.md) — request interruptible spare capacity and understand interruption handling.
- [EC2 Auto Scaling](ec2-auto-scaling.md) — make a launch template, maintain healthy capacity, and configure scaling.
- [Elastic Load Balancing](elastic-load-balancing.md) — create an Application Load Balancer with a target group and health checks.

## Network and deliver traffic

- [Amazon VPC and networking](amazon-vpc-networking.md) — build a VPC, subnets, routes, gateways, security groups, NACLs, endpoints, peering, flow logs, and remote-connectivity options.
- [AWS Client VPN](client-vpn.md) — create a managed remote-access endpoint, associate subnets, and control routes/authorization.
- [AWS Direct Connect](direct-connect.md) — request a dedicated connection and plan virtual interfaces, BGP, and network-provider work.
- [Amazon Route 53](route-53.md) — create DNS records and delegate a domain safely.
- [Amazon CloudFront](cloudfront.md) — create a distribution and keep a private S3 origin private with Origin Access Control.
- [AWS Certificate Manager](certificate-manager.md) — request/validate a TLS certificate and associate it with supported endpoints.
- [AWS Shield](shield.md) — understand automatic Shield Standard and the separate Shield Advanced subscription/protection workflow.
- [Amazon API Gateway](api-gateway.md) — create and deploy an HTTP API backed by Lambda, then test its endpoint.

## Control access and protect resources

- [AWS IAM](iam.md) — create a least-privilege workload role, review access, and secure console identities.
- [AWS KMS](kms.md) — create a customer-managed key and assign key administrators and users deliberately.
- [AWS Secrets Manager](secrets-manager.md) — store a secret, grant application access by role, and plan rotation.

## Observe, automate, and connect services

- [Amazon CloudWatch](cloudwatch.md) — view metrics/logs and create an alarm with an optional notification.
- [AWS CloudTrail](cloudtrail.md) — record account/API activity in a protected, multi-Region trail.
- [Amazon SQS](sqs.md) — create a queue, send/receive a test message, and understand visibility timeout.
- [Amazon SNS](sns.md) — create a topic, confirm a subscription, and publish a test notification.
- [AWS CloudFormation](cloudformation.md) — validate and launch a template as a stack, inspect events, and remove its resources.
- [AWS Amplify Hosting](amplify-hosting.md) — connect a Git repository and deploy a web application.

## A safe practice-session loop

1. Choose a dedicated sandbox account and Region. Check the account ID and Region in the console before creating anything.
2. Use a non-production name and add an `Environment=learning` tag where supported.
3. Keep credentials out of names, descriptions, screenshots, templates, and Git. Use IAM roles and Secrets Manager instead of long-lived access keys or copied passwords.
4. Before choosing **Create**, review public access, network exposure, encryption, backups, capacity, and estimated charges.
5. Verify the resource's state and test the smallest useful operation.
6. Follow the guide's cleanup section. Deleting a top-level service object may not remove all related resources, such as snapshots, NAT gateways, load balancers, logs, or retained buckets.

## Related study notes

Start from [the repository README](../../README.md), then use the matching topic note next to each guide (for example, [AWS S3.md](../../AWS%20S3.md) with the [S3 console walkthrough](amazon-s3.md)).
