# Amazon CloudWatch: Console Walkthrough

**Mental model:** Metrics tell you how much or how often; logs record events; alarms evaluate metrics and take an action. Dashboards summarize signals, but an alarm needs a useful metric, threshold, evaluation period, and response.

Related note: [Cloud Computing.md](../../Cloud%20Computing.md)

## Inspect a service metric

1. Open [CloudWatch](https://console.aws.amazon.com/cloudwatch/) and select the Region containing the resource.
2. Choose **Metrics → All metrics**, then select a service namespace (for example EC2) and the relevant dimension/resource.
3. Graph the metric, set a meaningful period/statistic, and compare it with expected behavior. Confirm the source service is publishing the metric; some detailed metrics require explicit enablement and can cost extra.

## Create a metric alarm

1. Choose **Alarms → All alarms → Create alarm → Select metric**.
2. Select the metric and resource. Choose a period, statistic, and threshold grounded in the service's normal range.
3. Set evaluation periods and missing-data behavior. Add an SNS notification or supported action only after selecting the intended target and verifying permissions.
4. Name and describe the alarm without secrets or personal data. Review the graph and conditions, then create it.
5. Trigger a safe test (where feasible) and confirm the alarm changes state and any notification arrives. Avoid forcing an alarm on a production resource for practice.

## Review logs

Open **Logs → Log groups**, select the workload's group (for example `/aws/lambda/function-name`), and inspect retention, streams, and sensitive-data handling. Set finite retention for practice logs; logs may contain identifiers or accidental secrets, so restrict access.

## Clean up

Delete test alarms and dashboards and shorten/delete test log groups only when no audit or troubleshooting need remains. Metrics, log ingestion, retention, alarms, dashboards, and queries may be charged.

**Remember:** **metric measures → alarm judges → action responds; logs explain why**.

**Official references:** [Create a CloudWatch alarm](https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/ConsoleAlarms.html) · [CloudWatch setup](https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/GettingSetup.html)
