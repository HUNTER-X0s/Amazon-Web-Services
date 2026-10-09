“API is like a middleman between two systems. It takes a request from the user or frontend, sends it to the server, and then returns the response back.”



“API stands for Application Programming Interface. It allows different software systems to communicate with each other. For example, when a frontend application sends a request to a backend server, the API handles that request, processes it, and sends back the appropriate response.”



“API stands for Application Programming Interface. It acts as a bridge that allows different applications to communicate. In web development, APIs are used when a client sends an HTTP request to a server, and the server responds with data, usually in JSON format.”



“For example, when I open a weather app, it calls a weather API. The API fetches data from the server and returns temperature and conditions to the app.”



👉 Types of API:



* REST(Representational State Transfer) API (most common)
* SOAP API
* GraphQL



👉 Methods:



GET → fetch data

POST → send data

PUT → update

DELETE → remove



GET (Read): Retrieves data from a server without modifying anything

POST (Create): Submits data to the server to create a new resource or trigger a side effect. Repeating a POST request can create duplicate resources

PUT (Update/Replace): Replaces a target resource entirely with the new payload. If the resource doesn't exist, it can create it.

PATCH (Partial Update): Applies minor, partial modifications to a resource instead of replacing the entire thing.

DELETE (Delete): Permanently removes the specified resource from the server





A network is a collection of interconnected computing devices (for example, computers) which is used to communicate to share  files, data, logs, or resources.



An IP address contains two parts:

the Network ID and the Host ID.

🏢 Network ID: This is like the street name. It identifies the specific network your device belongs to.

💻 Host ID: This is like the house number. It identifies your specific device (computer, phone, router) on that network

Together, they make sure data traveling across the internet finds the exact right network and the exact right device!





















⚡ What is FastAPI?



👉 FastAPI = a Python framework to build APIs



You use it to write backend logic

Define routes like /login, /users

Handle requests \& return responses (mostly JSON)



👉 Simple line:



“FastAPI is used to create APIs in Python.”



🚀 What is Uvicorn?



👉 Uvicorn = a server that runs your FastAPI app



It is an ASGI server

It actually executes your app

Handles incoming HTTP requests



👉 Simple line:



“Uvicorn is the server that runs FastAPI applications.”



🔗 Relationship Between FastAPI \& Uvicorn

🎯 Best Analogy:



👉 Think like this:



FastAPI = Chef 👨‍🍳 (logic, prepares response)

Uvicorn = Waiter/Server 🧑‍💼 (takes request, brings response)



👉 Flow:



Client sends request

Uvicorn receives it

Passes it to FastAPI

FastAPI processes

Uvicorn sends response back

💬 Simple Casual Answer



“FastAPI is used to build APIs, and Uvicorn is the server that runs those APIs.”



🎯 Interview-Ready Answer



“FastAPI is a Python framework used to build APIs, while Uvicorn is an ASGI server used to run FastAPI applications. Uvicorn handles incoming requests and passes them to the FastAPI app, which processes the request and returns a response.”



🔥 Stronger Answer (To Impress)



“FastAPI is an ASGI-compatible Python framework for building high-performance APIs. Uvicorn is a lightweight ASGI server that runs FastAPI applications and handles asynchronous request processing.”



⚡ Extra (If interviewer pushes deeper)



👉 What is ASGI?



ASGI = Asynchronous Server Gateway Interface

Allows handling multiple requests at the same time (async)



👉 Why Uvicorn?



Very fast ⚡

Supports async

Ideal for FastAPI

🧠 Final Memory Trick



👉 Remember this line:



“FastAPI builds the API, Uvicorn runs it.”

