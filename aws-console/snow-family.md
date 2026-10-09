# AWS Snow Family: Console Workflow

**Mental model:** A Snow Family job is a tracked offline transfer or edge-compute lifecycle: plan the job, prepare and ship the device, copy data locally, return it, then verify the cloud import/export report. It is for cases where network transfer is impractical or too slow.

Related note: [AWS S3.md](../../AWS%20S3.md)

## Plan before requesting a device

1. Estimate data volume, transfer window, destination S3 buckets, Regions, network constraints, encryption/key policy, and chain-of-custody requirements.
2. Confirm Snow Family device and job availability for your account, Region, and use case in the current AWS console. Product options and fulfillment are region-dependent.
3. Confirm that destination buckets and import IAM role follow least privilege. If using SSE-KMS, ensure the role and KMS key policy allow the import service to use the selected key.

## Create an import/export job

1. Open the [AWS Snow Family console](https://console.aws.amazon.com/importexport/) and choose the Region where the job will be managed.
2. Choose **Create job** or **Order an AWS Snowball Edge device**. Give the job a non-sensitive name.
3. Choose the job type: import into S3, export from S3, or local compute/storage if offered for the account/Region.
4. Choose the device capacity/features and destination/source S3 buckets. Review bucket/prefix mapping and how duplicate object keys will be handled.
5. In the permission step, create/select an IAM role for the Snow service. Inspect the policy and restrict it to the exact buckets/prefixes and KMS key required.
6. Choose shipping address and return method from authorized delivery details; set notifications. Review all settings, device charges, shipping, and security options before submitting the order.
7. Track job status in the console. When the device arrives, use the documented local client/OpsHub instructions to transfer data. After returning it, wait for processing and download the completion report/logs.

## Verify and close out

Compare imported object counts/keys and errors to the manifest. Keep the source copies until the completion report and destination data are verified. Follow chain-of-custody rules for device handling. Complete the return shipment promptly and keep the job record for audit.

**Remember:** **plan → order → copy → return → verify**.

**Official references:** [Create a Snowball Edge job](https://docs.aws.amazon.com/snowball/latest/developer-guide/create-job-common.html) · [Import jobs](https://docs.aws.amazon.com/snowball/latest/developer-guide/importtype.html)
