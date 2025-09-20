---
layout: exam
---

# Practice Exam 3

1. A company has a large Microsoft SharePoint deployment running on-premises that requires Microsoft Windows shared file storage. The company wants to migrate this workload to the AWS Cloud and is considering various storage options. The storage solution must be highly available and integrated with Active Directory for access control.
Which solution will satisfy these requirements?
    - A. Configure Amazon EFS storage and set the Active Directory domain for authentication
    - B. Create an SMB Me share on an AWS Storage Gateway tile gateway in two Availability Zones
    - C. Create an Amazon S3 bucket and configure Microsoft Windows Server to mount it as a volume
    - D. Create an Amazon FSx for Windows File Server file system on AWS and set the Active Directory domain for authentication

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: D
      Explanation: Amazon FSx for Windows File Server is a fully managed file storage service that is designed to be used with Microsoft Windows workloads. It is integrated with Active Directory for access control and is highly available, as it stores data across multiple availability zones. Additionally, FSx can be used to migrate data from on-premises Microsoft Windows file servers to the AWS Cloud. This makes it a good fit for the requirements described in the question.
    </details>

2. An image-processing company has a web application that users use to upload images. The application uploads the images into an Amazon S3 bucket. The company has set up S3 event notifications to publish the object creation events to an Amazon Simple Queue Service (Amazon SQS) standard queue. The SQS queue serves as the event source for an AWS Lambda function that processes the images and sends the results to users through email. Users report that they are receiving multiple email messages for every uploaded image. A solutions architect determines that SQS messages are invoking the Lambda function more than once, resulting in multiple email messages. What should the solutions architect do to resolve this issue with the LEAST operational overhead?
    - A. Set up long polling in the SQS queue by increasing the ReceiveMessage wait time to 30 seconds.
    - B. Change the SQS standard queue to an SQS FIFO queue. Use the message deduplication ID to discard duplicate messages.
    - C. Increase the visibility timeout in the SQS queue to a value that is greater than the total of the function timeout and the batch window timeout.
    - D. Modify the Lambda function to delete each message from the SQS queue immediately after the message is read before processing.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: C
      Explanation: Immediately after a message is received, it remains in the queue. To prevent other consumers from processing the message again, Amazon SQS sets a visibility timeout, a period of time during which Amazon SQS prevents other consumers from receiving and processing the message. The default visibility timeout for a message is 30 seconds. The minimum is 0 seconds. The maximum is 12 hours. https://docs.aws.amazon.com/AWSSimpleQueueService/latest/SQSDeveloperGuide/sqs- visibility-timeout.html
    </details>

3. A company is implementing a shared storage solution for a media application that is hosted in the AWS Cloud. The company needs the ability to use SMB clients to access data. The solution must he fully managed.
Which AWS solution meets these requirements?
    - A. Create an AWS Storage Gateway volume gateway. Create a file share that uses the required client protocol. Connect the application server to the tile share.
    - B. Create an AWS Storage Gateway tape gateway. Configure tapes to use Amazon S3. Connect the application server lo the tape gateway
    - C. Create an Amazon EC2 Windows instance. Install and configure a Windows file share role on the instance. Connect the application server to the file share.
    - D. Create an Amazon FSx for Windows File Server tile system. Attach the fie system to the origin server. Connect the application server to the tile system

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: D
      Explanation: Amazon FSx for Lustre is a fully managed file system that is designed for high-performance workloads, such as gaming applications. It provides a high-performance, scalable, and fully managed file system that is optimized for Lustre clients, and it is fully integrated with Amazon EC2. It is the only option that meets the requirements of being fully managed and able to support Lustre clients. https://aws.amazon.com/fsx/lustre/
    </details>

4. A company's containerized application runs on an Amazon EC2 instance. The application needs to download security certificates before it can communicate with other business applications. The company wants a highly secure solution to encrypt and decrypt the certificates in near real time. The solution also needs to store data in highly available storage after the data is encrypted. Which solution will meet these requirements with the LEAST operational overhead?
    - A. Create AWS Secrets Manager secrets for encrypted certificates. Manually update the certificates as needed. Control access to the data by using fine-grained IAM access.
    - B. Create an AWS Lambda function that uses the Python cryptography library to receive and perform encryption operations. Store the function in an Amazon S3 bucket.
    - C. Create an AWS Key Management Service (AWS KMS) customer managed key. Allow the EC2 role to use the KMS key for encryption operations. Store the encrypted data on Amazon S3.
    - D. Create an AWS Key Management Service (AWS KMS) customer managed key. Allow the EC2 role to use the KMS key for encryption operations. Store the encrypted data on Amazon Elastic Block Store (Amazon EBS) volumes.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: C
      Explanation: S3 is highly available with LEAST operational overhead. Amazon S3 provides durability by redundantly storing the data across multiple Availability Zones whereas EBS provides durability by redundantly storing the data in a single Availability Zone. Both S3 and EBS gives the availability of 99.99%, but the only difference that occurs is that S3 is accessed via the internet using API’s and EBS is accessed by the single instance attached to EBS.
    </details>

5. A solutions architect is designing a VPC with public and private subnets. The VPC and subnets use IPv4 CIDR blocks. There is one public subnet and one private subnet in each of three Availability Zones (AZs) for high availability. An internet gateway is used to provide internet access for the public subnets. The private subnets require access to the internet to allow Amazon EC2 instances to download software updates. What should the solutions architect do to enable Internet access for the private subnets?
    - A. Create three NAT gateways, one for each public subnet in each AZ. Create a private route table for each AZ that forwards non-VPC traffic to the NAT gateway in its AZ.
    - B. Create three NAT instances, one for each private subnet in each AZ. Create a private route table for each AZ that forwards non-VPC traffic to the NAT instance in its AZ.
    - C. Create a second internet gateway on one of the private subnets. Update the route table for the private subnets that forward non-VPC traffic to the private internet gateway.
    - D. Create an egress-only internet gateway on one of the public subnets. Update the route table for the private subnets that forward non-VPC traffic to the egress-only internet gateway.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: A
      Explanation: To enable Internet access for the private subnets, the solutions architect should create three NAT gateways, one for each public subnet in each Availability Zone (AZ). NAT gateways allow private instances to initiate outbound traffic to the Internet but do not allow inbound traffic from the Internet to reach the private instances. The solutions architect should then create a private route table for each AZ that forwards non-VPC traffic to the NAT gateway in its AZ. This will allow instances in the private subnets to access the Internet through the NAT gateways in the public subnets.
    </details>

6. A company has an AWS Glue extract. transform, and load (ETL) job that runs every day at the same time. The job processes XML data that is in an Amazon S3 bucket. New data is added to the S3 bucket every day. A solutions architect notices that AWS Glue is processing all the data during each run. What should the solutions architect do to prevent AWS Glue from reprocessing old data?
    - A. Edit the job to use job bookmarks.
    - B. Edit the job to delete data after the data is processed
    - C. Edit the job by setting the NumberOfWorkers field to 1.
    - D. Use a FindMatches machine learning (ML) transform.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: A
      Explanation: AWS Glue tracks data that has already been processed during a previous run of an ETL job by persisting state information from the job run. This persisted state information is called a job bookmark. Job bookmarks help AWS Glue maintain state information and prevent the reprocessing of old data. https://docs.aws.amazon.com/glue/latest/dg/monitor-continuations.html
    </details>

7. A company is preparing to deploy a new serverless workload. A solutions architect must use the principle of least privilege to configure permissions that will be used to run an AWS Lambda function. An Amazon EventBridge (Amazon CloudWatch Events) rule will invoke the function. Which solution meets these requirements?
    - A. Add an execution role to the function with lambda:InvokeFunction as the action and * as the principal.
    - B. Add an execution role to the function with lambda:InvokeFunction as the action and
Service:amazonaws.com as the principal.
    - C. Add a resource-based policy to the function with lambda:'* as the action and Service:events.amazonaws.com as the principal.
    - D. Add a resource-based policy to the function with lambda:InvokeFunction as the action and Service:events.amazonaws.com as the principal.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: D
      Explanation: The principle of least privilege requires that permissions are granted only to the minimum necessary to perform a task. In this case, the Lambda function needs to be able to be invoked by Amazon EventBridge (Amazon CloudWatch Events). To meet these requirements, you can add a resource- based policy to the function that allows the InvokeFunction action to be performed by the Service: events.amazonaws.com principal. This will allow Amazon EventBridge to invoke the function, but will not grant any additional permissions to the function. https://docs.aws.amazon.com/eventbridge/latest/userguide/resource-based-policies- eventbridge.html#lambda-permissions
    </details>

8. A company has an image processing workload running on Amazon Elastic Container Service (Amazon ECS) in two private subnets. Each private subnet uses a NAT instance for internet access. All images are stored in Amazon S3 buckets. The company is concerned about the data transfer costs between Amazon ECS and Amazon S3. What should a solutions architect do to reduce costs?
    - A. Configure a NAT gateway to replace the NAT instances.
    - B. Configure a gateway endpoint for traffic destined to Amazon S3.
    - C. Configure an interface endpoint for traffic destined to Amazon S3.
    - D. Configure Amazon CloudFront for the S3 bucket storing the images.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: B
      Explanation: S3 and Dynamo DB does not support interface endpoints. Both S3 and DynamoDB are routed via Gateway endpoint. https://docs.aws.amazon.com/vpc/latest/userguide/vpc-endpoints.html Interface Endpoint only supports services which are integrated with PrivateLink. https://docs.aws.amazon.com/vpc/latest/userguide/integrated-services-vpce-list.html
    </details>

9. A company is moving Its on-premises Oracle database to Amazon Aurora PostgreSQL. The database has several applications that write to the same tables. The applications need to be migrated one by one with a month in between each migration Management has expressed concerns that the database has a high number of reads and writes. The data must be kept in sync across both databases throughout tie migration. What should a solutions architect recommend?
    - A. Use AWS DataSync tor the initial migration. Use AWS Database Migration Service (AWS DMS) to create a change data capture (CDC) replication task and a table mapping to select all cables.
    - B. UseAVVS DataSync for the initial migration. Use AWS Database Migration Service (AWS DMS) to create a full load plus change data capture (CDC) replication task and a table mapping to select ail tables.
    - C. Use the AWS Schema Conversion led with AWS DataBase Migration Service (AWS DMS) using a memory optimized replication instance. Create a tui load plus change data capture (CDC) replication task and a table mapping lo select all tables.
    - D. Use the AWS Schema Conversion Tool with AWS Database Migration Service (AWS DMS) using a compute optimized implication instance. Create a full load plus change data capture (CDC) replication task and a table mapping to select the largest tables.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: C
      Explanation: As you can see, we have three important memory buffers in this architecture for CDC in AWS DMS. If any of these buffers experience memory pressure, the migration can have performance issues that can potentially cause failures. https://docs.aws.amazon.com/dms/latest/userguide/CHAP_ReplicationInstance.Types.html
    </details>

10. A company is experiencing growth as demand for its product has increased. The company's existing purchasing application is slow when traffic spikes. The application is a monolithic three tier application that uses synchronous transactions and sometimes sees bottlenecks in the application tier. A solutions architect needs to design a solution that can meet required application response times while accounting for traffic volume spikes. Which solution will meet these requirements?
    - A. Vertically scale the application instance using a larger Amazon EC2 instance size.
    - B. Scale the application's persistence layer horizontally by introducing Oracle RAC on AWS
    - C. Scale the web and application tiers horizontally using Auto Scaling groups and an Application Load Balancer
    - D. Decouple the application and data tiers using Amazon Simple Queue Service (Amazon SQS) with asynchronous AWS Lambda calls.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: C
      Explanation: The Application uses synchronous transactions each operation is dependent on the previous one. Using asynchronous lambda calls may not work here.
    </details>

11. A solutions architect needs to ensure that all Amazon Elastic Block Store (Amazon EBS) volumes restored from unencrypted EBS snapshots are encrypted. What should the solutions architect do to accomplish this?
    - A. Enable EBS encryption by default for the AWS Region
    - B. Enable EBS encryption by default for the specific volumes
    - C. Create a new volume and specify the symmetric customer master key (CMK) to use for encryption
    - D. Create a new volume and specify the asymmetric customer master key (CMK) to use for encryption.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: A
      Explanation: Question asked is to ensure that all volumes restored are encrypted. So have to be "Enable encryption by default". https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/EBSEncryption.html#encryption-by- default
    </details>

12. A company is storing backup files by using Amazon S3 Standard storage. The files are accessed frequently for 1 month. However, the files are not accessed after 1 month. The company must keep the files indefinitely. Which storage solution will meet these requirements MOST cost-effectively?
    - A. Configure S3 Intelligent-Tiering to automatically migrate objects.
    - B. Create an S3 Lifecycle configuration to transition objects from S3 Standard to S3 Glacier Deep Archive after 1 month.
    - C. Create an S3 Lifecycle configuration to transition objects from S3 Standard to S3 Standard- Infrequent Access (S3 Standard-IA) after 1 month.
    - D. Create an S3 Lifecycle configuration to transition objects from S3 Standard to S3 One Zone- Infrequent Access (S3 One Zone-IA) after 1 month.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: B
      Explanation: Transition to Glacier deep archive for cost efficiency.
    </details>

13. A company observes an increase in Amazon EC2 costs in its most recent bill. The billing team notices unwanted vertical scaling of instance types for a couple of EC2 instances. A solutions architect needs to create a graph comparing the last 2 months of EC2 costs and perform an in- depth analysis to identify the root cause of the vertical scaling. How should the solutions architect generate the information with the LEAST operational overhead?
    - A. Use AWS Budgets to create a budget report and compare EC2 costs based on instance types
    - B. Use Cost Explorer's granular filtering feature to perform an in-depth analysis of EC2 costs based on instance types
    - C. Use graphs from the AWS Billing and Cost Management dashboard to compare EC2 costs based on instance types for the last 2 months
    - D. Use AWS Cost and Usage Reports to create a report and send it to an Amazon S3 bucket. Use Amazon QuickSight with Amazon S3 as a source to generate an interactive graph based on instance types..

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: B
      Explanation: AWS Cost Explorer is a tool that enables you to view and analyze your costs and usage. You can explore your usage and costs using the main graph, the Cost Explorer cost and usage reports, or the Cost Explorer RI reports. You can view data for up to the last 12 months, forecast how much you're likely to spend for the next 12 months, and get recommendations for what Reserved Instances to purchase. You can use Cost Explorer to identify areas that need further inquiry and see trends that you can use to understand your costs. https://docs.aws.amazon.com/cost-management/latest/userguide/ce-what-is.html
    </details>

14. A company is designing an application. The application uses an AWS Lambda function to receive information through Amazon API Gateway and to store the information in an Amazon Aurora PostgreSQL database. During the proof-of-concept stage, the company has to increase the Lambda quotas significantly to handle the high volumes of data that the company needs to load into the database. A solutions architect must recommend a new design to improve scalability and minimize the configuration effort. Which solution will meet these requirements?
    - A. Refactor the Lambda function code to Apache Tomcat code that runs on Amazon EC2 instances. Connect the database by using native Java Database Connectivity (JDBC) drivers.
    - B. Change the platform from Aurora to Amazon DynamoDB. Provision a DynamoDB Accelerator (DAX) cluster. Use the DAX client SDK to point the existing DynamoDB API calls at the DAX cluster.
    - C. Set up two Lambda functions. Configure one function to receive the information. Configure the other function to load the information into the database. Integrate the Lambda functions by using Amazon Simple Notification Service (Amazon SNS).
    - D. Set up two Lambda functions. Configure one function to receive the information. Configure the other function to load the information into the database. Integrate the Lambda functions by using an Amazon Simple Queue Service (Amazon SQS) queue.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: D
      Explanation: Option D uses SQS, so the 2nd lambda function can go to the queue when responsive to keep with the DB load process. Usually the app decoupling helps with the performance improvement by distributing load.
    </details>

15. A company needs to review its AWS Cloud deployment to ensure that its Amazon S3 buckets do not have unauthorized configuration changes. What should a solutions architect do to accomplish this goal?
    - A. Turn on AWS Config with the appropriate rules.
    - B. Turn on AWS Trusted Advisor with the appropriate checks.
    - C. Turn on Amazon Inspector with the appropriate assessment template.
    - D. Turn on Amazon S3 server access logging. Configure Amazon EventBridge (Amazon Cloud Watch Events).

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: A
      Explanation: AWS Config is a fully managed service that provides you with an AWS resource inventory, configuration history, and configuration change notifications to enable security and governance.
    </details>

16. A company is launching a new application and will display application metrics on an Amazon CloudWatch dashboard. The company's product manager needs to access this dashboard periodically. The product manager does not have an AWS account. A solution architect must provide access to the product manager by following the principle of least privilege. Which solution will meet these requirements?
    - A. Share the dashboard from the CloudWatch console. Enter the product manager's email address, and complete the sharing steps. Provide a shareable link for the dashboard to the product manager.
    - B. Create an IAM user specifically for the product manager. Attach the CloudWatch Read Only Access managed policy to the user. Share the new login credential with the product manager. Share the browser URL of the correct dashboard with the product manager.
    - C. Create an IAM user for the company's employees. Attach the View Only Access AWS managed policy to the IAM user. Share the new login credentials with the product manager. Ask the product manager to navigate to the CloudWatch console and locate the dashboard by name in the Dashboards section.
    - D. Deploy a bastion server in a public subnet. When the product manager requires access to the dashboard, start the server and share the RDP credentials. On the bastion server, ensure that the browser is configured to open the dashboard URL with cached AWS credentials that have appropriate permissions to view the dashboard.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: A
      Explanation: Share a single dashboard and designate specific email addresses of the people who can view the dashboard. Each of these users creates their own password that they must enter to view the dashboard. https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/cloudwatch-dashboard- sharing.html
    </details>

17. A company is migrating applications to AWS. The applications are deployed in different accounts. The company manages the accounts centrally by using AWS Organizations. The company's security team needs a single sign-on (SSO) solution across all the company's accounts. The company must continue managing the users and groups in its on-premises self-managed Microsoft Active Directory. Which solution will meet these requirements?
    - A. Enable AWS Single Sign-On (AWS SSO) from the AWS SSO console. Create a one-way forest trust or a one-way domain trust to connect the company's self-managed Microsoft Active Directory with AWS SSO by using AWS Directory Service for Microsoft Active Directory.
    - B. Enable AWS Single Sign-On (AWS SSO) from the AWS SSO console. Create a two-way forest trust to connect the company's self-managed Microsoft Active Directory with AWS SSO by using AWS Directory Service for Microsoft Active Directory.
    - C. Use AWS Directory Service. Create a two-way trust relationship with the company's self-managed Microsoft Active Directory.
    - D. Deploy an identity provider (IdP) on premises. Enable AWS Single Sign-On (AWS SSO) from the AWS SSO console.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: B
      Explanation: You can configure one and two-way external and forest trust relationships between your AWS Directory Service for Microsoft Active Directory and self-managed (on-premises) directories, as well as between multiple AWS Managed Microsoft AD directories in the AWS cloud. AWS Managed Microsoft AD supports all three trust relationship directions: Incoming, Outgoing and Two-way (Bi- directional). https://aws.amazon.com/blogs/security/everything-you-wanted-to-know-about-trusts-with-aws- managed-microsoft-ad/
    </details>

18. A company provides a Voice over Internet Protocol (VoIP) service that uses UDP connections. The service consists of Amazon EC2 instances that run in an Auto Scaling group. The company has deployments across multiple AWS Regions. The company needs to route users to the Region with the lowest latency. The company also needs automated failover between Regions. Which solution will meet these requirements?
    - A. Deploy a Network Load Balancer (NLB) and an associated target group. Associate the target group with the Auto Scaling group. Use the NLB as an AWS Global Accelerator endpoint in each Region.
    - B. Deploy an Application Load Balancer (ALB) and an associated target group. Associate the target group with the Auto Scaling group. Use the ALB as an AWS Global Accelerator endpoint in each Region.
    - C. Deploy a Network Load Balancer (NLB) and an associated target group. Associate the target group with the Auto Scaling group. Create an Amazon Route 53 latency record that points to aliases for each NLB. Create an Amazon CloudFront distribution that uses the latency record as an origin.
    - D. Deploy an Application Load Balancer (ALB) and an associated target group. Associate the target group with the Auto Scaling group. Create an Amazon Route 53 weighted record that points to aliases for each ALB. Deploy an Amazon CloudFront distribution that uses the weighted record as an origin.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: A
      Explanation: Global Accelerator is a good fit for non-HTTP use cases, such as gaming (UDP), IoT (MQTT), or Voice over IP, as well as for HTTP use cases that specifically require static IP addresses or deterministic, fast regional failover. https://aws.amazon.com/global-accelerator/faqs/
    </details>

19. A development team runs monthly resource-intensive tests on its general purpose Amazon RDS for MySQL DB instance with Performance Insights enabled. The testing lasts for 48 hours once a month and is the only process that uses the database. The team wants to reduce the cost of running the tests without reducing the compute and memory attributes of the DB instance. Which solution meets these requirements MOST cost-effectively?
    - A. Stop the DB instance when tests are completed. Restart the DB instance when required.
    - B. Use an Auto Scaling policy with the DB instance to automatically scale when tests are completed.
    - C. Create a snapshot when tests are completed. Terminate the DB instance and restore the snapshot when required.
    - D. Modify the DB instance to a low-capacity instance when tests are completed. Modify the DB instance again when required.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: C
      Explanation: It's a DB instance, not an EC2 instance. If the DB instance is stopped, you are still paying for the storage.
    </details>

20. A company that hosts its web application on AWS wants to ensure all Amazon EC2 instances. Amazon RDS DB instances and Amazon Redshift clusters are configured with tags. The company wants to minimize the effort of configuring and operating this check. What should a solutions architect do to accomplish this?
    - A. Use AWS Config rules to define and detect resources that are not properly tagged.
    - B. Use Cost Explorer to display resources that are not properly tagged. Tag those resources manually.
    - C. Write API calls to check all resources for proper tag allocation. Periodically run the code on an EC2 instance.
    - D. Write API calls to check all resources for proper tag allocation. Schedule an AWS Lambda function through Amazon CloudWatch to periodically run the code.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: A
      Explanation: https://docs.aws.amazon.com/config/latest/developerguide/tagging.html
    </details>

21. A development team needs to host a website that will be accessed by other teams. The website contents consist of HTML, CSS, client-side JavaScript, and images. Which method is the MOST cost-effective for hosting the website?
    - A. Containerize the website and host it in AWS Fargate.
    - B. Create an Amazon S3 bucket and host the website there
    - C. Deploy a web server on an Amazon EC2 instance to host the website.
    - D. Configure an Application Loa d Balancer with an AWS Lambda target that uses the Express js framework.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: B
      Explanation: In Static Websites, Web pages are returned by the server which are prebuilt. They use simple languages such as HTML, CSS, or JavaScript. There is no processing of content on the server (according to the user) in Static Websites. Web pages are returned by the server with no change therefore, static Websites are fast. There is no interaction with databases. Also, they are less costly as the host does not need to support server-side processing with different languages. ============ In Dynamic Websites, Web pages are returned by the server which are processed during runtime means they are not prebuilt web pages but they are built during runtime according to the user's demand. These use server-side scripting languages such as PHP, Node.js, ASP.NET and many more supported by the server. So, they are slower than static websites but updates and interaction with databases are possible.
    </details>

22. A company runs an online marketplace web application on AWS. The application serves hundreds of thousands of users during peak hours. The company needs a scalable, near-real-time solution to share the details of millions of financial transactions with several other internal applications Transactions also need to be processed to remove sensitive data before being stored in a document database for low-latency retrieval. What should a solutions architect recommend to meet these requirements?
    - A. Store the transactions data into Amazon DynamoDB. Set up a rule in DynamoDB to remove sensitive data from every transaction upon write. Use DynamoDB Streams to share the transactions data with other applications
    - B. Stream the transactions data into Amazon Kinesis Data. Firehose to store data in Amazon DynamoDB and Amazon S3. Use AWS Lambda integration with Kinesis Data Firehose to remove sensitive data. Other applications can consume the data stored in Amazon S3.
    - C. Stream the transactions data into Amazon Kinesis Data Streams. Use AWS Lambda integration to remove sensitive data from every transaction and then store the transactions data in Amazon DynamoDB. Other applications can consume the transactions data off the Kinesis data stream.
    - D. Store the batched transactions data in Amazon S3 as files. Use AWS Lambda to process every file and remove sensitive data before updating the files in Amazon S3. The Lambda function then stores the data in Amazon DynamoDB. Other applications can consume transaction files stored in Amazon S3.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: C
      Explanation: The destination of your Kinesis Data Firehose delivery stream. Kinesis Data Firehose can send data records to various destinations, including Amazon Simple Storage Service (Amazon S3), Amazon Redshift, Amazon OpenSearch Service, and any HTTP endpoint that is owned by you or any of your third-party service providers. The following are the supported destinations: * Amazon OpenSearch Service * Amazon S3 * Datadog * Dynatrace
      * Honeycomb * HTTP Endpoint * Logic Monitor * MongoDB Cloud * New Relic * Splunk * Sumo Logic https://docs.aws.amazon.com/firehose/latest/dev/create-name.html https://aws.amazon.com/kinesis/data-streams/ Amazon Kinesis Data Streams (KDS) is a massively scalable and durable real-time data streaming service. KDS can continuously capture gigabytes of data per second from hundreds of thousands of sources such as website clickstreams, database event streams, financial transactions, social media feeds, IT logs, and location-tracking events.
    </details>

23. A company hosts its multi-tier applications on AWS. For compliance, governance, auditing, and security, the company must track configuration changes on its AWS resources and record a history of API calls made to these resources. What should a solutions architect do to meet these requirements?
    - A. Use AWS CloudTrail to track configuration changes and AWS Config to record API calls
    - B. Use AWS Config to track configuration changes and AWS CloudTrail to record API calls
    - C. Use AWS Config to track configuration changes and Amazon CloudWatch to record API calls
    - D. Use AWS CloudTrail to track configuration changes and Amazon CloudWatch to record API calls

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: B
      Explanation: CloudTrail - Track user activity and API call history. Config - Assess, audits, and evaluates the configuration and relationships of tag resources.
    </details>

24. A company is preparing to launch a public-facing web application in the AWS Cloud. The architecture consists of Amazon EC2 instances within a VPC behind an Elastic Load Balancer (ELB). A third-party service is used for the DNS. The company's solutions architect must recommend a solution to detect and protect against large-scale DDoS attacks. Which solution meets these requirements?
    - A. Enable Amazon GuardDuty on the account.
    - B. Enable Amazon Inspector on the EC2 instances.
    - C. Enable AWS Shield and assign Amazon Route 53 to it.
    - D. Enable AWS Shield Advanced and assign the ELB to it.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: D
      Explanation: AWS Shield Advanced provides expanded DDoS attack protection for your Amazon EC2 instances, Elastic Load Balancing load balancers, CloudFront distributions, Route 53 hosted zones, and AWS Global Accelerator standard accelerators. https://aws.amazon.com/shield/faqs/ https://docs.aws.amazon.com/whitepapers/latest/aws-best-practices-ddos-resiliency/elastic-load- balancing-bp6.html
    </details>

25. A company is building an application in the AWS Cloud. The application will store data in Amazon S3 buckets in two AWS Regions. The company must use an AWS Key Management Service (AWS KMS) customer managed key to encrypt all data that is stored in the S3 buckets. The data in both S3 buckets must be encrypted and decrypted with the same KMS key. The data and the key must be stored in each of the two Regions. Which solution will meet these requirements with the LEAST operational overhead?
    - A. Create an S3 bucket in each Region. Configure the S3 buckets to use server-side encryption with Amazon S3 managed encryption keys (SSE-S3). Configure replication between the S3 buckets.
    - B. Create a customer managed multi-Region KMS key. Create an S3 bucket in each Region. Configure replication between the S3 buckets. Configure the application to use the KMS key with client-side encryption.
    - C. Create a customer managed KMS key and an S3 bucket in each Region. Configure the S3 buckets to use server-side encryption with Amazon S3 managed encryption keys (SSE-S3). Configure replication between the S3 buckets.
    - D. Create a customer managed KMS key and an S3 bucket in each Region. Configure the S3 buckets to use server-side encryption with AWS KMS keys (SSE-KMS). Configure replication between the S3 buckets.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: B
      Explanation: KMS Multi-region keys are required. https://docs.aws.amazon.com/kms/latest/developerguide/multi-region-keys-overview.html
    </details>

26. A company is using a fleet of Amazon EC2 instances to ingest data from on-premises data sources. The data is in JSON format and ingestion rates can be as high as 1 MB/s. When an EC2 instance is rebooted, the data in-flight is lost. The company's data science team wants to query ingested data near-real time. Which solution provides near-real-time data querying that is scalable with minimal data loss?
    - A. Publish data to Amazon Kinesis Data Streams. Use Kinesis Data Analytics to query the data.
    - B. Publish data to Amazon Kinesis Data Firehose with Amazon Redshift as the destination. Use Amazon Redshift to query the data.
    - C. Store ingested data in an EC2 instance store. Publish data to Amazon Kinesis Data Firehose with Amazon S3 as the destination. Use Amazon Athena to query the data.
    - D. Store ingested data in an Amazon Elastic Block Store (Amazon EBS) volume. Publish data to Amazon ElastiCache for Redis. Subscribe to the Redis channel to query the data.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: B
      Explanation: Kinesis data streams consists of shards. The more througput is needed, the more shards you add, the less throughput, the more shards you remove, so it's scalable. Each shard can handle up to
      1MB/s of writes. However Kinesis data streams stores ingested data for only 1 to 7 days so there is a chance of data loss. Additionally, Kinesis data analytics and kinesis data streams are both for real-time ingestion and analytics. Firehouse on the other hand is also scalable and processes data in near real time as per the requirement. It also transfers data into Redshift which is a data warehouse so data won't be lost. Redshift also has a SQL interface for performing queries for data analytics.
    </details>

27. A company is developing a mobile game that streams score updates to a backend processor and then posts results on a leaderboard. A solutions architect needs to design a solution that can handle large traffic spikes, process the mobile game updates in order of receipt, and store the processed updates in a highly available database. The company also wants to minimize the management overhead required to maintain the solution. What should the solutions architect do to meet these requirements?
    - A. Push score updates to Amazon Kinesis Data Streams. Process the updates in Kinesis Data Streams with AWS Lambda. Store the processed updates in Amazon DynamoDB. - B. Push score updates to Amazon Kinesis Data Streams. Process the updates with a fleet of Amazon EC2 instances set up for Auto Scaling. Store the processed updates in Amazon Redshift.
    - C. Push score updates to an Amazon Simple Notification Service (Amazon SNS) topic. Subscribe an AWS Lambda function to the SNS topic to process the updates. Store the processed updates in a SQL database running on Amazon EC2.
    - D. Push score updates to an Amazon Simple Queue Service (Amazon SQS) queue. Use a fleet of Amazon EC2 instances with Auto Scaling to process the updates in the SOS queue. Store the processed updates in an Amazon RDS Multi-AZ DB instance.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: A
      Explanation: Keywords to focus on would be highly available database - DynamoDB would be a better choice for leaderboard.
    </details>

28. An ecommerce website is deploying its web application as Amazon Elastic Container Service (Amazon ECS) container instance behind an Application Load Balancer (ALB). During periods of high activity, the website slows down and availability is reduced. A solutions architect uses Amazon CloudWatch alarms to receive notifications whenever there is an availability issues so they can scale out resource Company management wants a solution that automatically responds to such events. Which solution meets these requirements?
    - A. Set up AWS Auto Scaling to scale out the ECS service when there are timeouts on the ALB. Set up AWS Auto Scaling to scale out the ECS cluster when the CPU or memory reservation is too high.
    - B. Set up AWS Auto Scaling to scale out the ECS service when the ALB CPU utilization is too high. Set up AWS Auto Scaling to scale out the ECS cluster when the CPU or memory reservation is too high.
    - C. Set up AWS Auto Scaling to scale out the ECS service when the service's CPU utilization is too
high. Set up AWS Auto Scaling to scale out the ECS cluster when the CPU or memory reservation is too high.
    - D. Set up AWS Auto Scaling to scale out the ECS service when the ALB target group CPU utilization is too high. Set up AWS Auto Scaling to scale out the ECS cluster when the CPU or memory reservation is too high.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: C
      Explanation: Match deployed capacity to the incoming application load, using scaling policies for both the ECS service and the Auto Scaling group in which the ECS cluster runs. Scaling up cluster instances and service tasks when needed and safely scaling them down when demand subsides, keeps you out of the capacity guessing game. This provides you high availability with lowered costs in the long run. https://aws.amazon.com/blogs/compute/automatic-scaling-with-amazon-ecs/
    </details>

29. A company has no existing file share services. A new project requires access to file storage that is mountable as a drive for on-premises desktops. The file server must authenticate users to an Active Directory domain before they are able to access the storage. Which service will allow Active Directory users to mount storage as a drive on their desktops?
    - A. AWS S3 Glacier
    - B. AWS DataSync
    - C. AWS Snowball Edge
    - D. AWS Storage Gateway

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: D
      Explanation: Before you create an SMB file share, make sure that you configure SMB security settings for your file gateway. You also configure either Microsoft Active Directory (AD) or guest access for authentication. https://docs.aws.amazon.com/storagegateway/latest/userguide/CreatingAnSMBFileShare.html
    </details>

30. Management has decided to deploy all AWS VPCs with IPv6 enabled. After sometime, a solutions architect tries to launch a new instance and receives an error stating that there is no enough IP address space available in the subnet. What should the solutions architect do to fix this?
    - A. Check to make sure that only IPv6 was used during the VPC creation
    - B. Create a new IPv4 subnet with a larger range, and then launch the instance
    - C. Create a new IPv6-only subnet with a larger range, and then launch the instance
    - D. Disable the IPv4 subnet and migrate all instances to IPv6 only. Once that is complete, launch the instance.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: B
      Explanation: https://cloudonaut.io/getting-started-with-ipv6-on-aws/ First of all, there is no IPv6-only VPC on AWS. A VPC is always IPv4 enabled, but you can
      optionally enable IPv6 (dual-stack).
    </details>

31. A company operates an ecommerce website on Amazon EC2 instances behind an Application Load Balancer (ALB) in an Auto Scaling group. The site is experiencing performance issues related to a high request rate from illegitimate external systems with changing IP addresses. The security team is worried about potential DDoS attacks against the website. The company must block the illegitimate incoming requests in a way that has a minimal impact on legitimate users. What should a solutions architect recommend?
    - A. Deploy Amazon Inspector and associate it with the ALB. - B. Deploy AWS WAF, associate it with the ALB, and configure a rate-limiting rule.
    - C. Deploy rules to the network ACLs associated with the ALB to block the incoming traffic.
    - D. Deploy Amazon GuardDuty and enable rate-limiting protection when configuring GuardDuty.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: B
      Explanation: Rate limit For a rate-based rule, enter the maximum number of requests to allow in any five-minute period from an IP address that matches the rule's conditions. The rate limit must be at least 100. You can specify a rate limit alone, or a rate limit and conditions. If you specify only a rate limit, AWS WAF places the limit on all IP addresses. If you specify a rate limit and conditions, AWS WAF places the limit on IP addresses that match the conditions. When an IP address reaches the rate limit threshold, AWS WAF applies the assigned action (block or count) as quickly as possible, usually within 30 seconds. Once the action is in place, if five minutes pass with no requests from the IP address, AWS WAF resets the counter to zero.
    </details>

32. A media company is evaluating the possibility of moving its systems to the AWS Cloud. The company needs at least 10 TB of storage with the maximum possible I/O performance for video processing, 300 TB of very durable storage for storing media content, and 900 TB of storage to meet requirements for archival media that is not in use anymore. Which set of services should a solutions architect recommend to meet these requirements?
    - A. Amazon EBS for maximum performance. Amazon S3 for durable data storage, and Amazon S3 Glacier for archival storage.
    - B. Amazon EBS for maximum performance. Amazon EFS for durable data storage and Amazon S3 Glacier for archival storage.
    - C. Amazon EC2 instance store for maximum performance. Amazon EFS for durable data storage and Amazon S3 for archival storage.
    - D. Amazon EC2 Instance store for maximum performance. Amazon S3 for durable data storage, and Amazon S3 Glacier for archival storage.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: D
      Explanation: Max instance store possible at this time is 30TB for NVMe which has the higher I/O compared to EBS. is4gen.8xlarge 4 x 7,500 GB (30 TB) NVMe SSD https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/InstanceStorage.html#instance-store- volumes
    </details>

33. A company wants to run applications in containers in the AWS Cloud. These applications are stateless and can tolerate disruptions within the underlying infrastructure. The company needs a solution that minimizes cost and operational overhead. What should a solutions architect do to meet these requirements?
    - A. Use Spot Instances in an Amazon EC2 Auto Scaling group to run the application containers.
    - B. Use Spot Instances in an Amazon Elastic Kubernetes Service (Amazon EKS) managed node group.
    - C. Use On-Demand Instances in an Amazon EC2 Auto Scaling group to run the application containers.
    - D. Use On-Demand Instances in an Amazon Elastic Kubernetes Service (Amazon EKS) managed node group.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: B
      Explanation: Running your Kubernetes and containerized workloads on Amazon EC2 Spot Instances is a great way to save costs. ... AWS makes it easy to run Kubernetes with Amazon Elastic Kubernetes Service (EKS) a managed Kubernetes service to run production-grade workloads on AWS. To cost optimize these workloads, run them on Spot Instances. https://aws.amazon.com/blogs/compute/cost-optimization-and-resilience-eks-with-spot-instances/
    </details>

34. An application runs on Amazon EC2 instances across multiple Availability Zones. The instances run in an Amazon EC2 Auto Scaling group behind an Application Load Balancer. The application performs best when the CPU utilization of the EC2 instances is at or near 40%. What should a solutions architect do to maintain the desired performance across all instances in the group?
    - A. Use a simple scaling policy to dynamically scale the Auto Scaling group
    - B. Use a target tracking policy to dynamically scale the Auto Scaling group
    - C. Use an AWS Lambda function to update the desired Auto Scaling group capacity.
    - D. Use scheduled scaling actions to scale up and scale down the Auto Scaling group

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: B
      Explanation: With a target tracking scaling policy, you can increase or decrease the current capacity of the group based on a target value for a specific metric. This policy will help resolve the over-provisioning of your resources. The scaling policy adds or removes capacity as required to keep the metric at, or close to, the specified target value. In addition to keeping the metric close to the target value, a target tracking scaling policy also adjusts to changes in the metric due to a changing load pattern. https://docs.aws.amazon.com/autoscaling/application/userguide/application-auto-scaling-target- tracking.html
    </details>

35. A company is developing a file-sharing application that will use an Amazon S3 bucket for storage. The company wants to serve all the files through an Amazon CloudFront distribution. The company does not want the files to be accessible through direct navigation to the S3 URL. What should a solutions architect do to meet these requirements?
    - A. Write individual policies for each S3 bucket to grant read permission for only CloudFront access.
    - B. Create an IAM user. Grant the user read permission to objects in the S3 bucket. Assign the user to CloudFront.
    - C. Write an S3 bucket policy that assigns the CloudFront distribution ID as the Principal and assigns the target S3 bucket as the Amazon Resource Name (ARN).
    - D. Create an origin access identity (OAI). Assign the OAI to the CloudFront distribution. Configure the S3 bucket permissions so that only the OAI has read permission.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: D
      Explanation: Create a CloudFront origin access identity (OAI) https://aws.amazon.com/premiumsupport/knowledge-center/cloudfront-access-to-amazon-s3/
    </details>

36. A company's website provides users with downloadable historical performance reports. The website needs a solution that will scale to meet the company's website demands globally. The solution should be cost-effective, limit the provisioning of infrastructure resources, and provide the fastest possible response time. Which combination should a solutions architect recommend to meet these requirements?
    - A. Amazon CloudFront and Amazon S3
    - B. AWS Lambda and Amazon DynamoDB
    - C. Application Load Balancer with Amazon EC2 Auto Scaling
    - D. Amazon Route 53 with internal Application Load Balancers

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: A
      Explanation: The solution should be cost-effective, limit the provisioning of infrastructure resources, and provide the fastest possible response time.
    </details>

37. A company runs an Oracle database on premises. As part of the company's migration to AWS, the company wants to upgrade the database to the most recent available version. The company also wants to set up disaster recovery (DR) for the database. The company needs to minimize the operational overhead for normal operations and DR setup. The company also needs to maintain access to the database's underlying operating system. Which solution will meet these requirements?
    - A. Migrate the Oracle database to an Amazon EC2 instance. Set up database replication to a different AWS Region.
    - B. Migrate the Oracle database to Amazon RDS for Oracle. Activate Cross-Region automated backups to replicate the snapshots to another AWS Region.
    - C. Migrate the Oracle database to Amazon RDS Custom for Oracle. Create a read replica for the database in another AWS Region.
    - D. Migrate the Oracle database to Amazon RDS for Oracle. Create a standby database in another Availability Zone.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: C
      Explanation: https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/rds-custom.html https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/working-with-custom-oracle.html
    </details>

38. A company wants to move its application to a serverless solution. The serverless solution needs to analyze existing and new data by using SQL. The company stores the data in an Amazon S3 bucket. The data requires encryption and must be replicated to a different AWS Region. Which solution will meet these requirements with the LEAST operational overhead?
    - A. Create a new S3 bucket. Load the data into the new S3 bucket. Use S3 Cross-Region Replication (CRR) to replicate encrypted objects to an S3 bucket in another Region. Use server-side encryption with AWS KMS multi-Region kays (SSE-KMS). Use Amazon Athena to query the data.
    - B. Create a new S3 bucket. Load the data into the new S3 bucket. Use S3 Cross-Region Replication (CRR) to replicate encrypted objects to an S3 bucket in another Region. Use server-side encryption with AWS KMS multi-Region keys (SSE-KMS). Use Amazon RDS to query the data.
    - C. Load the data into the existing S3 bucket. Use S3 Cross-Region Replication (CRR) to replicate encrypted objects to an S3 bucket in another Region. Use server-side encryption with Amazon S3 managed encryption keys (SSE-S3). Use Amazon Athena to query the data.
    - D. Load the data into the existing S3 bucket. Use S3 Cross-Region Replication (CRR) to replicate encrypted objects to an S3 bucket in another Region. Use server-side encryption with Amazon S3 managed encryption keys (SSE-S3). Use Amazon RDS to query the data.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: A
      Explanation: Amazon S3 Bucket Keys reduce the cost of Amazon S3 server-side encryption using AWS Key Management Service (SSE-KMS). This new bucket-level key for SSE can reduce AWS KMS request costs by up to 99 percent by decreasing the request traffic from Amazon S3 to AWS KMS. With a few clicks in the AWS Management Console, and without any changes to your client applications, you can configure your bucket to use an S3 Bucket Key for AWS KMS-based encryption on new objects. The Existing S3 bucket might have uncrypted data - encryption will apply new data received after the applying of encryption on the new bucket.
    </details>

39. A company runs workloads on AWS. The company needs to connect to a service from an external provider. The service is hosted in the provider's VPC. According to the company's security team, the connectivity must be private and must be restricted to the target service. The connection must be initiated only from the company's VPC. Which solution will mast these requirements?
    - A. Create a VPC peering connection between the company's VPC and the provider's VPC. Update the route table to connect to the target service.
    - B. Ask the provider to create a virtual private gateway in its VPC. Use AWS PrivateLink to connect to the target service.
    - C. Create a NAT gateway in a public subnet of the company's VPC. Update the route table to connect to the target service.
    - D. Ask the provider to create a VPC endpoint for the target service. Use AWS PrivateLink to connect to the target service.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: D
      Explanation: AWS PrivateLink provides private connectivity between VPCs, AWS services, and your on- premises networks, without exposing your traffic to the public internet. AWS PrivateLink makes it easy to connect services across different accounts and VPCs to significantly simplify your network architecture. Interface **VPC endpoints**, powered by AWS PrivateLink, connect you to services hosted by AWS Partners and supported solutions available in AWS Marketplace. https://aws.amazon.com/privatelink/
    </details>

40. A company uses AWS Organizations to create dedicated AWS accounts for each business unit to manage each business unit's account independently upon request. The root email recipient missed a notification that was sent to the root user email address of one account. The company wants to ensure that all future notifications are not missed. Future notifications must be limited to account administrators. Which solution will meet these requirements?
    - A. Configure the company's email server to forward notification email messages that are sent to the AWS account root user email address to all users in the organization.
    - B. Configure all AWS account root user email addresses as distribution lists that go to a few administrators who can respond to alerts. Configure AWS account alternate contacts in the AWS Organizations console or programmatically.
    - C. Configure all AWS account root user email messages to be sent to one administrator who is responsible for monitoring alerts and forwarding those alerts to the appropriate groups.
    - D. Configure all existing AWS accounts and all newly created accounts to use the same root user email address. Configure AWS account alternate contacts in the AWS Organizations console or programmatically.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: B
      Explanation: Use a group email address for the management account's root user https://docs.aws.amazon.com/organizations/latest/userguide/orgs_best-practices_mgmt- acct.html#best-practices_mgmt-acct_email-address
    </details>

41. A company recently launched a variety of new workloads on Amazon EC2 instances in its AWS account. The company needs to create a strategy to access and administer the instances remotely and securely. The company needs to implement a repeatable process that works with native AWS services and follows the AWS Well-Architected Framework. Which solution will meet these requirements with the LEAST operational overhead?
    - A. Use the EC2 serial console to directly access the terminal interface of each instance for administration.
    - B. Attach the appropriate IAM role to each existing instance and new instance. Use AWS Systems Manager Session Manager to establish a remote SSH session.
    - C. Create an administrative SSH key pair. Load the public key into each EC2 instance. Deploy a bastion host in a public subnet to provide a tunnel for administration of each instance.
    - D. Establish an AWS Site-to-Site VPN connection. Instruct administrators to use their local on-premises machines to connect directly to the instances by using SSH keys across the VPN tunnel.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: B
      Explanation: https://docs.aws.amazon.com/systems-manager/latest/userguide/setup-launch-managed- instance.html
    </details>

42. A company maintains a searchable repository of items on its website. The data is stored in an Amazon RDS for MySQL database table that contains more than 10 million rows. The database has 2 TB of General Purpose SSD storage. There are millions of updates against this data every day through the company's website. The company has noticed that some insert operations are taking 10 seconds or longer. The company has determined that the database storage performance is the problem. Which solution addresses this performance issue?
    - A. Change the storage type to Provisioned IOPS SSD
    - B. Change the DB instance to a memory optimized instance class
    - C. Change the DB instance to a burstable performance instance class
    - D. Enable Multi-AZ RDS read replicas with MySQL native asynchronous replication.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: A
      Explanation: Provisioned IOPS volumes are backed by solid-state drives (SSDs) and are the highest performance EBS volumes designed for your critical, I/O intensive database applications. These volumes are ideal for both IOPS-intensive and throughput-intensive workloads that require extremely low latency. https://aws.amazon.com/ebs/features/
    </details>

43. A company has thousands of edge devices that collectively generate 1 TB of status alerts each
day. Each alert is approximately 2 KB in size. A solutions architect needs to implement a solution to ingest and store the alerts for future analysis. The company wants a highly available solution. However, the company needs to minimize costs and does not want to manage additional infrastructure. Additionally, the company wants to keep 14 days of data available for immediate analysis and archive any data older than 14 days. What is the MOST operationally efficient solution that meets these requirements?
    - A. Create an Amazon Kinesis Data Firehose delivery stream to ingest the alerts. Configure the Kinesis Data Firehose stream to deliver the alerts to an Amazon S3 bucket. Set up an S3 Lifecycle configuration to transition data to Amazon S3 Glacier after 14 days.
    - B. Launch Amazon EC2 instances across two Availability Zones and place them behind an Elastic Load Balancer to ingest the alerts. Create a script on the EC2 instances that will store tne alerts in an Amazon S3 bucket. Set up an S3 Lifecycle configuration to transition data to Amazon S3 Glacier after 14 days.
    - C. Create an Amazon Kinesis Data Firehose delivery stream to ingest the alerts. Configure the Kinesis Data Firehose stream to deliver the alerts to an Amazon Elasticsearch Service (Amazon ES) duster. Set up the Amazon ES cluster to take manual snapshots every day and delete data from the duster that is older than 14 days
    - D. Create an Amazon Simple Queue Service (Amazon SQS) standard queue to ingest the alerts and set the message retention period to 14 days. Configure consumers to poll the SQS queue check the age of the message and analyze the message data as needed If the message is 14 days old the consumer should copy the message to an Amazon S3 bucket and delete the message from the SQS queue.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: A
      Explanation: Definitely A, it's the most operationally efficient compared to D, which requires a lot of code and infrastructure to maintain. A is mostly managed (firehose is fully managed and S3 lifecycles are also managed).
    </details>

44. A company's application integrates with multiple software-as-a-service (SaaS) sources for data collection. The company runs Amazon EC2 instances to receive the data and to upload the data to an Amazon S3 bucket for analysis. The same EC2 instance that receives and uploads the data also sends a notification to the user when an upload is complete. The company has noticed slow application performance and wants to improve the performance as much as possible. Which solution will meet these requirements with the LEAST operational overhead?
    - A. Create an Auto Scaling group so that EC2 instances can scale out. Configure an S3 event notification to send events to an Amazon Simple Notification Service (Amazon SNS) topic when the upload to the S3 bucket is complete.
    - B. Create an Amazon AppFlow flow to transfer data between each SaaS source and the S3 bucket. Configure an S3 event notification to send events to an Amazon Simple Notification Service (Amazon SNS) topic when the upload to the S3 bucket is complete.
    - C. Create an Amazon EventBridge (Amazon CloudWatch Events) rule for each SaaS source to send output data. Configure the S3 bucket as the rule's target. Create a second EventBridge (CloudWatch Events) rule to send events when the upload to the S3 bucket is complete. Configure an Amazon Simple Notification Service (Amazon SNS) topic as the second rule's target.
    - D. Create a Docker container to use instead of an EC2 instance. Host the containerized application on Amazon Elastic Container Service (Amazon ECS). Configure Amazon CloudWatch Container Insights to send events to an Amazon Simple Notification Service (Amazon SNS) topic when the upload to the S3 bucket is complete.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: B
      Explanation: Amazon AppFlow is a fully managed integration service that enables you to securely transfer data between Software-as-a-Service (SaaS) applications like Salesforce, SAP, Zendesk, Slack, and ServiceNow, and AWS services like Amazon S3 and Amazon Redshift, in just a few clicks. https://aws.amazon.com/appflow/
    </details>

45. A company runs a highly available image-processing application on Amazon EC2 instances in a single VPC. The EC2 instances run inside several subnets across multiple Availability Zones. The EC2 instances do not communicate with each other. However, the EC2 instances download images from Amazon S3 and upload images to Amazon S3 through a single NAT gateway. The company is concerned about data transfer charges. What is the MOST cost-effective way for the company to avoid Regional data transfer charges?
    - A. Launch the NAT gateway in each Availability Zone
    - B. Replace the NAT gateway with a NAT instance
    - C. Deploy a gateway VPC endpoint for Amazon S3
    - D. Provision an EC2 Dedicated Host to run the EC2 instances

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: C
      Explanation: VPC gateway endpoints allow communication to Amazon S3 and Amazon DynamoDB without incurring data transfer charges within the same Region. On the other hand NAT gateway incurs additional data processing charges. https://aws.amazon.com/blogs/architecture/overview-of-data-transfer-costs-for-common- architectures/
    </details>

46. A company has an on-premises application that generates a large amount of time-sensitive data that is backed up to Amazon S3. The application has grown and there are user complaints about internet bandwidth limitations. A solutions architect needs to design a long-term solution that allows for both timely backups to Amazon S3 and with minimal impact on internet connectivity for internal users. Which solution meets these requirements?
    - A. Establish AWS VPN connections and proxy all traffic through a VPC gateway endpoint
    - B. Establish a new AWS Direct Connect connection and direct backup traffic through this new connection.
    - C. Order daily AWS Snowball devices Load the data onto the Snowball devices and return the devices to AWS each day.
    - D. Submit a support ticket through the AWS Management Console. Request the removal of S3 service limits from the account.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: B
      Explanation: Direct connect is a dedicated connection between on-prem and AWS, this is the way to ensure stable network connectivity that will not wax and wane like internet connectivity.
    </details>

47. A company's web application is running on Amazon EC2 instances behind an Application Load
Balancer. The company recently changed its policy, which now requires the application to be accessed from one specific country only. Which configuration will meet this requirement?
    - A. Configure the security group for the EC2 instances.
    - B. Configure the security group on the Application Load Balancer.
    - C. Configure AWS WAF on the Application Load Balancer in a VPC. - D. Configure the network ACL for the subnet that contains the EC2 instances.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: C
      Explanation: Geographic (Geo) Match Conditions in AWS WAF. This new condition type allows you to use AWS WAF to restrict application access based on the geographic location of your viewers. With geo match conditions you can choose the countries from which AWS WAF should allow access. https://aws.amazon.com/about-aws/whats-new/2017/10/aws-waf-now-supports-geographic- match/
    </details>

48. A company has a multi-tier application that runs six front-end web servers in an Amazon EC2 Auto Scaling group in a single Availability Zone behind an Application Load Balancer (ALB). A solutions architect needs to modify the infrastructure to be highly available without modifying the application. Which architecture should the solutions architect choose that provides high availability?
    - A. Create an Auto Scaling group that uses three instances across each of two Regions.
    - B. Modify the Auto Scaling group to use three instances across each of two Availability Zones.
    - C. Create an Auto Scaling template that can be used to quickly create more instances in another Region.
    - D. Change the ALB in front of the Amazon EC2 instances in a round-robin configuration to balance traffic to the web tier.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: B
      Explanation: High availability can be enabled for this architecture quite simply by modifying the existing Auto Scaling group to use multiple availability zones. The ASG will automatically balance the load so you don't actually need to specify the instances per AZ.
    </details>

49. Organizers for a global event want to put daily reports online as static HTML pages. The pages are expected to generate millions of views from users around the world. The files are stored In an Amazon S3 bucket. A solutions architect has been asked to design an efficient and effective solution. Which action should the solutions architect take to accomplish this?
    - A. Generate presigned URLs for the files.
    - B. Use cross-Region replication to all Regions.
    - C. Use the geoproximity feature of Amazon Route 53.
    - D. Use Amazon CloudFront with the S3 bucket as its origin.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: D
      Explanation: CloudFront is a content delivery network (CDN) offered by Amazon Web Services (AWS). It functions as a reverse proxy service that caches web content across AWS's global data centers,
      improving loading speeds and reducing the strain on origin servers. CloudFront can be used to efficiently deliver large amounts of static or dynamic content anywhere in the world.
    </details>

50. A company runs an application using Amazon ECS. The application creates resized versions of an original image and then makes Amazon S3 API calls to store the resized images in Amazon S3. How can a solutions architect ensure that the application has permission to access Amazon S3?
    - A. Update the S3 role in AWS IAM to allow read/write access from Amazon ECS, and then relaunch the container.
    - B. Create an IAM role with S3 permissions, and then specify that role as the taskRoleArn in the task definition.
    - C. Create a security group that allows access from Amazon ECS to Amazon S3, and update the launch configuration used by the ECS cluster.
    - D. Create an IAM user with S3 permissions, and then relaunch the Amazon EC2 instances for the ECS cluster while logged in as this account.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: B
      Explanation: The short name or full Amazon Resource Name (ARN) of the AWS Identity and Access Management (IAM) role that grants containers in the task permission to call AWS APIs on your behalf.
    </details>

51. A solutions architect needs to securely store a database user name and password that an application uses to access an Amazon RDS DB instance. The application that accesses the database runs on an Amazon EC2 instance. The solutions architect wants to create a secure parameter in AWS Systems Manager Parameter Store. What should the solutions architect do to meet this requirement?
    - A. Create an IAM role that has read access to the Parameter Store parameter. Allow Decrypt access to an AWS Key Management Service (AWS KMS) key that is used to encrypt the parameter. Assign this IAM role to the EC2 instance.
    - B. Create an IAM policy that allows read access to the Parameter Store parameter. Allow Decrypt access to an AWS Key Management Service (AWS KMS) key that is used to encrypt the parameter. Assign this IAM policy to the EC2 instance.
    - C. Create an IAM trust relationship between the Parameter Store parameter and the EC2 instance. Specify Amazon RDS as a principal in the trust policy.
    - D. Create an IAM trust relationship between the DB instance and the EC2 instance. Specify Systems Manager as a principal in the trust policy.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: A
      Explanation: There should be the Decrypt access to KMS. "If you choose the SecureString parameter type when you create your parameter, Systems Manager uses AWS KMS to encrypt the parameter value." https://docs.aws.amazon.com/systems-manager/latest/userguide/systems-manager-parameter- store.html
    </details>

52. A company is running a batch application on Amazon EC2 instances. The application consists of a backend with multiple Amazon RDS databases. The application is causing a high number of leads on the databases. A solutions architect must reduce the number of database reads while ensuring high availability. What should the solutions architect do to meet this requirement?
    - A. Add Amazon RDS read replicas.
    - B. Use Amazon ElasbCache for Redls.
    - C. Use Amazon Route 53 DNS caching.
    - D. Use Amazon ElastiCache for Memcached.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: B
      Explanation: Use ElastiCache to reduce reading and choose redis to ensure high availability.
    </details>

53. A security team wants to limit access to specific services or actions in all of the team's AWS accounts. All accounts belong to a large organization in AWS Organizations. The solution must be scalable and there must be a single point where permissions can be maintained. What should a solutions architect do to accomplish this?
    - A. Create an ACL to provide access to the services or actions.
    - B. Create a security group to allow accounts and attach it to user groups.
    - C. Create cross-account roles in each account to deny access to the services or actions.
    - D. Create a service control policy in the root organizational unit to deny access to the services or actions.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: D
      Explanation: Service control policies (SCPs) are one type of policy that you can use to manage your organization. SCPs offer central control over the maximum available permissions for all accounts in your organization, allowing you to ensure your accounts stay within your organization's access control guidelines. https://docs.aws.amazon.com/organizations/latest/userguide/orgs_manage_policies_scp.html.
    </details>

54. A company is concerned about the security of its public web application due to recent web attacks. The application uses an Application Load Balancer (ALB). A solutions architect must reduce the risk of DDoS attacks against the application. What should the solutions architect do to meet this requirement?
    - A. Add an Amazon Inspector agent to the ALB. - B. Configure Amazon Macie to prevent attacks.
    - C. Enable AWS Shield Advanced to prevent attacks.
    - D. Configure Amazon GuardDuty to monitor the ALB. 

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: C
      Explanation: AWS Shield is a managed Distributed Denial of Service (DDoS) protection service that helps protect web applications running on AWS from DDoS attacks. AWS Shield Advanced is an additional layer of protection that provides enhanced DDoS protection capabilities, including proactive monitoring and automatic inline mitigations, to help protect against even the largest and
      most sophisticated DDoS attacks. By enabling AWS Shield Advanced, the solutions architect can help protect the application from DDoS attacks and reduce the risk of disruption to the application.
    </details>

55. A company runs a production application on a fleet of Amazon EC2 instances. The application reads the data from an Amazon SQS queue and processes the messages in parallel. The message volume is unpredictable and often has intermittent traffic. This application should continually process messages without any downtime. Which solution meets these requirements MOST cost-effectively?
    - A. Use Spot Instances exclusively to handle the maximum capacity required.
    - B. Use Reserved Instances exclusively to handle the maximum capacity required.
    - C. Use Reserved Instances for the baseline capacity and use Spot Instances to handle additional capacity.
    - D. Use Reserved Instances for the baseline capacity and use On-Demand Instances to handle additional capacity.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: D
      Explanation: We recommend that you use On-Demand Instances for applications with short-term, irregular workloads that cannot be interrupted. https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ec2-on-demand-instances.html
    </details>

56. A solutions architect must design a solution that uses Amazon CloudFront with an Amazon S3 origin to store a static website. The company’s security policy requires that all website traffic be inspected by AWS WAF. How should the solutions architect comply with these requirements?
    - A. Configure an S3 bucket policy lo accept requests coming from the AWS WAF Amazon Resource Name (ARN) only.
    - B. Configure Amazon CloudFront to forward all incoming requests to AWS WAF before requesting content from the S3 origin.
    - C. Configure a security group that allows Amazon CloudFront IP addresses to access Amazon S3 only. Associate AWS WAF to CloudFront.
    - D. Configure Amazon CloudFront and Amazon S3 to use an origin access identity (OAI) to restrict access to the S3 bucket. Enable AWS WAF on the distribution.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: D
      Explanation: Use an OAI to lockdown CloudFront to S3 origin & enable WAF on CF distribution. https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/private-content- restricting-access-to-s3.html https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/distribution-web- awswaf.html
    </details>

57. A company wants to manage Amazon Machine Images (AMIs). The company currently copies AMIs to the same AWS Region where the AMIs were created. The company needs to design an application that captures AWS API calls and sends alerts whenever the Amazon EC2 Createlmage API operation is called within the company's account.
Which solution will meet these requirements with the LEAST operational overhead?
    - A. Create an AWS Lambda function to query AWS CloudTrail logs and to send an alert when a Createlmage API call is detected.
    - B. Configure AWS CloudTrail with an Amazon Simple Notification Service (Amazon SNS) notification that occurs when updated logs are sent to Amazon S3. Use Amazon Athena to create a new table and to query on Createlmage when an API call is detected.
    - C. Create an Amazon EventBridge (Amazon CloudWatch Events) rule for the Createlmage API call. Configure the target as an Amazon Simple Notification Service (Amazon SNS) topic to send an alert when a Createlmage API call is detected.
    - D. Configure an Amazon Simple Queue Service (Amazon SQS) FIFO queue as a target for AWS CloudTrail logs. Create an AWS Lambda function to send an alert to an Amazon Simple Notification Service (Amazon SNS) topic when a Createlmage API call is detected.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: C
      Explanation: To create an EventBridge rule to send a notification when an AMI is created and in the available state. https://docs.aws.amazon.com/AWSEC2/latest/WindowsGuide/monitor-ami-events.html
    </details>

58. An online retail company has more than 50 million active customers and receives more than 25,000 orders each day. The company collects purchase data for customers and stores this data in Amazon S3. Additional customer data is stored in Amazon RDS. The company wants to make all the data available to various teams so that the teams can perform analytics. The solution must provide the ability to manage fine-grained permissions for the data and must minimize operational overhead. Which solution will meet these requirements?
    - A. Migrate the purchase data to write directly to Amazon RDS. Use RDS access controls to limit access.
    - B. Schedule an AWS Lambda function to periodically copy data from Amazon RDS to Amazon S3. Create an AWS Glue crawler. Use Amazon Athena to query the data. Use S3 policies to limit access.
    - C. Create a data lake by using AWS Lake Formation. Create an AWS Glue JDBC connection to Amazon RDS. Register (he S3 bucket in Lake Formation. Use Lake Formation access controls to limit access.
    - D. Create an Amazon Redshift cluster. Schedule an AWS Lambda function to periodically copy data from Amazon S3 and Amazon RDS to Amazon Redshift. Use Amazon Redshift access controls to limit access.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: C
      Explanation: Manage fine-grained access control using AWS Lake Formation. https://aws.amazon.com/blogs/big-data/manage-fine-grained-access-control-using-aws-lake- formation/
    </details>

59. A company owns an asynchronous API that is used to ingest user requests and, based on the request type, dispatch requests to the appropriate microservice for processing. The company is using Amazon API Gateway to deploy the API front end, and an AWS Lambda function that invokes Amazon DynamoDB to store user requests before dispatching them to the processing microservices. The company provisioned as much DynamoDB throughput as its budget allows, but the company is still experiencing availability issues and is losing user requests. What should a solutions architect do to address this issue without impacting existing users?
    - A. Add throttling on the API Gateway with server-side throttling limits.
    - B. Use DynamoDB Accelerator (DAX) and Lambda to buffer writes to DynamoDB. - C. Create a secondary index in DynamoDB for the table with the user requests.
    - D. Use the Amazon Simple Queue Service (Amazon SQS) queue and Lambda to buffer writes to DynamoDB. 

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: D
      Explanation: because all other options put some more charges to DynamoDB. But the company supplied as much as they can for DynamoDB. And it is async request and we need to have retry mechanism not to lose the customer data.
    </details>

60. A company needs to move data from an Amazon EC2 instance to an Amazon S3 bucket. The company must ensure that no API calls and no data are routed through public internet routes. Only the EC2 instance can have access to upload data to the S3 bucket. Which solution will meet these requirements?
    - A. Create an interface VPC endpoint for Amazon S3 in the subnet where the EC2 instance is located. Attach a resource policy to the S3 bucket to only allow the EC2 instance's IAM role for access.
    - B. Create a gateway VPC endpoint for Amazon S3 in the Availability Zone where the EC2 instance is located. Attach appropriate security groups to the endpoint. Attach a resource policy lo the S3 bucket to only allow the EC2 instance's IAM role for access.
    - C. Run the nslookup tool from inside the EC2 instance to obtain the private IP address of the S3 bucket's service API endpoint. Create a route in the VPC route table to provide the EC2 instance with access to the S3 bucket. Attach a resource policy to the S3 bucket to only allow the EC2 instance's IAM role for access.
    - D. Use the AWS provided, publicly available ip-ranges.json tile to obtain the private IP address of the S3 bucket's service API endpoint. Create a route in the VPC route table to provide the EC2 instance with access to the S3 bucket. Attach a resource policy to the S3 bucket to only allow the EC2 instance's IAM role for access.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: A
      Explanation: https://aws.amazon.com/premiumsupport/knowledge-center/connect-s3-vpc-endpoint/
    </details>

61. A gaming company hosts a browser-based application on AWS. The users of the application consume a large number of videos and images that are stored in Amazon S3. This content is the same for all users. The application has increased in popularity, and millions of users worldwide accessing these media files. The company wants to provide the files to the users while reducing the load on the origin. Which solution meets these requirements MOST cost-effectively?
    - A. Deploy an AWS Global Accelerator accelerator in front of the web servers.
    - B. Deploy an Amazon CloudFront web distribution in front of the S3 bucket.
    - C. Deploy an Amazon ElastiCache for Redis instance in front of the web servers.
    - D. Deploy an Amazon ElastiCache for Memcached instance in front of the web servers.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: B
      Explanation: Cloud front is best for content delivery. Global Accelerator is best for non-HTTP (TCP/UDP) cases and supports HTTP cases as well but with static IP (elastic IP) or anycast IP address only.
    </details>

62. A company has two applications: a sender application that sends messages with payloads to be processed and a processing application intended to receive the messages with payloads. The company wants to implement an AWS service to handle messages between the two applications. The sender application can send about 1.000 messages each hour. The messages may take up to 2 days to be processed. If the messages fail to process, they must be retained so that they do not impact the processing of any remaining messages. Which solution meets these requirements and is the MOST operationally efficient?
    - A. Set up an Amazon EC2 instance running a Redis database. Configure both applications to use the instance. Store, process, and delete the messages, respectively.
    - B. Use an Amazon Kinesis data stream to receive the messages from the sender application. Integrate the processing application with the Kinesis Client Library (KCL).
    - C. Integrate the sender and processor applications with an Amazon Simple Queue Service (Amazon SQS) queue. Configure a dead-letter queue to collect the messages that failed to process.
    - D. Subscribe the processing application to an Amazon Simple Notification Service (Amazon SNS) topic to receive notifications to process. Integrate the sender application to write to the SNS topic.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: C
      Explanation: Amazon SQS supports dead-letter queues (DLQ), which other queues (source queues) can target for messages that can't be processed (consumed) successfully. https://docs.aws.amazon.com/AWSSimpleQueueService/latest/SQSDeveloperGuide/sqs-dead- letter-queues.html
    </details>

63. A company has an AWS account used for software engineering. The AWS account has access to the company's on-premises data center through a pair of AWS Direct Connect connections. All non-VPC traffic routes to the virtual private gateway. A development team recently created an AWS Lambda function through the console. The development team needs to allow the function to access a database that runs in a private subnet in the company's data center. Which solution will meet these requirements?
    - A. Configure the Lambda function to run in the VPC with the appropriate security group.
    - B. Set up a VPN connection from AWS to the data center. Route the traffic from the Lambda function through the VPN.
    - C. Update the route tables in the VPC to allow the Lambda function to access the on-premises data center through Direct Connect.
    - D. Create an Elastic IP address. Configure the Lambda function to send traffic through the Elastic IP address without an elastic network interface.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: C
      Explanation: To connect to another AWS service, you can use VPC endpoints for private communications between your VPC and supported AWS services. An alternative approach is to use a NAT gateway to route outbound traffic to another AWS service. To give your function access to the internet, route outbound traffic to a NAT gateway in a public subnet. The NAT gateway has a public IP address and can connect to the internet through the VPC's internet gateway. https://docs.aws.amazon.com/lambda/latest/dg/foundation-networking.html#foundation-nw- connecting
    </details>

64. A company has a legacy data processing application that runs on Amazon EC2 instances. Data is processed sequentially, but the order of results does not matter. The application uses a monolithic architecture. The only way that the company can scale the application to meet increased demand is to increase the size of the instances. The company's developers have decided to rewrite the application to use a microservices architecture on Amazon Elastic Container Service (Amazon ECS). What should a solutions architect recommend for communication between the microservices?
    - A. Create an Amazon Simple Queue Service (Amazon SQS) queue. Add code to the data producers, and send data to the queue. Add code to the data consumers to process data from the queue.
    - B. Create an Amazon Simple Notification Service (Amazon SNS) topic. Add code to the data producers, and publish notifications to the topic. Add code to the data consumers to subscribe to the topic.
    - C. Create an AWS Lambda function to pass messages. Add code to the data producers to call the Lambda function with a data object. Add code to the data consumers to receive a data object that is passed from the Lambda function.
    - D. Create an Amazon DynamoDB table. Enable DynamoDB Streams. Add code to the data producers to insert data into the table. Add code to the data consumers to use the DynamoDB Streams API to detect new table entries and retrieve the data.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: A
      Explanation: Queue has Limited throughput (300 msg/s without batching, 3000 msg/s with batching whereby up- to 10 msg per batch operation; Msg duplicates not allowed in the queue (exactly-once delivery); Msg order is preserved (FIFO); Queue name must end with .fifo
    </details>

65. A solutions architect is optimizing a website for an upcoming musical event. Videos of the performances will be streamed in real time and then will be available on demand. The event is expected to attract a global online audience. Which service will improve the performance of both the real-lime and on-demand streaming?
    - A. Amazon CloudFront
    - B. AWS Global Accelerator
    - C. Amazon Route 53
    - D. Amazon S3 Transfer Acceleration

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: A
      Explanation: You can use CloudFront to deliver video on demand (VOD) or live streaming video using any HTTP origin. One way you can set up video workflows in the cloud is by using CloudFront together with AWS Media Services. https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/on-demand-streaming- video.html
    </details>
