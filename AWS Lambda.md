AWS Lambda





* AWS Lambda is a serverless computing service that lets you run code in response to events without managing servers. 
* You just upload your code and AWS automatically handles the rest, scaling as needed and only charging for the time your code runs. 





Event-Driven Execution :

* Lambda is an event-driven service, meaning that it runs your code in response to certain triggers or events.
* These events can come from many different AWS services like:
* S3 (file uploads)
* dynamoDB (database changes)
* api gateway (http requests)
* cloud watch (scheduled events), etc







* Execution Time Limit: Lambda functions can only run for a maximum of 15 minutes. If you need longer running tasks, Lambda might not be the best choice. 
* Stateless: Lambda functions don't keep state between invocations so they are best for tasks that don't require long-term memory. 
* cold Start Delays: If a lambda function has not run in a while, there is a slight delay called a cold Start when it starts up. This can add a little latency but AWS provides ways to mitigate it for critical functions.





* Image Processing: Let's say users upload images to your app. You can set up Lambda to automatically resize, compress, or even apply filters to each image as it is uploaded. 
* Data Transformation: If you need to clean up or process data before storing it in a database, a Lambda function can handle that transformation automatically. 
* Real-time notifications: if an event happens, like a new user signing up, you can use Lambda to trigger an email, SMS, or other notifications instantly. 







Automatic scaling :

* &#x20;AWS Lambda automatically scales the execution of functions in response to the number of incoming requests. 
* If a thousand requests come at the same time, AWS Lambda will handle them in parallel, making it highly scalable without any configuration.





Pay as you go :

* &#x20;Lambda uses a pay-as-you-go pricing model you had built based on the number of function executions and the duration of functions' runtime, measured in milliseconds. 
* This is cost-effective as you only pay for the compute time that you use and there is no charge for idle time. 





































