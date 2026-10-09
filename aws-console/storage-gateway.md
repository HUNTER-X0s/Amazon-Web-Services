# AWS Storage Gateway: Console Workflow

**Mental model:** Storage Gateway places an appliance between on-premises applications and AWS storage. The appliance uses local disks for cache/buffers while synchronizing data with cloud services. It needs local infrastructure, network paths, IAM, and storage resources; this is not a service to launch casually for a quick lab.

Related note: [AWS S3.md](../../AWS%20S3.md)

## Choose the gateway type

- **S3 File Gateway:** presents NFS/SMB file shares backed by S3 objects.
- **Volume Gateway:** presents iSCSI block volumes with cloud backup/recovery behavior.
- **Tape Gateway:** presents virtual tapes to compatible backup software.
- Check current console eligibility: FSx File Gateway is not available to new customers, and the Storage Gateway hardware appliance is no longer offered to new customers. Virtual deployments remain available for supported configurations.

## Create and activate a virtual gateway

1. Prepare a supported hypervisor or EC2 host, CPU/RAM, dedicated local cache/upload-buffer disks, DNS/NTP, firewall rules, and outbound connectivity to the chosen AWS service endpoint.
2. Open [Storage Gateway](https://console.aws.amazon.com/storagegateway/home/), choose the Region, then **Create gateway**.
3. Select gateway type and host platform; follow the console instructions to download/deploy the virtual appliance or launch the supported EC2 image.
4. Obtain the appliance's IP or activation key from its local console. Return to the AWS console, choose public or VPC service endpoint as appropriate, enter the activation details, and review carefully. Some activation/network settings cannot be changed after activation.
5. Configure local cache and upload-buffer disks, logging/CloudWatch alarms, encryption, and tags. Choose **Configure**.
6. Create a storage resource for the chosen gateway: an S3 file share (bucket, IAM role, NFS/SMB access, client security group/allowlist), an iSCSI volume, or virtual tapes. Configure directory services only for SMB use cases that require them.
7. Mount/connect from the on-premises clients using the service endpoint and protocol-specific instructions. Test a small non-sensitive file, verify cloud data, and monitor cache, upload, and health metrics.

## Verify and retire carefully

Check gateway state, cache/upload buffer, CloudWatch metrics, IAM access, and the associated bucket/volume/tape resources. For retirement, stop application writes, ensure data has uploaded, detach or migrate clients, remove file shares/volumes/tapes according to retention policy, and only then deactivate/delete the gateway. Cloud storage, device compute, and data transfer remain billable.

**Remember:** **appliance → activation → local disks → cloud resource → client mount**.

**Official references:** [Create a gateway](https://docs.aws.amazon.com/storagegateway/latest/tgw/creating-your-gateway.html) · [Create an S3 File Gateway](https://docs.aws.amazon.com/storagegateway/latest/s3/creating-s3-file-gateway.html) · [Create a Volume Gateway](https://docs.aws.amazon.com/storagegateway/latest/vgw/create-volume-gateway.html)
