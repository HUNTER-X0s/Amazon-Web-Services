PROXY AND REVERSE PROXY





What is a Proxy Server?

* A proxy server acts as an intermediary between a client (user) and the internet.
* Mechanism: Instead of a client connecting directly to a web server, the request is routed through the proxy. The server perceives the request as coming from the proxy, not the client.
* Real-life analogy: Just as a student might ask a friend to mark their presence in class (proxy), 
* a company uses a proxy to handle web requests, masking the internal IP address.



Key Advantages:

* Privacy: Hides the client's identity and IP address.
* Security: Filters incoming responses to block malicious data, viruses, or worms
* Activity Logging: Monitors and records user web activity for administrative control
* Performance: Uses caching to store frequently accessed content locally, saving bandwidth and improving speed
* Popular Example: Squid and Apache are widely used software options for forward proxying.





Forward vs. Reverse Proxy

* The primary distinction lies in where the proxy is positioned:
* Forward Proxy: Sits between the client and the internet. It serves the client.
* Reverse Proxy: Sits between the internet and the back-end servers. It serves the server infrastructure by managing incoming requests.





Features of a Reverse Proxy

* Reverse proxies are essential for professional server management:
* Security: Protects back-end servers from attacks like DDoS or DoS.
* Load Balancing: Distributes incoming traffic across multiple servers to ensure no single server is overwhelmed
* SSL/TLS Termination: Decrypts incoming encrypted requests at the proxy level, freeing up valuable processing power on the back-end applications.
* Popular Examples: NGINX, HAProxy, and Apache HTTP Server are industry standards for reverse proxy configurations.









Difference between Proxies and Firewalls:

* While both are security tools, they function differently. A proxy acts as an intermediary, processing and often filtering application-level traffic (like web requests) on behalf of clients or servers. A firewall is generally designed to monitor and control network traffic (at the packet or connection level) based on security rules to block or allow data, acting more like a gatekeeper.





Using a single server as both a Forward and Reverse Proxy:

* Yes, it is possible to configure a single server to act as both. Software like Nginx is powerful enough to handle both roles simultaneously, managing outbound requests for a local network (Forward Proxy) while also managing inbound traffic for backend servers (Reverse Proxy).

## Remember proxy direction by asking whom it serves

A **forward proxy serves clients**: internal users send requests through it toward outside services. A **reverse proxy serves an application**: outside clients connect to it, and it forwards requests to private backend servers. Both mediate requests, but their trust boundaries, authentication, and logging needs differ.

For a reverse proxy, preserve only the required headers, validate forwarded identity/IP information, restrict direct backend access, and avoid treating a proxy-provided header as trustworthy unless the proxy that set it is trusted. A proxy can add control and caching, but it does not replace application authorization or a network firewall.

**Recall check:** A server sees every user's address as the load balancer's address. Which configuration matters? Trusted proxy forwarding headers and the application's trusted-proxy list.





































