# Amazon VPC and Networking: Console Walkthrough

**Mental model:** A VPC is your private address space. Subnets divide it by Availability Zone; route tables pick destinations; gateways provide paths out; security groups and network ACLs filter traffic. Think **address → placement → route → permission**.

Related note: [AWS VPC.md](../../AWS%20VPC.md)

## Build a small VPC

1. Open [Amazon VPC](https://console.aws.amazon.com/vpc/), choose the Region, and select **Your VPCs → Create VPC**.
2. Choose **VPC and more** for a guided network, not **VPC only**. Add a name tag, a non-overlapping IPv4 CIDR (for example `10.20.0.0/16`), and two Availability Zones.
3. Create public and private subnets across those AZs. Review the diagram, subnet CIDRs, route tables, and gateways before creating.
4. For a learning network, avoid a NAT Gateway unless private instances need outbound internet access: it has hourly and data-processing charges. If selected, one NAT Gateway per AZ improves availability but increases cost.
5. Choose **Create VPC**, then verify the VPC, subnets, route tables, and gateway attachments show the intended state.

## Understand and configure the network pieces

- **Subnet:** From **Subnets → Create subnet**, select the VPC, AZ, and a non-overlapping range inside the VPC CIDR. Public/private is determined by routes and address assignment, not by the subnet's name.
- **Internet Gateway (IGW):** Create one under **Internet gateways**, attach it to the VPC, then add `0.0.0.0/0 → IGW` only to a public subnet route table. A public IPv4 address and restrictive security group are also required for direct inbound IPv4 access.
- **NAT Gateway:** Under **NAT gateways → Create NAT gateway**, select a public subnet and allocate/associate an Elastic IP. Add `0.0.0.0/0 → NAT Gateway` to the private route table. This allows private resources to initiate outbound IPv4 connections; it does not accept unsolicited inbound connections.
- **Route table:** Create/edit routes under **Route tables** and associate the table with each intended subnet. A route is a destination plus a target; more specific routes win.
- **Security group:** Create under **Security groups**, choose the VPC, then allow only required protocol/port/source. Security groups are stateful and allow rules only. Prefer a source security group over a broad IP range for app-to-database traffic.
- **Network ACL:** Under **Network ACLs**, associate it with subnets and set ordered inbound/outbound allow and deny rules. NACLs are stateless, so return traffic must be allowed in the opposite direction; the default NACL is usually simpler for a first lab.
- **VPC endpoint:** Under **Endpoints → Create endpoint**, choose AWS service or endpoint service, the VPC, endpoint type, and route tables/subnets as appropriate. Gateway endpoints (S3/DynamoDB) update route tables; interface endpoints create ENIs and use security groups.
- **VPC peering:** Under **Peering connections → Create**, request the peer VPC/account/Region, accept the request, add routes on both sides, and allow traffic in security groups. CIDRs must not overlap; peering is not transitive.
- **Flow Logs:** Under **Your VPCs → select VPC → Actions → Create flow log**, choose traffic scope, destination (CloudWatch Logs or S3), and the required delivery role. Flow Logs help diagnose IP traffic; they do not capture packet payloads.
- **Client VPN:** Use the dedicated [Client VPN walkthrough](client-vpn.md) for the endpoint, subnet association, route, authorization, and client-configuration steps.
- **Direct Connect:** Use the dedicated [Direct Connect workflow](direct-connect.md) for physical connection ordering, provider cross-connect, virtual interfaces, BGP, and redundancy. This is not a quick disposable lab resource.
- **Bastion host:** Prefer Systems Manager Session Manager where possible. If a bastion is required, place it in a public subnet and restrict its administrative ingress to approved source IPs; keep application and database hosts private.

## Verify the path

For an instance in a public subnet, check its subnet association, default route to an attached IGW, public address, and inbound/outbound security rules. For a private instance, check its route (NAT or endpoint), DNS settings, and source/destination firewall rules. Use Reachability Analyzer or Flow Logs to narrow down path problems.

## Clean up

Delete dependent resources before the VPC: instances and ENIs, NAT gateways, endpoints, VPN attachments, peering, custom route table associations, then subnets and gateways, and finally the VPC. Release unused Elastic IPs. NAT gateways, interface endpoints, VPNs, and data transfer can continue to cost money while present.

**Official references:** [Create a VPC](https://docs.aws.amazon.com/vpc/latest/userguide/create-vpc.html) · [Route tables](https://docs.aws.amazon.com/vpc/latest/userguide/VPC_Route_Tables.html) · [Security groups](https://docs.aws.amazon.com/vpc/latest/userguide/vpc-security-groups.html) · [VPC endpoints](https://docs.aws.amazon.com/vpc/latest/privatelink/vpc-endpoints.html)
