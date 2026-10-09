# AWS Lambda: Console Walkthrough

**Mental model:** A Lambda function is code plus configuration, triggered by an event. The execution role is its AWS identity; the event is its input; CloudWatch Logs records its output.

Related note: [AWS Lambda.md](../../AWS%20Lambda.md)

## Create and test a function

1. Open [AWS Lambda](https://console.aws.amazon.com/lambda/), choose the Region, and select **Functions → Create function**.
2. Choose **Author from scratch**, provide a name, current supported runtime, and architecture, then create the function. Lambda can create a basic execution role for CloudWatch Logs.
3. In **Code**, use the built-in editor for a supported interpreted runtime, or upload a deployment package/container image for your chosen runtime. Keep function code and dependencies small and reproducible.
4. In **Configuration → General configuration**, set memory and timeout to suit the task. In **Permissions**, inspect the execution role; add only the required actions and resource ARNs.
5. Choose **Test → Create new event**, provide a harmless JSON event, save it, and run the test. Inspect response, duration, errors, and logs.
6. Open **Monitor → View CloudWatch logs** to inspect the function's log group. Configure alarms for production workloads.

## Add a trigger safely

1. Open **Function overview → Add trigger** and select an event source (such as S3, EventBridge, API Gateway, or DynamoDB).
2. Select the specific bucket/table/rule/API resource and event types. Review both sides of permissions: the source must be allowed to invoke the function, and the function role must be allowed to read/write what it needs.
3. Enable retries, a dead-letter destination, concurrency limits, and idempotency where the workload needs them. Test with a non-sensitive event, then inspect logs and metrics.

## Clean up

Remove the event-source mapping/trigger, function, dedicated log group if no longer needed, and any IAM policy/role created only for the lab. Logs and provisioned concurrency can continue to incur costs.

**Remember:** **event enters → role authorizes → code runs → logs explain**.

**Official reference:** [Create your first Lambda function](https://docs.aws.amazon.com/lambda/latest/dg/getting-started.html)
