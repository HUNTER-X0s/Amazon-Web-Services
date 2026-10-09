Client-side and Server-side





Distinction between client-side and server-side technologies in web development. Different parts of a website's code are executed and why this separation is necessary.



Web Architecture Overview

At its core, a web application operates on a client-server architecture. A user (the client) sends a request from their device to a web server, which then processes that request and sends back a response. A modern website is composed of multiple technologies working in tandem, including structural languages (HTML), styling languages (CSS), interactive scripting (JavaScript), and backend languages (like Python or Java) alongside database management systems.



Client-Side Technology

Client-side technology refers to the code that is executed directly on the user's device, typically within their web browser. When a user requests a page, the server sends the source code (such as HTML, CSS, and JavaScript) to the browser, which then handles the rendering and execution. Because the browser performs this work, client-side technologies are essential for creating the visual interface and interactivity of a website. A key characteristic of client-side code is that it is accessible and can be viewed by the user via the browser's "View Source" feature.



Server-Side Technology

Server-side technology refers to code that runs on the web server rather than the user's device. Technologies like JSP (Java Server Pages), servlets, or Django/Python frameworks fall into this category. The primary reason for using server-side execution is to maintain consistency and security across different operating systems. By running code on the server, developers ensure that the end result is processed uniformly before being sent to the client, regardless of whether the user is on Windows, macOS, or Linux. This prevents potential compatibility issues where code might behave differently depending on the user's local machine.



Key Comparison

* Execution Location: Client-side code runs on the user's browser, while server-side code runs on the remote web server.
* Dependencies: Client-side code relies on the browser to execute, whereas server-side code requires a web server environment to process requests and communicate with databases.
* Independence: Server-side processing is crucial for platform independence, ensuring that the application logic remains stable across different computing environments.

## Remember client and server by asking “who runs this code?”

The browser owns client-side execution: page layout, user interaction, and code shipped to each user's device. The server owns server-side execution: trusted business rules, protected credentials, database access, and responses sent back over the network. A browser can display a button, but it cannot be trusted to enforce authorization; the server must check permissions for every protected action.

The common flow is `browser request → server validation/business logic → data service → response → browser render`. Keep secrets and private signing keys on trusted server-side systems, and treat all client input as untrusted even when the UI validates it.

**Recall check:** Where should the rule “only the owner may edit this record” be enforced? On the server, regardless of what the client interface shows.

