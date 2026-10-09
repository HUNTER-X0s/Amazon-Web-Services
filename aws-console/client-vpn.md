# AWS Client VPN: Console Walkthrough

**Mental model:** A Client VPN endpoint is the managed termination point; a target-network association connects it to a VPC subnet; routes define destinations; authorization rules decide which authenticated clients may reach them.

Related note: [AWS VPC.md](../../AWS%20VPC.md)

## Prepare authentication and network ranges

1. Choose the Region and VPC the endpoint will serve. Select a client CIDR that does not overlap the VPC, target networks, or routes; it cannot be changed after endpoint creation.
2. Decide mutual-certificate authentication or federated/Active Directory authentication. For certificate auth, request/import the server certificate in the same Region and prepare client certificates securely.
3. Choose split tunnel vs. full tunnel, DNS servers, transport protocol, and access requirements before building the endpoint. Use a security group that permits only required destination traffic.

## Create and configure the endpoint

1. Open [Amazon VPC](https://console.aws.amazon.com/vpc/), then **Client VPN Endpoints → Create Client VPN Endpoint**.
2. Choose **Quickstart** only if its broader default access rules fit the sandbox; otherwise choose **Standard** and configure the endpoint name, client CIDR, server certificate, authentication, DNS, and security groups.
3. Create the endpoint and wait for its state to become ready for association.
4. Select it and open **Target network associations → Associate target network**. Choose the VPC and subnet; associate subnets in multiple AZs when availability requirements justify it.
5. Under **Route table**, add routes to networks clients need to reach. Under **Authorization rules**, grant access only to the required destination CIDRs and user groups.
6. Check security-group rules on the associated resources and endpoint. For internet access, configure routes/NAT or an egress path intentionally; do not treat VPN access as automatic internet routing.
7. Choose **Download client configuration**, distribute the configuration file and credentials/certificates through an approved secure channel, and test with one authorized client.

## Verify and delete carefully

Confirm endpoint state, association state, routes, authorization rules, DNS, and client connection logs. Delete a practice endpoint only after disconnecting users and removing its associations/routes. Client VPN endpoints and connections incur hourly charges; do not leave a lab endpoint running.

**Remember:** **authenticate → associate → route → authorize → connect**.

**Official references:** [Create a Client VPN endpoint](https://docs.aws.amazon.com/vpn/latest/clientvpn-admin/cvpn-working-endpoint-create.html) · [Client VPN getting started](https://docs.aws.amazon.com/vpn/latest/clientvpn-admin/cvpn-getting-started.html)
