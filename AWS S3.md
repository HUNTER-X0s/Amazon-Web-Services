AWS S3

AWS S3 bucket :
AWS S3 - Simple Storage Service 
Uploading Static Website
Version Control 
Website host and access 

- S3 Versioning
- S3 Replication
- Data Encryption
- S3 Bucket Policies
- S3 Storage Classes
- Logging Monitoring
- Hosting Static Website
- Snow Family
- Storage gateway (Hybrid Solution)


AWS S3 (Simple Storage Service) is a cloud-based storage service that allows you to store, manage, and retrieve large amounts of data like files, images, videos, and backups securely and at scale. 
It provides highly reliable scalable object storage, making your data accessible from anywhere, anytime via the internet. 

Store data as objects
globally unique name
region-specific
Each object within a bucket is stored as a key-value pair.
           - Key is the object's name, which can contain slashes, mimicking directory structure.
           - Value is the content of the object, the file or data itself.

Maximum object size: 5 TB is the maximum size for a single object in Amazon S3. 
Multi-part upload is recommended for objects larger than 5 GB. Split the file into smaller parts and upload them separately. 

S3 bucket policies :
JSON-based access control policies that you attach directly to an S3 bucket to manage permissions for accessing the bucket and its objects.
They allow you to define who can access the data and what actions they can perform, just read, write, or delete, enabling fine-grained control over the utility of your data stored in S3.
Write or paste your JSON policy in the bucket policy editor.
You can use AWS Policy generator to create a custom policy or you can manually write the policy in JSON format. 

 - GetObject is used to retrieve or download files from an S3 bucket
 - PutObject is used to upload or add files into an S3 bucket. 

S3 Versioning:
It allows you to keep multiple versions of an object in the same bucket, providing protection against accidental deletions or overrides.
When versioning is enabled S3 stores every version of an object, allowing you to recover older versions if needed, making it ideal for data safety and back-up. 

S3 Replication :
It allows you to automatically copy objects from one S3 bucket to another, which can be within
 - the same region (Same Region Replication SRR) or
 - in different regions (Cross Region Replication CRR). 
It is commonly used for compliance, redundancy, and to improve data access performance by maintaining copies close to your users. 

S3 storage class :
- S3 Standard
- S3 Intelligent Tiring
- S3 Standard Infrequent Access
- S3 One zone I/A Infrequent Access
- S3 Glacier
- S3 Glacier Deep Archive
- S3 Outpost

S3 bucket lifecycle:
You can use lifecycle policies to control the movement of objects between different storage classes or delete them entirely based on specific conditions like age or inactivity. 

S3 snow family :
The S3 Snow Family is a group of physical devices supported by AWS to help move large amounts of data to the cloud when using the Internet is not practical. These devices are used when there is too much data to upload over a regular connection or when dealing with remote areas without good internet. 

The Snow family includes:
AWS Snow Cone, a small portable device for a few terabytes of data
AWS SnowBall, a larger device for moving peta-bytes of data and can also be used for edge computing
AWS Snow Mobile, a massive truck-sized container used for exabyte-scale data transports, typically used by big companies moving entire data centers
These devices help you transfer data quickly, securely, and cost-effectively to AWS, especially when internet speed or reliability is an issue

Amazon S3 Storage Gateway  :
It is a hybrid cloud storage service that connects premises environments to cloud storage in Amazon S3. It helps extend your local storage to the cloud by acting as a bridge. 



