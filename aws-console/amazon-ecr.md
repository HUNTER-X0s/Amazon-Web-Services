# Amazon ECR: Console Walkthrough

**Mental model:** ECR is a private registry for container images. A repository organizes images; a tag names a build, while a digest identifies the image contents exactly.

Related note: [DOCKER.md](../../DOCKER.md)

## Create a private repository

1. Open [Amazon ECR](https://console.aws.amazon.com/ecr/repositories), confirm the Region, and choose **Private repositories → Create repository**.
2. Enter a lowercase repository name. Choose immutable tags if a published tag should never be overwritten; enable image scanning according to your security workflow.
3. Review encryption, lifecycle policy, and repository policy. Choose **Create repository**.
4. Open the repository and choose **View push commands**. Follow the displayed authentication/build/tag/push commands from a trusted workstation or build system. The console stores the images, but the Docker build/push happens outside the browser.
5. Return to the repository and verify the image tag and digest. Use that full image URI in an ECS task definition or Kubernetes workload.

## Clean up

Delete only test images and repositories with no running workloads or rollback dependency. Lifecycle policies can remove old untagged images; review their effect before applying. Image storage, scans, and data transfer can incur charges.

**Remember:** **build → tag → push → deploy by immutable digest where possible**.

**Official reference:** [Create an ECR private repository](https://docs.aws.amazon.com/AmazonECR/latest/userguide/repository-create.html)
