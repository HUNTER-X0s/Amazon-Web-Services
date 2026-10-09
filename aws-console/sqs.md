# Amazon SQS: Console Walkthrough

**Mental model:** A queue buffers work between producers and consumers. Receiving a message hides it for the visibility timeout; deleting it acknowledges successful processing. If it is not deleted in time, it becomes available again.

Related note: [Cloud Computing.md](../../Cloud%20Computing.md)

## Create and test a standard queue

1. Open [Amazon SQS](https://console.aws.amazon.com/sqs/), choose the Region, and select **Create queue**.
2. Choose **Standard** for at-least-once, best-effort ordering, or **FIFO** when the workload requires ordering/deduplication. Queue type cannot be changed after creation.
3. Name the queue. Review visibility timeout, retention period, delivery delay, long polling, encryption, access policy, and dead-letter queue settings.
4. Use a non-sensitive tag and choose **Create queue**.
5. Open **Send and receive messages**, send a harmless test message, then receive it. Observe the receipt handle/visibility behavior and choose **Delete** only after the test is complete.

## Configure a consumer

Give the consumer's IAM role only the queue operations it needs. Set visibility timeout longer than typical processing time or extend it while processing; make handlers idempotent because standard queues may deliver duplicates. Configure a dead-letter queue and redrive policy for messages that repeatedly fail.

## Clean up

Delete only a test queue with no active producer/consumer. Queue storage, API requests, encryption keys, and data transfer can be billed. Review and remove the dead-letter queue separately.

**Remember:** **receive hides; process; delete acknowledges**.

**Official references:** [Create an SQS standard queue](https://docs.aws.amazon.com/AWSSimpleQueueService/latest/SQSDeveloperGuide/creating-sqs-standard-queues.html) · [SQS getting started](https://docs.aws.amazon.com/AWSSimpleQueueService/latest/SQSDeveloperGuide/sqs-getting-started.html)
