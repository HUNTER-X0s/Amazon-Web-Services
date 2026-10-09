# Amazon EBS: Console Walkthrough

**Mental model:** EBS is a network-attached block disk for EC2. Create it in the same Availability Zone as its instance, attach it, then make the operating system recognize and mount it. A snapshot is a point-in-time backup, not a live filesystem.

Related note: [AWS EBS.md](../../AWS%20EBS.md)

## Create and attach a data volume

1. In [Amazon EC2](https://console.aws.amazon.com/ec2/), open **Volumes → Create volume**.
2. Choose a volume type and size for the workload; `gp3` is the console default for many workflows. Select the same Availability Zone as the target instance.
3. Enable encryption and select a KMS key if appropriate. Add tags, review estimated costs, then create the volume.
4. Wait for state **Available**, select the volume, and choose **Actions → Attach volume**.
5. Choose the target EC2 instance in the same AZ and an available device name. Choose **Attach volume**.
6. Connect to the instance with Session Manager or another approved method. Verify the device, create a partition/filesystem if it is a new empty disk, then mount it. **Formatting the wrong disk destroys data**; identify the device and confirm it is empty before running any formatting command.

## Snapshot and restore

1. Quiesce writes or use an application-consistent backup process if the data needs consistency across multiple volumes.
2. Select the volume and choose **Actions → Create snapshot**. Name and tag it, then monitor snapshot state under **Snapshots**.
3. To restore, select a snapshot and choose **Create volume from snapshot**. Pick the destination AZ and encryption settings; wait until available, attach, and mount.

## Detach and clean up

Unmount the filesystem in the guest OS first, then select **Actions → Detach volume**. Do not force-detach unless recovery procedures require it. Delete a volume only after confirming its data is backed up; delete snapshots separately if no longer needed. EBS volumes and snapshots incur storage charges.

**Remember:** **AZ match → attach → mount; unmount → detach**.

**Official references:** [Create an EBS volume](https://docs.aws.amazon.com/ebs/latest/userguide/ebs-creating-volume.html) · [Attach a volume](https://docs.aws.amazon.com/ebs/latest/userguide/ebs-attaching-volume.html) · [Create a snapshot](https://docs.aws.amazon.com/ebs/latest/userguide/ebs-creating-snapshot.html)
