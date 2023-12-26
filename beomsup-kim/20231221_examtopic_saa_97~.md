# 총평

# 문제 97 - 틀림

A company has a large Microsoft SharePoint deployment running on-premises that requires Microsoft Windows shared file storage. The company wants to migrate this workload to the AWS Cloud and is considering various storage options. The storage solution must be highly available and integrated with Active Directory for access control.
Which solution will satisfy these requirements?

- A. Configure Amazon EFS storage and set the Active Directory domain for authentication.
- B. Create an SMB file share on an AWS Storage Gateway file gateway in two Availability Zones.
- C. Create an Amazon S3 bucket and configure Microsoft Windows Server to mount it as a volume.
- D. Create an Amazon FSx for Windows File Server file system on AWS and set the Active Directory domain for authentication.

<details>
<summary>정답 및 해설</summary>

> 정답: D

Microsoft Windows shared file storage = Amazon FSx for Windows File Server

설명에 보니 마이그레이션도 지원한다 한다.


[Examtopics](https://www.examtopics.com/discussions/amazon/view/86626-exam-aws-certified-solutions-architect-associate-saa-c03/)
</details>


# 문제 98 - 틀림

An image-processing company has a web application that users use to upload images. The application uploads the images into an Amazon S3 bucket. The company has set up S3 event notifications to publish the object creation events to an Amazon Simple Queue Service (Amazon SQS) standard queue. The SQS queue serves as the event source for an AWS Lambda function that processes the images and sends the results to users through email.
Users report that they are receiving multiple email messages for every uploaded image. A solutions architect determines that SQS messages are invoking the Lambda function more than once, resulting in multiple email messages.
What should the solutions architect do to resolve this issue with the LEAST operational overhead?

- A. Set up long polling in the SQS queue by increasing the ReceiveMessage wait time to 30 seconds.
- B. Change the SQS standard queue to an SQS FIFO queue. Use the message deduplication ID to discard duplicate messages.
- C. Increase the visibility timeout in the SQS queue to a value that is greater than the total of the function timeout and the batch window timeout.
- D. Modify the Lambda function to delete each message from the SQS queue immediately after the message is read before processing.

<details>
<summary>정답 및 해설</summary>

> 정답: C

람다가 메시지를 폴링 하면서 시작부분에 메시지를 보내기 때문이라고 한다.
좀 더 분석이 필요함

아래는 댓글 중 하나

users get duplicated messages because -> lambda polls the message, and starts processing the message.
However, before the first lambda can finish processing the message, the visibility timeout runs out on SQS, and SQS returns the message to the poll, causing another Lambda node to process that same message.
By increasing the visibility timeout, it should prevent SQS from returning a message back to the poll before Lambda can finish processing the message


[Examtopics](https://www.examtopics.com/discussions/amazon/view/85185-exam-aws-certified-solutions-architect-associate-saa-c03/)
</details>


# 문제 99 - 맞음

A company is implementing a shared storage solution for a gaming application that is hosted in an on-premises data center. The company needs the ability to use Lustre clients to access data. The solution must be fully managed.
Which solution meets these requirements?

- A. Create an AWS Storage Gateway file gateway. Create a file share that uses the required client protocol. Connect the application server to the file share.
- B. Create an Amazon EC2 Windows instance. Install and configure a Windows file share role on the instance. Connect the application server to the file share.
- C. Create an Amazon Elastic File System (Amazon EFS) file system, and configure it to support Lustre. Attach the file system to the origin server. Connect the application server to the file system.
- D. Create an Amazon FSx for Lustre file system. Attach the file system to the origin server. Connect the application server to the file system.

<details>
<summary>정답 및 해설</summary>

> 정답: D

Lustre[러스터]는 Linux + Cluster를 합친 말이다.
FSx 진도 나가진 않았지만 윈도우 버젼도 있는 걸로 봤을때 FSx 파일 시스템 관련 서비스이지 않을까?


[Examtopics](https://www.examtopics.com/discussions/amazon/view/85811-exam-aws-certified-solutions-architect-associate-saa-c03/)
</details>


# 문제 100

<details>
<summary>정답 및 해설</summary>

A company's containerized application runs on an Amazon EC2 instance. The application needs to download security certificates before it can communicate with other business applications. The company wants a highly secure solution to encrypt and decrypt the certificates in near real time. The solution also needs to store data in highly available storage after the data is encrypted.
Which solution will meet these requirements with the LEAST operational overhead?

- A. Create AWS Secrets Manager secrets for encrypted certificates. Manually update the certificates as needed. Control access to the data by using fine-grained IAM access.
- B. Create an AWS Lambda function that uses the Python cryptography library to receive and perform encryption operations. Store the function in an Amazon S3 bucket.
- C. Create an AWS Key Management Service (AWS KMS) customer managed key. Allow the EC2 role to use the KMS key for encryption operations. Store the encrypted data on Amazon S3.
- D. Create an AWS Key Management Service (AWS KMS) customer managed key. Allow the EC2 role to use the KMS key for encryption operations. Store the encrypted data on Amazon Elastic Block Store (Amazon EBS) volumes.

> 정답: C

A는 암호화 과정은 있어도 복호화 과정은 없다.
B의 "Store the function in an Amazon S3 bucket" 문제가 있다. S3 파일 저장 서비스지 펑션을 저장하는 장소가 아니다.
D: EBS 볼륨은 EC2에 연결되어 있다. 공유에 적합하진 않다.


[Examtopics](https://www.examtopics.com/discussions/amazon/view/85186-exam-aws-certified-solutions-architect-associate-saa-c03/)
</details>


# 문제 101

A solutions architect is designing a VPC with public and private subnets. The VPC and subnets use IPv4 CIDR blocks. There is one public subnet and one private subnet in each of three Availability Zones (AZs) for high availability. An internet gateway is used to provide internet access for the public subnets. The private subnets require access to the internet to allow Amazon EC2 instances to download software updates.
What should the solutions architect do to enable Internet access for the private subnets?

- A. Create three NAT gateways, one for each public subnet in each AZ. Create a private route table for each AZ that forwards non-VPC traffic to the NAT gateway in its AZ.
- B. Create three NAT instances, one for each private subnet in each AZ. Create a private route table for each AZ that forwards non-VPC traffic to the NAT instance in its AZ.
- C. Create a second internet gateway on one of the private subnets. Update the route table for the private subnets that forward non-VPC traffic to the private internet gateway.
- D. Create an egress-only internet gateway on one of the public subnets. Update the route table for the private subnets that forward non-VPC traffic to the egress-only Internet gateway.

<details>
<summary>정답 및 해설</summary>

> 정답: A


[Examtopics](https://www.examtopics.com/discussions/amazon/view/86019-exam-aws-certified-solutions-architect-associate-saa-c03/)
</details>




