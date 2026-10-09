# Amazon EC2: Console Walkthrough

**Mental model:** An EC2 instance is a virtual computer. Its AMI is the starting disk image, instance type is its CPU/memory shape, EBS is persistent block storage, a subnet places it in the network, and an IAM role grants AWS permissions.

Related note: [AWS EC2.md](../../AWS%20EC2.md)

## Launch a small test instance

1. Open [Amazon EC2](https://console.aws.amazon.com/ec2/), confirm the Region, and choose **Instances → Launch instances**.
2. Add a useful name tag. Under **Application and OS Images**, pick a trusted Quick Start image such as Amazon Linux. Confirm its architecture.
3. Select a small instance type suitable for the exercise. Check the current price and account Free Tier terms before proceeding.
4. Under **Key pair**, choose an existing key or create one and store the private key securely. A lost private key cannot be downloaded again.
5. Choose a VPC and subnet. For administration, prefer Systems Manager Session Manager or EC2 Instance Connect with tightly scoped permissions over opening SSH to the world.
6. Under **Network settings**, create/select a security group with only required access. If hosting a test web page, allow HTTP/HTTPS only when needed. Never leave SSH/RDP open to `0.0.0.0/0`.
7. Attach an IAM instance profile only if the workload needs AWS APIs. Use a narrowly scoped role; do not put access keys on the instance.
8. Review root EBS volume size, encryption, termination behavior, and tags. Choose **Launch instance**.

## Connect and verify

1. Wait for **Instance state = Running** and both status checks to pass.
2. Select the instance and use **Connect**. Choose Session Manager (requires the right instance role, SSM agent, and network access), EC2 Instance Connect, or the supported SSH/RDP method.
3. Confirm the instance's VPC, subnet, address, security group, IAM role, and EBS volumes. Stop when done if you will resume soon; terminate if the exercise is complete.

## Stop or terminate

- **Stop** a supported EBS-backed instance to pause compute charges; attached EBS storage and other resources can still cost money. Instance-store data is not durable across stop/termination.
- **Terminate** only when you are finished. Check each volume's **Delete on termination** setting first; detached volumes, snapshots, Elastic IPs, and load balancers may remain billable.
- Before deleting an instance, create an AMI or EBS snapshot if you need a recoverable copy.

**Remember:** **image → shape → network → identity → storage** is the EC2 launch checklist.

**Official references:** [Launch an instance](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ec2-launch-instance-wizard.html) · [Connect to an instance](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/connect.html) · [Systems Manager Session Manager](https://docs.aws.amazon.com/systems-manager/latest/userguide/session-manager.html)
