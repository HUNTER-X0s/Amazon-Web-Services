# AWS Shield: Console Overview

**Mental model:** AWS Shield Standard provides baseline DDoS protection automatically for AWS customers. Shield Advanced is an additional subscription and operational program for selected protected resources; adding it is a paid decision, not a routine checkbox.

Related note: [AWS CloudFront CDN.md](../../AWS%20CloudFront%20CDN.md)

## Understand the two protection levels

- **Shield Standard:** baseline network and transport layer DDoS protections are automatically available; there is no setup workflow for enabling it.
- **Shield Advanced:** subscription-based enhanced protection for supported resources, with additional detection/response capabilities and operational requirements. Check current eligibility, billing terms, support prerequisites, and service scope before subscribing.

## Add protection with Shield Advanced

1. Confirm the business owner, security contact, incident process, budget, and the resources/Regions to protect. Review the current Shield Advanced subscription terms and charges.
2. Open the [AWS WAF & Shield console](https://console.aws.amazon.com/wafv2/) and choose **AWS Shield → Protected resources**.
3. Choose **Add resources to protect**. Select resource Regions/types, load the resource list, and choose only the intended CloudFront distributions, load balancers, Route 53 resources, or other supported resources.
4. Review tags and protection scope, then choose **Protect with Shield Advanced** only when subscription and operational readiness are approved.
5. Configure any recommended response/support integrations and alarms, document escalation contacts, and test the response plan using an approved exercise.

## Verify and manage

Confirm protected-resource inventory, Regions, protection status, health signals, and escalation contact details. Removal from protection does not undo the Advanced subscription; manage billing/subscription state separately. Do not use destructive traffic tests against public services.

**Remember:** **Standard is automatic; Advanced is subscribed, scoped, monitored, and staffed**.

**Official references:** [Set up Shield Advanced](https://docs.aws.amazon.com/waf/latest/developerguide/getting-started-ddos.html) · [Add protected resources](https://docs.aws.amazon.com/waf/latest/developerguide/configure-new-protection.html)
