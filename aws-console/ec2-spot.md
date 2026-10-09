# EC2 Spot Instances: Console Walkthrough

**Mental model:** Spot uses spare EC2 capacity at a discount, but AWS can reclaim it with interruption notice. Use it for restartable, fault-tolerant work—not a single irreplaceable server.

Related note: [Cloud Computing.md](../../Cloud%20Computing.md)

## Launch a small Spot test

1. Open [EC2](https://console.aws.amazon.com/ec2/) and choose **Instances → Launch instances**.
2. Select an AMI and an instance type that your task can tolerate losing. Keep durable state on suitable persistent storage or external services.
3. In **Advanced details** or purchasing options, choose Spot when offered. For sustained workloads, create a launch template and use an Auto Scaling group with a mix of eligible instance types/AZs rather than a one-off request.
4. Configure interruption handling in the application (checkpoint, drain, retry). Restrict network access, set a role if needed, and review the current Spot price and any persistent request settings.
5. Launch and verify the instance's lifecycle and interruption behavior from the EC2 console. Do not test interruption against valuable data.

## Clean up

Cancel any persistent Spot request and terminate the instance when done. Review attached EBS volumes, snapshots, public IPv4 addresses, and Auto Scaling resources for continuing charges.

**Remember:** Spot is **cheap spare capacity + interruption-aware software**.

**Official reference:** [Spot Instances](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/using-spot-instances.html)
