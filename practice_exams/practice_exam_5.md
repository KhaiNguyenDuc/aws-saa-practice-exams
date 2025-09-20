---
layout: exam
---

# Practice Exam 5

1. A company wants to use a custom distributed application that calculates various profit and loss scenarios. To achieve this goal, the company needs to provide a network connection between its Amazon EC2 instances. The connection must minimize latency and must maximize throughput Which solution will meet these requirements?
    - A. Provision the application to use EC2 Dedicated Hosts of the same instance type.
    - B. Configure a placement group for EC2 instances that have the same instance type.
    - C. Use multiple AWS elastic network interfaces and link aggregation.
    - D. Configure AWS PrivateLink for the EC2 instances.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: B
      Explanation: Cluster placement groups are recommended for applications that benefit from low network latency, high network throughput, or both. They are also recommended when the majority of the network traffic is between the instances in the group. To provide the lowest latency and the highest packet- per-second network performance for your placement group, choose an instance type that supports enhanced networking. https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/placement-groups.html#placement- groups-cluster
    </details>

2. A company needs to run a critical application on AWS. The company needs to use Amazon EC2 for the application’s database. The database must be highly available and must fail over automatically if a disruptive event occurs. Which solution will meet these requirements?
    - A. Launch two EC2 instances, each in a different Availability Zone in the same AWS Region. Install the database on both EC2 instances. Configure the EC2 instances as a cluster. Set up database replication.
    - B. Launch an EC2 instance in an Availability Zone. Install the database on the EC2 instance. Use an Amazon Machine Image (AMI) to back up the data. Use AWS CloudFormation to automate provisioning of the EC2 instance if a disruptive event occurs.
    - C. Launch two EC2 instances, each in a different AWS Region. Install the database on both EC2 instances. Set up database replication. Fail over the database to a second Region.
    - D. Launch an EC2 instance in an Availability Zone. Install the database on the EC2 instance. Use an Amazon Machine Image (AMI) to back up the data. Use EC2 automatic recovery to recover the instance if a disruptive event occurs.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: A
      Explanation: Configure the EC2 instances as a cluster) Cluster consist of one or more DB instances and a cluster volume that manages the data for those DB instances. Cluster Volume is a VIRTUAL DATABASE storage volume that spans multiple Availability Zones, with each Availability Zone having a copy of the DB cluster data. https://docs.aws.amazon.com/AmazonRDS/latest/AuroraUserGuide/Aurora.Overview.html
    </details>

3. A company hosts its application on AWS. The company uses Amazon Cognito to manage users. When users log in to the application, the application fetches required data from Amazon DynamoDB by using a REST API that is hosted in Amazon API Gateway. The company wants an AWS managed solution that will control access to the REST API to reduce development efforts. Which solution will meet these requirements with the LEAST operational overhead?
    - A. Configure an AWS Lambda function to be an authorizer in API Gateway to validate which user made the request.
    - B. For each user, create and assign an API key that must be sent with each request. Validate the key by using an AWS Lambda function.
    - C. Send the user’s email address in the header with every request. Invoke an AWS Lambda function to validate that the user with that email address has proper access.
    - D. Configure an Amazon Cognito user pool authorizer in API Gateway to allow Amazon Cognito to validate each request.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: D
      Explanation: Use the Amazon Cognito console, CLI/SDK, or API to create a user pool—or use one that's owned by another AWS account. https://docs.aws.amazon.com/apigateway/latest/developerguide/apigateway-integrate-with- cognito.html
    </details>

4. A company is developing a marketing communications service that targets mobile app users. The company needs to send confirmation messages with Short Message Service (SMS) to its users. The users must be able to reply to the SMS messages. The company must store the responses for a year for analysis. What should a solutions architect do to meet these requirements?
    - A. Create an Amazon Connect contact flow to send the SMS messages. Use AWS Lambda to process the responses.
    - B. Build an Amazon Pinpoint journey. Configure Amazon Pinpoint to send events to an Amazon Kinesis data stream for analysis and archiving.
    - C. Use Amazon Simple Queue Service (Amazon SQS) to distribute the SMS messages. Use AWS Lambda to process the responses.
    - D. Create an Amazon Simple Notification Service (Amazon SNS) FIFO topic. Subscribe an Amazon Kinesis data stream to the SNS topic for analysis and archiving.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: B
      Explanation: https://aws.amazon.com/pinpoint/product-details/sms/ Two-Way Messaging: Receive SMS messages from your customers and reply back to them in a chat-like interactive experience. With Amazon Pinpoint, you can create automatic responses when customers send you messages that contain certain keywords. You can even use Amazon Lex to create conversational bots. A majority of mobile phone users read incoming SMS messages almost immediately after receiving them. If you need to be able to provide your customers with urgent or important information, SMS messaging may be the right solution for you. You can use Amazon Pinpoint to create targeted groups of customers, and then send them campaign-based messages. You can also use Amazon Pinpoint to send direct messages, such as appointment confirmations, order updates, and one-time passwords.
    </details>

5. The customers of a finance company request appointments with financial advisors by sending text messages. A web application that runs on Amazon EC2 instances accepts the appointment requests. The text messages are published to an Amazon Simple Queue Service (Amazon SQS) queue through the web application. Another application that runs on EC2 instances then sends meeting invitations and meeting confirmation email messages to the customers. After successful scheduling, this application stores the meeting information in an Amazon DynamoDB database. As the company expands, customers report that their meeting invitations are taking longer to arrive. What should a solutions architect recommend to resolve this issue?
    - A. Add a DynamoDB Accelerator (DAX) cluster in front of the DynamoDB database.
    - B. Add an Amazon API Gateway API in front of the web application that accepts the appointment requests.
    - C. Add an Amazon CloudFront distribution. Set the origin as the web application that accepts the appointment requests.
    - D. Add an Auto Scaling group for the application that sends meeting invitations. Configure the Auto Scaling group to scale based on the depth of the SQS queue.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: D
      Explanation: To resolve the issue of longer delivery times for meeting invitations, the solutions architect can recommend adding an Auto Scaling group for the application that sends meeting invitations and configuring the Auto Scaling group to scale based on the depth of the SQS queue. This will allow the application to scale up as the number of appointment requests increases, improving the performance and delivery times of the meeting invitations.
    </details>

6. A company offers a food delivery service that is growing rapidly. Because of the growth, the company’s order processing system is experiencing scaling problems during peak traffic hours. The current architecture includes the following: - A group of Amazon EC2 instances that run in an Amazon EC2 Auto Scaling group to collect orders from the application - Another group of EC2 instances that run in an Amazon EC2 Auto Scaling group to fulfill orders The order collection process occurs quickly, but the order fulfillment process can take longer. Data must not be lost because of a scaling event. A solutions architect must ensure that the order collection process and the order fulfillment process can both scale properly during peak traffic hours. The solution must optimize utilization of the
company’s AWS resources. Which solution meets these requirements?
    - A. Use Amazon CloudWatch metrics to monitor the CPU of each instance in the Auto Scaling groups. Configure each Auto Scaling group’s minimum capacity according to peak workload values.
    - B. Use Amazon CloudWatch metrics to monitor the CPU of each instance in the Auto Scaling groups. Configure a CloudWatch alarm to invoke an Amazon Simple Notification Service (Amazon SNS) topic that creates additional Auto Scaling groups on demand.
    - C. Provision two Amazon Simple Queue Service (Amazon SQS) queues: one for order collection and another for order fulfillment. Configure the EC2 instances to poll their respective queue. Scale the Auto Scaling groups based on notifications that the queues send.
    - D. Provision two Amazon Simple Queue Service (Amazon SQS) queues: one for order collection and another for order fulfillment. Configure the EC2 instances to poll their respective queue. Create a metric based on a backlog per instance calculation. Scale the Auto Scaling groups based on this metric.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: D
      Explanation: The number of instances in your Auto Scaling group can be driven by how long it takes to process a message and the acceptable amount of latency (queue delay). The solution is to use a backlog per instance metric with the target value being the acceptable backlog per instance to maintain.
    </details>

7. A company hosts multiple production applications. One of the applications consists of resources from Amazon EC2, AWS Lambda, Amazon RDS, Amazon Simple Notification Service (Amazon SNS), and Amazon Simple Queue Service (Amazon SQS) across multiple AWS Regions. All company resources are tagged with a tag name of “application” and a value that corresponds to each application. A solutions architect must provide the quickest solution for identifying all of the tagged components. Which solution meets these requirements?
    - A. Use AWS CloudTrail to generate a list of resources with the application tag.
    - B. Use the AWS CLI to query each service across all Regions to report the tagged components.
    - C. Run a query in Amazon CloudWatch Logs Insights to report on the components with the application tag.
    - D. Run a query with the AWS Resource Groups Tag Editor to report on the resources globally with the application tag.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: D
      Explanation: https://docs.aws.amazon.com/ARG/latest/userguide/tag-editor.html Tags are words or phrases that act as metadata that you can use to identify and organize your AWS resources. A resource can have up to 50 user-applied tags. It can also have read-only system tags. Each tag consists of a key and one optional value.
    </details>

8. A company needs to export its database once a day to Amazon S3 for other teams to access. The exported object size varies between 2 GB and 5 GB. The S3 access pattern for the data is variable and changes rapidly. The data must be immediately available and must remain accessible for up to 3 months. The company needs the most cost-effective solution that will not increase retrieval time. Which S3 storage class should the company use to meet these requirements?
    - A. S3 Intelligent-Tiering
    - B. S3 Glacier Instant Retrieval
    - C. S3 Standard
    - D. S3 Standard-Infrequent Access (S3 Standard-IA)

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: A
      Explanation: S3 Intelligent-Tiering monitors access patterns and moves objects that have not been accessed for 30 consecutive days to the Infrequent Access tier and after 90 days of no access to the Archive Instant Access tier.
    </details>

9. A company is developing a new mobile app. The company must implement proper traffic filtering to protect its Application Load Balancer (ALB) against common application-level attacks, such as cross-site scripting or SQL injection. The company has minimal infrastructure and operational staff. The company needs to reduce its share of the responsibility in managing, updating, and securing servers for its AWS environment. What should a solutions architect recommend to meet these requirements?
    - A. Configure AWS WAF rules and associate them with the ALB. - B. Deploy the application using Amazon S3 with public hosting enabled.
    - C. Deploy AWS Shield Advanced and add the ALB as a protected resource.
    - D. Create a new ALB that directs traffic to an Amazon EC2 instance running a third-party firewall, which then passes the traffic to the current ALB. 

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: A
      Explanation: A solutions architect should recommend option A, which is to configure AWS WAF rules and associate them with the ALB. This will allow the company to apply traffic filtering at the application layer, which is necessary for protecting the ALB against common application-level attacks such as cross-site scripting or SQL injection. AWS WAF is a managed service that makes it easy to protect web applications from common web exploits that could affect application availability, compromise security, or consume excessive resources. The company can easily manage and update the rules to ensure the security of its application.
    </details>

10. A company’s reporting system delivers hundreds of .csv files to an Amazon S3 bucket each day. The company must convert these files to Apache Parquet format and must store the files in a transformed data bucket. Which solution will meet these requirements with the LEAST development effort?
    - A. Create an Amazon EMR cluster with Apache Spark installed. Write a Spark application to transform the data. Use EMR File System (EMRFS) to write files to the transformed data bucket.
    - B. Create an AWS Glue crawler to discover the data. Create an AWS Glue extract, transform, and load (ETL) job to transform the data. Specify the transformed data bucket in the output step.
    - C. Use AWS Batch to create a job definition with Bash syntax to transform the data and output the data to the transformed data bucket. Use the job definition to submit a job. Specify an array job as the job type.
    - D. Create an AWS Lambda function to transform the data and output the data to the transformed data bucket. Configure an event notification for the S3 bucket. Specify the Lambda function as the destination for the event notification.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: B
      Explanation: https://docs.aws.amazon.com/prescriptive-guidance/latest/patterns/three-aws-glue-etl-job-types- for-converting-data-to-apache-parquet.html
    </details>

11. A company has a serverless website with millions of objects in an Amazon S3 bucket. The company uses the S3 bucket as the origin for an Amazon CloudFront distribution. The company did not set encryption on the S3 bucket before the objects were loaded. A solutions architect needs to enable encryption for all existing objects and for all objects that are added to the S3 bucket in the future. Which solution will meet these requirements with the LEAST amount of effort?
    - A. Create a new S3 bucket. Turn on the default encryption settings for the new S3 bucket. Download all existing objects to temporary local storage. Upload the objects to the new S3 bucket.
    - B. Turn on the default encryption settings for the S3 bucket. Use the S3 Inventory feature to create a .csv file that lists the unencrypted objects. Run an S3 Batch Operations job that uses the copy command to encrypt those objects.
    - C. Create a new encryption key by using AWS Key Management Service (AWS KMS). Change the settings on the S3 bucket to use server-side encryption with AWS KMS managed encryption keys (SSE-KMS). Turn on versioning for the S3 bucket.
    - D. Navigate to Amazon S3 in the AWS Management Console. Browse the S3 bucket’s objects. Sort by the encryption field. Select each unencrypted object. Use the Modify button to apply default encryption settings to every unencrypted object in the S3 bucket.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: B
      Explanation: Step 1: S3 inventory to get object list Step 2 (If needed): Use S3 Select to filter Step 3: S3 object operations to encrypt the unencrypted objects. On the going object use default encryption. https://aws.amazon.com/blogs/storage/encrypting-objects-with-amazon-s3-batch-operations/
    </details>

12. A solutions architect is designing a new API using Amazon API Gateway that will receive requests from users. The volume of requests is highly variable; several hours can pass without receiving a single request. The data processing will take place asynchronously, but should be completed within a few seconds after a request is made. Which compute service should the solutions architect have the API invoke to deliver the requirements at the lowest cost?
    - A. An AWS Glue job
    - B. An AWS Lambda function
    - C. A containerized service hosted in Amazon Elastic Kubernetes Service (Amazon EKS)
    - D. A containerized service hosted in Amazon ECS with Amazon EC2

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: B
      Explanation: API Gateway + Lambda is the perfect solution for modern applications with serverless architecture.
    </details>

13. A company runs an application on a group of Amazon Linux EC2 instances. For compliance reasons, the company must retain all application log files for 7 years. The log files will be analyzed by a reporting tool that must be able to access all the files concurrently. Which storage solution meets these requirements MOST cost-effectively?
    - A. Amazon Elastic Block Store (Amazon EBS)
    - B. Amazon Elastic File System (Amazon EFS)
    - C. Amazon EC2 instance store
    - D. Amazon S3

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: D
      Explanation: Amazon S3 - Requests to Amazon S3 can be authenticated or anonymous. Authenticated access requires credentials that AWS can use to authenticate your requests. When making REST API calls directly from your code, you create a signature using valid credentials and include the signature in your request. Amazon Simple Storage Service (Amazon S3) is an object storage service that offers industry-leading scalability, data availability, security, and performance. This means customers of all sizes and industries can use it to store and protect any amount of data for a range of use cases, such as websites, mobile applications, backup and restore, archive, enterprise applications, IoT devices, and big data analytics. Amazon S3 provides easy-to-use management features so you can organize your data and configure finely-tuned access controls to meet your specific business, organizational, and compliance requirements. Amazon S3 is designed for 99.999999999% (11 9's) of durability, and stores data for millions of applications for companies all around the world. Reference: https://aws.amazon.com/s3/
    </details>

14. A company has hired an external vendor to perform work in the company’s AWS account. The vendor uses an automated tool that is hosted in an AWS account that the vendor owns. The vendor does not have IAM access to the company’s AWS account. How should a solutions architect grant this access to the vendor?
    - A. Create an IAM role in the company’s account to delegate access to the vendor’s IAM role. Attach the appropriate IAM policies to the role for the permissions that the vendor requires.
    - B. Create an IAM user in the company’s account with a password that meets the password complexity requirements. Attach the appropriate IAM policies to the user for the permissions that the vendor requires.
    - C. Create an IAM group in the company’s account. Add the tool’s IAM user from the vendor account to the group. Attach the appropriate IAM policies to the group for the permissions that the vendor requires.
    - D. Create a new identity provider by choosing “AWS account” as the provider type in the IAM console. Supply the vendor’s AWS account ID and user name. Attach the appropriate IAM policies to the new provider for the permissions that the vendor requires.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: A
      Explanation: https://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles_common-scenarios_third-party.html
    </details>

15. A company needs to retain its AWS CloudTrail logs for 3 years. The company is enforcing CloudTrail across a set of AWS accounts by using AWS Organizations from the parent account. The CloudTrail target S3 bucket is configured with S3 Versioning enabled. An S3 Lifecycle policy is in place to delete current objects after 3 years. After the fourth year of use of the S3 bucket, the S3 bucket metrics show that the number of objects has continued to rise. However, the number of new CloudTrail logs that are delivered to the S3 bucket has remained consistent. Which solution will delete objects that are older than 3 years in the MOST cost-effective manner?
    - A. Configure the organization’s centralized CloudTrail trail to expire objects after 3 years.
    - B. Configure the S3 Lifecycle policy to delete previous versions as well as current versions.
    - C. Create an AWS Lambda function to enumerate and delete objects from Amazon S3 that are older than 3 years.
    - D. Configure the parent account as the owner of all objects that are delivered to the S3 bucket.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: B
      Explanation: To delete objects that are older than 3 years in the most cost-effective manner, the company should configure the S3 Lifecycle policy to delete previous versions as well as current versions. This will ensure that all versions of the objects, including the previous versions, are deleted after 3 years.
    </details>

16. A company has an API that receives real-time data from a fleet of monitoring devices. The API stores this data in an Amazon RDS DB instance for later analysis. The amount of data that the monitoring devices send to the API fluctuates. During periods of heavy traffic, the API often returns timeout errors. After an inspection of the logs, the company determines that the database is not capable of processing the volume of write traffic that comes from the API. A solutions architect must minimize the number of connections to the database and must ensure that data is not lost during periods of heavy traffic. Which solution will meet these requirements?
    - A. Increase the size of the DB instance to an instance type that has more available memory.
    - B. Modify the DB instance to be a Multi-AZ DB instance. Configure the application to write to all active RDS DB instances.
    - C. Modify the API to write incoming data to an Amazon Simple Queue Service (Amazon SQS) queue. Use an AWS Lambda function that Amazon SQS invokes to write data from the queue to the database.
    - D. Modify the API to write incoming data to an Amazon Simple Notification Service (Amazon SNS) topic. Use an AWS Lambda function that Amazon SNS invokes to write data from the topic to the database.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: C
      Explanation: Using Amazon SQS will help minimize the number of connections to the database, as the API will write data to a queue instead of directly to the database. Additionally, using an AWS Lambda function that Amazon SQS invokes to write data from the queue to the database will help ensure that data is not lost during periods of heavy traffic, as the queue will serve as a buffer between the API and the database.
    </details>

17. A company manages its own Amazon EC2 instances that run MySQL databases. The company is manually managing replication and scaling as demand increases or decreases. The company needs a new solution that simplifies the process of adding or removing compute capacity to or from its database tier as needed. The solution also must offer improved performance, scaling, and durability with minimal effort from operations. Which solution meets these requirements?
    - A. Migrate the databases to Amazon Aurora Serverless for Aurora MySQL.
    - B. Migrate the databases to Amazon Aurora Serverless for Aurora PostgreSQL.
    - C. Combine the databases into one larger MySQL database. Run the larger database on larger EC2 instances.
    - D. Create an EC2 Auto Scaling group for the database tier. Migrate the existing databases to the new environment.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: A
      Explanation: https://aws.amazon.com/rds/aurora/serverless/
    </details>

18. A company is concerned that two NAT instances in use will no longer be able to support the traffic needed for the company’s application. A solutions architect wants to implement a solution that is highly available, fault tolerant, and automatically scalable. What should the solutions architect recommend?
    - A. Remove the two NAT instances and replace them with two NAT gateways in the same Availability Zone.
    - B. Use Auto Scaling groups with Network Load Balancers for the NAT instances in different Availability Zones.
    - C. Remove the two NAT instances and replace them with two NAT gateways in different Availability Zones.
    - D. Replace the two NAT instances with Spot Instances in different Availability Zones and deploy a Network Load Balancer.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: C
      Explanation: If you have resources in multiple Availability Zones and they share one NAT gateway, and if the NAT gateway's Availability Zone is down, resources in the other Availability Zones lose internet access. To create an Availability Zone-independent architecture, create a NAT gateway in each Availability Zone and configure your routing to ensure that resources use the NAT gateway in the same Availability Zone. https://docs.aws.amazon.com/vpc/latest/userguide/vpc-nat-gateway.html#nat-gateway-basics
    </details>

19. An application runs on an Amazon EC2 instance that has an Elastic IP address in VPC
    - A. The application requires access to a database in VPC
    - B. Both VPCs are in the same AWS account. Which solution will provide the required access MOST securely?
    - A. Create a DB instance security group that allows all traffic from the public IP address of the application server in VPC
    - A. - B. Configure a VPC peering connection between VPC A and VPC
    - B. - C. Make the DB instance publicly accessible. Assign a public IP address to the DB instance.
    - D. Launch an EC2 instance with an Elastic IP address into VPC
    - B. Proxy all requests through the new EC2 instance.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: B
      Explanation: https://aws.amazon.com/premiumsupport/knowledge-center/rds-connectivity-instance-subnet- vpc/
    </details>

20. A company runs demonstration environments for its customers on Amazon EC2 instances. Each environment is isolated in its own VPC. The company’s operations team needs to be notified when RDP or SSH access to an environment has been established.
    - A. Configure Amazon CloudWatch Application Insights to create AWS Systems Manager OpsItems when RDP or SSH access is detected.
    - B. Configure the EC2 instances with an IAM instance profile that has an IAM role with the AmazonSSMManagedInstanceCore policy attached.
    - C. Publish VPC flow logs to Amazon CloudWatch Logs. Create required metric filters. Create an Amazon CloudWatch metric alarm with a notification action for when the alarm is in the ALARM state.
    - D. Configure an Amazon EventBridge rule to listen for events of type EC2 Instance State-change Notification. Configure an Amazon Simple Notification Service (Amazon SNS) topic as a target. Subscribe the operations team to the topic.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: C
      Explanation: EC2 Instance State-change Notifications are not the same as RDP or SSH established connection notifications. Use Amazon CloudWatch Logs to monitor SSH access to your Amazon EC2 Linux instances so that you can monitor rejected (or established) SSH connection requests and take action. https://aws.amazon.com/blogs/security/how-to-monitor-and-visualize-failed-ssh-access-attempts- to-amazon-ec2-linux-instances/
    </details>

21. A company has a three-tier application for image sharing. The application uses an Amazon EC2
instance for the front-end layer, another EC2 instance for the application layer, and a third EC2 instance for a MySQL database. A solutions architect must design a scalable and highly available solution that requires the least amount of change to the application. Which solution meets these requirements?
    - A. Use Amazon S3 to host the front-end layer. Use AWS Lambda functions for the application layer. Move the database to an Amazon DynamoDB table. Use Amazon S3 to store and serve users’ images.
    - B. Use load-balanced Multi-AZ AWS Elastic Beanstalk environments for the front-end layer and the application layer. Move the database to an Amazon RDS DB instance with multiple read replicas to serve users’ images.
    - C. Use Amazon S3 to host the front-end layer. Use a fleet of EC2 instances in an Auto Scaling group for the application layer. Move the database to a memory optimized instance type to store and serve users’ images.
    - D. Use load-balanced Multi-AZ AWS Elastic Beanstalk environments for the front-end layer and the application layer. Move the database to an Amazon RDS Multi-AZ DB instance. Use Amazon S3 to store and serve users’ images.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: D
      Explanation: for "Highly available": Multi-AZ & for "least amount of changes to the application": Elastic Beanstalk automatically handles the deployment, from capacity provisioning, load balancing, auto-scaling to application health monitoring
    </details>

22. A company wants to experiment with individual AWS accounts for its engineer team. The company wants to be notified as soon as the Amazon EC2 instance usage for a given month exceeds a specific threshold for each account. What should a solutions architect do to meet this requirement MOST cost-effectively?
    - A. Use Cost Explorer to create a daily report of costs by service. Filter the report by EC2 instances. Configure Cost Explorer to send an Amazon Simple Email Service (Amazon SES) notification when a threshold is exceeded.
    - B. Use Cost Explorer to create a monthly report of costs by service. Filter the report by EC2 instances. Configure Cost Explorer to send an Amazon Simple Email Service (Amazon SES) notification when a threshold is exceeded.
    - C. Use AWS Budgets to create a cost budget for each account. Set the period to monthly. Set the scope to EC2 instances. Set an alert threshold for the budget. Configure an Amazon Simple Notification Service (Amazon SNS) topic to receive a notification when a threshold is exceeded.
    - D. Use AWS Cost and Usage Reports to create a report with hourly granularity. Integrate the report data with Amazon Athena. Use Amazon EventBridge to schedule an Athena query. Configure an Amazon Simple Notification Service (Amazon SNS) topic to receive a notification when a threshold is exceeded.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: C
      Explanation: AWS Budgets allows you to create budgets for your AWS accounts and set alerts when usage exceeds a certain threshold. By creating a budget for each account, specifying the period as monthly and the scope as EC2 instances, you can effectively track the EC2 usage for each account and be notified when a threshold is exceeded. This solution is the most cost-effective option as it does not require additional resources such as Amazon Athena or Amazon EventBridge. https://aws.amazon.com/getting-started/hands-on/control-your-costs-free-tier-budgets/
    </details>

23. A company previously migrated its data warehouse solution to AWS. The company also has an AWS Direct Connect connection. Corporate office users query the data warehouse using a visualization tool. The average size of a query returned by the data warehouse is 50 MB and each webpage sent by the visualization tool is approximately 500 KB. Result sets returned by the data warehouse are not cached. Which solution provides the LOWEST data transfer egress cost for the company?
    - A. Host the visualization tool on premises and query the data warehouse directly over the internet.
    - B. Host the visualization tool in the same AWS Region as the data warehouse. Access it over the internet.
    - C. Host the visualization tool on premises and query the data warehouse directly over a Direct Connect connection at a location in the same AWS Region.
    - D. Host the visualization tool in the same AWS Region as the data warehouse and access it over a Direct Connect connection at a location in the same Region.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: D
      Explanation: https://aws.amazon.com/directconnect/pricing/ https://aws.amazon.com/blogs/aws/aws-data-transfer-prices-reduced/
    </details>

24. An online learning company is migrating to the AWS Cloud. The company maintains its student records in a PostgreSQL database. The company needs a solution in which its data is available and online across multiple AWS Regions at all times. Which solution will meet these requirements with the LEAST amount of operational overhead?
    - A. Migrate the PostgreSQL database to a PostgreSQL cluster on Amazon EC2 instances.
    - B. Migrate the PostgreSQL database to an Amazon RDS for PostgreSQL DB instance with the Multi- AZ feature turned on.
    - C. Migrate the PostgreSQL database to an Amazon RDS for PostgreSQL DB instance. Create a read replica in another Region.
    - D. Migrate the PostgreSQL database to an Amazon RDS for PostgreSQL DB instance. Set up DB snapshots to be copied to another Region.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: C
      Explanation: https://aws.amazon.com/blogs/aws/cross-region-read-replicas-for-amazon-rds-for-mysql/
    </details>

25. A medical research lab produces data that is related to a new study. The lab wants to make the data available with minimum latency to clinics across the country for their on-premises, file-based applications. The data files are stored in an Amazon S3 bucket that has read-only permissions for each clinic. What should a solutions architect recommend to meet these requirements?
    - A. Deploy an AWS Storage Gateway file gateway as a virtual machine (VM) on premises at each clinic.
    - B. Migrate the files to each clinic’s on-premises applications by using AWS DataSync for processing.
    - C. Deploy an AWS Storage Gateway volume gateway as a virtual machine (VM) on premises at each clinic.
    - D. Attach an Amazon Elastic File System (Amazon EFS) file system to each clinic’s on-premises servers.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: A
      Explanation: AWS Storage Gateway is a service that connects an on-premises software appliance with cloud- based storage to provide seamless and secure integration between an organization's on-premises IT environment and AWS's storage infrastructure. By deploying a file gateway as a virtual machine on each clinic's premises, the medical research lab can provide low-latency access to the data stored in the S3 bucket while maintaining read-only permissions for each clinic. This solution allows the clinics to access the data files directly from their on-premises file-based applications without the need for data transfer or migration.
    </details>

26. A company is using a content management system that runs on a single Amazon EC2 instance. The EC2 instance contains both the web server and the database software. The company must make its website platform highly available and must enable the website to scale to meet user demand. What should a solutions architect recommend to meet these requirements?
    - A. Move the database to Amazon RDS, and enable automatic backups. Manually launch another EC2 instance in the same Availability Zone. Configure an Application Load Balancer in the Availability Zone, and set the two instances as targets.
    - B. Migrate the database to an Amazon Aurora instance with a read replica in the same Availability Zone as the existing EC2 instance. Manually launch another EC2 instance in the same Availability Zone. Configure an Application Load Balancer, and set the two EC2 instances as targets.
    - C. Move the database to Amazon Aurora with a read replica in another Availability Zone. Create an Amazon Machine Image (AMI) from the EC2 instance. Configure an Application Load Balancer in two Availability Zones. Attach an Auto Scaling group that uses the AMI across two Availability Zones.
    - D. Move the database to a separate EC2 instance, and schedule backups to Amazon S3. Create an Amazon Machine Image (AMI) from the original EC2 instance. Configure an Application Load Balancer in two Availability Zones. Attach an Auto Scaling group that uses the AMI across two Availability Zones.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: C
      Explanation: This approach will provide both high availability and scalability for the website platform. By moving the database to Amazon Aurora with a read replica in another availability zone, it will provide a failover option for the database. The use of an Application Load Balancer and an Auto Scaling group across two availability zones allows for automatic scaling of the website to meet increased user demand. Additionally, creating an AMI from the original EC2 instance allows for easy replication of the instance in case of failure.
    </details>

27. A company is launching an application on AWS. The application uses an Application Load Balancer (ALB) to direct traffic to at least two Amazon EC2 instances in a single target group. The instances are in an Auto Scaling group for each environment. The company requires a development environment and a production environment. The production environment will have periods of high traffic. Which solution will configure the development environment MOST cost-effectively?
    - A. Reconfigure the target group in the development environment to have only one EC2 instance as a target.
    - B. Change the ALB balancing algorithm to least outstanding requests.
    - C. Reduce the size of the EC2 instances in both environments.
    - D. Reduce the maximum number of EC2 instances in the development environment’s Auto Scaling group.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: D
      Explanation: This option will configure the development environment in the most cost-effective way as it reduces the number of instances running in the development environment and therefore reduces the cost of running the application. The development environment typically requires less resources than the production environment, and it is unlikely that the development environment will have periods of high traffic that would require a large number of instances. By reducing the maximum number of instances in the development environment's Auto Scaling group, the company can save on costs while still maintaining a functional development environment.
    </details>

28. A company runs a web application on Amazon EC2 instances in multiple Availability Zones. The EC2 instances are in private subnets. A solutions architect implements an internet-facing Application Load Balancer (ALB) and specifies the EC2 instances as the target group. However, the internet traffic is not reaching the EC2 instances. How should the solutions architect reconfigure the architecture to resolve this issue?
    - A. Replace the ALB with a Network Load Balancer. Configure a NAT gateway in a public subnet to allow internet traffic.
    - B. Move the EC2 instances to public subnets. Add a rule to the EC2 instances’ security groups to allow outbound traffic to 0.0.0.0/0.
    - C. Update the route tables for the EC2 instances’ subnets to send 0.0.0.0/0 traffic through the internet gateway route. Add a rule to the EC2 instances’ security groups to allow outbound traffic to 0.0.0.0/0.
    - D. Create public subnets in each Availability Zone. Associate the public subnets with the ALB. Update the route tables for the public subnets with a route to the private subnets.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: D
      Explanation: https://aws.amazon.com/premiumsupport/knowledge-center/public-load-balancer-private-ec2/
    </details>

29. A company runs analytics software on Amazon EC2 instances. The software accepts job requests from users to process data that has been uploaded to Amazon S3. Users report that some submitted data is not being processed Amazon CloudWatch reveals that the EC2 instances have a consistent CPU utilization at or near 100%. The company wants to improve system performance and scale the system based on user load. What should a solutions architect do to meet these requirements?
    - A. Create a copy of the instance. Place all instances behind an Application Load Balancer.
    - B. Create an S3 VPC endpoint for Amazon S3. Update the software to reference the endpoint.
    - C. Stop the EC2 instances. Modify the instance type to one with a more powerful CPU and more memory. Restart the instances.
    - D. Route incoming requests to Amazon Simple Queue Service (Amazon SQS). Configure an EC2 Auto Scaling group based on queue size. Update the software to read from the queue.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: D
      Explanation: By routing incoming requests to Amazon SQS, the company can decouple the job requests from the processing instances. This allows them to scale the number of instances based on the size of the queue, providing more resources when needed. Additionally, using an Auto Scaling group based on the queue size will automatically scale the number of instances up or down depending on the workload. Updating the software to read from the queue will allow it to process the job requests in a more efficient manner, improving the performance of the system.
    </details>

30. A company is implementing a shared storage solution for a media application that is hosted in the AWS Cloud. The company needs the ability to use SMB clients to access data. The solution must be fully managed. Which AWS solution meets these requirements?
    - A. Create an AWS Storage Gateway volume gateway. Create a file share that uses the required client protocol. Connect the application server to the file share.
    - B. Create an AWS Storage Gateway tape gateway. Configure tapes to use Amazon S3. Connect the application server to the tape gateway.
    - C. Create an Amazon EC2 Windows instance. Install and configure a Windows file share role on the instance. Connect the application server to the file share.
    - D. Create an Amazon FSx for Windows File Server file system. Attach the file system to the origin server. Connect the application server to the file system.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: D
      Explanation: Amazon FSx has native support for Windows file system features and for the industry-standard Server Message Block (SMB) protocol to access file storage over a network. https://docs.aws.amazon.com/fsx/latest/WindowsGuide/what-is.html
    </details>

31. A company’s security team requests that network traffic be captured in VPC Flow Logs. The logs will be frequently accessed for 90 days and then accessed intermittently. What should a solutions architect do to meet these requirements when configuring the logs?
    - A. Use Amazon CloudWatch as the target. Set the CloudWatch log group with an expiration of 90 days
    - B. Use Amazon Kinesis as the target. Configure the Kinesis stream to always retain the logs for 90 days.
    - C. Use AWS CloudTrail as the target. Configure CloudTrail to save to an Amazon S3 bucket, and enable S3 Intelligent-Tiering.
    - D. Use Amazon S3 as the target. Enable an S3 Lifecycle policy to transition the logs to S3 Standard- Infrequent Access (S3 Standard-IA) after 90 days.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: D
      Explanation: https://docs.aws.amazon.com/AmazonCloudWatch/latest/logs/CloudWatchLogsConcepts.html
    </details>

32. A solutions architect needs to design a system to store client case files. The files are core company assets and are important. The number of files will grow over time. The files must be simultaneously accessible from multiple application servers that run on Amazon EC2 instances. The solution must have built-in redundancy. Which solution meets these requirements?
    - A. Amazon Elastic File System (Amazon EFS)
    - B. Amazon Elastic Block Store (Amazon EBS)
    - C. Amazon S3 Glacier Deep Archive
    - D. AWS Backup

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: A
      Explanation: Amazon EFS provides a simple, scalable, fully managed file system that can be simultaneously accessed from multiple EC2 instances and provides built-in redundancy. It is optimized for multiple EC2 instances to access the same files, and it is designed to be highly available, durable, and secure. It can scale up to petabytes of data and can handle thousands of concurrent connections, and is a cost-effective solution for storing and accessing large amounts of data.
    </details>

33. A solutions architect has created two IAM policies: Policy1 and Policy2. Both policies are attached to an IAM group. A cloud engineer is added as an IAM user to the IAM group. Which action will the cloud engineer be able to perform?
    - A. Deleting IAM users
    - B. Deleting directories
    - C. Deleting Amazon EC2 instances
    - D. Deleting logs from Amazon CloudWatch Logs

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: C
      Explanation: There is an explicit DENY on deleting directories in the second policy. So the only thing that can be deleted is EC2 instances as per the permission in the first policy.
    </details>

34. A company is reviewing a recent migration of a three-tier application to a VPC. The security team discovers that the principle of least privilege is not being applied to Amazon EC2 security group ingress and egress rules between the application tiers.
What should a solutions architect do to correct this issue?
    - A. Create security group rules using the instance ID as the source or destination.
    - B. Create security group rules using the security group ID as the source or destination.
    - C. Create security group rules using the VPC CIDR blocks as the source or destination.
    - D. Create security group rules using the subnet CIDR blocks as the source or destination.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: B
      Explanation: The ID of a security group (referred to here as the specified security group). For example, the current security group, a security group from the same VPC, or a security group for a peered VPC. This allows traffic based on the private IP addresses of the resources associated with the specified security group. This does not add rules from the specified security group to the current security group. https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/security-group-rules.html
    </details>

35. A company is building a solution that will report Amazon EC2 Auto Scaling events across all the applications in an AWS account. The company needs to use a serverless solution to store the EC2 Auto Scaling status data in Amazon S3. The company then will use the data in Amazon S3 to provide near-real-time updates in a dashboard. The solution must not affect the speed of EC2 instance launches. How should the company move the data to Amazon S3 to meet these requirements?
    - A. Use an Amazon CloudWatch metric stream to send the EC2 Auto Scaling status data to Amazon Kinesis Data Firehose. Store the data in Amazon S3.
    - B. Launch an Amazon EMR cluster to collect the EC2 Auto Scaling status data and send the data to Amazon Kinesis Data Firehose. Store the data in Amazon S3.
    - C. Create an Amazon EventBridge rule to invoke an AWS Lambda function on a schedule. Configure the Lambda function to send the EC2 Auto Scaling status data directly to Amazon S3.
    - D. Use a bootstrap script during the launch of an EC2 instance to install Amazon Kinesis Agent. Configure Kinesis Agent to collect the EC2 Auto Scaling status data and send the data to Amazon
Kinesis Data Firehose. Store the data in Amazon S3.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: A
      Explanation: You can use metric streams to continually stream CloudWatch metrics to a destination of your choice, with near-real-time delivery and low latency. One of the use cases is Data Lake: create a metric stream and direct it to an Amazon Kinesis Data Firehose delivery stream that delivers your CloudWatch metrics to a data lake such as Amazon S3. https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/CloudWatch-Metric- Streams.html
    </details>

36. A company has an application that places hundreds of .csv files into an Amazon S3 bucket every hour. The files are 1 GB in size. Each time a file is uploaded, the company needs to convert the file to Apache Parquet format and place the output file into an S3 bucket. Which solution will meet these requirements with the LEAST operational overhead?
    - A. Create an AWS Lambda function to download the .csv files, convert the files to Parquet format, and place the output files in an S3 bucket. Invoke the Lambda function for each S3 PUT event.
    - B. Create an Apache Spark job to read the .csv files, convert the files to Parquet format, and place the output files in an S3 bucket. Create an AWS Lambda function for each S3 PUT event to invoke the Spark job.
    - C. Create an AWS Glue table and an AWS Glue crawler for the S3 bucket where the application places the .csv files. Schedule an AWS Lambda function to periodically use Amazon Athena to query the AWS Glue table, convert the query results into Parquet format, and place the output files into an S3 bucket.
    - D. Create an AWS Glue extract, transform, and load (ETL) job to convert the .csv files to Parquet format and place the output files into an S3 bucket. Create an AWS Lambda function for each S3 PUT event to invoke the ETL job.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: D
      Explanation: https://docs.aws.amazon.com/prescriptive-guidance/latest/patterns/three-aws-glue-etl-job-types- for-converting-data-to-apache-parquet.html
    </details>

37. A company’s compliance team needs to move its file shares to AWS. The shares run on a Windows Server SMB file share. A self-managed on-premises Active Directory controls access to the files and folders. The company wants to use Amazon FSx for Windows File Server as part of the solution. The company must ensure that the on-premises Active Directory groups restrict access to the FSx for Windows File Server SMB compliance shares, folders, and files after the move to AWS. The company has created an FSx for Windows File Server file system. Which solution will meet these requirements?
    - A. Create an Active Directory Connector to connect to the Active Directory. Map the Active Directory groups to IAM groups to restrict access.
    - B. Assign a tag with a Restrict tag key and a Compliance tag value. Map the Active Directory groups to IAM groups to restrict access.
    - C. Create an IAM service-linked role that is linked directly to FSx for Windows File Server to restrict access.
    - D. Join the file system to the Active Directory to restrict access.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: D
      Explanation: Joining the FSx for Windows File Server file system to the on-premises Active Directory will allow the company to use the existing Active Directory groups to restrict access to the file shares, folders, and files after the move to AWS. This option allows the company to continue using their existing access controls and management structure, making the transition to AWS more seamless.
    </details>

38. A company plans to use Amazon ElastiCache for its multi-tier web application. A solutions architect creates a Cache VPC for the ElastiCache cluster and an App VPC for the application’s Amazon EC2 instances. Both VPCs are in the us-east-1 Region. The solutions architect must implement a solution to provide the application’s EC2 instances with access to the ElastiCache cluster. Which solution will meet these requirements MOST cost-effectively?
    - A. Create a peering connection between the VPCs. Add a route table entry for the peering connection in both VPCs. Configure an inbound rule for the ElastiCache cluster’s security group to allow inbound connection from the application’s security group.
    - B. Create a Transit VPC. Update the VPC route tables in the Cache VPC and the App VPC to route traffic through the Transit VPC. Configure an inbound rule for the ElastiCache cluster's security group to allow inbound connection from the application’s security group.
    - C. Create a peering connection between the VPCs. Add a route table entry for the peering connection in both VPCs. Configure an inbound rule for the peering connection’s security group to allow inbound connection from the application’s security group.
    - D. Create a Transit VPC. Update the VPC route tables in the Cache VPC and the App VPC to route traffic through the Transit VPC. Configure an inbound rule for the Transit VPC’s security group to allow inbound connection from the application’s security group.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: A
      Explanation: Creating a peering connection between the VPCs allows the application's EC2 instances to communicate with the ElastiCache cluster directly and efficiently. This is the most cost-effective solution as it does not involve creating additional resources such as a Transit VPC, and it does not incur additional costs for traffic passing through the Transit VPC. Additionally, it is also more secure as it allows you to configure a more restrictive security group rule to allow inbound connection from only the application's security group.
    </details>

39. A company has a web application hosted over 10 Amazon EC2 instances with traffic directed by Amazon Route 53. The company occasionally experiences a timeout error when attempting to browse the application. The networking team finds that some DNS queries return IP addresses of unhealthy instances, resulting in the timeout error. What should a solutions architect implement to overcome these timeout errors?
    - A. Create a Route 53 simple routing policy record for each EC2 instance. Associate a health check with each record.
    - B. Create a Route 53 failover routing policy record for each EC2 instance. Associate a health check with each record.
    - C. Create an Amazon CloudFront distribution with EC2 instances as its origin. Associate a health check with the EC2 instances.
    - D. Create an Application Load Balancer (ALB) with a health check in front of the EC2 instances. Route to the ALB from Route 53.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: D
      Explanation: An Application Load Balancer (ALB) allows you to distribute incoming traffic across multiple backend instances, and can automatically route traffic to healthy instances while removing traffic from unhealthy instances. By using an ALB in front of the EC2 instances and routing traffic to it from Route 53, the load balancer can perform health checks on the instances and only route traffic to healthy instances, which should help to reduce or eliminate timeout errors caused by unhealthy instances.
    </details>

40. A solutions architect needs to design a highly available application consisting of web, application, and database tiers. HTTPS content delivery should be as close to the edge as possible, with the least delivery time. Which solution meets these requirements and is MOST secure?
    - A. Configure a public Application Load Balancer (ALB) with multiple redundant Amazon EC2 instances in public subnets. Configure Amazon CloudFront to deliver HTTPS content using the public ALB as the origin.
    - B. Configure a public Application Load Balancer with multiple redundant Amazon EC2 instances in private subnets. Configure Amazon CloudFront to deliver HTTPS content using the EC2 instances as the origin.
    - C. Configure a public Application Load Balancer (ALB) with multiple redundant Amazon EC2 instances in private subnets. Configure Amazon CloudFront to deliver HTTPS content using the public ALB as the origin.
    - D. Configure a public Application Load Balancer with multiple redundant Amazon EC2 instances in public subnets. Configure Amazon CloudFront to deliver HTTPS content using the EC2 instances as the origin.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: C
      Explanation: This solution meets the requirements for a highly available application with web, application, and database tiers, as well as providing edge-based content delivery. Additionally, it maximizes security by having the ALB in a private subnet, which limits direct access to the web servers, while still being able to serve traffic over the Internet via the public ALB. This will ensure that the web servers are
      not exposed to the public Internet, which reduces the attack surface and provides a secure way to access the application. https://aws.amazon.com/premiumsupport/knowledge-center/public-load-balancer-private-ec2/
    </details>

41. A company has a popular gaming platform running on AWS. The application is sensitive to latency because latency can impact the user experience and introduce unfair advantages to some players. The application is deployed in every AWS Region. It runs on Amazon EC2 instances that are part of Auto Scaling groups configured behind Application Load Balancers (ALBs). A solutions architect needs to implement a mechanism to monitor the health of the application and redirect traffic to healthy endpoints. Which solution meets these requirements?
    - A. Configure an accelerator in AWS Global Accelerator. Add a listener for the port that the application listens on, and attach it to a Regional endpoint in each Region. Add the ALB as the endpoint.
    - B. Create an Amazon CloudFront distribution and specify the ALB as the origin server. Configure the cache behavior to use origin cache headers. Use AWS Lambda functions to optimize the traffic.
    - C. Create an Amazon CloudFront distribution and specify Amazon S3 as the origin server. Configure the cache behavior to use origin cache headers. Use AWS Lambda functions to optimize the traffic.
    - D. Configure an Amazon DynamoDB database to serve as the data store for the application. Create a DynamoDB Accelerator (DAX) cluster to act as the in-memory cache for DynamoDB hosting the application data.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: A
      Explanation: When you have an Application Load Balancer or Network Load Balancer that includes multiple target groups, Global Accelerator considers the load balancer endpoint to be healthy only if each target group behind the load balancer has at least one healthy target. If any single target group for the load balancer has only unhealthy targets, Global Accelerator considers the endpoint to be unhealthy. https://docs.aws.amazon.com/global-accelerator/latest/dg/about-endpoint-groups-health-check- options.html
    </details>

42. A company has one million users that use its mobile app. The company must analyze the data usage in near-real time. The company also must encrypt the data in near-real time and must store the data in a centralized location in Apache Parquet format for further processing. Which solution will meet these requirements with the LEAST operational overhead?
    - A. Create an Amazon Kinesis data stream to store the data in Amazon S3. Create an Amazon Kinesis Data Analytics application to analyze the data. Invoke an AWS Lambda function to send the data to the Kinesis Data Analytics application.
    - B. Create an Amazon Kinesis data stream to store the data in Amazon S3. Create an Amazon EMR cluster to analyze the data. Invoke an AWS Lambda function to send the data to the EMR cluster.
    - C. Create an Amazon Kinesis Data Firehose delivery stream to store the data in Amazon S3. Create an Amazon EMR cluster to analyze the data.
    - D. Create an Amazon Kinesis Data Firehose delivery stream to store the data in Amazon S3. Create an Amazon Kinesis Data Analytics application to analyze the data.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: D
      Explanation: This solution will meet the requirements with the least operational overhead as it uses Amazon Kinesis Data Firehose, which is a fully managed service that can automatically handle the data
      collection, data transformation, encryption, and data storage in near-real time. Kinesis Data Firehose can automatically store the data in Amazon S3 in Apache Parquet format for further processing. Additionally, it allows you to create an Amazon Kinesis Data Analytics application to analyze the data in near real-time, with no need to manage any infrastructure or invoke any Lambda function. This way you can process a large amount of data with the least operational overhead.
    </details>

43. An ecommerce company has noticed performance degradation of its Amazon RDS based web application. The performance degradation is attributed to an increase in the number of read-only SQL queries triggered by business analysts. A solutions architect needs to solve the problem with minimal changes to the existing web application. What should the solutions architect recommend?
    - A. Export the data to Amazon DynamoDB and have the business analysts run their queries.
    - B. Load the data into Amazon ElastiCache and have the business analysts run their queries.
    - C. Create a read replica of the primary database and have the business analysts run their queries.
    - D. Copy the data into an Amazon Redshift cluster and have the business analysts run their queries.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: C
      Explanation: Creating a read replica of the primary RDS database will offload the read-only SQL queries from the primary database, which will help to improve the performance of the web application. Read replicas are exact copies of the primary database that can be used to handle read-only traffic, which will reduce the load on the primary database and improve the performance of the web application. This solution can be implemented with minimal changes to the existing web application, as the business analysts can continue to run their queries on the read replica without modifying the code.
    </details>

44. A company provides an online service for posting video content and transcoding it for use by any mobile platform. The application architecture uses Amazon Elastic File System (Amazon EFS) Standard to collect and store the videos so that multiple Amazon EC2 Linux instances can access the video content for processing. As the popularity of the service has grown over time, the storage costs have become too expensive. Which storage solution is MOST cost-effective?
    - A. Use AWS Storage Gateway for files to store and process the video content.
    - B. Use AWS Storage Gateway for volumes to store and process the video content.
    - C. Use Amazon EFS for storing the video content. Once processing is complete, transfer the files to Amazon Elastic Block Store (Amazon EBS).
    - D. Use Amazon S3 for storing the video content. Move the files temporarily over to an Amazon Elastic Block Store (Amazon EBS) volume attached to the server for processing.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: D
      Explanation: A better solution would be to use a transcoding service like Amazon Elastic Transcoder to process the video content directly from Amazon S3. This would eliminate the need for storing the content on an EBS volume, reduce storage costs, and simplify the architecture by removing the need for managing EBS volumes.
    </details>

45. A company is using Amazon CloudFront with its website. The company has enabled logging on the CloudFront distribution, and logs are saved in one of the company's Amazon S3 buckets. The company needs to perform advanced analyses on the logs and build visualizations. What should a solutions architect do to meet these requirements?
    - A. Use standard SQL queries in Amazon Athena to analyze the CloudFront logs in the S3 bucket. Visualize the results with AWS Glue.
    - B. Use standard SQL queries in Amazon Athena to analyze the CloudFront logs in the S3 bucket. Visualize the results with Amazon QuickSight.
    - C. Use standard SQL queries in Amazon DynamoDB to analyze the CloudFront logs in the S3 bucket. Visualize the results with AWS Glue.
    - D. Use standard SQL queries in Amazon DynamoDB to analyze the CloudFront logs in the S3 bucket. Visualize the results with Amazon QuickSight.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: B
      Explanation: Quicksite creating data visualizations. https://docs.aws.amazon.com/quicksight/latest/user/welcome.html
    </details>

46. A company runs a fleet of web servers using an Amazon RDS for PostgreSQL DB instance. After a routine compliance check, the company sets a standard that requires a recovery point objective (RPO) of less than 1 second for all its production databases. Which solution meets these requirements?
    - A. Enable a Multi-AZ deployment for the DB instance.
    - B. Enable auto scaling for the DB instance in one Availability Zone.
    - C. Configure the DB instance in one Availability Zone, and create multiple read replicas in a separate Availability Zone.
    - D. Configure the DB instance in one Availability Zone, and configure AWS Database Migration Service (AWS DMS) change data capture (CDC) tasks.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: A
      Explanation: By using Multi-AZ deployment, the company can achieve an RPO of less than 1 second because the standby instance is always in sync with the primary instance, ensuring that data changes are continuously replicated.
    </details>

47. A company runs a web application that is deployed on Amazon EC2 instances in the private subnet of a VPC. An Application Load Balancer (ALB) that extends across the public subnets directs web traffic to the EC2 instances. The company wants to implement new security measures to restrict inbound traffic from the ALB to the EC2 instances while preventing access from any other source inside or outside the private subnet of the EC2 instances. Which solution will meet these requirements?
    - A. Configure a route in a route table to direct traffic from the internet to the private IP addresses of the EC2 instances.
    - B. Configure the security group for the EC2 instances to only allow traffic that comes from the security group for the ALB. - C. Move the EC2 instances into the public subnet. Give the EC2 instances a set of Elastic IP addresses.
    - D. Configure the security group for the ALB to allow any TCP traffic on any port.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: B
      Explanation: This ensures that only the traffic originating from the ALB is allowed access to the EC2 instances in the private subnet, while denying any other traffic from other sources.
    </details>

48. A research company runs experiments that are powered by a simulation application and a visualization application. The simulation application runs on Linux and outputs intermediate data to an NFS share every 5 minutes. The visualization application is a Windows desktop application that displays the simulation output and requires an SMB file system. The company maintains two synchronized file systems. This strategy is causing data duplication and inefficient resource usage. The company needs to migrate the applications to AWS without making code changes to either application.
Which solution will meet these requirements?
    - A. Migrate both applications to AWS Lambda. Create an Amazon S3 bucket to exchange data between the applications.
    - B. Migrate both applications to Amazon Elastic Container Service (Amazon ECS). Configure Amazon FSx File Gateway for storage.
    - C. Migrate the simulation application to Linux Amazon EC2 instances. Migrate the visualization application to Windows EC2 instances. Configure Amazon Simple Queue Service (Amazon SQS) to exchange data between the applications.
    - D. Migrate the simulation application to Linux Amazon EC2 instances. Migrate the visualization application to Windows EC2 instances. Configure Amazon FSx for NetApp ONTAP for storage.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: D
      Explanation: Amazon FSx for NetApp ONTAP is a fully-managed shared storage service built on NetApp's popular ONTAP file system. Amazon FSx for NetApp ONTAP provides the popular features, performance, and APIs of ONTAP file systems with the agility, scalability, and simplicity of a fully managed AWS service, making it easier for customers to migrate on-premises applications that rely on NAS appliances to AWS. FSx for ONTAP file systems are similar to on-premises NetApp clusters. Within each file system that you create, you also create one or more storage virtual machines (SVMs). These are isolated file servers each with their own endpoints for NFS, SMB, and management access, as well as authentication (for both administration and end-user data access). In turn, each SVM has one or more volumes which store your data. https://aws.amazon.com/de/blogs/storage/getting-started-cloud-file-storage-with-amazon-fsx-for- netapp-ontap-using-netapp-management-tools/
    </details>

49. A company hosts its static website by using Amazon S3. The company wants to add a contact form to its webpage. The contact form will have dynamic server-side components for users to input their name, email address, phone number, and user message. The company anticipates that there will be fewer than 100 site visits each month. Which solution will meet these requirements MOST cost-effectively?
    - A. Host a dynamic contact form page in Amazon Elastic Container Service (Amazon ECS). Set up Amazon Simple Email Service (Amazon SES) to connect to any third-party email provider.
    - B. Create an Amazon API Gateway endpoint with an AWS Lambda backend that makes a call to Amazon Simple Email Service (Amazon SES).
    - C. Convert the static webpage to dynamic by deploying Amazon Lightsail. Use client-side scripting to build the contact form. Integrate the form with Amazon WorkMail.
    - D. Create a t2.micro Amazon EC2 instance. Deploy a LAMP (Linux, Apache, MySQL, PHP/Perl/Python) stack to host the webpage. Use client-side scripting to build the contact form. Integrate the form with Amazon WorkMail.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: B
      Explanation: https://aws.amazon.com/blogs/architecture/create-dynamic-contact-forms-for-s3-static-websites- using-aws-lambda-amazon-api-gateway-and-amazon-ses/
    </details>

50. A company has a static website that is hosted on Amazon CloudFront in front of Amazon S3. The static website uses a database backend. The company notices that the website does not reflect updates that have been made in the website's Git repository. The company checks the continuous integration and continuous delivery (CI/CD) pipeline between the Git repository and Amazon S3. The company verifies that the webhooks are configured properly and that the CI/CD pipeline is sending messages that indicate successful deployments. A solutions architect needs to implement a solution that displays the updates on the website. Which solution will meet these requirements?
    - A. Add an Application Load Balancer.
    - B. Add Amazon ElastiCache for Redis or Memcached to the database layer of the web application.
    - C. Invalidate the CloudFront cache.
    - D. Use AWS Certificate Manager (ACM) to validate the website's SSL certificate.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: C
      Explanation: Invalidate the CloudFront cache: The solutions architect should invalidate the CloudFront cache to ensure that the latest version of the website is being served to users.
    </details>

51. A company wants to migrate a Windows-based application from on premises to the AWS Cloud. The application has three tiers: an application tier, a business tier, and a database tier with Microsoft SQL Server. The company wants to use specific features of SQL Server such as native backups and Data Quality Services. The company also needs to share files for processing between the tiers. How should a solutions architect design the architecture to meet these requirements?
    - A. Host all three tiers on Amazon EC2 instances. Use Amazon FSx File Gateway for file sharing between the tiers.
    - B. Host all three tiers on Amazon EC2 instances. Use Amazon FSx for Windows File Server for file sharing between the tiers.
    - C. Host the application tier and the business tier on Amazon EC2 instances. Host the database tier on Amazon RDS. Use Amazon Elastic File System (Amazon EFS) for file sharing between the tiers.
    - D. Host the application tier and the business tier on Amazon EC2 instances. Host the database tier on Amazon RDS. Use a Provisioned IOPS SSD (io2) Amazon Elastic Block Store (Amazon EBS) volume for file sharing between the tiers.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: B
      Explanation: Data Quality Services: If this feature is critical to your workload, consider choosing Amazon RDS Custom or Amazon EC2. https://docs.aws.amazon.com/prescriptive-guidance/latest/migration-sql-server/comparison.html
    </details>

52. A company is migrating a Linux-based web server group to AWS. The web servers must access files in a shared file store for some content. The company must not make any changes to the application. What should a solutions architect do to meet these requirements?
    - A. Create an Amazon S3 Standard bucket with access to the web servers.
    - B. Configure an Amazon CloudFront distribution with an Amazon S3 bucket as the origin.
    - C. Create an Amazon Elastic File System (Amazon EFS) file system. Mount the EFS file system on all web servers.
    - D. Configure a General Purpose SSD (gp3) Amazon Elastic Block Store (Amazon EBS) volume. Mount the EBS volume to all web servers.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: C
      Explanation: Create an Amazon Elastic File System (Amazon EFS) file system. Mount the EFS file system on all web servers. To meet the requirements of providing a shared file store for Linux-based web servers without making changes to the application, using an Amazon EFS file system is the best solution. Amazon EFS is a managed NFS file system service that provides shared access to files across multiple Linux-based instances, which makes it suitable for this use case. Amazon S3 is not ideal for this scenario since it is an object storage service and not a file system, and it requires additional tools or libraries to mount the S3 bucket as a file system. Amazon CloudFront can be used to improve content delivery performance but is not necessary for this requirement. Additionally, Amazon EBS volumes can only be mounted to one instance at a time, so it is not suitable for sharing files across multiple instances.
    </details>

53. A company has an AWS Lambda function that needs read access to an Amazon S3 bucket that is located in the same AWS account. Which solution will meet these requirements in the MOST secure manner?
    - A. Apply an S3 bucket policy that grants read access to the S3 bucket.
    - B. Apply an IAM role to the Lambda function. Apply an IAM policy to the role to grant read access to the S3 bucket.
    - C. Embed an access key and a secret key in the Lambda function's code to grant the required IAM permissions for read access to the S3 bucket.
    - D. Apply an IAM role to the Lambda function. Apply an IAM policy to the role to grant read access to all S3 buckets in the account.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: B
      Explanation: This is the most secure and recommended way to provide an AWS Lambda function with access to an S3 bucket. It involves creating an IAM role that the Lambda function assumes, and attaching an IAM policy to the role that grants the necessary permissions to read from the S3 bucket.
      https://docs.aws.amazon.com/lambda/latest/dg/lambda-permissions.html
    </details>

54. A company hosts a web application on multiple Amazon EC2 instances. The EC2 instances are in an Auto Scaling group that scales in response to user demand. The company wants to optimize cost savings without making a long-term commitment. Which EC2 instance purchasing option should a solutions architect recommend to meet these requirements?
    - A. Dedicated Instances only
    - B. On-Demand Instances only
    - C. A mix of On-Demand Instances and Spot Instances
    - D. A mix of On-Demand Instances and Reserved Instances

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: C
      Explanation: https://docs.aws.amazon.com/autoscaling/ec2/userguide/ec2-auto-scaling-mixed-instances- groups.html
    </details>

55. A company has an on-premises volume backup solution that has reached its end of life. The company wants to use AWS as part of a new backup solution and wants to maintain local access to all the data while it is backed up on AWS. The company wants to ensure that the data backed up on AWS is automatically and securely transferred. Which solution meets these requirements?
    - A. Use AWS Snowball to migrate data out of the on-premises solution to Amazon S3. Configure on- premises systems to mount the Snowball S3 endpoint to provide local access to the data.
    - B. Use AWS Snowball Edge to migrate data out of the on-premises solution to Amazon S3. Use the Snowball Edge file interface to provide on-premises systems with local access to the data.
    - C. Use AWS Storage Gateway and configure a cached volume gateway. Run the Storage Gateway software appliance on premises and configure a percentage of data to cache locally. Mount the gateway storage volumes to provide local access to the data.
    - D. Use AWS Storage Gateway and configure a stored volume gateway. Run the Storage Gateway software appliance on premises and map the gateway storage volumes to on-premises storage. Mount the gateway storage volumes to provide local access to the data.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: D
      Explanation: In the cached mode, your primary data is written to S3, while retaining your frequently accessed data locally in a cache for low-latency access. In the stored mode, your primary data is stored locally and your entire dataset is available for low- latency access while asynchronously backed up to AWS.
    </details>

56. An ecommerce company stores terabytes of customer data in the AWS Cloud. The data contains personally identifiable information (PII). The company wants to use the data in three applications. Only one of the applications needs to process the PII. The PII must be removed before the other two applications process the data. Which solution will meet these requirements with the LEAST operational overhead?
    - A. Store the data in an Amazon DynamoDB table. Create a proxy application layer to intercept and process the data that each application requests.
    - B. Store the data in an Amazon S3 bucket. Process and transform the data by using S3 Object Lambda before returning the data to the requesting application.
    - C. Process the data and store the transformed data in three separate Amazon S3 buckets so that each application has its own custom dataset. Point each application to its respective S3 bucket.
    - D. Process the data and store the transformed data in three separate Amazon DynamoDB tables so that each application has its own custom dataset. Point each application to its respective DynamoDB table.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: B
      Explanation: Amazon S3 Object Lambda allows you to add custom code to S3 GET requests, which means that you can modify the data before it is returned to the requesting application. In this case, you can use S3 Object Lambda to remove the PII before the data is returned to the two applications that do not need to process PII. This approach has the least operational overhead because it does not require creating separate datasets or proxy application layers, and it allows you to maintain a single copy of the data in an S3 bucket. https://aws.amazon.com/ko/blogs/korea/introducing-amazon-s3-object-lambda-use-your-code-to- process-data-as-it-is-being-retrieved-from-s3/
    </details>

57. A development team has launched a new application that is hosted on Amazon EC2 instances inside a development VPC. A solutions architect needs to create a new VPC in the same account. The new VPC will be peered with the development VPC. The VPC CIDR block for the development VPC is 192.168.0.0/24. The solutions architect needs to create a CIDR block for the new VPC. The CIDR block must be valid for a VPC peering connection to the development VPC. What is the SMALLEST CIDR block that meets these requirements?
    - A. 10.0.1.0/32
    - B. 192.168.0.0/24
    - C. 192.168.1.0/32
    - D. 10.0.1.0/24

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: D
      Explanation: The allowed block size is between a /28 netmask and /16 netmask. The CIDR block must not overlap with any existing CIDR block that's associated with the VPC. https://docs.aws.amazon.com/vpc/latest/userguide/configure-your-vpc.html
    </details>

58. A company deploys an application on five Amazon EC2 instances. An Application Load Balancer (ALB) distributes traffic to the instances by using a target group. The average CPU usage on each of the instances is below 10% most of the time, with occasional surges to 65%. A solutions architect needs to implement a solution to automate the scalability of the application. The solution must optimize the cost of the architecture and must ensure that the application has enough CPU resources when surges occur. Which solution will meet these requirements?
    - A. Create an Amazon CloudWatch alarm that enters the ALARM state when the CPUUtilization metric is less than 20%. Create an AWS Lambda function that the CloudWatch alarm invokes to terminate one of the EC2 instances in the ALB target group.
    - B. Create an EC2 Auto Scaling group. Select the existing ALB as the load balancer and the existing target group as the target group. Set a target tracking scaling policy that is based on the ASGAverageCPUUtilization metric. Set the minimum instances to 2, the desired capacity to 3, the maximum instances to 6, and the target value to 50%. Add the EC2 instances to the Auto Scaling group.
    - C. Create an EC2 Auto Scaling group. Select the existing ALB as the load balancer and the existing target group as the target group. Set the minimum instances to 2, the desired capacity to 3, and the maximum instances to 6. Add the EC2 instances to the Auto Scaling group.
    - D. Create two Amazon CloudWatch alarms. Configure the first CloudWatch alarm to enter the ALARM state when the average CPUUtilization metric is below 20%. Configure the second CloudWatch alarm to enter the ALARM state when the average CPUUtilization matric is above 50%. Configure the alarms to publish to an Amazon Simple Notification Service (Amazon SNS) topic to send an email message. After receiving the message, log in to decrease or increase the number of EC2 instances that are running.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: B
      Explanation: It allows for automatic scaling based on the average CPU utilization of the EC2 instances in the target group. With the use of a target tracking scaling policy based on the ASGAverageCPUUtilization metric, the EC2 Auto Scaling group can ensure that the target value of 50% is maintained while scaling the number of instances in the group up or down as needed. This will help ensure that the application has enough CPU resources during surges without overprovisioning, thus optimizing the cost of the architecture.
    </details>

59. A company is running a critical business application on Amazon EC2 instances behind an Application Load Balancer. The EC2 instances run in an Auto Scaling group and access an Amazon RDS DB instance. The design did not pass an operational review because the EC2 instances and the DB instance are all located in a single Availability Zone. A solutions architect must update the design to use a second Availability Zone. Which solution will make the application highly available?
    - A. Provision a subnet in each Availability Zone. Configure the Auto Scaling group to distribute the EC2 instances across both Availability Zones. Configure the DB instance with connections to each network.
    - B. Provision two subnets that extend across both Availability Zones. Configure the Auto Scaling group to distribute the EC2 instances across both Availability Zones. Configure the DB instance with connections to each network.
    - C. Provision a subnet in each Availability Zone. Configure the Auto Scaling group to distribute the EC2 instances across both Availability Zones. Configure the DB instance for Multi-AZ deployment.
    - D. Provision a subnet that extends across both Availability Zones. Configure the Auto Scaling group to distribute the EC2 instances across both Availability Zones. Configure the DB instance for Multi- AZ deployment.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: C
      Explanation: A subnet must reside within a single Availability Zone. https://aws.amazon.com/vpc/faqs/#:~:text=Can%20a%20subnet%20span%20Availability,within% 20a%20single%20Availability%20Zone.
    </details>

60. A research laboratory needs to process approximately 8 TB of data. The laboratory requires sub- millisecond latencies and a minimum throughput of 6 GBps for the storage subsystem. Hundreds of Amazon EC2 instances that run Amazon Linux will distribute and process the data. Which solution will meet the performance requirements?
    - A. Create an Amazon FSx for NetApp ONTAP file system. Sat each volume' tiering policy to ALL. Import the raw data into the file system. Mount the fila system on the EC2 instances.
    - B. Create an Amazon S3 bucket to store the raw data. Create an Amazon FSx for Lustre file system that uses persistent SSD storage. Select the option to import data from and export data to Amazon S3. Mount the file system on the EC2 instances.
    - C. Create an Amazon S3 bucket to store the raw data. Create an Amazon FSx for Lustre file system that uses persistent HDD storage. Select the option to import data from and export data to Amazon S3. Mount the file system on the EC2 instances.
    - D. Create an Amazon FSx for NetApp ONTAP file system. Set each volume's tiering policy to NONE. Import the raw data into the file system. Mount the file system on the EC2 instances.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: B
      Explanation: Create an Amazon S3 bucket to store the raw data Create an Amazon FSx for Lustre file system that uses persistent SSD storage Select the option to import data from and export data to Amazon S3 Mount the file system on the EC2 instances. Amazon FSx for Lustre uses SSD storage for sub- millisecond latencies and up to 6 GBps throughput, and can import data from and export data to Amazon S3. Additionally, the option to select persistent SSD storage will ensure that the data is stored on the disk and not lost if the file system is stopped.
    </details>

61. A company needs to migrate a legacy application from an on-premises data center to the AWS Cloud because of hardware capacity constraints. The application runs 24 hours a day, 7 days a week. The application's database storage continues to grow over time. What should a solutions architect do to meet these requirements MOST cost-effectively?
    - A. Migrate the application layer to Amazon EC2 Spot Instances. Migrate the data storage layer to Amazon S3.
    - B. Migrate the application layer to Amazon EC2 Reserved Instances. Migrate the data storage layer to Amazon RDS On-Demand Instances.
    - C. Migrate the application layer to Amazon EC2 Reserved Instances. Migrate the data storage layer to Amazon Aurora Reserved Instances.
    - D. Migrate the application layer to Amazon EC2 On-Demand Instances. Migrate the data storage layer to Amazon RDS Reserved Instances.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: C
      Explanation: https://docs.aws.amazon.com/AmazonRDS/latest/AuroraUserGuide/Aurora.AuroraMySQL.html
    </details>

62. A university research laboratory needs to migrate 30 TB of data from an on-premises Windows file server to Amazon FSx for Windows File Server. The laboratory has a 1 Gbps network link that many other departments in the university share. The laboratory wants to implement a data migration service that will maximize the performance of the data transfer. However, the laboratory needs to be able to control the amount of bandwidth that the service uses to minimize the impact on other departments. The data migration must take place within the next 5 days. Which AWS solution will meet these requirements?
    - A. AWS Snowcone
    - B. Amazon FSx File Gateway
    - C. AWS DataSync
    - D. AWS Transfer Family

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: C
      Explanation: DataSync can be used to migrate data between on-premises Windows file servers and Amazon FSx for Windows File Server with its compatibility for Windows file systems. The laboratory needs to migrate a large amount of data (30 TB) within a relatively short timeframe (5 days) and limit the impact on other departments' network traffic. Therefore, AWS DataSync can meet these requirements by providing fast and efficient data transfer with network throttling capability to control bandwidth usage. https://docs.aws.amazon.com/datasync/latest/userguide/configure-bandwidth.html
    </details>

63. A company is launching a new application deployed on an Amazon Elastic Container Service (Amazon ECS) cluster and is using the Fargate launch type for ECS tasks. The company is monitoring CPU and memory usage because it is expecting high traffic to the application upon its launch. However, the company wants to reduce costs when utilization decreases. What should a solutions architect recommend?
    - A. Use Amazon EC2 Auto Scaling to scale at certain periods based on previous traffic patterns.
    - B. Use an AWS Lambda function to scale Amazon ECS based on metric breaches that trigger an Amazon CloudWatch alarm.
    - C. Use Amazon EC2 Auto Scaling with simple scaling policies to scale when ECS metric breaches trigger an Amazon CloudWatch alarm.
    - D. Use AWS Application Auto Scaling with target tracking policies to scale when ECS metric breaches trigger an Amazon CloudWatch alarm.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: D
      Explanation: https://docs.aws.amazon.com/autoscaling/application/userguide/what-is-application-auto- scaling.html
    </details>

64. A company recently created a disaster recovery site in a different AWS Region. The company needs to transfer large amounts of data back and forth between NFS file systems in the two Regions on a periodic basis. Which solution will meet these requirements with the LEAST operational overhead?
    - A. Use AWS DataSync.
    - B. Use AWS Snowball devices.
    - C. Set up an SFTP server on Amazon EC2.
    - D. Use AWS Database Migration Service (AWS DMS).

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: A
      Explanation: AWS DataSync is a fully managed data transfer service that simplifies moving large amounts of data between on-premises storage systems and AWS services. It can also transfer data between different AWS services, including different AWS Regions. DataSync provides a simple, scalable, and automated solution to transfer data, and it minimizes the operational overhead because it is fully managed by AWS.
    </details>

65. A company uses Amazon API Gateway to run a private gateway with two REST APIs in the same VPC. The BuyStock RESTful web service calls the CheckFunds RESTful web service to ensure that enough funds are available before a stock can be purchased. The company has noticed in the VPC flow logs that the BuyStock RESTful web service calls the CheckFunds RESTful web service over the internet instead of through the VPC. A solutions architect must implement a solution so that the APIs communicate through the VPC. Which solution will meet these requirements with the FEWEST changes to the code?
    - A. Add an X-API-Key header in the HTTP header for authorization.
    - B. Use an interface endpoint.
    - C. Use a gateway endpoint.
    - D. Add an Amazon Simple Queue Service (Amazon SQS) queue between the two REST APIs.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: B
      Explanation: An interface endpoint is a horizontally scaled, redundant VPC endpoint that provides private connectivity to a service. It is an elastic network interface with a private IP address that serves as an entry point for traffic destined to the AWS service. Interface endpoints are used to connect VPCs with AWS services. https://docs.aws.amazon.com/apigateway/latest/developerguide/apigateway-private-apis.html
    </details>
