---
layout: exam
---

# Practice Exam 7

1. A solutions architect must migrate a Windows Internet Information Services (IIS) web application to AWS. The application currently relies on a file share hosted in the user's on-premises network- attached storage (NAS). The solutions architect has proposed migrating the MS web servers to Amazon EC2 instances in multiple Availability Zones that are connected to the storage solution, and configuring an Elastic Load Balancer attached to the instances. Which replacement to the on-premises file share is MOST resilient and durable?
    - A. Migrate the file share to Amazon RDS
    - B. Migrate the file share to AWS Storage Gateway
    - C. Migrate the file share to Amazon FSx for Windows File Server
    - D. Migrate the file share to Amazon Elastic File System (Amazon EFS)

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: C
      Explanation: Amazon FSx makes it easy and cost effective to launch, run, and scale feature-rich, high- performance file systems in the cloud.
    </details>

2. An ecommerce company is building a distributed application that involves several serverless functions and AWS services to complete order-processing tasks. These tasks require manual approvals as part of the workflow. A solutions architect needs to design an architecture for the order-processing application. The solution must be able to combine multiple AWS Lambda functions into responsive serverless applications. The solution also must orchestrate data and services that run on Amazon EC2 instances, containers, or on-premises servers. Which solution will meet these requirements with the LEAST operational overhead?
    - A. Use AWS Step Functions to build the application.
    - B. Integrate all the application components in an AWS Glue job
    - C. Use Amazon Simple Queue Service (Amazon SQS) to build the application
    - D. Use AWS Lambda functions and Amazon EventBridge (Amazon CloudWatch Events) events to build the application

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: A
      Explanation: AWS Step Functions is a fully managed service that makes it easy to build applications by coordinating the components of distributed applications and microservices using visual workflows. With Step Functions, you can combine multiple AWS Lambda functions into responsive serverless applications and orchestrate data and services that run on Amazon EC2 instances, containers, or on-premises servers. Step Functions also allows for manual approvals as part of the workflow. This solution meets all the requirements with the least operational overhead.
    </details>

3. A company is using Amazon Route 53 latency-based routing to route requests to its UDP-based application for users around the world. The application is hosted on redundant servers in the company's on-premises data centers in the United States. Asia, and Europe. The company's compliance requirements state that the application must be hosted on premises. The company wants to improve the performance and availability of the application. What should a solutions architect do to meet these requirements?
    - A. A Configure three Network Load Balancers (NLBs) in the three AWS Regions to address the on- premises endpoints. Create an accelerator by using AWS Global Accelerator, and register the NLBs
as its endpoints. Provide access to the application by using a CNAME that points to the accelerator DNS.
    - B. Configure three Application Load Balancers (ALBs) in the three AWS Regions to address the on- premises endpoints. Create an accelerator by using AWS Global Accelerator and register the ALBs as its endpoints. Provide access to the application by using a CNAME that points to the accelerator DNS.
    - C. Configure three Network Load Balancers (NLBs) in the three AWS Regions to address the on- premises endpoints. In Route 53, create a latency-based record that points to the three NLBs. and use it as an origin for an Amazon CloudFront distribution Provide access to the application by using a CNAME that points to the CloudFront DNS.
    - D. Configure three Application Load Balancers (ALBs) in the three AWS Regions to address the on- premises endpoints. In Route 53 create a latency-based record that points to the three ALBs and use it as an origin for an Amazon CloudFront distribution. Provide access to the application by using a CNAME that points to the CloudFront DNS.v

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: A
      Explanation: Q: How is AWS Global Accelerator different from Amazon CloudFront? A: AWS Global Accelerator and Amazon CloudFront are separate services that use the AWS global network and its edge locations around the world. CloudFront improves performance for both cacheable content (such as images and videos) and dynamic content (such as API acceleration and dynamic site delivery). Global Accelerator improves performance for a wide range of applications over TCP or UDP by proxying packets at the edge to applications running in one or more AWS Regions. Global Accelerator is a good fit for non-HTTP use cases, such as gaming (UDP), IoT (MQTT), or Voice over IP, as well as for HTTP use cases that specifically require static IP addresses or deterministic, fast regional failover. Both services integrate with AWS Shield for DDoS protection.
    </details>

4. A company runs an application on Amazon EC2 Linux instances across multiple Availability Zones. The application needs a storage layer that is highly available and Portable Operating System Interface (POSIX)-compliant. The storage layer must provide maximum data durability and must be shareable across the EC2 instances. The data in the storage layer will be accessed frequently for the first 30 days and will be accessed infrequently after that time. Which solution will meet these requirements MOST cost-effectively?
    - A. Use the Amazon S3 Standard storage class. Create an S3 Lifecycle policy to move infrequently accessed data to S3 Glacier.
    - B. Use the Amazon S3 Standard storage class. Create an S3 Lifecycle policy to move infrequently accessed data to S3 Standard-Infrequent Access (EF3 Standard-IA).
    - C. Use the Amazon Elastic File System (Amazon EFS) Standard storage class. Create a Lifecycle management policy to move infrequently accessed data to EFS Standard-Infrequent Access (EFS Standard-IA).
    - D. Use the Amazon Elastic File System (Amazon EFS) One Zone storage class. Create a Lifecycle management policy to move infrequently accessed data to EFS One Zone-Infrequent Access (EFS One Zone-IA).

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: C
      Explanation: https://aws.amazon.com/efs/features/infrequent-access/
    </details>

5. A company runs an application that receives data from thousands of geographically dispersed remote devices that use UDP. The application processes the data immediately and sends a message back to the device if necessary. No data is stored. The company needs a solution that minimizes latency for the data transmission from the devices. The solution also must provide rapid failover to another AWS Region. Which solution will meet these requirements?
    - A. Configure an Amazon Route 53 failover routing policy. Create a Network Load Balancer (NLB) in each of the two Regions. Configure the NLB to invoke an AWS Lambda function to process the data.
    - B. Use AWS Global Accelerator. Create a Network Load Balancer (NLB) in each of the two Regions as an endpoint. Create an Amazon Elastic Container Service (Amazon ECS) cluster with the Fargate launch type. Create an ECS service on the cluster. Set the ECS service as the target for the NLProcess the data in Amazon ECS.
    - C. Use AWS Global Accelerator Create an Application Load Balancer (ALB) in each of the two Regions as an endpoint. Create an Amazon Elastic Container Service (Amazon ECS) cluster with the Fargate launch type. Create an ECS service on the cluster. Set the ECS service as the target for the ALB Process the data in Amazon ECS.
    - D. Configure an Amazon Route 53 failover routing policy. Create an Application Load Balancer (ALB) in each of the two Regions. Create an Amazon Elastic Container Service (Amazon ECS) cluster with the Fargate launch type. Create an ECS service on the cluster. Set the ECS service as the target for the ALB Process the data in Amazon ECS.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: B
      Explanation: Geographically dispersed (related to UDP) - Global Accelerator - multiple entrances worldwide to the AWS network to provide better transfer rates. UDP - NLB (Network Load Balancer).
    </details>

6. An ecommerce company is running a multi-tier application on AWS. The front-end and backend tiers both run on Amazon EC2, and the database runs on Amazon RDS for MySQL. The backend tier communicates with the RDS instance. There are frequent calls to return identical datasets from the database that are causing performance slowdowns. Which action should be taken to improve the performance of the backend?
    - A. Implement Amazon SNS to store the database calls.
    - B. Implement Amazon ElasticCache to cache the large database.
    - C. Implement an RDS for MySQL read replica to cache database calls.
    - D. Implement Amazon Kinesis Data Firehose to stream the calls to the database.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: B
      Explanation: Key term is identical datasets from the database it means caching can solve this issue by cached in frequently used dataset from DB.
    </details>

7. A solutions architect is creating a new VPC design. There are two public subnets for the load balancer, two private subnets for web servers, and two private subnets for MySQL. The web servers use only HTTPS. The solutions architect has already created a security group for the load balancer allowing port 443 from 0.0.0.0/0. Company policy requires that each resource has the least access required to still be able to perform its tasks. Which additional configuration strategy should the solutions architect use to meet these requirements?
    - A. Create a security group for the web servers and allow port 443 from 0.0.0.0/0. Create a security group for the MySQL servers and allow port 3306 from the web servers security group.
    - B. Create a network ACL for the web servers and allow port 443 from 0.0.0.0/0. Create a network ACL for the MySQL servers and allow port 3306 from the web servers security group.
    - C. Create a security group for the web servers and allow port 443 from the load balancer. Create a security group for the MySQL servers and allow port 3306 from the web servers security group.
    - D. Create a network ACL for the web servers and allow port 443 from the load balancer. Create a network ACL for the MySQL servers and allow port 3306 from the web servers security group.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: C
      Explanation: Load balancer is public facing accepting all traffic coming towards the VPC (0.0.0.0/0). The web server needs to trust traffic originating from the ALB. The DB will only trust traffic originating from the Web server on port 3306 for Mysql.
    </details>

8. A company recently deployed a new auditing system to centralize information about operating system versions patching and installed software for Amazon EC2 instances. A solutions architect must ensure all instances provisioned through EC2 Auto Scaling groups successfully send reports to the auditing system as soon as they are launched and terminated. Which solution achieves these goals MOST efficiently?
    - A. Use a scheduled AWS Lambda function and run a script remotely on all EC2 instances to send data to the audit system.
    - B. Use EC2 Auto Scaling lifecycle hooks to run a custom script to send data to the audit system when instances are launched and terminated.
    - C. Use an EC2 Auto Scaling launch configuration to run a custom script through user data to send data to the audit system when instances are launched and terminated.
    - D. Run a custom script on the instance operating system to send data to the audit system. Configure the script to be invoked by the EC2 Auto Scaling group when the instance starts and is terminated.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: B
      Explanation: Amazon EC2 Auto Scaling offers the ability to add lifecycle hooks to your Auto Scaling groups. These hooks let you create solutions that are aware of events in the Auto Scaling instance lifecycle, and then perform a custom action on instances when the corresponding lifecycle event occurs. https://docs.aws.amazon.com/autoscaling/ec2/userguide/lifecycle-hooks.html
    </details>

9. A company has launched an Amazon RDS for MySQL DB instance. Most of the connections to the database come from serverless applications. Application traffic to the database changes significantly at random intervals. At limes of high demand, users report that their applications experience database connection rejection errors. Which solution will resolve this issue with the LEAST operational overhead?
    - A. Create a proxy in RDS Proxy. Configure the users' applications to use the DB instance through RDS Proxy.
    - B. Deploy Amazon ElastCache for Memcached between the users' application and the DB instance.
    - C. Migrate the DB instance to a different instance class that has higher I/O capacity. Configure the users' applications to use the new DB instance.
    - D. Configure Multi-AZ for the DB instance. Configure the users' application to switch between the DB instances.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: A
      Explanation: Many applications, including those built on modern serverless architectures, can have a large number of open connections to the database server and may open and close database connections at a high rate, exhausting database memory and compute resources. Amazon RDS Proxy allows applications to pool and share connections established with the database, improving database efficiency and application scalability. https://aws.amazon.com/pt/rds/proxy/
    </details>

10. A company has deployed a serverless application that invokes an AWS Lambda function when new documents are uploaded to an Amazon S3 bucket. The application uses the Lambda function to process the documents. After a recent marketing campaign, the company noticed that the application did not process many of the documents. What should a solutions architect do to improve the architecture of this application?
    - A. Set the Lambda function's runtime timeout value to 15 minutes.
    - B. Configure an S3 bucket replication policy. Stage the documents m the S3 bucket for later processing.
    - C. Deploy an additional Lambda function Load balance the processing of the documents across the two Lambda functions.
    - D. Create an Amazon Simple Queue Service (Amazon SOS) queue. Send the requests to the queue. Configure the queue as an event source for Lambda.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: D
      Explanation: To improve the architecture of this application, the best solution would be to use Amazon Simple Queue Service (Amazon SQS) to buffer the requests and decouple the S3 bucket from the Lambda function. This will ensure that the documents are not lost and can be processed at a later time if the Lambda function is not available. This will ensure that the documents are not lost and can be processed at a later time if the Lambda function is not available. By using Amazon SQS, the architecture is decoupled and the Lambda function can process the documents in a scalable and fault-tolerant manner.
    </details>

11. A developer has an application that uses an AWS Lambda function to upload files to Amazon S3 and needs the required permissions to perform the task. The developer already has an IAM user with valid IAM credentials required for Amazon S3. What should a solutions architect do to grant the permissions?
    - A. Add required IAM permissions in the resource policy of the Lambda function.
    - B. Create a signed request using the existing IAM credentials in the Lambda function
    - C. Create a new IAM user and use the existing IAM credentials in the Lambda function.
    - D. Create an IAM execution role with the required permissions and attach the IAM rote to the Lambda function.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: D
      Explanation: To grant the necessary permissions to an AWS Lambda function to upload files to Amazon S3, a solutions architect should create an IAM execution role with the required permissions and attach the IAM role to the Lambda function. This approach follows the principle of least privilege and ensures that the Lambda function can only access the resources it needs to perform its specific task.
    </details>

12. A meteorological startup company has a custom web application to sell weather data to its users online. The company uses Amazon DynamoDB to store is data and wants to build a new service that sends an alert to the managers of four Internal teams every time a new weather event is recorded. The company does not want true new service to affect the performance of the current application. What should a solutions architect do to meet these requirement with the LEAST amount of operational overhead?
    - A. Use DynamoDB transactions to write new event data to the table. Configure the transactions to notify internal teams.
    - B. Have the current application publish a message to four Amazon Simple Notification Service (Amazon SNS) topics. Have each team subscribe to one topic.
    - C. Enable Amazon DynamoDB Streams on the table. Use triggers to write to a mingle Amazon Simple Notification Service (Amazon SNS) topic to which the teams can subscribe.
    - D. Add a custom attribute to each record to flag new items. Write a cron job that scans the table every minute for items that are new and notifies an Amazon Simple Queue Service (Amazon SOS) queue to which the teams can subscribe.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: C
      Explanation: The best solution to meet these requirements with the least amount of operational overhead is to enable Amazon DynamoDB Streams on the table and use triggers to write to a single Amazon Simple Notification Service (Amazon SNS) topic to which the teams can subscribe. This solution requires minimal configuration and infrastructure setup, and Amazon DynamoDB Streams provide a low-latency way to capture changes to the DynamoDB table. The triggers automatically capture the changes and publish them to the SNS topic, which notifies the internal teams.
    </details>

13. A company is developing a real-time multiplayer game that uses UDP for communications between the client and servers. In an Auto Scaling group Spikes in demand are anticipated during the day, so the game server platform must adapt accordingly. Developers want to store gamer scores and other non-relational data in a database solution that will scale without intervention. Which solution should a solutions architect recommend?
    - A. Use Amazon Route 53 for traffic distribution and Amazon Aurora Serverless for data storage.
    - B. Use a Network Load Balancer for traffic distribution and Amazon DynamoDB on-demand for data storage.
    - C. Use a Network Load Balancer for traffic distribution and Amazon Aurora Global Database for data storage.
    - D. Use an Application Load Balancer for traffic distribution and Amazon DynamoDB global tables for data storage.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: B
      Explanation: A Network Load Balancer can handle UDP traffic, and Amazon DynamoDB on-demand can provide automatic scaling without intervention.
    </details>

14. A company has a web application with sporadic usage patterns. There is heavy usage at the beginning of each month moderate usage at the start of each week and unpredictable usage during the week. The application consists of a web server and a MySQL database server running inside the data center. The company would like to move the application to the AWS Cloud and needs to select a cost-effective database platform that will not require database modifications. Which solution will meet these requirements?
    - A. Amazon DynamoDB
    - B. Amazon RDS for MySQL
    - C. MySQL-compatible Amazon Aurora Serverless
    - D. MySQL deployed on Amazon EC2 in an Auto Scaling group

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: C
      Explanation: Amazon RDS for MySQL is a fully-managed relational database service that makes it easy to set up, operate, and scale MySQL deployments in the cloud. Amazon Aurora Serverless is an on- demand, auto-scaling configuration for Amazon Aurora (MySQL-compatible edition), where the database will automatically start up, shut down, and scale capacity up or down based on your application’s needs. It is a simple, cost-effective option for infrequent, intermittent, or unpredictable workloads.
    </details>

15. An IAM user made several configuration changes to AWS resources in their company's account during a production deployment last week. A solutions architect learned that a couple of security group rules are not configured as desired. The solutions architect wants to confirm which IAM user was responsible for making changes. Which service should the solutions architect use to find the desired information?
    - A. Amazon GuardDuty
    - B. Amazon Inspector
    - C. AWS CloudTrail
    - D. AWS Config

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: C
      Explanation: The best option is to use AWS CloudTrail to find the desired information. AWS CloudTrail is a service that enables governance, compliance, operational auditing, and risk auditing of AWS account activities. CloudTrail can be used to log all changes made to resources in an AWS account, including changes made by IAM users, EC2 instances, AWS management console, and other AWS services. By using CloudTrail, the solutions architect can identify the IAM user who made the configuration changes to the security group rules.
    </details>

16. A company runs a public three-Tier web application in a VPC. The application runs on Amazon EC2 instances across multiple Availability Zones. The EC2 instances that run in private subnets need to communicate with a license server over the internet. The company needs a managed solution that minimizes operational maintenance. Which solution meets these requirements?
    - A. Provision a NAT instance in a public subnet. Modify each private subnets route table with a default route that points to the NAT instance.
    - B. Provision a NAT instance in a private subnet. Modify each private subnet's route table with a default route that points to the NAT instance.
    - C. Provision a NAT gateway in a public subnet. Modify each private subnet's route table with a default route that points to the NAT gateway.
    - D. Provision a NAT gateway in a private subnet. Modify each private subnet's route table with a default route that points to the NAT gateway.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: C
      Explanation: As the company needs a managed solution that minimizes operational maintenance - NAT Gateway is a public subnet is the answer.
    </details>

17. A company needs to transfer 600 TB of data from its on-premises network-attached storage (NAS) system to the AWS Cloud. The data transfer must be complete within 2 weeks. The data is sensitive and must be encrypted in transit. The company's internet connection can support an upload speed of 100 Mbps. Which solution meets these requirements MOST cost-effectively?
    - A. Use Amazon S3 multi-part upload functionality to transfer the fees over HTTPS.
    - B. Create a VPN connection between the on-premises NAS system and the nearest AWS Region. Transfer the data over the VPN connection.
    - C. Use the AWS Snow Family console to order several AWS Snowball Edge Storage Optimized devices. Use the devices to transfer the data to Amazon S3.
    - D. Set up a 10 Gbps AWS Direct Connect connection between the company location and the nearest AWS Region. Transfer the data over a VPN connection into the Region to store the data in Amazon S3.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: C
      Explanation: The best option is to use the AWS Snow Family console to order several AWS Snowball Edge Storage Optimized devices and use the devices to transfer the data to Amazon S3. Snowball Edge is a petabyte-scale data transfer device that can help transfer large amounts of data securely and quickly. Using Snowball Edge can be the most cost-effective solution for transferring large amounts of data over long distances and can help meet the requirement of transferring 600 TB of data within two weeks.
    </details>

18. A company needs a backup strategy for its three-tier stateless web application. The web application runs on Amazon EC2 instances in an Auto Scaling group with a dynamic scaling policy that is configured to respond to scaling events. The database tier runs on Amazon RDS for PostgreSQL. The web application does not require temporary local storage on the EC2 instances. The company’s recovery point objective (RPO) is 2 hours. The backup strategy must maximize scalability and optimize resource utilization for this environment. Which solution will meet these requirements?
    - A. Take snapshots of Amazon Elastic Block Store (Amazon EBS) volumes of the EC2 instances and database every 2 hours to meet the RPO.
    - B. Configure a snapshot lifecycle policy to take Amazon Elastic Block Store (Amazon EBS) snapshots. Enable automated backups in Amazon RDS to meet the RPO.
    - C. Retain the latest Amazon Machine Images (AMIs) of the web and application tiers. Enable automated backups in Amazon RDS and use point-in-time recovery to meet the RPO.
    - D. Take snapshots of Amazon Elastic Block Store (Amazon EBS) volumes of the EC2 instances every 2 hours. Enable automated backups in Amazon RDS and use point-in-time recovery to meet the RPO.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: C
      Explanation: The web application does not require temporary local storage on the EC2 instances => No EBS snapshot is required, retaining the latest AMI is enough.
    </details>

19. A company needs to ingest and handle large amounts of streaming data that its application generates. The application runs on Amazon EC2 instances and sends data to Amazon Kinesis Data Streams, which is configured with default settings. Every other day, the application consumes the data and writes the data to an Amazon S3 bucket for business intelligence (BI) processing. The company observes that Amazon S3 is not receiving all the data that the application sends to Kinesis Data Streams. What should a solutions architect do to resolve this issue?
    - A. Update the Kinesis Data Streams default settings by modifying the data retention period.
    - B. Update the application to use the Kinesis Producer Library (KPL) lo send the data to Kinesis Data Streams.
    - C. Update the number of Kinesis shards lo handle the throughput of me data that is sent to Kinesis Data Streams.
    - D. Turn on S3 Versioning within the S3 bucket to preserve every version of every object that is ingested in the S3 bucket.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: A
      Explanation: https://docs.aws.amazon.com/streams/latest/dev/kinesis-extended-retention.html The question mentioned Kinesis data stream default settings and "every other day". After 24hrs, the data isn't in the Data stream if the default settings is not modified to store data more than 24hrs.
    </details>

20. A company has migrated an application to Amazon EC2 Linux instances. One of these EC2 instances runs several 1-hour tasks on a schedule. These tasks were written by different teams and have no common programming language. The company is concerned about performance and scalability while these tasks run on a single instance. A solutions architect needs to implement a solution to resolve these concerns. Which solution will meet these requirements with the LEAST operational overhead?
    - A. Use AWS Batch to run the tasks as jobs. Schedule the jobs by using Amazon EventBridge (Amazon CloudWatch Events).
    - B. Convert the EC2 instance to a container. Use AWS App Runner to create the container on demand to run the tasks as jobs.
    - C. Copy the tasks into AWS Lambda functions. Schedule the Lambda functions by using Amazon EventBridge (Amazon CloudWatch Events).
    - D. Create an Amazon Machine Image (AMI) of the EC2 instance that runs the tasks. Create an Auto Scaling group with the AMI to run multiple copies of the instance.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: A
      Explanation: Lambda functions are short lived; the Lambda max timeout is 900 seconds (15 minutes). This can be difficult to manage and can cause issues in production applications. We'll take a look at AWS Lambda timeout limits, timeout errors, monitoring timeout errors, and how to apply best practices to handle them effectively.
    </details>

21. A company has implemented a self-managed DNS service on AWS. The solution consists of the following: - Amazon EC2 instances in different AWS Regions - Endpoints of a standard accelerator in AWS Global Accelerator The company wants to protect the solution against DDoS attacks. What should a solutions architect do to meet this requirement?
    - A. Subscribe to AWS Shield Advanced. Add the accelerator as a resource to protect.
    - B. Subscribe to AWS Shield Advanced. Add the EC2 instances as resources to protect.
    - C. Create an AWS WAF web ACL that includes a rate-based rule. Associate the web ACL with the accelerator.
    - D. Create an AWS WAF web ACL that includes a rate-based rule. Associate the web ACL with the EC2 instances.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: A
      Explanation: AWS Shield is a managed service that provides protection against Distributed Denial of Service (DDoS) attacks for applications running on AWS. AWS Shield Standard is automatically enabled to all AWS customers at no additional cost. AWS Shield Advanced is an optional paid service. AWS Shield Advanced provides additional protections against more sophisticated and larger attacks for
      your applications running on Amazon Elastic Compute Cloud (EC2), Elastic Load Balancing (ELB), Amazon CloudFront, AWS Global Accelerator, and Route 53.
    </details>

22. A company is migrating an old application to AWS. The application runs a batch job every hour and is CPU intensive. The batch job takes 15 minutes on average with an on-premises server. The server has 64 virtual CPU (vCPU) and 512 GiB of memory. Which solution will run the batch job within 15 minutes with the LEAST operational overhead?
    - A. Use AWS Lambda with functional scaling
    - B. Use Amazon Elastic Container Service (Amazon ECS) with AWS Fargate
    - C. Use Amazon Lightsail with AWS Auto Scaling
    - D. Use AWS Batch on Amazon EC2

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: D
      Explanation: Use AWS Batch on Amazon EC2. AWS Batch is a fully managed batch processing service that can be used to easily run batch jobs on Amazon EC2 instances. It can scale the number of instances to match the workload, allowing the batch job to be completed in the desired time frame with minimal operational overhead.
    </details>

23. A company hosts a frontend application that uses an Amazon API Gateway API backend that is integrated with AWS Lambda. When the API receives requests, the Lambda function loads many
libraries. Then the Lambda function connects to an Amazon RDS database, processes the data, and returns the data to the frontend application. The company wants to ensure that response latency is as low as possible for all its users with the fewest number of changes to the company's operations. Which solution will meet these requirements?
    - A. Establish a connection between the frontend application and the database to make queries faster by bypassing the API.
    - B. Configure provisioned concurrency for the Lambda function that handles the requests.
    - C. Cache the results of the queries in Amazon S3 for faster retrieval of similar datasets.
    - D. Increase the size of the database to increase the number of connections Lambda can establish at one time.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: B
      Explanation: Configure provisioned concurrency for the Lambda function that handles the requests. Provisioned concurrency allows you to set the amount of compute resources that are available to the Lambda function, so that it can handle more requests at once and reduce latency. Caching the results of the queries in Amazon S3 could also help to reduce latency, but it would not be as effective as setting up provisioned concurrency. Increasing the size of the database would not help to reduce latency, as this would not increase the number of connections the Lambda function could establish, and establishing a direct connection between the frontend application and the database would bypass the API, which would not be the best solution either.
    </details>

24. An ecommerce company is running a multi-tier application on AWS. The front-end and backend tiers both run on Amazon EC2, and the database runs on Amazon RDS for MySQL. The backend tier communicates with the RDS instance. There are frequent calls to return identical datasets from the database that are causing performance slowdowns. Which action should be taken to improve the performance of the backend?
    - A. Implement Amazon SNS to store the database calls.
    - B. Implement Amazon ElastiCache to cache the large datasets.
    - C. Implement an RDS for MySQL read replica to cache database calls.
    - D. Implement Amazon Kinesis Data Firehose to stream the calls to the database.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: B
      Explanation: Key term is identical datasets from the database it means caching can solve this issue by cached in frequently used dataset from DB.
    </details>

25. A company has a business system that generates hundreds of reports each day. The business system saves the reports to a network share in CSV format. The company needs to store this data in the AWS Cloud in near-real time for analysis. Which solution will meet these requirements with the LEAST administrative overhead?
    - A. Use AWS DataSync to transfer the files to Amazon S3. Create a scheduled task that runs at the end of each day.
    - B. Create an Amazon S3 File Gateway. Update the business system to use a new network share from the S3 File Gateway.
    - C. Use AWS DataSync to transfer the files to Amazon S3. Create an application that uses the DataSync API in the automation workflow.
    - D. Deploy an AWS Transfer for SFTP endpoint. Create a script that checks for new files on the network share and uploads the new files by using SFTP.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: B
      Explanation: https://aws.amazon.com/storagegateway/file/?nc1=h_ls
    </details>

26. A company is storing petabytes of data in Amazon S3 Standard. The data is stored in multiple S3 buckets and is accessed with varying frequency. The company does not know access patterns for all the data. The company needs to implement a solution for each S3 bucket to optimize the cost of S3 usage. Which solution will meet these requirements with the MOST operational efficiency?
    - A. Create an S3 Lifecycle configuration with a rule to transition the objects in the S3 bucket to S3 Intelligent-Tiering.
    - B. Use the S3 storage class analysis tool to determine the correct tier for each object in the S3 bucket. Move each object to the identified storage tier.
    - C. Create an S3 Lifecycle configuration with a rule to transition the objects in the S3 bucket to S3 Glacier Instant Retrieval.
    - D. Create an S3 Lifecycle configuration with a rule to transition the objects in the S3 bucket to S3 One Zone-Infrequent Access (S3 One Zone-IA).

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: A
      Explanation: https://aws.amazon.com/s3/storage-classes/intelligent-tiering/
    </details>

27. A solutions architect needs to allow team members to access Amazon S3 buckets in two different AWS accounts: a development account and a production account. The team currently has access to S3 buckets in the development account by using unique IAM users that are assigned to an IAM group that has appropriate permissions in the account. The solutions architect has created an IAM role in the production account. The role has a policy that grants access to an S3 bucket in the production account. Which solution will meet these requirements while complying with the principle of least privilege?
    - A. Attach the Administrator Access policy to the development account users.
    - B. Add the development account as a principal in the trust policy of the role in the production account.
    - C. Turn off the S3 Block Public Access feature on the S3 bucket in the production account.
    - D. Create a user in the production account with unique credentials for each team member.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: B
      Explanation: By adding the development account as a principal in the trust policy of the IAM role in the production account, you are allowing users from the development account to assume the role in the production account. This allows the team members to access the S3 bucket in the production account without granting them unnecessary privileges.
    </details>

28. A company wants to use an Amazon RDS for PostgreSQL DB cluster to simplify time-consuming database administrative tasks for production database workloads. The company wants to ensure that its database is highly available and will provide automatic failover support in most scenarios in less than 40 seconds. The company wants to offload reads off of the primary instance and keep costs as low as possible. Which solution will meet these requirements?
    - A. Use an Amazon RDS Multi-AZ DB instance deployment. Create one read replica and point the read workload to the read replica.
    - B. Use an Amazon RDS Multi-AZ DB duster deployment Create two read replicas and point the read workload to the read replicas.
    - C. Use an Amazon RDS Multi-AZ DB instance deployment. Point the read workload to the secondary instances in the Multi-AZ pair.
    - D. Use an Amazon RDS Multi-AZ DB cluster deployment Point the read workload to the reader
endpoint.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: D
      Explanation: https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/Concepts.MultiAZSingleStandby.ht ml
    </details>

29. A company runs a highly available SFTP service. The SFTP service uses two Amazon EC2 Linux instances that run with elastic IP addresses to accept traffic from trusted IP sources on the internet. The SFTP service is backed by shared storage that is attached to the instances. User accounts are created and managed as Linux users in the SFTP servers. The company wants a serverless option that provides high IOPS performance and highly configurable security. The company also wants to maintain control over user permissions. Which solution will meet these requirements?
    - A. Create an encrypted Amazon Elastic Block Store (Amazon EBS) volume. Create an AWS Transfer Family SFTP service with a public endpoint that allows only trusted IP addresses. Attach the EBS volume to the SFTP service endpoint. Grant users access to the SFTP service.
    - B. Create an encrypted Amazon Elastic File System (Amazon EFS) volume. Create an AWS Transfer Family SFTP service with elastic IP addresses and a VPC endpoint that has internet-facing access. Attach a security group to the endpoint that allows only trusted IP addresses. Attach the EFS volume to the SFTP service endpoint. Grant users access to the SFTP service.
    - C. Create an Amazon S3 bucket with default encryption enabled. Create an AWS Transfer Family SFTP service with a public endpoint that allows only trusted IP addresses. Attach the S3 bucket to the SFTP service endpoint. Grant users access to the SFTP service.
    - D. Create an Amazon S3 bucket with default encryption enabled. Create an AWS Transfer Family SFTP service with a VPC endpoint that has internal access in a private subnet. Attach a security group that allows only trusted IP addresses. Attach the S3 bucket to the SFTP service endpoint. Grant users access to the SFTP service.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: B
      Explanation: https://aws.amazon.com/blogs/storage/use-ip-whitelisting-to-secure-your-aws-transfer-for-sftp- servers/
    </details>

30. A company is developing a new machine learning (ML) model solution on AWS. The models are developed as independent microservices that fetch approximately 1 GB of model data from Amazon S3 at startup and load the data into memory. Users access the models through an asynchronous API. Users can send a request or a batch of requests and specify where the results should be sent. The company provides models to hundreds of users. The usage patterns for the models are irregular. Some models could be unused for days or weeks. Other models could receive batches of thousands of requests at a time. Which design should a solutions architect recommend to meet these requirements?
    - A. Direct the requests from the API to a Network Load Balancer (NLB). Deploy the models as AWS Lambda functions that are invoked by the NLB. - B. Direct the requests from the API to an Application Load Balancer (ALB). Deploy the models as Amazon Elastic Container Service (Amazon ECS) services that read from an Amazon Simple Queue Service (Amazon SQS) queue. Use AWS App Mesh to scale the instances of the ECS cluster based on the SQS queue size.
    - C. Direct the requests from the API into an Amazon Simple Queue Service (Amazon SQS) queue. Deploy the models as AWS Lambda functions that are invoked by SQS events. Use AWS Auto Scaling to increase the number of vCPUs for the Lambda functions based on the SQS queue size.
    - D. Direct the requests from the API into an Amazon Simple Queue Service (Amazon SQS) queue. Deploy the models as Amazon Elastic Container Service (Amazon ECS) services that read from the queue. Enable AWS Auto Scaling on Amazon ECS for both the cluster and copies of the service based on the queue size.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: D
      Explanation: https://aws.amazon.com/blogs/containers/amazon-elastic-container-service-ecs-auto-scaling- using-custom-metrics/
    </details>

31. A company uses high block storage capacity to runs its workloads on premises. The company's daily peak input and output transactions per second are not more than 15,000 IOPS. The company wants to migrate the workloads to Amazon EC2 and to provision disk performance independent of storage capacity. Which Amazon Elastic Block Store (Amazon EBS) volume type will meet these requirements MOST cost-effectively?
    - A. GP2 volume type
    - B. io2 volume type
    - C. GP3 volume type
    - D. io1 volume type

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: C
      Explanation: Both GP2 and GP3 has max IOPS 16000 but GP3 is cost effective. https://aws.amazon.com/blogs/storage/migrate-your-amazon-ebs-volumes-from-gp2-to-gp3-and- save-up-to-20-on-costs/
    </details>

32. A company needs to store data from its healthcare application. The application's data frequently changes. A new regulation requires audit access at all levels of the stored data. The company hosts the application on an on-premises infrastructure that is running out of storage capacity. A solutions architect must securely migrate the existing data to AWS while satisfying the new regulation. Which solution will meet these requirements?
    - A. Use AWS DataSync to move the existing data to Amazon S3. Use AWS CloudTrail to log data events.
    - B. Use AWS Snowcone to move the existing data to Amazon S3. Use AWS CloudTrail to log management events.
    - C. Use Amazon S3 Transfer Acceleration to move the existing data to Amazon S3. Use AWS CloudTrail to log data events.
    - D. Use AWS Storage Gateway to move the existing data to Amazon S3. Use AWS CloudTrail to log management events.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: A
      Explanation: https://docs.aws.amazon.com/ja_jp/datasync/latest/userguide/encryption-in-transit.html
    </details>

33. A solutions architect is implementing a complex Java application with a MySQL database. The Java application must be deployed on Apache Tomcat and must be highly available. What should the solutions architect do to meet these requirements?
    - A. Deploy the application in AWS Lambda. Configure an Amazon API Gateway API to connect with the Lambda functions.
    - B. Deploy the application by using AWS Elastic Beanstalk. Configure a load-balanced environment and a rolling deployment policy.
    - C. Migrate the database to Amazon ElastiCache. Configure the ElastiCache security group to allow access from the application.
    - D. Launch an Amazon EC2 instance. Install a MySQL server on the EC2 instance. Configure the application on the server. Create an AMI. Use the AMI to create a launch template with an Auto Scaling group.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: B
      Explanation: AWS Elastic Beanstalk provides an easy and quick way to deploy, manage, and scale applications. It supports a variety of platforms, including Java and Apache Tomcat. By using Elastic Beanstalk, the solutions architect can upload the Java application and configure the environment to run Apache Tomcat.
    </details>

34. A serverless application uses Amazon API Gateway, AWS Lambda, and Amazon DynamoDB. The Lambda function needs permissions to read and write to the DynamoDB table. Which solution will give the Lambda function access to the DynamoDB table MOST securely?
    - A. Create an IAM user with programmatic access to the Lambda function. Attach a policy to the user that allows read and write access to the DynamoDB table. Store the access_key_id and secret_access_key parameters as part of the Lambda environment variables. Ensure that other AWS users do not have read and write access to the Lambda function configuration.
    - B. Create an IAM role that includes Lambda as a trusted service. Attach a policy to the role that allows read and write access to the DynamoDB table. Update the configuration of the Lambda function to use the new role as the execution role.
    - C. Create an IAM user with programmatic access to the Lambda function. Attach a policy to the user that allows read and write access to the DynamoDB table. Store the access_key_id and secret_access_key parameters in AWS Systems Manager Parameter Store as secure string parameters. Update the Lambda function code to retrieve the secure string parameters before connecting to the DynamoDB table.
    - D. Create an IAM role that includes DynamoDB as a trusted service. Attach a policy to the role that allows read and write access from the Lambda function. Update the code of the Lambda function to attach to the new role as an execution role.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: B
      Explanation: Option B suggests creating an IAM role that includes Lambda as a trusted service, meaning the role is specifically designed for Lambda functions. The role should have a policy attached to it that grants the required read and write access to the DynamoDB table.
    </details>

35. A company has developed a new video game as a web application. The application is in a three- tier architecture in a VPC with Amazon RDS for MySQL in the database layer. Several players will compete concurrently online. The game's developers want to display a top-10 scoreboard in near- real time and offer the ability to stop and restore the game while preserving the current scores. What should a solutions architect do to meet these requirements?
    - A. Set up an Amazon ElastiCache for Memcached cluster to cache the scores for the web application to display.
    - B. Set up an Amazon ElastiCache for Redis cluster to compute and cache the scores for the web application to display.
    - C. Place an Amazon CloudFront distribution in front of the web application to cache the scoreboard in a section of the application.
    - D. Create a read replica on Amazon RDS for MySQL to run queries to compute the scoreboard and serve the read traffic to the web application.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: B
      Explanation: https://aws.amazon.com/jp/blogs/news/building-a-real-time-gaming-leaderboard-with-amazon- elasticache-for-redis/
    </details>

36. An ecommerce company wants to use machine learning (ML) algorithms to build and train models. The company will use the models to visualize complex scenarios and to detect trends in customer data. The architecture team wants to integrate its ML models with a reporting platform to analyze the augmented data and use the data directly in its business intelligence dashboards. Which solution will meet these requirements with the LEAST operational overhead?
    - A. Use AWS Glue to create an ML transform to build and train models. Use Amazon OpenSearch Service to visualize the data.
    - B. Use Amazon SageMaker to build and train models. Use Amazon QuickSight to visualize the data.
    - C. Use a pre-built ML Amazon Machine Image (AMI) from the AWS Marketplace to build and train models. Use Amazon OpenSearch Service to visualize the data.
    - D. Use Amazon QuickSight to build and train models by using calculated fields. Use Amazon QuickSight to visualize the data.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: B
      Explanation: Amazon SageMaker is a fully managed service that provides a complete set of tools and capabilities for building, training, and deploying ML models. It simplifies the end-to-end ML workflow and reduces operational overhead by handling infrastructure provisioning, model training, and deployment. To visualize the data and integrate it into business intelligence dashboards, Amazon QuickSight can be used. QuickSight is a cloud-native business intelligence service that allows users to easily create interactive visualizations, reports, and dashboards from various data sources, including the augmented data generated by the ML models.
    </details>

37. A company is running its production and nonproduction environment workloads in multiple AWS accounts. The accounts are in an organization in AWS Organizations. The company needs to design a solution that will prevent the modification of cost usage tags. Which solution will meet these requirements?
    - A. Create a custom AWS Config rule to prevent tag modification except by authorized principals.
    - B. Create a custom trail in AWS CloudTrail to prevent tag modification.
    - C. Create a service control policy (SCP) to prevent tag modification except by authorized principals.
    - D. Create custom Amazon CloudWatch logs to prevent tag modification.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: C
      Explanation: https://docs.aws.amazon.com/ja_jp/organizations/latest/userguide/orgs_manage_policies_scps_e xamples_tagging.html
    </details>

38. A company needs to migrate a MySQL database from its on-premises data center to AWS within 2 weeks. The database is 20 TB in size. The company wants to complete the migration with minimal downtime. Which solution will migrate the database MOST cost-effectively?
    - A. Order an AWS Snowball Edge Storage Optimized device. Use AWS Database Migration Service (AWS DMS) with AWS Schema Conversion Tool (AWS SCT) to migrate the database with replication of ongoing changes. Send the Snowball Edge device to AWS to finish the migration and continue the ongoing replication.
    - B. Order an AWS Snowmobile vehicle. Use AWS Database Migration Service (AWS DMS) with AWS Schema Conversion Tool (AWS SCT) to migrate the database with ongoing changes. Send the Snowmobile vehicle back to AWS to finish the migration and continue the ongoing replication.
    - C. Order an AWS Snowball Edge Compute Optimized with GPU device. Use AWS Database Migration Service (AWS DMS) with AWS Schema Conversion Tool (AWS SCT) to migrate the database with ongoing changes. Send the Snowball device to AWS to finish the migration and continue the ongoing replication
    - D. Order a 1 GB dedicated AWS Direct Connect connection to establish a connection with the data center. Use AWS Database Migration Service (AWS DMS) with AWS Schema Conversion Tool (AWS SCT) to migrate the database with replication of ongoing changes.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: A
      Explanation: https://docs.aws.amazon.com/dms/latest/userguide/CHAP_LargeDBs.Process.html
    </details>

39. A company moved its on-premises PostgreSQL database to an Amazon RDS for PostgreSQL DB instance. The company successfully launched a new product. The workload on the database has increased. The company wants to accommodate the larger workload without adding infrastructure. Which solution will meet these requirements MOST cost-effectively?
    - A. Buy reserved DB instances for the total workload. Make the Amazon RDS for PostgreSQL DB instance larger.
    - B. Make the Amazon RDS for PostgreSQL DB instance a Multi-AZ DB instance.
    - C. Buy reserved DB instances for the total workload. Add another Amazon RDS for PostgreSQL DB
instance.
    - D. Make the Amazon RDS for PostgreSQL DB instance an on-demand DB instance.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: A
      Explanation: "without adding infrastructure" means scaling vertically and choosing larger instance. "MOST cost-effectively" reserved instances
    </details>

40. A company operates an ecommerce website on Amazon EC2 instances behind an Application Load Balancer (ALB) in an Auto Scaling group. The site is experiencing performance issues related to a high request rate from illegitimate external systems with changing IP addresses. The security team is worried about potential DDoS attacks against the website. The company must block the illegitimate incoming requests in a way that has a minimal impact on legitimate users. What should a solutions architect recommend?
    - A. Deploy Amazon Inspector and associate it with the ALB. - B. Deploy AWS WAF, associate it with the ALB, and configure a rate-limiting rule.
    - C. Deploy rules to the network ACLs associated with the ALB to block the incomingtraffic.
    - D. Deploy Amazon GuardDuty and enable rate-limiting protection when configuring GuardDuty.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: B
      Explanation: AWS WAF (Web Application Firewall) is a service that provides protection for web applications against common web exploits. By associating AWS WAF with the Application Load Balancer (ALB), you can inspect incoming traffic and define rules to allow or block requests based on various criteria.
    </details>

41. A company wants to share accounting data with an external auditor. The data is stored in an Amazon RDS DB instance that resides in a private subnet. The auditor has its own AWS account and requires its own copy of the database. What is the MOST secure way for the company to share the database with the auditor?
    - A. Create a read replica of the database. Configure IAM standard database authentication to grant the auditor access.
    - B. Export the database contents to text files. Store the files in an Amazon S3 bucket. Create a new IAM user for the auditor. Grant the user access to the S3 bucket.
    - C. Copy a snapshot of the database to an Amazon S3 bucket. Create an IAM user. Share the user's keys with the auditor to grant access to the object in the S3 bucket.
    - D. Create an encrypted snapshot of the database. Share the snapshot with the auditor. Allow access to the AWS Key Management Service (AWS KMS) encryption key.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: D
      Explanation: The most secure way for the company to share the database with the auditor is option D: Create an encrypted snapshot of the database, share the snapshot with the auditor, and allow access to the AWS Key Management Service (AWS KMS) encryption key. By creating an encrypted snapshot, the company ensures that the database data is protected at rest. Sharing the encrypted snapshot with the auditor allows them to have their own copy of the database securely.
      In addition, granting access to the AWS KMS encryption key ensures that the auditor has the necessary permissions to decrypt and access the encrypted snapshot. This allows the auditor to restore the snapshot and access the data securely. This approach provides both data protection and access control, ensuring that the database is securely shared with the auditor while maintaining the confidentiality and integrity of the data.
    </details>

42. A solutions architect configured a VPC that has a small range of IP addresses. The number of Amazon EC2 instances that are in the VPC is increasing, and there is an insufficient number of IP addresses for future workloads. Which solution resolves this issue with the LEAST operational overhead?
    - A. Add an additional IPv4 CIDR block to increase the number of IP addresses and create additional subnets in the VPC. Create new resources in the new subnets by using the new CIDR.
    - B. Create a second VPC with additional subnets. Use a peering connection to connect the second VPC with the first VPC Update the routes and create new resources in the subnets of the second VPC. - C. Use AWS Transit Gateway to add a transit gateway and connect a second VPC with the first VPUpdate the routes of the transit gateway and VPCs. Create new resources in the subnets of the second VPC. - D. Create a second VPC. Create a Site-to-Site VPN connection between the first VPC and the second VPC by using a VPN-hosted solution on Amazon EC2 and a virtual private gateway. Update the route between VPCs to the traffic through the VPN. Create new resources in the subnets of the second VPC. 

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: A
      Explanation: You assign a single CIDR IP address range as the primary CIDR block when you create a VPC and can add up to four secondary CIDR blocks after creation of the VPC.
    </details>

43. A company hosts a multi-tier web application on Amazon Linux Amazon EC2 instances behind an Application Load Balancer. The instances run in an Auto Scaling group across multiple Availability Zones. The company observes that the Auto Scaling group launches more On-Demand Instances when the application's end users access high volumes of static web content. The company wants to optimize cost. What should a solutions architect do to redesign the application MOST cost-effectively?
    - A. Update the Auto Scaling group to use Reserved Instances instead of On-Demand Instances.
    - B. Update the Auto Scaling group to scale by launching Spot Instances instead of On-Demand Instances.
    - C. Create an Amazon CloudFront distribution to host the static web contents from an Amazon S3 bucket.
    - D. Create an AWS Lambda function behind an Amazon API Gateway API to host the static website contents.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: C
      Explanation: By leveraging Amazon CloudFront, you can cache and serve the static web content from edge locations worldwide, reducing the load on your EC2 instances. This can help lower the number of On-Demand Instances required to handle high volumes of static web content requests. Storing the static content in an Amazon S3 bucket and using CloudFront as a content delivery network (CDN) improves performance and reduces costs by reducing the load on your EC2 instances.
    </details>

44. A company stores several petabytes of data across multiple AWS accounts. The company uses AWS Lake Formation to manage its data lake. The company's data science team wants to securely share selective data from its accounts with the company's engineering team for analytical purposes. Which solution will meet these requirements with the LEAST operational overhead?
    - A. Copy the required data to a common account. Create an IAM access role in that account. Grant access by specifying a permission policy that includes users from the engineering team accounts as trusted entities.
    - B. Use the Lake Formation permissions Grant command in each account where the data is stored to allow the required engineering team users to access the data.
    - C. Use AWS Data Exchange to privately publish the required data to the required engineering team accounts.
    - D. Use Lake Formation tag-based access control to authorize and grant cross-account permissions for the required data to the engineering team accounts.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: D
      Explanation: By utilizing Lake Formation's tag-based access control, you can define tags and tag-based policies to grant selective access to the required data for the engineering team accounts. This approach allows you to control access at a granular level without the need to copy or move the data to a common account or manage permissions individually in each account. It provides a centralized and scalable solution for securely sharing data across accounts with minimal operational overhead.
      https://aws.amazon.com/blogs/big-data/securely-share-your-data-across-aws-accounts-using- aws-lake-formation/
    </details>

45. A company wants to host a scalable web application on AWS. The application will be accessed by users from different geographic regions of the world. Application users will be able to download and upload unique data up to gigabytes in size. The development team wants a cost-effective solution to minimize upload and download latency and maximize performance. What should a solutions architect do to accomplish this?
    - A. Use Amazon S3 with Transfer Acceleration to host the application.
    - B. Use Amazon S3 with CacheControl headers to host the application.
    - C. Use Amazon EC2 with Auto Scaling and Amazon CloudFront to host the application.
    - D. Use Amazon EC2 with Auto Scaling and Amazon ElastiCache to host the application.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: A
      Explanation: https://docs.aws.amazon.com/ja_jp/AmazonS3/latest/userguide/transfer-acceleration.html
    </details>

46. A company has hired a solutions architect to design a reliable architecture for its application. The application consists of one Amazon RDS DB instance and two manually provisioned Amazon EC2 instances that run web servers. The EC2 instances are located in a single Availability Zone. An employee recently deleted the DB instance, and the application was unavailable for 24 hours as a result. The company is concerned with the overall reliability of its environment. What should the solutions architect do to maximize reliability of the application's infrastructure?
    - A. Delete one EC2 instance and enable termination protection on the other EC2 instance. Update the DB instance to be Multi-AZ, and enable deletion protection.
    - B. Update the DB instance to be Multi-AZ, and enable deletion protection. Place the EC2 instances behind an Application Load Balancer, and run them in an EC2 Auto Scaling group across multiple Availability Zones.
    - C. Create an additional DB instance along with an Amazon API Gateway and an AWS Lambda function. Configure the application to invoke the Lambda function through API Gateway. Have the Lambda function write the data to the two DB instances.
    - D. Place the EC2 instances in an EC2 Auto Scaling group that has multiple subnets located in multiple Availability Zones. Use Spot Instances instead of On-Demand Instances. Set up Amazon CloudWatch alarms to monitor the health of the instances Update the DB instance to be Multi-AZ, and enable deletion protection.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: B
      Explanation: Update the DB instance to be Multi-AZ, and enable deletion protection. Place the EC2 instances behind an Application Load Balancer, and run them in an EC2 Auto Scaling group across multiple Availability Zones.
    </details>

47. A company is storing 700 terabytes of data on a large network-attached storage (NAS) system in its corporate data center. The company has a hybrid environment with a 10 Gbps AWS Direct
Connect connection. After an audit from a regulator, the company has 90 days to move the data to the cloud. The company needs to move the data efficiently and without disruption. The company still needs to be able to access and update the data during the transfer window. Which solution will meet these requirements?
    - A. Create an AWS DataSync agent in the corporate data center. Create a data transfer task Start the transfer to an Amazon S3 bucket.
    - B. Back up the data to AWS Snowball Edge Storage Optimized devices. Ship the devices to an AWS data center. Mount a target Amazon S3 bucket on the on-premises file system.
    - C. Use rsync to copy the data directly from local storage to a designated Amazon S3 bucket over the Direct Connect connection.
    - D. Back up the data on tapes. Ship the tapes to an AWS data center. Mount a target Amazon S3 bucket on the on-premises file system.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: A
      Explanation: By leveraging AWS DataSync in combination with AWS Direct Connect, the company can efficiently and securely transfer its 700 terabytes of data to an Amazon S3 bucket without disruption. The solution allows continued access and updates to the data during the transfer window, ensuring business continuity throughout the migration process.
    </details>

48. A company stores data in PDF format in an Amazon S3 bucket. The company must follow a legal requirement to retain all new and existing data in Amazon S3 for 7 years. Which solution will meet these requirements with the LEAST operational overhead?
    - A. Turn on the S3 Versioning feature for the S3 bucket. Configure S3 Lifecycle to delete the data after 7 years. Configure multi-factor authentication (MFA) delete for all S3 objects.
    - B. Turn on S3 Object Lock with governance retention mode for the S3 bucket. Set the retention period to expire after 7 years. Recopy all existing objects to bring the existing data into compliance.
    - C. Turn on S3 Object Lock with compliance retention mode for the S3 bucket. Set the retention period to expire after 7 years. Recopy all existing objects to bring the existing data into compliance.
    - D. Turn on S3 Object Lock with compliance retention mode for the S3 bucket. Set the retention period to expire after 7 years. Use S3 Batch Operations to bring the existing data into compliance.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: D
      Explanation: To replicate existing object/data in S3 Bucket to bring them to compliance, optionally we use "S3 Batch Replication", so option D is the most appropriate, especially if we have big data in S3.
    </details>

49. A company has a stateless web application that runs on AWS Lambda functions that are invoked by Amazon API Gateway. The company wants to deploy the application across multiple AWS Regions to provide Regional failover capabilities. What should a solutions architect do to route traffic to multiple Regions?
    - A. Create Amazon Route 53 health checks for each Region. Use an active-active failover
configuration.
    - B. Create an Amazon CloudFront distribution with an origin for each Region. Use CloudFront health checks to route traffic.
    - C. Create a transit gateway. Attach the transit gateway to the API Gateway endpoint in each Region. Configure the transit gateway to route requests.
    - D. Create an Application Load Balancer in the primary Region. Set the target group to point to the API Gateway endpoint hostnames in each Region.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: A
      Explanation: https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/dns-failover.html
    </details>

50. A company has two VPCs named Management and Production. The Management VPC uses VPNs through a customer gateway to connect to a single device in the data center. The Production VPC uses a virtual private gateway with two attached AWS Direct Connect connections. The Management and Production VPCs both use a single VPC peering connection to allow communication between the applications. What should a solutions architect do to mitigate any single point of failure in this architecture?
    - A. Add a set of VPNs between the Management and Production VPCs.
    - B. Add a second virtual private gateway and attach it to the Management VPC. - C. Add a second set of VPNs to the Management VPC from a second customer gateway device.
    - D. Add a second VPC peering connection between the Management VPC and the Production VPC. 

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: C
      Explanation: Redundant VPN connections: Instead of relying on a single device in the data center, the Management VPC should have redundant VPN connections established through multiple customer gateways. This will ensure high availability and fault tolerance in case one of the VPN connections or customer gateways fails.
    </details>

51. A company runs its application on an Oracle database. The company plans to quickly migrate to AWS because of limited resources for the database, backup administration, and data center maintenance. The application uses third-party database features that require privileged access. Which solution will help the company migrate the database to AWS MOST cost-effectively?
    - A. Migrate the database to Amazon RDS for Oracle. Replace third-party features with cloud services.
    - B. Migrate the database to Amazon RDS Custom for Oracle. Customize the database settings to support third-party features.
    - C. Migrate the database to an Amazon EC2 Amazon Machine Image (AMI) for Oracle. Customize the database settings to support third-party features.
    - D. Migrate the database to Amazon RDS for PostgreSQL by rewriting the application code to remove dependency on Oracle APEX.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: B
      Explanation: https://aws.amazon.com/about-aws/whats-new/2021/10/amazon-rds-custom-oracle/
    </details>

52. A company runs a Java-based job on an Amazon EC2 instance. The job runs every hour and takes 10 seconds to run. The job runs on a scheduled interval and consumes 1 GB of memory. The CPU utilization of the instance is low except for short surges during which the job uses the maximum CPU available. The company wants to optimize the costs to run the job. Which solution will meet these requirements?
    - A. Use AWS App2Container (A2C) to containerize the job. Run the job as an Amazon Elastic
Container Service (Amazon ECS) task on AWS Fargate with 0.5 virtual CPU (vCPU) and 1 GB of memory.
    - B. Copy the code into an AWS Lambda function that has 1 GB of memory. Create an Amazon EventBridge scheduled rule to run the code each hour.
    - C. Use AWS App2Container (A2C) to containerize the job. Install the container in the existing Amazon Machine Image (AMI). Ensure that the schedule stops the container when the task finishes.
    - D. Configure the existing schedule to stop the EC2 instance at the completion of the job and restart the EC2 instance when the next job starts.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: B
      Explanation: https://docs.aws.amazon.com/lambda/latest/operatorguide/computing-power.html
    </details>

53. A company wants to implement a backup strategy for Amazon EC2 data and multiple Amazon S3 buckets. Because of regulatory requirements, the company must retain backup files for a specific time period. The company must not alter the files for the duration of the retention period. Which solution will meet these requirements?
    - A. Use AWS Backup to create a backup vault that has a vault lock in governance mode. Create the required backup plan.
    - B. Use Amazon Data Lifecycle Manager to create the required automated snapshot policy.
    - C. Use Amazon S3 File Gateway to create the backup. Configure the appropriate S3 Lifecycle management.
    - D. Use AWS Backup to create a backup vault that has a vault lock in compliance mode. Create the required backup plan.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: D
      Explanation: https://docs.aws.amazon.com/aws-backup/latest/devguide/vault-lock.html
    </details>

54. A company has resources across multiple AWS Regions and accounts. A newly hired solutions architect discovers a previous employee did not provide details about the resources inventory. The solutions architect needs to build and map the relationship details of the various workloads across all accounts. Which solution will meet these requirements in the MOST operationally efficient way?
    - A. Use AWS Systems Manager Inventory to generate a map view from the detailed view report.
    - B. Use AWS Step Functions to collect workload details. Build architecture diagrams of the workloads manually.
    - C. Use Workload Discovery on AWS to generate architecture diagrams of the workloads.
    - D. Use AWS X-Ray to view the workload details. Build architecture diagrams with relationships.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: C
      Explanation: Workload Discovery on AWS is a service that helps visualize and understand the architecture of your workloads across multiple AWS accounts and Regions. It automatically discovers and maps the relationships between resources, providing an accurate representation of the architecture.
    </details>

55. A company runs applications on Amazon EC2 instances in one AWS Region. The company wants to back up the EC2 instances to a second Region. The company also wants to provision EC2 resources in the second Region and manage the EC2 instances centrally from one AWS account. Which solution will meet these requirements MOST cost-effectively?
    - A. Create a disaster recovery (DR) plan that has a similar number of EC2 instances in the second Region. Configure data replication.
    - B. Create point-in-time Amazon Elastic Block Store (Amazon EBS) snapshots of the EC2 instances. Copy the snapshots to the second Region periodically.
    - C. Create a backup plan by using AWS Backup. Configure cross-Region backup to the second Region for the EC2 instances.
    - D. Deploy a similar number of EC2 instances in the second Region. Use AWS DataSync to transfer the data from the source Region to the second Region.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: C
      Explanation: Using AWS Backup, you can create backup plans that automate the backup process for your EC2 instances. By configuring cross-Region backup, you can ensure that backups are replicated to the second Region, providing a disaster recovery capability. This solution is cost-effective as it leverages AWS Backup's built-in features and eliminates the need for manual snapshot management or deploying and managing additional EC2 instances in the second Region.
    </details>

56. A company that uses AWS is building an application to transfer data to a product manufacturer.
The company has its own identity provider (IdP). The company wants the IdP to authenticate application users while the users use the application to transfer data. The company must use Applicability Statement 2 (AS2) protocol. Which solution will meet these requirements?
    - A. Use AWS DataSync to transfer the data. Create an AWS Lambda function for IdP authentication.
    - B. Use Amazon AppFlow flows to transfer the data. Create an Amazon Elastic Container Service (Amazon ECS) task for IdP authentication.
    - C. Use AWS Transfer Family to transfer the data. Create an AWS Lambda function for IdP authentication.
    - D. Use AWS Storage Gateway to transfer the data. Create an Amazon Cognito identity pool for IdP authentication.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: C
      Explanation: To authenticate your users, you can use your existing identity provider with AWS Transfer Family. You integrate your identity provider using an AWS Lambda function, which authenticates and authorizes your users for access to Amazon S3 or Amazon Elastic File System (Amazon EFS). https://docs.aws.amazon.com/transfer/latest/userguide/custom-identity-provider-users.html
    </details>

57. A company uses AWS Organizations to run workloads within multiple AWS accounts. A tagging policy adds department tags to AWS resources when the company creates tags. An accounting team needs to determine spending on Amazon EC2 consumption. The accounting team must determine which departments are responsible for the costs regardless ofAWS account. The accounting team has access to AWS Cost Explorer for all AWS accounts within the organization and needs to access all reports from Cost Explorer. Which solution meets these requirements in the MOST operationally efficient way?
    - A. From the Organizations management account billing console, activate a user-defined cost
allocation tag named department. Create one cost report in Cost Explorer grouping by tag name, and filter by EC2.
    - B. From the Organizations management account billing console, activate an AWS-defined cost allocation tag named department. Create one cost report in Cost Explorer grouping by tag name, and filter by EC2.
    - C. From the Organizations member account billing console, activate a user-defined cost allocation tag named department. Create one cost report in Cost Explorer grouping by the tag name, and filter by EC2.
    - D. From the Organizations member account billing console, activate an AWS-defined cost allocation tag named department. Create one cost report in Cost Explorer grouping by tag name, and filter by EC2.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: A
      Explanation: By activating a user-defined cost allocation tag named "department" and creating a cost report in Cost Explorer that groups by the tag name and filters by EC2, the accounting team will be able to track and attribute costs to specific departments across all AWS accounts within the organization. This approach allows for consistent cost allocation and reporting regardless of the AWS account structure.
    </details>

58. A company wants to securely exchange data between its software as a service (SaaS) application Salesforce account and Amazon S3. The company must encrypt the data at rest by using AWS Key Management Service (AWS KMS) customer managed keys (CMKs). The company must also encrypt the data in transit. The company has enabled API access for the Salesforce account.
    - A. Create AWS Lambda functions to transfer the data securely from Salesforce to Amazon S3.
    - B. Create an AWS Step Functions workflow. Define the task to transfer the data securely from Salesforce to Amazon S3.
    - C. Create Amazon AppFlow flows to transfer the data securely from Salesforce to Amazon S3.
    - D. Create a custom connector for Salesforce to transfer the data securely from Salesforce to Amazon S3.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: C
      Explanation: Amazon AppFlow is a fully managed integration service that allows you to securely transfer data between different SaaS applications and AWS services. It provides built-in encryption options and supports encryption in transit using SSL/TLS protocols. With AppFlow, you can configure the data transfer flow from Salesforce to Amazon S3, ensuring data encryption at rest by utilizing AWS KMS CMKs.
    </details>

59. A company is developing a mobile gaming app in a single AWS Region. The app runs on multiple Amazon EC2 instances in an Auto Scaling group. The company stores the app data in Amazon DynamoDB. The app communicates by using TCP traffic and UDP traffic between the users and the servers. The application will be used globally. The company wants to ensure the lowest possible latency for all users. Which solution will meet these requirements?
    - A. Use AWS Global Accelerator to create an accelerator. Create an Application Load Balancer (ALB) behind an accelerator endpoint that uses Global Accelerator integration and listening on the TCP
and UDP ports. Update the Auto Scaling group to register instances on the ALB. - B. Use AWS Global Accelerator to create an accelerator. Create a Network Load Balancer (NLB) behind an accelerator endpoint that uses Global Accelerator integration and listening on the TCP and UDP ports. Update the Auto Scaling group to register instances on the NLB. - C. Create an Amazon CloudFront content delivery network (CDN) endpoint. Create a Network Load Balancer (NLB) behind the endpoint and listening on the TCP and UDP ports. Update the Auto Scaling group to register instances on the NLB. Update CloudFront to use the NLB as the origin.
    - D. Create an Amazon CloudFront content delivery network (CDN) endpoint. Create an Application Load Balancer (ALB) behind the endpoint and listening on the TCP and UDP ports. Update the Auto Scaling group to register instances on the ALB. Update CloudFront to use the ALB as the origin.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: B
      Explanation: AWS Global Accelerator is a better solution for the mobile gaming app than CloudFront.
    </details>

60. A company has an application that processes customer orders. The company hosts the application on an Amazon EC2 instance that saves the orders to an Amazon Aurora database. Occasionally when traffic is high the workload does not process orders fast enough. What should a solutions architect do to write the orders reliably to the database as quickly as possible?
    - A. Increase the instance size of the EC2 instance when traffic is high. Write orders to Amazon Simple Notification Service (Amazon SNS). Subscribe the database endpoint to the SNS topic.
    - B. Write orders to an Amazon Simple Queue Service (Amazon SQS) queue. Use EC2 instances in an Auto Scaling group behind an Application Load Balancer to read from the SQS queue and process orders into the database.
    - C. Write orders to Amazon Simple Notification Service (Amazon SNS). Subscribe the database endpoint to the SNS topic. Use EC2 instances in an Auto Scaling group behind an Application Load Balancer to read from the SNS topic.
    - D. Write orders to an Amazon Simple Queue Service (Amazon SQS) queue when the EC2 instance reaches CPU threshold limits. Use scheduled scaling of EC2 instances in an Auto Scaling group behind an Application Load Balancer to read from the SQS queue and process orders into the database.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: B
      Explanation: By decoupling the write operation from the processing operation using SQS, you ensure that the orders are reliably stored in the queue, regardless of the processing capacity of the EC2 instances. This allows the processing to be performed at a scalable rate based on the available EC2 instances, improving the overall reliability and speed of order processing.
    </details>

61. An IoT company is releasing a mattress that has sensors to collect data about a user's sleep. The sensors will send data to an Amazon S3 bucket. The sensors collect approximately 2 MB of data every night for each mattress. The company must process and summarize the data for each mattress. The results need to be available as soon as possible. Data processing will require 1 GB of memory and will finish within 30 seconds. Which solution will meet these requirements MOST cost-effectively?
    - A. Use AWS Glue with a Scala job
    - B. Use Amazon EMR with an Apache Spark script
    - C. Use AWS Lambda with a Python script
    - D. Use AWS Glue with a PySpark job

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: C
      Explanation: AWS Lambda charges you based on the number of invocations and the execution time of your function. Since the data processing job is relatively small (2 MB of data), Lambda is a cost-effective choice. You only pay for the actual usage without the need to provision and maintain infrastructure.
    </details>

62. A company hosts an online shopping application that stores all orders in an Amazon RDS for PostgreSQL Single-AZ DB instance. Management wants to eliminate single points of failure and has asked a solutions architect to recommend an approach to minimize database downtime without requiring any changes to the application code. Which solution meets these requirements?
    - A. Convert the existing database instance to a Multi-AZ deployment by modifying the database instance and specifying the Multi-AZ option.
    - B. Create a new RDS Multi-AZ deployment. Take a snapshot of the current RDS instance and restore the new Multi-AZ deployment with the snapshot.
    - C. Create a read-only replica of the PostgreSQL database in another Availability Zone. Use Amazon Route 53 weighted record sets to distribute requests across the databases.
    - D. Place the RDS for PostgreSQL database in an Amazon EC2 Auto Scaling group with a minimum group size of two. Use Amazon Route 53 weighted record sets to distribute requests across instances.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: A
      Explanation: Compared to other solutions that involve creating new instances, restoring snapshots, or setting up replication manually, converting to a Multi-AZ deployment is a simpler and more streamlined approach with lower overhead. Overall, option A offers a cost-effective and efficient way to minimize database downtime without requiring significant changes or additional complexities.
    </details>

63. A company is developing an application to support customer demands. The company wants to deploy the application on multiple Amazon EC2 Nitro-based instances within the same Availability Zone. The company also wants to give the application the ability to write to multiple block storage volumes in multiple EC2 Nitro-based instances simultaneously to achieve higher application availability. Which solution will meet these requirements?
    - A. Use General Purpose SSD (gp3) EBS volumes with Amazon Elastic Block Store (Amazon EBS) Multi-Attach
    - B. Use Throughput Optimized HDD (st1) EBS volumes with Amazon Elastic Block Store (Amazon EBS) Multi-Attach
    - C. Use Provisioned IOPS SSD (io2) EBS volumes with Amazon Elastic Block Store (Amazon EBS) Multi-Attach
    - D. Use General Purpose SSD (gp2) EBS volumes with Amazon Elastic Block Store (Amazon EBS) Multi-Attach

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: C
      Explanation: Multi-Attach is supported exclusively on Provisioned IOPS SSD (io1 and io2) volumes.
    </details>

64. A company designed a stateless two-tier application that uses Amazon EC2 in a single Availability Zone and an Amazon RDS Multi-AZ DB instance. New company management wants to ensure the application is highly available. What should a solutions architect do to meet this requirement?
    - A. Configure the application to use Multi-AZ EC2 Auto Scaling and create an Application Load Balancer
    - B. Configure the application to take snapshots of the EC2 instances and send them to a different AWS Region
    - C. Configure the application to use Amazon Route 53 latency-based routing to feed requests to the application
    - D. Configure Amazon Route 53 rules to handle incoming requests and create a Multi-AZ Application Load Balancer

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: A
      Explanation: By combining Multi-AZ EC2 Auto Scaling and an Application Load Balancer, you achieve high availability for the EC2 instances hosting your stateless two-tier application.
    </details>

65. A company uses AWS Organizations. A member account has purchased a Compute Savings Plan. Because of changes in the workloads inside the member account, the account no longer receives the full benefit of the Compute Savings Plan commitment. The company uses less than 50% of its purchased compute power.
    - A. Turn on discount sharing from the Billing Preferences section of the account console in the member account that purchased the Compute Savings Plan.
    - B. Turn on discount sharing from the Billing Preferences section of the account console in the company's Organizations management account.
    - C. Migrate additional compute workloads from another AWS account to the account that has the Compute Savings Plan.
    - D. Sell the excess Savings Plan commitment in the Reserved Instance Marketplace.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: B
      Explanation: https://docs.aws.amazon.com/awsaccountbilling/latest/aboutv2/ri-turn-off.html Sign in to the AWS Management Console and open the AWS Billing console at https://console.aws.amazon.com/billing/ Ensure you're logged in to the management account of your AWS Organizations.
    </details>
