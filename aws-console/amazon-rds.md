# Amazon RDS: Console Walkthrough

**Mental model:** RDS operates the database server; you still choose the engine, size, network access, credentials, and data-protection settings. Keep the database on a private network and let only the application tier reach its port.

Related note: [AWS RDS.md](../../AWS%20RDS.md)

## Before creating a database

- Choose the engine (for example PostgreSQL or MySQL), Region, identifier, and a suitable sandbox instance class.
- Plan a DB subnet group across Availability Zones and a security group whose inbound rule names the application security group as its source.
- Decide backups, encryption, deletion protection, and how credentials will be managed. Use RDS-managed credentials in Secrets Manager where available.
- RDS instances, storage, backups, snapshots, and data transfer can incur charges. A stopped DB may still incur storage or backup costs.

## Create a private practice DB

1. Open [Amazon RDS](https://console.aws.amazon.com/rds/), confirm the Region, then choose **Databases → Create database → Standard create**.
2. Select an engine and engine version. Choose a learning/dev template only after reviewing what defaults it selects.
3. Give the DB a neutral identifier. Set a unique master username and use **Manage master credentials in AWS Secrets Manager** if the option fits the exercise; never reuse or paste a real password into notes.
4. Choose a small supported instance class and storage appropriate to a throwaway exercise. Enable storage encryption.
5. In **Connectivity**, choose the intended VPC and DB subnet group. Keep **Public access = No**. Select or create a security group that permits the DB port only from the app tier's security group—not from `0.0.0.0/0`.
6. In **Additional configuration**, review initial database name, automated backup retention, maintenance settings, and deletion protection. Enable deletion protection for persistent data; for a disposable lab, note that it must be turned off before deletion.
7. Review the estimated configuration and choose **Create database**. Wait for status **Available**.

## Connect and verify

1. Open the DB details and copy the endpoint and port; the endpoint is not a password.
2. Connect from a permitted client in the VPC using the engine's database client and the credential retrieved securely from Secrets Manager.
3. Verify the security group source, subnet group, encryption, backup setting, and CloudWatch metrics. Test a simple connection/query, then close the session.

## Clean up a learning DB

1. Back up/export any data you need. In **Databases**, select the instance and choose **Actions → Delete**.
2. Decide explicitly whether to create a final snapshot. A retained snapshot continues to use storage and may incur charges.
3. Turn off deletion protection if requested, confirm the delete prompt, and wait until the DB is gone.
4. Remove unused snapshots, manual parameter groups, subnet groups, and security groups only after confirming no other resource uses them.

> **Credential safety:** the original RDS note includes a password-like value in an example. Treat it as exposed: rotate it in the database and replace it with a placeholder before publishing the notes. This guide does not reproduce it.

**Remember:** Database access is the intersection of **route + security group + valid DB credentials**.

**Official references:** [Create an RDS DB instance](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/USER_CreateDBInstance.html) · [RDS and Secrets Manager](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/rds-secrets-manager.html) · [RDS networking](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/USER_VPC.html)
