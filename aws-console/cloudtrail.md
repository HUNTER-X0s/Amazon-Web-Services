# AWS CloudTrail: Console Walkthrough

**Mental model:** CloudTrail answers who called which AWS API, when, and from where. A trail stores selected events for later investigation; an Event history view is useful for recent management events but is not a substitute for a durable, protected trail.

Related note: [Cloud Computing.md](../../Cloud%20Computing.md)

## Create a multi-Region trail

1. Open [CloudTrail](https://console.aws.amazon.com/cloudtrail/) and choose **Trails → Create trail**.
2. Enter a neutral name. For a normal account-level audit trail, keep multi-Region logging enabled so enabled Regions are covered.
3. Choose a new or approved S3 bucket for delivery. Review bucket policy, encryption, log-file validation, and optional CloudWatch Logs delivery.
4. Select management events (read/write as appropriate). Add data events (such as S3 object or Lambda activity) only for the resources you need; these may incur additional charges.
5. Review KMS key, event selectors, account/organization scope, notifications, and tags. Choose **Create trail**.
6. Wait for log delivery, then open **Event history** and verify a recent safe action appears. Confirm logs arrive in the expected bucket/prefix.

## Preserve audit integrity

Restrict who can read, change, or delete the S3 destination; consider a separate log archive account, retention controls, and a KMS key policy reviewed by the security team. CloudTrail records activity; it does not prevent the action. Route critical findings into CloudWatch/EventBridge or a SIEM as needed.

## Cleanup caution

Do not delete or stop an organization/security trail as a casual lab cleanup step. For a disposable account, follow the account's retention policy and verify alternative audit coverage before removing it. S3, data events, CloudWatch delivery, and Insights can add charges.

**Remember:** **CloudTrail = who did what; CloudWatch = how the system is behaving**.

**Official references:** [Create a trail in the console](https://docs.aws.amazon.com/awscloudtrail/latest/userguide/cloudtrail-create-a-trail-using-the-console-first-time.html) · [Trail settings](https://docs.aws.amazon.com/awscloudtrail/latest/userguide/cloudtrail-create-and-update-a-trail-by-using-the-console.html)
