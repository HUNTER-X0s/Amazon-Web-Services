# Amazon SNS: Console Walkthrough

**Mental model:** An SNS topic broadcasts one published message to its subscriptions. SNS is a fan-out channel; a queue such as SQS is often used when a consumer must process work independently and retry safely.

Related note: [Cloud Computing.md](../../Cloud%20Computing.md)

## Create a topic and email subscription

1. Open [Amazon SNS](https://console.aws.amazon.com/sns/v3/home), select the Region, and choose **Topics → Create topic**.
2. Choose **Standard** or **FIFO**. Give the topic a neutral name (never put PII/secrets in names), review encryption and access policy, then create it.
3. Copy the topic ARN. Choose **Create subscription**, select the ARN, choose a protocol such as email, and enter an address you control for the exercise.
4. Confirm the subscription using the email link. SNS will not deliver to an email endpoint until it is confirmed.
5. Select the topic and choose **Publish message**. Send a harmless test, then verify delivery at the confirmed endpoint.

## Verify and secure

Review subscriptions, topic access policy, encryption, delivery retry/logging, and CloudWatch metrics. Limit who can publish and subscribe. For application workloads, prefer service-to-service IAM/resource policies rather than public topic policies.

## Clean up

Delete the practice subscription and topic. Consider any pending confirmation and downstream subscriptions. Notifications and data transfer may have charges.

**Remember:** **publish once → SNS fans out → each subscriber receives**.

**Official references:** [Create an SNS topic](https://docs.aws.amazon.com/sns/latest/dg/sns-create-topic.html) · [Create topic and publish](https://docs.aws.amazon.com/sns/latest/dg/sns-getting-started.html)
