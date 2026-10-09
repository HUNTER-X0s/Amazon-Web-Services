# Amazon S3: Console Walkthrough

**Mental model:** A bucket is a globally unique container; an object is data plus its key and metadata. A folder-looking path is just a key prefix. Think **bucket → key → object**.

Related note: [AWS S3.md](../../AWS%20S3.md)

## Before creating anything

- Pick a Region and a unique bucket name. S3 general purpose bucket names are globally unique within the partition.
- Decide whether this is private storage, a website origin, or an application data bucket. For learning, keep it private.
- Consider charges for stored bytes, requests, retrieval, replication, and data transfer. Check current pricing and free-plan eligibility.

## Create a private bucket and upload a test object

1. Sign in to the AWS Management Console and open [Amazon S3](https://console.aws.amazon.com/s3/). Confirm the account and Region.
2. Choose **Buckets → Create bucket**.
3. Enter a unique name and choose the intended Region. Keep **Block Public Access** enabled. Leave ACLs disabled unless a specific integration requires them.
4. Keep default encryption enabled; choose a customer-managed KMS key only when you need its additional controls and understand its permissions and charges.
5. For a learning bucket, leave versioning off until ready to test it. Add a tag such as `Environment=learning`, then create the bucket.
6. Open the bucket, choose **Upload → Add files**, select a harmless test file, and choose **Upload**.
7. Select the uploaded object and use **Download** to verify the write/read path. An object URL alone does not make a private object public.

## Try versioning (optional)

1. Open the bucket's **Properties** tab and find **Bucket Versioning**.
2. Choose **Edit → Enable → Save changes**.
3. Upload a changed file under the same key. In **Objects**, enable **Show versions** to see both versions.
4. Delete the object once and inspect the delete marker. Versioning helps recover from overwrites and ordinary deletes, but it can retain storage and is not a substitute for a backup strategy.

## Verify and clean up

- Confirm the bucket is in the intended Region, Block Public Access is on, encryption is enabled, and the test key appears.
- Remove test objects and every retained version/delete marker. Then delete the empty bucket if it was only for practice.
- Check that no replication rule, access point, inventory, or lifecycle configuration was accidentally left behind.

**Remember:** S3 grants access through policy and identity; a URL is an address, not permission.

**Official references:** [Getting started with S3](https://docs.aws.amazon.com/AmazonS3/latest/userguide/GetStartedWithS3.html) · [Block public access](https://docs.aws.amazon.com/AmazonS3/latest/userguide/access-control-block-public-access.html) · [Versioning](https://docs.aws.amazon.com/AmazonS3/latest/userguide/Versioning.html)
