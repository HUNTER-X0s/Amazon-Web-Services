# AMIs and EC2 Image Builder: Console Walkthrough

**Mental model:** An AMI is a reusable launch blueprint for EC2. It captures boot volume contents and launch metadata; it is a way to reproduce a configured server, not a running server.

Related note: [AWS AMI.md](../../AWS%20AMI.md)

## Create a one-off AMI from an instance

1. Prepare the source EC2 instance: patch it, remove temporary files and secrets, stop app processes that must be quiescent, and decide how to handle attached data volumes.
2. Open [Amazon EC2](https://console.aws.amazon.com/ec2/), choose **Instances**, select the instance, then **Actions → Image and templates → Create image**.
3. Enter a descriptive image name and notes that identify its purpose, owner, and patch level. Review which attached volumes are included, their sizes, delete-on-termination flags, and encryption settings.
4. Choose **Create image**. Check **AMIs → Owned by me** and the **Pending → Available** state. Associated snapshots can be found under **Snapshots**.
5. Launch a disposable test instance from the AMI and confirm its expected software and settings before promoting it for broader use.

## Build a repeatable image with EC2 Image Builder

1. Open **EC2 Image Builder → Image pipelines → Create image pipeline**.
2. Configure the image recipe (base image, components, and block-device mappings), infrastructure configuration (instance profile, network, instance type), and distribution settings (Region/account targets).
3. Create or choose a pipeline schedule, add an output AMI name, review permissions and encryption, then create and run the pipeline.
4. Inspect pipeline execution history, component logs, and the resulting AMI. Test the image before sharing or assigning it to a production launch template.

## Keep images safe and economical

Never bake passwords, private keys, database dumps, access tokens, or customer data into an image. Share an AMI only with intended accounts and Regions. Deregister unused AMIs and separately delete their snapshots only after confirming no launch template or backup depends on them. Snapshot storage may incur charges.

**Remember:** **prepare → capture → test → share**. An AMI is useful only if it is clean and reproducible.

**Official references:** [Create an AMI from an instance](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/creating-an-ami-ebs.html) · [EC2 Image Builder](https://docs.aws.amazon.com/imagebuilder/latest/userguide/what-is-image-builder.html)
