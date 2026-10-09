HTTP





HTTP protocol and how it facilitates communication across the internet. 



1\. Fundamentals of HTTP

* Protocols: Defined as a set of rules for communication between entities 
* Client-Server Architecture: HTTP operates on a client-server model, where the client sends requests and the server provides responses 
* Statelessness: HTTP is an "application-level" and "stateless" protocol (2:01). It is designed to be stateless to save memory and improve scalability, as servers do not store information about previous requests 





2\. Communication Mechanisms

* Client-First: Typically, the client must initiate the request to receive a response (4:40). Other technologies like WebSockets and Polling are used for real-time or continuous data updates 





3\. Anatomy of Requests and Responses

* URL Structure: A URL is composed of a scheme, authority (user info, host, port), path, and query parameters
* Request Structure: Consists of a start line (method, path, version), headers (metadata like User-Agent or Authorization), an empty line, and an optional body 
* Response Structure: Includes a status code, headers, and the requested data 





4\. Status Codes

* Status codes categorize the result of a request:
* 1xx: Information/Continue
* 2xx: Success
* 3xx: Redirection
* 4xx: Client Errors (e.g., 401 Unauthorized vs 403 Forbidden) 
* 5xx: Server Errors 





5\. HTTP Methods

* Methods include GET (retrieval), POST (creating data), PUT (replacing resources), PATCH (updating resources), and DELETE 
* Safe vs. Idempotent: Methods are categorized by whether they modify data ("safe") or produce the same result regardless of how many times they are called ("idempotent") 





6\. Session Management and Security

* Cookies and Sessions: Since HTTP is stateless, cookies are used to keep users logged in by passing data back and forth 
* Cookie Security: Using HttpOnly and Secure flags prevents vulnerabilities like cross-site scripting 
* HTTPS: Adds a TLS layer on top of HTTP to encrypt data in transit, ensuring privacy 















Postman



A open source leading tool for API testing. It walks through the complete workflow of setting up the environment, organizing requests, and testing various API functionalities.







