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


# 문제 98

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


# 문제 99

<details>
<summary>정답 및 해설</summary>

> 정답:


[Examtopics](https://www.examtopics.com/discussions/amazon/view/85811-exam-aws-certified-solutions-architect-associate-saa-c03/)
</details>


# 문제 100

<details>
<summary>정답 및 해설</summary>

> 정답:


[Examtopics](https://www.examtopics.com/discussions/amazon/view/85186-exam-aws-certified-solutions-architect-associate-saa-c03/)
</details>


# 문제 101

<details>
<summary>정답 및 해설</summary>

> 정답:


[Examtopics](https://www.examtopics.com/discussions/amazon/view/86019-exam-aws-certified-solutions-architect-associate-saa-c03/)
</details>


# 문제 102

<details>
<summary>정답 및 해설</summary>

> 정답:


[Examtopics](https://www.examtopics.com/discussions/amazon/view/85814-exam-aws-certified-solutions-architect-associate-saa-c03/)
</details>


# 문제 103

<details>
<summary>정답 및 해설</summary>

> 정답:


[Examtopics](https://www.examtopics.com/discussions/amazon/view/85781-exam-aws-certified-solutions-architect-associate-saa-c03/)
</details>


# 문제 104

<details>
<summary>정답 및 해설</summary>

> 정답:


[Examtopics](https://www.examtopics.com/discussions/amazon/view/85342-exam-aws-certified-solutions-architect-associate-saa-c03/)
</details>


# 문제 105

<details>
<summary>정답 및 해설</summary>

> 정답:


[Examtopics](https://www.examtopics.com/discussions/amazon/view/85816-exam-aws-certified-solutions-architect-associate-saa-c03/)
</details>


# 문제 106

<details>
<summary>정답 및 해설</summary>

> 정답:


[Examtopics](https://www.examtopics.com/discussions/amazon/view/85817-exam-aws-certified-solutions-architect-associate-saa-c03/)
</details>


