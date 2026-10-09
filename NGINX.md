NGINX





What is Nginx?

* Nginx is a lightweight, high-performance web server designed to handle massive amounts of traffic efficiently compared to traditional servers like Apache.



HTTP Request Basics :

* When a user enters a URL, an HTTP request is sent to a web server, which processes it and returns the requested data as a response.



Load Balancer :

* Nginx acts as a load balancer by distributing incoming traffic across multiple backend servers. This prevents any single server from being overwhelmed, ensuring faster performance.



Reverse Proxy :

* It sits in front of backend servers, acting as a single entry point. This hides the internal infrastructure from users and improves security and management.



SSL Termination :

* Nginx can handle the decryption of secure (HTTPS) traffic, offloading this resource-heavy process from the backend servers.



Compression and Segmentation :

* To optimize bandwidth, Nginx compresses data before sending it and segments large files into smaller chunks to prevent network congestion.



Nginx vs. Apache :

* While Apache uses a thread-based model, Nginx uses an event-driven, asynchronous model, making it superior for serving static content and handling high concurrency.



Caching :

* It can store copies of frequently requested content, allowing the server to respond faster without needing to query the database repeatedly.

## Remember Nginx as a traffic handler

Nginx accepts client connections, evaluates the request, and either serves a local/static response or forwards the request to an upstream application. As a reverse proxy, it can centralize TLS termination, routing, compression, and caching. The upstream application's own authorization and input checks still protect the data.

When debugging, trace **DNS → listener/port → TLS certificate → Nginx server/location rule → upstream address/health → app response**. Check logs and test configuration before reload. Set cache rules conservatively so personalized or authenticated content is not shared between users.

**Recall check:** Nginx returns `502`. Which hop is most likely failing? The connection from Nginx to its configured upstream, though logs and network checks determine the cause.













