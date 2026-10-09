# Elastic Load Balancing: Console Walkthrough

**Mental model:** A load balancer is the stable front door; a listener accepts a protocol/port, a rule selects a target group, and health checks keep unhealthy targets out of rotation. For HTTP apps, start by understanding an Application Load Balancer (ALB).

Related note: [AWS ELB.md](../../AWS%20ELB.md)

## Create a target group

1. Open [EC2](https://console.aws.amazon.com/ec2/) and choose **Target groups → Create target group**.
2. Choose **Instances** for EC2 targets, **IP addresses** for routable IP targets, or the appropriate target type for the workload. Choose **HTTP/HTTPS** for a web app or TCP/TLS for a lower-level service.
3. Select the VPC, set the application port and path for health checks, and create the group.
4. Register test instances or addresses. Make sure each target's security group allows traffic from the ALB security group on the target port.

## Create an Application Load Balancer

1. In **Load balancers → Create load balancer**, choose **Application Load Balancer**.
2. Give it a name, choose **Internet-facing** only for a public app (otherwise choose internal), and select at least two public subnets in different AZs for an internet-facing ALB.
3. Create/select an ALB security group. Permit only intended client traffic (for example HTTPS from the required sources); do not open management ports.
4. Add a listener and forward action to the target group. For a real public site, configure HTTPS using an ACM certificate and consider redirecting HTTP to HTTPS.
5. Review listeners, subnets, security groups, target group, and estimated charges, then create the ALB.
6. Wait for ALB state **Active** and target health **Healthy**. Test the DNS name with a harmless request.

## Choose another load balancer type

- **Network Load Balancer:** choose for high-performance TCP/UDP/TLS and connection-level routing.
- **Gateway Load Balancer:** choose when inserting supported network appliances into traffic paths.
- For any type, confirm target registration, health checks, cross-zone behavior, exposure, and idle cost before creating.

## Clean up

Delete the listener/load balancer and target group when unused, then remove any practice instances and security-group rules. Load balancers have hourly and capacity charges while provisioned.

**Remember:** **listener receives → rule routes → target group checks health**.

**Official references:** [Create an ALB](https://docs.aws.amazon.com/elasticloadbalancing/latest/application/create-application-load-balancer.html) · [Target groups](https://docs.aws.amazon.com/elasticloadbalancing/latest/application/load-balancer-target-groups.html)
