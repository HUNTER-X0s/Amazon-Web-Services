AWS DynamoDB

* Amazon DynamoDB is a fast and flexible NoSQL database service for any scale. 
* DynamoDB is a fully managed key-value and document database that delivers single-digit millisecond performance at any scale. 





What is NoSQL?

\-> NoSQL is a type of database designed to store and manage data in flexible non-tabular formats, making it ideal for volumes of unstructured data. 





DynamoDB stores data as items in tables. With each item represented as a JSON-like document consisting of key-value pairs 





DynamoDB also offers a free tier that provides 25 GB of storage. The free tier also includes 25 provisioned read/write capacity units (WCU/RCU), which is enough to handle 200 M requests per month. 





* Serverless: no need for server provisioning, software installation, maintenance, or patching.  
* Automatic scaling : instantly scales up or down based on demand with no manual adjustments needed. 
* Zero downtime : provides continuous availability without maintenance windows. 
* On-Demand Pricing: Pay only for the read/write requests used. Ideal for fluctuating workloads. 
* Idle cost savings: scale down to zero during inactivity so there no cost when tables have no traffic. 



* DynamoDB :

create a table contacts with primary key as id, type string 

* EC2 instance :

\- sudo yam install -y docker

\- sudo service docker start

\- sudo user-mode -aG docker ec2-user

\- sudo docker pull philippaul/node-dynamodb-demo



sudo docker run --rm -p 80:3000 -e DB\_HOST="YOUR_ACCESS_KEY_ID" -e DB\_USER="admin" -e DB\_PASSWORD="YOUR_SECRET_ACCESS_KEY" -d philippaul/node-mysql-app:02





* IAM access keys :

Create access and security keys for your app to connect with DynamoDB. 





sudo docker run --rm-d -p 80:3000 --name node-dynamo-app -e AWS\_REGION=es-east-1 -e AWS\_ACCESS\_KEY\_ID=YOUR_ACCESS_KEY_ID -e AWS\_SECRET\_ACCESS\_KEY=YOUR_SECRET_ACCESS_KEY philippaul/node-dynamodb-demo











It's flexible data model and reliable performance make DynamoDB a great fit for mobile, web, gaming, advertising technology, Internet of Things, and other applications. 





DynamoDB Accelerator - DAX :

* Fully managed in-memory cache for DynamoDB  
* DAX offers microsecond latency, achieving up to a 10x performance over standard DynamoDB queries. 
* High Availability and Scalability : can be deployed in multiple available zones. 
* DAX is only used for and is integrated with DynamoDB while ElasticCache can be used for other databases. 
