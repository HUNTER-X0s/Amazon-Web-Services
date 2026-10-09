AWS VPC
Virtual Private Cloud



Virtual Private Cloud (VPC)

* A Private isolated network within the AWS cloud where you can launch and manage your resources securely.
* Why do we need VPC?
To securely isolate and control network environments



VPC CIDR block
When you create a VPC, you specify a CIDR block that defines the IP address range for the entire VPC. For example, 10.0.0/16.
This block allows for 65,536 IP addresses, but in reality, 65,531 usable addresses. CIDR (Classless Inter-Domain Routing) is a method for allocating IP addresses and routing Internet Protocol (IP) packets.



What is a subnet?
A subnet is a smaller, segmented part of a larger network that isolates and organizes devices within a specific IP address range.
For example, VPC: 100 IPs divided into 50 IPs public subnet and  50 IPs private subnet.



What happens when creating a subnet? 

* CIDR block allocation: You specify a range of IP addresses (CIDR block) within the VPC's IP address range for the subnet.
* This determines the pool of IP addresses available for instances in the subnet.





Subnets/CIDR blocks 

* within the virtual private cloud: you can create subnets by allocating smaller CIDR blocks from the VPC's range. 
* For example public subnet 10.0.1.0/24 and private subnet 10.0.2.0/24. Each of these subnets has 256 IP addresses (251) usable.





IPv4 address is 32 bits long. 

Example in binary: 10.0.1.0 is equals to  00001010.000000000.0000000001.000000000 



The /24 indicates that the first 24 bits are the network portion of the address and the remaining 8 bits are available for host addresses within the network. 

10.0.1.0/24, 10.0.1.255 is the full range. 





Route table:

A route table is a set of rules called routes that are used to determine where network traffic from your subnets or gateway is directed. Each subnet in your VPC must be associated with a route table, which controls the routing for that subnet. 





Internet gateway:

An internet gateway is a component that allows communication between instances in your VPC and the internet. 





Security groups:

Network firewall rules that control inbound and outbound traffic for instances 





Network (ACLs) Access Control Lists :

* Optional layer of security for your VPC that acts as a firewall for controlling traffic in and out of one or more subnets. 
* Allow or deny rule 





NAT (network address translation) gateway :

It enables instances in a private subnet to connect to the Internet or other AWS services but prevents the Internet from initiating connections to those instances. 





VPC peering is a networking connection between two VPCs that enables you to route traffic between them privately. 





VPC endpoints allow you to privately connect your VPC to supported AWS services and VPC Endpoints services powered by AWS Private Link. 







Bastion hosts : a special-purpose instance that provides secure access to your instances in private subnets. 







Elastic IP addresses : Static IP address is designed for dynamic cloud computing. 







VPC flow logs : capture information about the IP traffic going to and from network interfaces in your VPC. 





Direct Connect : establishes a dedicated network connection from your premises to the database. 





AWS Client VPN: 

Managed VPN service that enables secure remote access to AWS resources and on premises networks using open VPN-based clients. 





























