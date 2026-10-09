Amazon Route 53 





AWS Route 53 is a scalable DNS service, a domain name system service for domain registration, traffic routing, and health checking capabilities. 



What is DNS? 

* DNS, or domain name system, is the internet service that translates human-friendly domain names, like www.example.com, into machine-readable IP addresses. 
* Default code for DNS domain name system service is 53. 



Global website with low latency :



How Route 53 works?

* Domain name registration : Register a domain and point it to AWS Route 53 
* Hosted Zone creation: Creating hosted Zone to manage DNS records 
* DNS records : add records, for example A, CNAME, MX, to route traffic to various endpoints.
* Routing Policies: Set up routing policies based on your needs, such as latency-based or fail-over routing.  
* Health checks: configure health checks to monitor endpoints and trigger a fail-over when needed. 





Types of records :

* A record (ipv4): maps a domain name to an IPv4 address, for example, www.google.com to 12.34.56.78. 
* AAAA Record: maps a domain name to an IPv6 address, for example, www.example.com to 2001:db8::1 
* CNAME record :  maps a domain name to another domain name, alias. For example, blog.example.com to www.example.com 
* MX record : direct mail to an email server for example : example.com to mail.example.com (priority 10)
* TXT record: provides text information to external sources for verification or configuration. For example: example.com to "v=spf1 include:\_spf.example.com \~all"
* NS record : specifies the authoritative names servers for the domain. For example example.com to ns-123.awsdns-45.org  
* SRV record: specifies the location of services. For example \_sip.\_tcp.example.com to 10 60 5060 sipserver.example.com 







Route 53 Use Cases :

* Hosting websites: Manage domain names and route traffic to web applications. 
* Load balancing: Distribute traffic across multiple endpoints using weighted or latency-based routing. 
* Disaster Recovery: Use health checks and fail-over routing for high availability. 
* Multi-region deployments: route traffic to the closest region for low latency. 





Summary of Billing: 

* Billable components include:
* \- Hosted Zones
* \- DNS queries
* \- Health checks
* \- Domain registration
* \- Traffic policies
* Costs vary based on usage and the type of configuration. Example: Standard vs Advanced Routing Policies. 
* Free tier: Route 53 does not include a free tier so charges start as well as due user services.





Domain Names: A domain is the name, such as example.com, that your users use to access your application. 



Hosted zones: specify how you want Route 53 to respond to DNS queries for a domain such as example.com. 



Health Checks: Monitor your application and web resources and direct DNS queries to healthy resources. 



Traffic flow: use a visual tool to create policies for multiple endpoints in complex configurations. 



Resolver: route DNS queries between your VPCs and your network. 

























