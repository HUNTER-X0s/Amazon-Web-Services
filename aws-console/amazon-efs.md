# Amazon EFS: Console Walkthrough

**Mental model:** EFS is a shared Linux file system that several compute clients can mount at once. The file system stores shared files; mount targets provide network entry points inside selected Availability Zones.

Related note: [Cloud Computing.md](../../Cloud%20Computing.md)

## Create a file system

1. Open [Amazon EFS](https://console.aws.amazon.com/efs/), choose the Region and **Create file system**.
2. Choose a VPC. The quick-create path uses service-recommended settings; inspect availability type, storage lifecycle, throughput, encryption, and backups before accepting them.
3. Create the file system and wait for **Available**. Open its details and review its mount targets and security groups.
4. Ensure a mount target exists in each AZ where clients need access. The mount-target security group must allow NFS TCP 2049 **from the client instances' security group**, not from the entire internet.
5. On a Linux client in the same VPC, use the EFS mount helper instructions shown in **Attach** for the specific file system. Verify the mount and test creating/reading a harmless file.

## Verify and clean up

Confirm VPC, mount targets, encryption, lifecycle policy, backups, and client security-group references. Unmount all clients before deleting the file system. EFS data and provisioned resources can incur charges while present; remove unused mount targets and backups after checking retention needs.

**Remember:** **shared files need reachable mount targets and NFS permission from the client tier**.

**Official references:** [Create an EFS file system](https://docs.aws.amazon.com/efs/latest/ug/creating-using-create-fs.html) · [Mount from EC2](https://docs.aws.amazon.com/efs/latest/ug/mounting-fs.html)
