AWS ELB

Elastic Load balancing



ELB - Elastic load balancer

ASG - Auto scaling groups



scalability : scalability means the ability to grow your system's resources when your application or website gets more traffic or more users. 



Vertical scalability (scaling up) :

* It means adding more power (CPU, RAM) to your existing server. 
* For example, t2.micro to m5.large 



Horizontal scalability (scaling out) : 

* Horizontal scalability means adding more instances/servers to distribute the load. 
* We can add more EC2 instances behind a load balancer. 



High Availability :

High Availability means keeping your service up and running with minimal downtime so it's always accessible to users.  

Example : running resources in multiple availability Zones. 





Elasticity ::

Elasticity means the ability to automatically adjust resources as the demand changes, adding more when needed and removing when it is no longer necessary. 

Ex - ASG





Elastic Load Balancer Points :

* Distributes traffic: It splits incoming traffic across multiple servers so no single server gets overloaded. 
* It improves availability : If one server goes down, the load balancer automatically sends traffic to the working servers, ensuring your application stays available. 
* It scales resources : It helps manage high demand by adding more servers during peak times and distributing the load. 

Single point of access needs to be exposed. 

High availability across availability zones 





AWS offers different types of load balancers depending on your needs :

* Application load balancer (ALB) is perfect for web applications handling complex HTTP and HTTPS requests layer 7. 
* Network Load Balancer (NLB) is designed for high performance and low latency, perfect for TCP/UDP traffic. Example: Gaming, Financial Apps, Layer 4. 
* Gateway Load Balancer helps deploy, scale, and manage third-party virtual appliances such as firewalls and monitoring solutions. 





Creating ELB :

1\. Set up EC2 instances.

2\. Create 2 or more EC2 instances.

3\. Install a web server and tag them for easy identification.

4\. Configure security groups.

5\. Set up a security group allowing HTTP and SSH access.

6\. Create the load balancer.

7\. Use EC2 Dashboard to create an application load balancer and set it as internet-facing.

8\. Register targets.

9\. Add EC2 instances to the target group and configure health checks.

10\. Test the load balancer.

11\. Access the DNS name of the load balancer and observe load balancing in action.



Auto Scaling Group (ASG) :

* AWS ASG Auto Scaling Group is a service that automatically adds or removes EC2 instances based on demand to ensure your application is always available. 
* It helps scale up when more capacity is needed and scale down during low usage to save costs, keeping the right number of servers running at all times. 



Functions :

* Automatic scaling: scale the number of EC2 instances up or down based on the demand. 
* Maintain instance health and replace unhealthy instances automatically to ensure reliability.
* Use scaling policies and set rules for scaling based on metrics like CPU usage or request count.
* Ensure availability and always keep a defined number of instances running to meet application needs. 
* Schedule scaling and pre-configure scaling activities for specific times 

&#x20;- Ex : during traffic peaks. 

* Distribute instances : Deploy instances across multiple availability zones for high availability. 
* Integrate with ELB : Attach instances to an elastic load balancer to automatically balance traffic. 
* Optimize costs : scale down during low demand to save on infrastructure costs. 





Steps to create an ASG 

* Launch Template or Configuration
* Create Auto Scaling Group
* Select VPC and Subnets
* Attach Load Balancer (optional)
* Configure scaling policies
* Health Checks
* Add Notifications (optional)
* Review and create

## Keep the traffic layers separate in your memory

An Elastic Load Balancer is the **front door and traffic distributor**. Its listener accepts a protocol/port, its rules choose a target group, and health checks decide which targets are ready. An Auto Scaling group is a different service: it changes how many EC2 instances exist and replaces unhealthy ones. Connecting them lets capacity changes and traffic routing work together.

Choose ALB for HTTP/HTTPS application routing, NLB for high-performance transport-level traffic, and Gateway Load Balancer for supported virtual network appliances. For public web traffic, terminate HTTPS with a valid certificate and let the target group health path reflect actual app readiness.

**Recall check:** The ALB is healthy but no page loads. Check listener/rule, target registration and health, target port, and the target security group's source rule.

**Console practice:** [Load Balancer walkthrough](guides/aws-console/elastic-load-balancing.md) · [Auto Scaling walkthrough](guides/aws-console/ec2-auto-scaling.md)



























































