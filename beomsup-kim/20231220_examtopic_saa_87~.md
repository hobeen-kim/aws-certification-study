# 총평

정답율 30%

복습을 해야하는데 복습을 안해서...

# 문제 87 - 틀림

A company hosts an application on AWS Lambda functions that are invoked by an Amazon API Gateway API. The Lambda functions save customer data to an Amazon Aurora MySQL database. Whenever the company upgrades the database, the Lambda functions fail to establish database connections until the upgrade is complete. The result is that customer data is not recorded for some of the event.
A solutions architect needs to design a solution that stores customer data that is created during database upgrades.
Which solution will meet these requirements?

 - A. Provision an Amazon RDS proxy to sit between the Lambda functions and the database. Configure the Lambda functions to connect to the RDS proxy.
- B. Increase the run time of the Lambda functions to the maximum. Create a retry mechanism in the code that stores the customer data in the database.
- C. Persist the customer data to Lambda local storage. Configure new Lambda functions to scan the local storage to save the customer data to the database.
- D. Store the customer data in an Amazon Simple Queue Service (Amazon SQS) FIFO queue. Create a new Lambda function that polls the queue and stores the customer data in the database.


<details>
<summary>정답 및 해설</summary>

> 정답: A, 과반수: D

업그레이드 도중 아키텍트 디자인이 필요하니 올바른 솔루션을 고르라는 문제였습니다. 프록시를 통해서 다른 인스턴스에 연결 가능성 때문에 선택했지만 Aurora DB는 프록시를 지원하지 않는다며 D를 고른 사람도 많았습니다.

[Examtopics](https://www.examtopics.com/discussions/amazon/view/85319-exam-aws-certified-solutions-architect-associate-saa-c03/)
</details>

# 문제 88 - 틀림

A survey company has gathered data for several years from areas in the United States. The company hosts the data in an Amazon S3 bucket that is 3 TB in size and growing. The company has started to share the data with a European marketing firm that has S3 buckets. The company wants to ensure that its data transfer costs remain as low as possible.
Which solution will meet these requirements?

- A. Configure the Requester Pays feature on the company's S3 bucket.
- B. Configure S3 Cross-Region Replication from the company's S3 bucket to one of the marketing firm's S3 buckets.
- C. Configure cross-account access for the marketing firm so that the marketing firm has access to the company's S3 bucket.
- D. Configure the company's S3 bucket to use S3 Intelligent-Tiering. Sync the S3 bucket to one of the marketing firm's S3 buckets.

<details>
<summary>정답 및 해설</summary>

> 정답: B 45%, A 47%

[Examtopics](https://www.examtopics.com/discussions/amazon/view/85738-exam-aws-certified-solutions-architect-associate-saa-c03/)
</details>

# 문제 89 - 틀림

A company uses Amazon S3 to store its confidential audit documents. The S3 bucket uses bucket policies to restrict access to audit team IAM user credentials according to the principle of least privilege. Company managers are worried about accidental deletion of documents in the S3 bucket and want a more secure solution.
What should a solutions architect do to secure the audit documents?

- A. Enable the versioning and MFA Delete features on the S3 bucket.
- B. Enable multi-factor authentication (MFA) on the IAM user credentials for each audit team IAM user account.
- C. Add an S3 Lifecycle policy to the audit team's IAM user accounts to deny the s3:DeleteObject action during audit dates.
- D. Use AWS Key Management Service (AWS KMS) to encrypt the S3 bucket and restrict audit team IAM user accounts from accessing the KMS key.

<details>
<summary>정답 및 해설</summary>

> 정답: A

[Examtopics](https://www.examtopics.com/discussions/amazon/view/85808-exam-aws-certified-solutions-architect-associate-saa-c03/)
</details>

# 문제 90 - 맞음

A company is using a SQL database to store movie data that is publicly accessible. The database runs on an Amazon RDS Single-AZ DB instance. A script runs queries at random intervals each day to record the number of new movies that have been added to the database. The script must report a final total during business hours.
The company's development team notices that the database performance is inadequate for development tasks when the script is running. A solutions architect must recommend a solution to resolve this issue.
Which solution will meet this requirement with the LEAST operational overhead?

- A. Modify the DB instance to be a Multi-AZ deployment.
- B. Create a read replica of the database. Configure the script to query only the read replica.
- C. Instruct the development team to manually export the entries in the database at the end of each day.
- D. Use Amazon ElastiCache to cache the common queries that the script runs against the database.

<details>
<summary>정답 및 해설</summary>

> 정답: B

[Examtopics](https://www.examtopics.com/discussions/amazon/view/85339-exam-aws-certified-solutions-architect-associate-saa-c03/)
</details>

# 문제 91 - 틀림

A company has applications that run on Amazon EC2 instances in a VPC. One of the applications needs to call the Amazon S3 API to store and read objects. According to the company's security regulations, no traffic from the applications is allowed to travel across the internet.
Which solution will meet these requirements?

- A. Configure an S3 gateway endpoint.
- B. Create an S3 bucket in a private subnet.
- C. Create an S3 bucket in the same AWS Region as the EC2 instances.
- D. Configure a NAT gateway in the same subnet as the EC2 instances.

<details>
<summary>정답 및 해설</summary>

> 정답: A

***CORRECT***
The correct solution is Option A (Configure an S3 gateway endpoint.)

A gateway endpoint is a VPC endpoint that you can use to connect to Amazon S3 from within your VPC. Traffic between your VPC and Amazon S3 never leaves the Amazon network, so it doesn't traverse the internet. This means you can access Amazon S3 without the need to use a NAT gateway or a VPN connection.

***WRONG***
Option B (creating an S3 bucket in a private subnet) is not a valid solution because S3 buckets do not have subnets.

Option C (creating an S3 bucket in the same AWS Region as the EC2 instances) is not a requirement for meeting the given security regulations.

Option D (configuring a NAT gateway in the same subnet as the EC2 instances) is not a valid solution because it would allow traffic to leave the VPC and travel across the Internet.

[Examtopics](https://www.examtopics.com/discussions/amazon/view/85667-exam-aws-certified-solutions-architect-associate-saa-c03/)
</details>

# 문제 92 - 틀림

<details>
<summary>정답 및 해설</summary>

A company is storing sensitive user information in an Amazon S3 bucket. The company wants to provide secure access to this bucket from the application tier running on Amazon EC2 instances inside a VPC.
Which combination of steps should a solutions architect take to accomplish this? (Choose two.)

- A. Configure a VPC gateway endpoint for Amazon S3 within the VPC.
- B. Create a bucket policy to make the objects in the S3 bucket public.
- C. Create a bucket policy that limits access to only the application tier running in the VPC.
- D. Create an IAM user with an S3 access policy and copy the IAM credentials to the EC2 instance.
- E. Create a NAT instance and have the EC2 instances use the NAT instance to access the S3 bucket.

> 정답: A, C

A. This eliminates the need for the traffic to go over the internet, providing an added layer of security.

B. It is important to restrict access to the bucket and its objects only to authorized entities.

C. This helps maintain the confidentiality of the sensitive user information by limiting access to authorized resources.

D. In this case, since the EC2 instances are accessing the S3 bucket from within the VPC, using IAM user credentials is unnecessary and can introduce additional security risks.

E. a NAT instance to access the S3 bucket adds unnecessary complexity and overhead.

In summary, the recommended steps to provide secure access to the S3 from the application tier running on EC2 inside a VPC are to configure a VPC gateway endpoint for S3 within the VPC (option A) and create a bucket policy that limits access to only the application tier running in the VPC (option C).

[Examtopics](https://www.examtopics.com/discussions/amazon/view/85903-exam-aws-certified-solutions-architect-associate-saa-c03/)
</details>

# 문제 93 - 맞음

<details>
<summary>정답 및 해설</summary>

A company runs an on-premises application that is powered by a MySQL database. The company is migrating the application to AWS to increase the application's elasticity and availability.
The current architecture shows heavy read activity on the database during times of normal operation. Every 4 hours, the company's development team pulls a full export of the production database to populate a database in the staging environment. During this period, users experience unacceptable application latency. The development team is unable to use the staging environment until the procedure completes.
A solutions architect must recommend replacement architecture that alleviates the application latency issue. The replacement architecture also must give the development team the ability to continue using the staging environment without delay.
Which solution meets these requirements?

- A. Use Amazon Aurora MySQL with Multi-AZ Aurora Replicas for production. Populate the staging database by implementing a backup and restore process that uses the mysqldump utility.
- B. Use Amazon Aurora MySQL with Multi-AZ Aurora Replicas for production. Use database cloning to create the staging database on-demand.
- C. Use Amazon RDS for MySQL with a Multi-AZ deployment and read replicas for production. Use the standby instance for the staging database.
- D. Use Amazon RDS for MySQL with a Multi-AZ deployment and read replicas for production. Populate the staging database by implementing a backup and restore process that uses the mysqldump utility.

> 정답: B

[Examtopics](https://www.examtopics.com/discussions/amazon/view/85729-exam-aws-certified-solutions-architect-associate-saa-c03/)
</details>

# 문제 94 - 틀림

<details>
<summary>정답 및 해설</summary>

A company is designing an application where users upload small files into Amazon S3. After a user uploads a file, the file requires one-time simple processing to transform the data and save the data in JSON format for later analysis.
Each file must be processed as quickly as possible after it is uploaded. Demand will vary. On some days, users will upload a high number of files. On other days, users will upload a few files or no files.
Which solution meets these requirements with the LEAST operational overhead?

- A. Configure Amazon EMR to read text files from Amazon S3. Run processing scripts to transform the data. Store the resulting JSON file in an Amazon Aurora DB cluster.
- B. Configure Amazon S3 to send an event notification to an Amazon Simple Queue Service (Amazon SQS) queue. Use Amazon EC2 instances to read from the queue and process the data. Store the resulting JSON file in Amazon DynamoDB.
- C. Configure Amazon S3 to send an event notification to an Amazon Simple Queue Service (Amazon SQS) queue. Use an AWS Lambda function to read from the queue and process the data. Store the resulting JSON file in Amazon DynamoDB.
- D. Configure Amazon EventBridge (Amazon CloudWatch Events) to send an event to Amazon Kinesis Data Streams when a new file is uploaded. Use an AWS Lambda function to consume the event from the stream and process the data. Store the resulting JSON file in an Amazon Aurora DB cluster.

> 정답: C

[Examtopics](https://www.examtopics.com/discussions/amazon/view/86676-exam-aws-certified-solutions-architect-associate-saa-c03/)
</details>

# 문제 95 - 맞음

<details>
<summary>정답 및 해설</summary>

An application allows users at a company's headquarters to access product data. The product data is stored in an Amazon RDS MySQL DB instance. The operations team has isolated an application performance slowdown and wants to separate read traffic from write traffic. A solutions architect needs to optimize the application's performance quickly.
What should the solutions architect recommend?

- A. Change the existing database to a Multi-AZ deployment. Serve the read requests from the primary Availability Zone.
- B. Change the existing database to a Multi-AZ deployment. Serve the read requests from the secondary Availability Zone.
- C. Create read replicas for the database. Configure the read replicas with half of the compute and storage resources as the source database.
- D. Create read replicas for the database. Configure the read replicas with the same compute and storage resources as the source database.

> 정답: D

[Examtopics](https://www.examtopics.com/discussions/amazon/view/85906-exam-aws-certified-solutions-architect-associate-saa-c03/)
</details>

# 문제 96 - 틀림

An Amazon EC2 administrator created the following policy associated with an IAM group containing several users:
![image-001](https://img.examtopics.com/aws-certified-solutions-architect-associate-saa-c03/image1.png)
What is the effect of this policy?

- A. Users can terminate an EC2 instance in any AWS Region except us-east-1.
- B. Users can terminate an EC2 instance with the IP address 10.100.100.1 in the us-east-1 Region.
- C. Users can terminate an EC2 instance in the us-east-1 Region when the user's source IP is 10.100.100.254.
- D. Users cannot terminate an EC2 instance in the us-east-1 Region when the user's source IP is 10.100.100.254.

<details>
<summary>정답 및 해설</summary>

> 정답: C

[Examtopics](https://www.examtopics.com/discussions/amazon/view/86460-exam-aws-certified-solutions-architect-associate-saa-c03/)
</details>

