# Amazon ECS: Console Walkthrough

**Mental model:** A task definition is the container recipe; a task is one running copy; a service keeps the requested number of copies running; a cluster is the logical home and capacity boundary.

Related note: [AWS ECS.md](../../AWS%20ECS.md)

## Prepare an image

Build a small container image and push it to [Amazon ECR](amazon-ecr.md), or use an approved public sample image for a disposable learning task. Keep secrets out of the image; inject them at runtime from Secrets Manager or Parameter Store with a task role.

## Define the task

1. Open [Amazon ECS](https://console.aws.amazon.com/ecs/v2), select the Region, and choose **Task definitions → Create new task definition**.
2. Choose **AWS Fargate** for serverless container capacity or **Amazon EC2** for instances you manage.
3. Name the task family. Add a container image URI, CPU/memory, port mappings if needed, environment configuration, logging, and the correct task execution/task roles.
4. Choose **Create** and verify the task definition revision appears as **ACTIVE**.

## Deploy a service

1. Choose **Clusters → Create cluster** and name it. For a first lab, use a Fargate-only cluster unless the exercise specifically requires EC2 capacity.
2. Open the cluster and choose **Services → Create**. Select the task family and revision, enter a service name, and choose a small desired task count.
3. Configure the VPC, subnets, and security group. Assign public IPs only if the task genuinely needs direct public ingress/egress; for a web app, use a load balancer and private tasks.
4. Optionally attach an ALB target group, enable deployment health checks/rollback, and review logging, IAM, autoscaling, and costs.
5. Create the service. Wait for the task to become **RUNNING** and the deployment to stabilize; inspect service events and CloudWatch logs if it does not.

## Clean up

Delete the ECS service (scale desired count to zero), then its cluster. Remove the ECR image/repository, load balancer, target group, log groups, and supporting networking only if they are not shared. Fargate tasks, EC2 capacity, ALBs, logs, and public IPv4 addresses may incur charges.

**Remember:** **definition describes → task runs → service maintains → cluster groups**.

**Official references:** [Create an ECS service](https://docs.aws.amazon.com/AmazonECS/latest/developerguide/create-service-console-v2.html) · [Create a cluster](https://docs.aws.amazon.com/AmazonECS/latest/developerguide/create-cluster-console-v2.html)
