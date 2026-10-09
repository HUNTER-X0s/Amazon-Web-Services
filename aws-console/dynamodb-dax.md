# DynamoDB Accelerator (DAX): Console Walkthrough

**Mental model:** DAX is a managed in-memory cache for DynamoDB reads. The application uses the DAX client/endpoint; DynamoDB remains the durable source of truth. Add DAX only when a workload's access pattern and latency justify another networked component.

Related note: [AWS DynamoDB.md](../../AWS%20DynamoDB.md)

## Create a test DAX cluster

1. Open the [DynamoDB console](https://console.aws.amazon.com/dynamodb/) and select **DAX → Subnet groups**.
2. Create or select a subnet group in the intended VPC. Use subnets across Availability Zones for a production multi-node cluster.
3. Choose **DAX → Clusters → Create cluster**. Enter a name, choose a node type and cluster size, then select the subnet group and security group.
4. Configure the IAM service role so DAX can access only the DynamoDB tables required. Review encryption at rest/in transit, maintenance window, parameter group, and tags.
5. Create the cluster and wait for **Available**. Configure the attached security group to allow the DAX port from the application tier's security group only (commonly 8111 without in-transit encryption or 9111 with it; verify current settings).
6. From an app instance in the same VPC, use the DAX SDK client and cluster endpoint for a harmless read test. The console alone does not convert a generic DynamoDB client into a DAX client.

## Clean up

Delete the cluster, then remove its dedicated subnet group, service role, and security group only if unused. DAX nodes incur hourly charges while running.

**Remember:** **DAX speeds repeated reads; DynamoDB still owns the data**.

**Official reference:** [Create a DAX cluster in the console](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/DAX.create-cluster.console.html)
