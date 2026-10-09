AWS ECS



Aws ECS
Elastic container service
It is a cloud based container management service that allows you to run and manage docker containers on a cluster of virtual servers.

why ECS ?
It automatically handles :
- creation
- management 
- and updating. 

ECS Terms:
- Cluster : A group of tasks and services. Hosts all the resources and infrastructure.
- Service : Handles scalability and load balancing of container.
- Task : Represents the running containers of your applications.

## Remember ECS with a restaurant analogy

The **task definition** is the recipe card (image, ports, CPU/memory, roles, logs). A **task** is one running kitchen using that recipe. A **service** keeps the requested number of kitchens open and replaces failed tasks. A **cluster** groups the service and the capacity it can use.

Fargate removes EC2 host management; EC2 capacity gives you more control over the underlying instances. In either model, the application still needs image access, a task role for AWS permissions, network placement, logs, and health checks. Keep credentials out of the image and environment literals; retrieve secrets securely at runtime.

**Recall check:** A task exits successfully, but the desired count returns to one. Why? The ECS service is maintaining its desired count.

**Console practice:** [ECS walkthrough](guides/aws-console/amazon-ecs.md) · [ECR walkthrough](guides/aws-console/amazon-ecr.md)









