# Amazon DynamoDB: Console Walkthrough

**Mental model:** A table is a collection; each item is keyed by a partition key (and optionally a sort key). Choose keys around the questions your app must answer—DynamoDB is not a relational table with arbitrary joins.

Related note: [AWS DynamoDB.md](../../AWS%20DynamoDB.md)

## Create a table

1. Open [DynamoDB](https://console.aws.amazon.com/dynamodb/), choose the Region, then **Tables → Create table**.
2. Enter a table name and a simple partition key such as `id` with type **String**. Add a sort key only if your access patterns need multiple related items per partition.
3. Choose **On-demand** capacity for a small, unpredictable practice workload. Provisioned capacity can suit steady workloads but requires capacity planning and may throttle if undersized.
4. Review encryption (enabled by default), point-in-time recovery, deletion protection, and tags. These features and requests may affect cost.
5. Choose **Create table** and wait for **Active**.

## Write and read an item

1. Open the table and choose **Explore table items**.
2. Choose **Create item** and add an item whose partition-key value is unique, such as `contact-001`.
3. Add a few typed attributes (for example `name` as String and `active` as Boolean), then create the item.
4. Use the item explorer to retrieve it by key. This validates the console path; production apps should use an IAM role with only the table actions they need.

## Verify and clean up

- Confirm table state, key schema, capacity mode, encryption, and recovery settings.
- For a disposable table, select it and choose **Delete** after confirming no app depends on it. Export or back up any data you need first.
- Review backups and global tables separately; deleting a table does not necessarily remove every related retained backup.

**Remember:** Design from **access pattern → key schema → item shape**.

**Official references:** [Create a table](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/getting-started-step-1.html) · [Write data](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/getting-started-step-2.html) · [Capacity modes](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/HowItWorks.ReadWriteCapacityMode.html)
