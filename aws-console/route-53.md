# Amazon Route 53: Console Walkthrough

**Mental model:** A hosted zone is the DNS rulebook for a domain; records are the rules; the registrar's name-server delegation points the public internet to that rulebook. Creating a hosted zone alone does not move a domain's DNS.

Related note: [Amazon Route 53.md](../../Amazon%20Route%2053.md)

## Create DNS for a domain you control

1. Open [Route 53](https://console.aws.amazon.com/route53/). Verify that you own or are authorized to manage the domain before editing public DNS.
2. Choose **Hosted zones → Create hosted zone**. Enter the domain exactly, select **Public hosted zone** for internet DNS or **Private hosted zone** for DNS within selected VPCs, and create it.
3. For a public zone, copy the assigned NS records. At the domain registrar, replace the existing name-server delegation only when you intend to make this zone authoritative. Keep the previous values so you can roll back.
4. In the hosted zone, choose **Create record**. Select a record type and routing policy. Use an Alias record for supported AWS resources such as CloudFront or load balancers; use an A/AAAA/CNAME/TXT record as appropriate for other targets.
5. Set a suitable TTL for non-alias records, review the name and value carefully, then save. Test DNS resolution and wait for TTL/caching effects.

## Add a health check or routing policy (optional)

Choose **Health checks → Create health check**, specify a supported endpoint/protocol and failure thresholds, then create a failover/weighted/latency policy only after understanding the health-check behavior and target health. Monitor check status before relying on automated failover.

## Connect on-premises DNS with Route 53 Resolver (optional)

1. Open **Route 53 → Resolver → Inbound endpoints** to let on-premises DNS resolvers send queries into a VPC, or **Outbound endpoints** to let VPC clients forward selected queries to on-premises DNS.
2. Choose **Create endpoint**, set a clear name, select the VPC and subnets in multiple AZs, and choose security groups that permit TCP and UDP port 53 only from the trusted DNS resolvers/clients.
3. For outbound resolution, create a Resolver rule for the relevant domain suffix, choose the outbound endpoint and target DNS server IPs, then associate the rule with the intended VPCs.
4. Update the on-premises DNS forwarders for inbound queries, test both directions, and check endpoint/rule status. Resolver endpoints and query volume can incur charges.

## Verify and clean up

Confirm the zone type, NS/SOA records, intended records, and authoritative DNS response. Deleting a hosted zone removes its records and can take a site offline. Route 53 hosted zones, queries, health checks, and domains have separate charges; delete only resources you own and no longer need.

**Remember:** **zone stores records; registrar delegates the zone; resolvers cache answers**.

**Official references:** [Create a public hosted zone](https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/CreatingHostedZone.html) · [Configure a new domain](https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/dns-configuring-new-domain.html)
