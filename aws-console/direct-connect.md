# AWS Direct Connect: Console Workflow

**Mental model:** Direct Connect is a dedicated network path from a customer network to an AWS Direct Connect location. The console tracks a connection and its virtual interface, but the physical cross-connect, router configuration, BGP session, and redundancy plan require coordination with the colocation provider/network team.

Related note: [AWS VPC.md](../../AWS%20VPC.md)

## Plan the connection

1. Decide whether a dedicated or partner-hosted connection fits the required bandwidth, lead time, and account ownership.
2. Select a Direct Connect location and confirm that your network provider or colocation facility can establish the physical cross-connect.
3. Design redundancy (separate connections/locations when required), routing domains, VLANs, BGP ASN, advertised prefixes, and the target: a virtual private gateway, Direct Connect gateway, or supported transit gateway architecture.
4. Estimate port-hour, data-transfer, provider/cross-connect, and any transit costs. Direct Connect is not an instant, no-cost lab resource.

## Request a connection in the console

1. Open [AWS Direct Connect](https://console.aws.amazon.com/directconnect/v2/home), choose **Connections → Create connection**.
2. Choose the connection ordering workflow and resiliency level that match the network design. Provide a name, location, bandwidth, and authorized account details.
3. Submit the request and monitor its state. Complete the physical cross-connect with the provider using the AWS-provided LOA-CFA and port details. The connection becomes available only after the physical/network handoff is complete.
4. Choose **Virtual interfaces → Create virtual interface**. Select private, public, or transit according to the destination; choose the connection, VLAN, BGP ASN, and gateway association. Do not advertise broad routes without network approval.
5. Download the router configuration and coordinate BGP settings with the network team. Verify the BGP peer state and routes from both AWS and customer-router sides.
6. Test only approved prefixes and failover behavior. For a production network, prove redundancy by a reviewed maintenance/failover exercise.

## Verify and retire

Check connection and virtual-interface state, BGP session, advertised/received routes, alarms, and provider cross-connect. To retire, coordinate traffic migration first, remove/disable virtual interfaces as needed, and cancel the physical connection through the required provider/AWS process. Contract terms may apply.

**Remember:** **physical circuit → connection → virtual interface → BGP routes → tested redundancy**.

**Official references:** [Create a dedicated connection](https://docs.aws.amazon.com/directconnect/latest/UserGuide/create-connection.html) · [Create a private virtual interface](https://docs.aws.amazon.com/directconnect/latest/UserGuide/create-private-vif.html)
