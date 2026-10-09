# Amazon ElastiCache: Console Walkthrough

**Mental model:** ElastiCache is an in-memory cache that can reduce repeated database work and latency. A cache is not the source of truth: your application must cope with misses, expiry, and stale entries.

Related note: [AWS DynamoDB.md](../../AWS%20DynamoDB.md)

## Create a small serverless cache

1. Open [Amazon ElastiCache](https://console.aws.amazon.com/elasticache/), choose the Region, and select **Get started** or **Create cache**.
2. Choose the engine supported for the desired cache (for example Valkey, Redis OSS, or Memcached). Check application-client compatibility before selecting.
3. Choose **Serverless** for a managed, variable workload where available. Enter a non-sensitive name and review engine version, usage limits, VPC/subnets, security groups, encryption, authentication, snapshots, and tags.
4. Keep network access private and allow only the application tier's security group on the cache port. Never expose a cache endpoint publicly for a routine app workload.
5. Review data/usage limits, KMS key, endpoint access, and estimated charges, then create the cache. Wait for status **Available/Active**.
6. Copy the endpoint, configure an application in the same permitted network, and test a harmless set/get operation. Do not store the only copy of important data in the cache.

## Verify and clean up

Check engine, endpoint, subnet group, security group source, authentication, encryption, and metrics. Delete the cache only after the app no longer depends on it. Provisioned nodes and serverless capacity, snapshots, and data transfer can incur charges.

**Remember:** **cache-aside = read cache → on miss read source → populate cache → expire/invalidate**.

**Official references:** [ElastiCache getting started](https://docs.aws.amazon.com/AmazonElastiCache/latest/dg/GettingStarted.html) · [Create a serverless cache](https://docs.aws.amazon.com/AmazonElastiCache/latest/dg/create-serverless-cache-mem.html)
