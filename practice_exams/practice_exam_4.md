---
layout: exam
---

# Practice Exam 4

1. A company wants to migrate its MySQL database from on premises to AWS. The company recently experienced a database outage that significantly impacted the business. To ensure this does not happen again, the company wants a reliable database solution on AWS that minimizes data loss and stores every transaction on at least two nodes. Which solution meets these requirements?
    - A. Create an Amazon RDS DB instance with synchronous replication to three nodes in three Availability Zones.
    - B. Create an Amazon RDS MySQL DB instance with Multi-AZ functionality enabled to synchronously replicate the data.
    - C. Create an Amazon RDS MySQL DB instance and then create a read replica in a separate AWS Region that synchronously replicates the data.
    - D. Create an Amazon EC2 instance with a MySQL engine installed that triggers an AWS Lambda function to synchronously replicate the data to an Amazon RDS MySQL DB instance.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: B
      Explanation: Q: What does Amazon RDS manage on my behalf? Amazon RDS manages the work involved in setting up a relational database: from provisioning the infrastructure capacity you request to installing the database software. Once your database is up and running, Amazon RDS automates common administrative tasks such as performing backups and patching the software that powers your database. With optional Multi-AZ deployments, Amazon RDS also manages synchronous data replication across Availability Zones with automatic failover. https://aws.amazon.com/rds/faqs/
    </details>

2. A company has a Windows-based application that must be migrated to AWS. The application requires the use of a shared Windows file system attached to multiple Amazon EC2 Windows instances that are deployed across multiple Availability Zones. What should a solutions architect do to meet this requirement?
    - A. Configure AWS Storage Gateway in volume gateway mode. Mount the volume to each Windows instance.
    - B. Configure Amazon FSx for Windows File Server. Mount the Amazon FSx file system to each Windows instance.
    - C. Configure a file system by using Amazon Elastic File System (Amazon EFS). Mount the EFS file system to each Windows instance.
    - D. Configure an Amazon Elastic Block Store (Amazon EBS) volume with the required size. Attach each EC2 instance to the volume. Mount the file system within the volume to each Windows instance.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: B
      Explanation: Microsoft Windows-based application = shared Windows file system = Amazon FSX for Windows https://docs.aws.amazon.com/AWSEC2/latest/WindowsGuide/AmazonEFS.html
    </details>

3. A solutions architect is creating a new Amazon CloudFront distribution for an application. Some of the information submitted by users is sensitive. The application uses HTTPS but needs another layer of security. The sensitive information should be protected throughout the entire application stack, and access to the information should be restricted to certain applications. Which action should the solutions architect take?
    - A. Configure a CloudFront signed URL.
    - B. Configure a CloudFront signed cookie.
    - C. Configure a CloudFront field-level encryption profile.
    - D. Configure CloudFront and set the Origin Protocol Policy setting to HTTPS Only for the Viewer Protocol Policy.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: C
      Explanation: https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/field-level- encryption.html "With Amazon CloudFront, you can enforce secure end-to-end connections to origin servers by using HTTPS. Field-level encryption adds an additional layer of security that lets you protect specific data throughout system processing so that only certain applications can see it."
    </details>

4. A company is planning to move its data to an Amazon S3 bucket. The data must be encrypted when it is stored in the S3 bucket. Additionally, the encryption key must be automatically rotated every year. Which solution will meet these requirements with the LEAST operational overhead?
    - A. Move the data to the S3 bucket. Use server-side encryption with Amazon S3 managed encryption keys (SSE-S3). Use the built-in key rotation behavior of SSE-S3 encryption keys.
    - B. Create an AWS Key Management Service (AWS KMS) customer managed key. Enable automatic key rotation. Set the S3 bucket's default encryption behavior to use the customer managed KMS key. Move the data to the S3 bucket.
    - C. Create an AWS Key Management Service (AWS KMS) customer managed key. Set the S3 bucket's default encryption behavior to use the customer managed KMS key. Move the data to the S3 bucket. Manually rotate the KMS key every year.
    - D. Encrypt the data with customer key material before moving the data to the S3 bucket. Create an AWS Key Management Service (AWS KMS) key without key material. Import the customer key material into the KMS key. Enable automatic key rotation.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: B
      Explanation: https://docs.aws.amazon.com/kms/latest/developerguide/rotate-keys.html Customer managed keys Automatic key rotation is disabled by default on customer managed keys but authorized users can enable and disable it. When you enable (or re-enable) automatic key rotation, AWS KMS automatically rotates the KMS key one year (approximately 365 days) after the enable date and every year thereafter.
    </details>

5. An application runs on Amazon EC2 instances in private subnets. The application needs to access an Amazon DynamoDB table. What is the MOST secure way to access the table while ensuring that the traffic does not leave the AWS network?
    - A. Use a VPC endpoint for DynamoDB. - B. Use a NAT gateway in a public subnet.
    - C. Use a NAT instance in a private subnet.
    - D. Use the internet gateway attached to the VPC. 

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: A
      Explanation: https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/vpc-endpoints- dynamodb.html A VPC endpoint for DynamoDB enables Amazon EC2 instances in your VPC to use their private IP addresses to access DynamoDB with no exposure to the public internet. Your EC2 instances do not require public IP addresses, and you don't need an internet gateway, a NAT device, or a virtual private gateway in your VPC. You use endpoint policies to control access to DynamoDB. Traffic between your VPC and the AWS service does not leave the Amazon network.
    </details>

6. A company provides an API to its users that automates inquiries for tax computations based on item prices. The company experiences a larger number of inquiries during the holiday season only that cause slower response times. A solutions architect needs to design a solution that is scalable and elastic. What should the solutions architect do to accomplish this?
    - A. Provide an API hosted on an Amazon EC2 instance. The EC2 instance performs the required computations when the API request is made.
    - B. Design a REST API using Amazon API Gateway that accepts the item names. API Gateway passes item names to AWS Lambda for tax computations.
    - C. Create an Application Load Balancer that has two Amazon EC2 instances behind it. The EC2 instances will compute the tax on the received item names.
    - D. Design a REST API using Amazon API Gateway that connects with an API hosted on an Amazon EC2 instance. API Gateway accepts and passes the item names to the EC2 instance for tax computations.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: B
      Explanation: Lambda server-less is scalable and elastic than EC2 api gateway solution.
    </details>

7. A company wants to use high performance computing (HPC) infrastructure on AWS for financial risk modeling. The company's HPC workloads run on Linux. Each HPC workflow runs on hundreds of AmazonEC2 Spot Instances, is short-lived, and generates thousands of output files that are ultimately stored in persistent storage for analytics and long-term future use. The company seeks a cloud storage solution that permits the copying of on premises data to long- term persistent storage to make data available for processing by all EC2 instances. The solution should also be a high performance file system that is integrated with persistent storage to read and write datasets and output files. Which combination of AWS services meets these requirements?
    - A. Amazon FSx for Lustre integrated with Amazon S3
    - B. Amazon FSx for Windows File Server integrated with Amazon S3
    - C. Amazon S3 Glacier integrated with Amazon Elastic Block Store (Amazon EBS)
    - D. Amazon S3 bucket with a VPC endpoint integrated with an Amazon Elastic Block Store (Amazon EBS) General Purpose SSD (gp2) volume

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: A
      Explanation: https://aws.amazon.com/fsx/lustre/ Amazon FSx for Lustre is a fully managed service that provides cost-effective, high-performance,
      scalable storage for compute workloads. Many workloads such as machine learning, high performance computing (HPC), video rendering, and financial simulations depend on compute instances accessing the same set of data through high-performance shared storage.
    </details>

8. A solutions architect is designing the architecture of a new application being deployed to the AWS Cloud. The application will run on Amazon EC2 On-Demand Instances and will automatically scale across multiple Availability Zones. The EC2 instances will scale up and down frequently throughout the day. An Application Load Balancer (ALB) will handle the load distribution. The architecture needs to support distributed session data management. The company is willing to make changes to code if needed. What should the solutions architect do to ensure that the architecture supports distributed session data management?
    - A. Use Amazon ElastiCache to manage and store session data.
    - B. Use session affinity (sticky sessions) of the ALB to manage session data.
    - C. Use Session Manager from AWS Systems Manager to manage the session.
    - D. Use the GetSessionToken API operation in AWS Security Token Service (AWS STS) to manage the session

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: A
      Explanation: https://aws.amazon.com/vi/caching/session-management/ In order to address scalability and to provide a shared data storage for sessions that can be accessible from any individual web server, you can abstract the HTTP sessions from the web servers themselves. A common solution to for this is to leverage an In-Memory Key/Value store such as Redis and Memcached. ElastiCache offerings for In-Memory key/value stores include ElastiCache for Redis, which can support replication, and ElastiCache for Memcached which does not support replication.
    </details>

9. A company hosts a marketing website in an on-premises data center. The website consists of static documents and runs on a single server. An administrator updates the website content infrequently and uses an SFTP client to upload new documents. The company decides to host its website on AWS and to use Amazon CloudFront. The company's solutions architect creates a CloudFront distribution. The solutions architect must design the most cost-effective and resilient architecture for website hosting to serve as the CloudFront origin. Which solution will meet these requirements?
    - A. Create a virtual server by using Amazon Lightsail. Configure the web server in the Lightsail instance. Upload website content by using an SFTP client.
    - B. Create an AWS Auto Scaling group for Amazon EC2 instances. Use an Application Load Balancer. Upload website content by using an SFTP client.
    - C. Create a private Amazon S3 bucket. Use an S3 bucket policy to allow access from a CloudFront origin access identity (OAI). Upload website content by using the AWS CLI.
    - D. Create a public Amazon S3 bucket. Configure AWS Transfer for SFTP. Configure the S3 bucket for website hosting. Upload website content by using the SFTP client.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: C
      Explanation: AWS transfer is a cost and doesn't mention using CloudFront. https://aws.amazon.com/aws-transfer-family/pricing/
    </details>

10. A company has a web application that is based on Java and PHP. The company plans to move the application from on premises to AWS. The company needs the ability to test new site features frequently. The company also needs a highly available and managed solution that requires minimum operational overhead. Which solution will meet these requirements?
    - A. Create an Amazon S3 bucket. Enable static web hosting on the S3 bucket. Upload the static content to the S3 bucket. Use AWS Lambda to process all dynamic content.
    - B. Deploy the web application to an AWS Elastic Beanstalk environment. Use URL swapping to switch between multiple Elastic Beanstalk environments for feature testing.
    - C. Deploy the web application lo Amazon EC2 instances that are configured with Java and PHP. Use Auto Scaling groups and an Application Load Balancer to manage the website's availability.
    - D. Containerize the web application. Deploy the web application to Amazon EC2 instances. Use the AWS Load Balancer Controller to dynamically route traffic between containers that contain the new site features for testing.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: B
      Explanation: Elastic Beanstalk is a fully managed service that makes it easy to deploy and run applications in the AWS; To enable frequent testing of new site features, you can use URL swapping to switch between multiple Elastic Beanstalk environments. https://docs.aws.amazon.com/elasticbeanstalk/latest/dg/using-features.CNAMESwap.html
    </details>

11. A rapidly growing ecommerce company is running its workloads in a single AWS Region. A solutions architect must create a disaster recovery (DR) strategy that includes a different AWS Region. The company wants its database to be up to date in the DR Region with the least possible latency. The remaining infrastructure in the DR Region needs to run at reduced capacity and must be able to scale up if necessary. Which solution will meet these requirements with the LOWEST recovery time objective (RTO)?
    - A. Use an Amazon Aurora global database with a pilot light deployment
    - B. Use an Amazon Aurora global database with a warm standby deployment
    - C. Use an Amazon RDS Multi-AZ DB instance with a pilot light deployment
    - D. Use an Amazon RDS Multi-AZ DB instance with a warm standby deployment

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: B
      Explanation: In case of disaster, both pilot light and warm standby offer the capability to limit data loss (RPO). Both offer sufficient RTO performance that enables you to limit downtime. Between these two strategies, you have a choice of optimizing for RTO or for cost. https://aws.amazon.com/es/blogs/architecture/disaster-recovery-dr-architecture-on-aws-part-iii- pilot-light-and-warm-standby/
    </details>

12. A company runs an application on a large fleet of Amazon EC2 instances. The application reads and write entries into an Amazon DynamoDB table. The size of the DynamoDB table continuously grows, but the application needs only data from the last 30 days. The company needs a solution that minimizes cost and development effort. Which solution meets these requirements?
    - A. Use an AWS CloudFormation template to deploy the complete solution. Redeploy the CloudFormation stack every 30 days, and delete the original stack.
    - B. Use an EC2 instance that runs a monitoring application from AWS Marketplace. Configure the monitoring application to use Amazon DynamoDB Streams to store the timestamp when a new item is created in the table. Use a script that runs on the EC2 instance to delete items that have a timestamp that is older than 30 days.
    - C. Configure Amazon DynamoDB Streams to invoke an AWS Lambda function when a new item is created in the table.
Configure the Lambda function to delete items in the table that are older than 30 days.
    - D. Extend the application to add an attribute that has a value of the current timestamp plus 30 days to each new item that is created in the table. Configure DynamoDB to use the attribute as the TTL attribute.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: D
      Explanation: Amazon DynamoDB Time to Live (TTL) allows you to define a per-item timestamp to determine when an item is no longer needed. Shortly after the date and time of the specified timestamp, DynamoDB deletes the item from your table without consuming any write throughput. TTL is provided at no extra cost as a means to reduce stored data volumes by retaining only the items that remain current for your workload's needs. TTL is useful if you store items that lose relevance after a specific time. The following are example TTL use cases: - Remove user or sensor data after one year of inactivity in an application. - Archive expired items to an Amazon S3 data lake via Amazon DynamoDB Streams and AWS Lambda. - Retain sensitive data for a certain amount of time according to contractual or regulatory obligations. https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/TTL.html
    </details>

13. A company runs a containerized application on a Kubernetes cluster in an on-premises data center. The company is using a MongoDB database for data storage. The company wants to migrate some of these environments to AWS, but no code changes or deployment method changes are possible at this time. The company needs a solution that minimizes operational overhead. Which solution meets these requirements?
    - A. Use Amazon Elastic Container Service (Amazon ECS) with Amazon EC2 worker nodes for compute and MongoOB on EC2 for data storage.
    - B. Use Amazon Elastic Container Service (Amazon ECS) with AWS Fargate for compute and Amazon DynamoDB tor data storage.
    - C. Use Amazon Elastic Kubernetes Service (Amazon EKS) with Amazon EC2 worker nodes for compute and Amazon DynamoDB for data storage.
    - D. Use Amazon Elastic Kubernetes Service (Amazon EKS) with AWS Fargate for compute and Amazon DocumentDB (with MongoDB compatibility) for data storage.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: D
      Explanation: Amazon DocumentDB (with MongoDB compatibility) is a fast, reliable, and fully managed database service. Amazon DocumentDB makes it easy to set up, operate, and scale MongoDB-compatible databases in the cloud. With Amazon DocumentDB, you can run the same application code and use the same drivers and tools that you use with MongoDB. https://docs.aws.amazon.com/documentdb/latest/developerguide/what-is.html
    </details>

14. A company selves a dynamic website from a fleet of Amazon EC2 instances behind an Application Load Balancer (ALB). The website needs to support multiple languages to serve customers around the world. The website's architecture is running in the us-west-1 Region and is exhibiting high request latency tor users that are located in other parts of the world. The website needs to serve requests quickly and efficiently regardless of a user's location. However the company does not want to recreate the existing architecture across multiple Regions.
What should a solutions architect do to meet these requirements?
    - A. Replace the existing architecture with a website that is served from an Amazon S3 bucket. Configure an Amazon CloudFront distribution with the S3 bucket as the origin. Set the cache behavior settings to cache based on the Accept-Language request header.
    - B. Configure an Amazon CloudFront distribution with the ALB as the origin. Set the cache behavior settings to cache based on the Accept-Language request header.
    - C. Create an Amazon API Gateway API that is integrated with the ALB. Configure the API to use the HTTP integration type. Set up an API Gateway stage to enable the API cache based on the Accept-Language request header.
    - D. Launch an EC2 instance in each additional Region and configure NGINX to act as a cache server for that Region. Put all the EC2 instances and the ALB behind an Amazon Route 53 record set with a geotocation routing policy.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: B
      Explanation: Configuring caching based on the language of the viewer. If you want CloudFront to cache different versions of your objects based on the language specified in the request, configure CloudFront to forward the Accept-Language header to your origin. https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/header-caching.html
    </details>

15. A telemarketing company is designing its customer call center functionality on AWS. The company needs a solution to provides multiples ipsafcar recognition and generates transcript files. The company wants to query the transcript files to analyze the business patterns. The transcript files must be stored for 7 years for auditing policies. Which solution will meet these requirements?
    - A. Use Amazon Rekognition for multiple speaker recognition. Store the transcript files in Amazon S3. Use machine teaming models for transcript file analysis.
    - B. Use Amazon Transcribe for multiple speaker recognition. Use Amazon Athena for transcript file analysts
    - C. Use Amazon Translate for multiple speaker recognition. Store the transcript files in Amazon Redshift. Use SQL queues for transcript file analysis
    - D. Use Amazon Rekognition for multiple speaker recognition. Store the transcript files in Amazon S3. Use Amazon Textract for transcript file analysis.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: B
      Explanation: Amazon Transcribe now supports speaker labeling for streaming transcription. Amazon Transcribe is an automatic speech recognition (ASR) service that makes it easy for you to convert speech-to- text. In live audio transcription, each stream of audio may contain multiple speakers. Now you can conveniently turn on the ability to label speakers, thus helping to identify who is saying what in the output transcript. https://aws.amazon.com/about-aws/whats-new/2020/08/amazon-transcribe-supports-speaker- labeling-streaming-transcription/
    </details>

16. A company has a small Python application that processes JSON documents and outputs the results to an on-premises SQL database. The application runs thousands of times each day. The company wants to move the application to the AWS Cloud. The company needs a highly available solution that maximizes scalability and minimizes operational overhead. Which solution will meet these requirements?
    - A. Place the JSON documents in an Amazon S3 bucket. Run the Python code on multiple Amazon EC2 instances to process the documents. Store the results in an Amazon Aurora DB cluster.
    - B. Place the JSON documents in an Amazon S3 bucket. Create an AWS Lambda function that runs the Python code to process the documents as they arrive in the S3 bucket. Store the results in an Amazon Aurora DB cluster.
    - C. Place the JSON documents in an Amazon Elastic Block Store (Amazon EBS) volume. Use the EBS Multi-Attach feature to attach the volume to multiple Amazon EC2 instances. Run the Python code on the EC2 instances to process the documents. Store the results on an Amazon RDS DB instance.
    - D. Place the JSON documents in an Amazon Simple Queue Service (Amazon SQS) queue as messages. Deploy the Python code as a container on an Amazon Elastic Container Service (Amazon ECS) cluster that is configured with the Amazon EC2 launch type. Use the container to process the SQS messages. Store the results on an Amazon RDS DB instance.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: B
      Explanation: By placing the JSON documents in an S3 bucket, the documents will be stored in a highly durable and scalable object storage service. The use of AWS Lambda allows the company to run their Python code to process the documents as they arrive in the S3 bucket without having to worry
      about the underlying infrastructure. This also allows for horizontal scalability, as AWS Lambda will automatically scale the number of instances of the function based on the incoming rate of requests. The results can be stored in an Amazon Aurora DB cluster, which is a fully-managed, high- performance database service that is compatible with MySQL and PostgreSQL. This will provide the necessary durability and scalability for the results of the processing. https://aws.amazon.com/rds/aurora/
    </details>

17. A company's infrastructure consists of Amazon EC2 instances and an Amazon RDS DB instance in a single AWS Region. The company wants to back up its data in a separate Region. Which solution will meet these requirements with the LEAST operational overhead?
    - A. Use AWS Backup to copy EC2 backups and RDS backups to the separate Region.
    - B. Use Amazon Data Lifecycle Manager (Amazon DLM) to copy EC2 backups and RDS backups to the separate Region.
    - C. Create Amazon Machine Images (AMIs) of the EC2 instances. Copy the AMIs to the separate Region. Create a read replica for the RDS DB instance in the separate Region.
    - D. Create Amazon Elastic Block Store (Amazon EBS) snapshots. Copy the EBS snapshots to the separate Region. Create RDS snapshots. Export the RDS snapshots to Amazon S3. Configure S3 Cross-Region Replication (CRR) to the separate Region.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: A
      Explanation: Cross-Region backup Using AWS Backup, you can copy backups to multiple different AWS Regions on demand or automatically as part of a scheduled backup plan. Cross-Region backup is particularly valuable if you have business continuity or compliance requirements to store backups a minimum distance away from your production data. https://docs.aws.amazon.com/aws-backup/latest/devguide/whatisbackup.html
    </details>

18. A company is building a new dynamic ordering website. The company wants to minimize server maintenance and patching. The website must be highly available and must scale read and write capacity as quickly as possible to meet changes in user demand. Which solution will meet these requirements?
    - A. Host static content in Amazon S3. Host dynamic content by using Amazon API Gateway and AWS Lambda. Use Amazon DynamoDB with on-demand capacity for the database. Configure Amazon CloudFront to deliver the website content.
    - B. Host static content in Amazon S3. Host dynamic content by using Amazon API Gateway and AWS Lambda. Use Amazon Aurora with Aurora Auto Scaling for the database. Configure Amazon CloudFront to deliver the website content.
    - C. Host all the website content on Amazon EC2 instances. Create an Auto Scaling group to scale the EC2 instances. Use an Application Load Balancer to distribute traffic. Use Amazon DynamoDB with provisioned write capacity for the database.
    - D. Host all the website content on Amazon EC2 instances. Create an Auto Scaling group to scale the EC2 instances. Use an Application Load Balancer to distribute traffic. Use Amazon Aurora with Aurora Auto Scaling for the database.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: A
      Explanation: On-demand mode is a good option if any of the following are true: You create new tables with unknown workloads. You have unpredictable application traffic. You prefer the ease of paying for only what you use. https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/HowItWorks.ReadWriteC apacityMode.html
    </details>

19. A company uses Amazon S3 as its data lake. The company has a new partner that must use SFTP to upload data files. A solutions architect needs to implement a highly available SFTP solution that minimizes operational overhead. Which solution will meet these requirements?
    - A. Use AWS Transfer Family to configure an SFTP-enabled server with a publicly accessible endpoint. Choose the S3 data lake as the destination.
    - B. Use Amazon S3 File Gateway as an SFTP server. Expose the S3 File Gateway endpoint URL to the new partner. Share the S3 File Gateway endpoint with the new partner.
    - C. Launch an Amazon EC2 instance in a private subnet in a VPInstruct the new partner to upload files to the EC2 instance by using a VPN. Run a cron job script, on the EC2 instance to upload files to the S3 data lake.
    - D. Launch Amazon EC2 instances in a private subnet in a VPC. Place a Network Load Balancer (NLB) in front of the EC2 instances. Create an SFTP listener port for the NLB. Share the NLB hostname with the new partner. Run a cron job script on the EC2 instances to upload files to the S3 data lake.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: A
      Explanation: AWS Transfer for SFTP, a fully-managed, highly-available SFTP service. You simply create a server, set up user accounts, and associate the server with one or more Amazon Simple Storage Service (Amazon S3) buckets.
    </details>

20. You have been given a scope to deploy some AWS infrastructure for a large organisation. The requirements are that you will have a lot of EC2 instances but may need to add more when the average utilization of your Amazon EC2 fleet is high and conversely remove them when CPU utilization is low. Which AWS services would be best to use to accomplish this?
    - A. Auto Scaling, Amazon CloudWatch and AWS Elastic Beanstalk
    - B. Auto Scaling, Amazon CloudWatch and Elastic Load Balancing.
    - C. Amazon CloudFront, Amazon CloudWatch and Elastic Load Balancing.
    - D. AWS Elastic Beanstalk , Amazon CloudWatch and Elastic Load Balancing.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: B
      Explanation: Auto Scaling enables you to follow the demand curve for your applications closely, reducing the need to manually provision Amazon EC2 capacity in advance. For example, you can set a condition to add new Amazon EC2 instances in increments to the Auto Scaling group when the average utilization of your Amazon EC2 fleet is high; and similarly, you can set a condition to remove instances in the same increments when CPU utilization is low. If you have predictable load changes, you can set a schedule through Auto Scaling to plan your scaling activities. You can use Amazon CloudWatch to send alarms to trigger scaling activities and Elastic Load Balancing to help distribute traffic to your instances within Auto Scaling groups. Auto Scaling enables you to run your Amazon EC2 fleet at optimal utilization. Reference: http://aws.amazon.com/autoscaling/
    </details>

21. Which of the below mentioned options is not available when an instance is launched by Auto Scaling with EC2 Classic?
    - A. Public IP
    - B. Elastic IP
    - C. Private DNS
    - D. Private IP

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: B
      Explanation: Auto Scaling supports both EC2 classic and EC2-VPC. When an instance is launched as a part of EC2 classic, it will have the public IP and DNS as well as the private IP and DNS. Reference: http://docs.aws.amazon.com/AutoScaling/latest/DeveloperGuide/GettingStartedTutorial.html
    </details>

22. A recently acquired company is required to buikl its own infrastructure on AWS and migrate multiple applications to the cloud within a month. Each application has approximately 50 TB of data to be transferred. After the migration is complete this company and its parent company will both require secure network connectivity with consistent throughput from their data centers to the applications. A solutions architect must ensure one-time data migration and ongoing network connectivity. Which solution will meet these requirements''
    - A. AWS Direct Connect for both the initial transfer and ongoing connectivity
    - B. AWS Site-to-Site VPN for both the initial transfer and ongoing connectivity
    - C. AWS Snowball for the initial transfer and AWS Direct Connect for ongoing connectivity
    - D. AWS Snowball for the initial transfer and AWS Site-to-Site VPN for ongoing connectivity

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: C
      Explanation: "Each application has approximately 50 TB of data to be transferred" = AWS Snowball; "secure network connectivity with consistent throughput from their data centers to the applications" What are the benefits of using AWS Direct Connect and private network connections? In many circumstances, private network connections can reduce costs, increase bandwidth, and provide a more consistent network experience than Internet-based connections. "more consistent network experience", hence AWS Direct Connect. Direct Connect is better than VPN; reduced cost+increased bandwith+(remain connection or consistent network) = direct connect
    </details>

23. Much of your company's data does not need to be accessed often, and can take several hours for retrieval time, so it's stored on Amazon Glacier. However someone within your organization has expressed concerns that his data is more sensitive than the other data, and is wondering whether
the high level of encryption that he knows is on S3 is also used on the much cheaper Glacier service. Which of the following statements would be most applicable in regards to this concern?
    - A. There is no encryption on Amazon Glacier, that's why it is cheaper.
    - B. Amazon Glacier automatically encrypts the data using AES-128 a lesser encryption method than Amazon S3 but you can change it to AES-256 if you are willing to pay more.
    - C. Amazon Glacier automatically encrypts the data using AES-256, the same as Amazon S3.
    - D. Amazon Glacier automatically encrypts the data using AES-128 a lesser encryption method than Amazon S3.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: C
      Explanation: Like Amazon S3, the Amazon Glacier service provides low-cost, secure, and durable storage. But where S3 is designed for rapid retrieval, Glacier is meant to be used as an archival service for data that is not accessed often, and for which retrieval times of several hours are suitable. Amazon Glacier automatically encrypts the data using AES-256 and stores it durably in an immutable form. Amazon Glacier is designed to provide average annual durability of 99.999999999% for an archive. It stores each archive in multiple facilities and multiple devices. Unlike traditional systems which can require laborious data verification and manual repair, Glacier performs regular, systematic data integrity checks, and is built to be automatically self-healing. Reference: http://d0.awsstatic.com/whitepapers/Security/AWS%20Security%20Whitepaper.pdf
    </details>

24. Your EBS volumes do not seem to be performing as expected and your team leader has requested you look into improving their performance. Which of the following is not a true statement relating to the performance of your EBS volumes?
    - A. Frequent snapshots provide a higher level of data durability and they will not degrade the performance of your application while the snapshot is in progress.
    - B. General Purpose (SSD) and Provisioned IOPS (SSD) volumes have a throughput limit of 128 MB/s per volume.
    - C. There is a relationship between the maximum performance of your EBS volumes, the amount of I/O you are driving to them, and the amount of time it takes for each transaction to complete.
    - D. There is a 5 to 50 percent reduction in IOPS when you first access each block of data on a newly created or restored EBS volume

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: A
      Explanation: Several factors can affect the performance of Amazon EBS volumes, such as instance configuration, I/O characteristics, workload demand, and storage configuration. Frequent snapshots provide a higher level of data durability, but they may slightly degrade the performance of your application while the snapshot is in progress. This trade off becomes critical when you have data that changes rapidly. Whenever possible, plan for snapshots to occur during off-peak times in order to minimize workload impact. Reference: http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/EBSPerformance.html
    </details>

25. You are building infrastructure for a data warehousing solution and an extra request has come through that there will be a lot of business reporting queries running all the time and you are not sure if your current DB instance will be able to handle it. What would be the best solution for this?
    - A. DB Parameter Groups
    - B. Read Replicas
    - C. Multi-AZ DB Instance deployment
    - D. Database Snapshots

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: B
      Explanation: Read Replicas make it easy to take advantage of MySQL's built-in replication functionality to elastically scale out beyond the capacity constraints of a single DB Instance for read-heavy database workloads. There are a variety of scenarios where deploying one or more Read Replicas for a given source DB Instance may make sense. Common reasons for deploying a Read Replica include: Scaling beyond the compute or I/O capacity of a single DB Instance for read-heavy database workloads. This excess read traffic can be directed to one or more Read Replicas. Serving read traffic while the source DB Instance is unavailable. If your source DB Instance cannot take I/O requests (e.g. due to I/O suspension for backups or scheduled maintenance), you can direct read traffic to your Read Replica(s). For this use case, keep in mind that the data on the Read Replica may be "stale" since the source DB Instance is unavailable. Business reporting or data warehousing scenarios; you may want business reporting queries to run against a Read Replica, rather than your primary, production DB Instance. Reference: https://aws.amazon.com/rds/faqs/
    </details>

26. You've created your first load balancer and have registered your EC2 instances with the load balancer. Elastic Load Balancing routinely performs health checks on all the registered EC2 instances and automatically distributes all incoming requests to the DNS name of your load balancer across your registered, healthy EC2 instances. By default, the load balancer uses the ___ protocol for checking the health of your instances.
    - A. HTTPS
    - B. HTTP
    - C. ICMP
    - D. IPv6

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: B
      Explanation: In Elastic Load Balancing a health configuration uses information such as protocol, ping port, ping path (URL), response timeout period, and health check interval to determine the health state of the instances registered with the load balancer. Currently, HTTP on port 80 is the default health check. Reference: http://docs.aws.amazon.com/ElasticLoadBalancing/latest/DeveloperGuide/TerminologyandKeyCo ncepts.html
    </details>

27. A major finance organisation has engaged your company to set up a large data mining application. Using AWS you decide the best service for this is Amazon Elastic MapReduce(EMR) which you know uses Hadoop. Which of the following statements best describes Hadoop?
    - A. Hadoop is 3rd Party software which can be installed using AMI
    - B. Hadoop is an open source python web framework
    - C. Hadoop is an open source Java software framework
    - D. Hadoop is an open source javascript framework

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: C
      Explanation: Amazon EMR uses Apache Hadoop as its distributed data processing engine. Hadoop is an open source, Java software framework that supports data-intensive distributed applications running on large clusters of commodity hardware. Hadoop implements a programming model named "MapReduce," where the data is divided into many small fragments of work, each of which may be executed on any node in the cluster. This framework has been widely used by developers, enterprises and startups and has proven to be a reliable software platform for processing up to petabytes of data on clusters of thousands of commodity machines. Reference: http://aws.amazon.com/elasticmapreduce/faqs/
    </details>

28. A company wants to host a scalable web application on AWS. The application will be accessed by users from different geographic regions of the world. Application users will be able to download and upload unique data up to gigabytes in size. The development team wants a cost-effective solution to minimize upload and download latency and maximize performance. What should a solutions architect do to accomplish this?
    - A. Use Amazon S3 with Transfer Acceleration to host the application.
    - B. Use Amazon S3 with CacheControl headers to host the application.
    - C. Use Amazon EC2 with Auto Scaling and Amazon CloudFront to host the application.
    - D. Use Amazon EC2 with Auto Scaling and Amazon ElastiCache to host the application.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: A
      Explanation: The maximum size of a single file that can be delivered through Amazon CloudFront is 20 GB. This limit applies to all Amazon CloudFront distributions.
    </details>

29. A company is migrating a three-tier application to AWS. The application requires a MySQL database. In the past, the application users reported poor application performance when creating new entries. These performance issues were caused by users generating different real-time reports from the application duringworking hours. Which solution will improve the performance of the application when it is moved to AWS?
    - A. Import the data into an Amazon DynamoDB table with provisioned capacity. Refactor the application to use DynamoDB for reports.
    - B. Create the database on a compute optimized Amazon EC2 instance. Ensure compute resources exceed the on-premises database.
    - C. Create an Amazon Aurora MySQL Multi-AZ DB cluster with multiple read replicas. Configure the application reader endpoint for reports.
    - D. Create an Amazon Aurora MySQL Multi-AZ DB cluster. Configure the application to use the backup instance of the cluster as an endpoint for the reports.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: C
      Explanation: The MySQL-compatible edition of Aurora delivers up to 5X the throughput of standard MySQL running on the same hardware, and enables existing MySQL applications and tools to run without requiring modification. https://aws.amazon.com/rds/aurora/mysql-features/
    </details>

30. A start-up company has a web application based in the us-east-1 Region with multiple Amazon EC2 instances running behind an Application Load Balancer across multiple Availability Zones. As the company's user base grows in the us-west-1 Region, it needs a solution with low latency and high availability. What should a solutions architect do to accomplish this?
    - A. Provision EC2 instances in us-west-1. Switch the Application Load Balancer to a Network Load Balancer to achieve cross-Region load balancing.
    - B. Provision EC2 instances and an Application Load Balancer in us-west-1. Make the load balancer distribute the traffic based on the location of the request.
    - C. Provision EC2 instances and configure an Application Load Balancer in us-west-1. Create an accelerator in AWS Global Accelerator that uses an endpoint group that includes the load balancer endpoints in both Regions.
    - D. Provision EC2 instances and configure an Application Load Balancer in us-west-1. Configure Amazon Route 53 with a weighted routing policy. Create alias records in Route 53 that point to the Application Load Balancer.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: C
      Explanation: "ELB provides load balancing within one Region, AWS Global Accelerator provides traffic management across multiple Regions [...] AWS Global Accelerator complements ELB by extending these capabilities beyond a single AWS Region, allowing you to provision a global interface for your applications in any number of Regions. If you have workloads that cater to a global client base, we recommend that you use AWS Global Accelerator. If you have workloads hosted in a single AWS Region and used by clients in and around the same Region, you can use an Application Load Balancer or Network Load Balancer to manage your resources." https://aws.amazon.com/global-accelerator/faqs/
    </details>

31. A company must generate sales reports at the beginning of every month. The reporting process launches 20 Amazon EC2 instances on the first of the month. The process runs for 7 days and cannot be interrupted. The company wants to minimize costs. Which pricing model should the company choose?
    - A. Reserved Instances
    - B. Spot Block Instances
    - C. On-Demand Instances
    - D. Scheduled Reserved Instances

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: D
      Explanation: Scheduled Reserved Instances (Scheduled Instances) enable you to purchase capacity reservations that recur on a daily, weekly, or monthly basis, with a specified start time and duration, for a one-year term. You reserve the capacity in advance, so that you know it is available when you need it. You pay for the time that the instances are scheduled, even if you do not use them. Scheduled Instances are a good choice for workloads that do not run continuously, but do run on a regular schedule. For example, you can use Scheduled Instances for an application that runs during business hours or for batch processing that runs at the end of the week. https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ec2-scheduled-instances.html
    </details>

32. A company's web application uses an Amazon RDS PostgreSQL DB instance to store its application data. During the financial closing period at the start of every month. Accountants run large queries that impact the database's performance due to high usage. The company wants to minimize the impact that the reporting activity has on the web application. What should a solutions architect do to reduce the impact on the database with the LEAST amount of effort?
    - A. Create a read replica and direct reporting traffic to the replica.
    - B. Create a Multi-AZ database and direct reporting traffic to the standby.
    - C. Create a cross-Region read replica and direct reporting traffic to the replica.
    - D. Create an Amazon Redshift database and direct reporting traffic to the Amazon Redshift database.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: A
      Explanation: Amazon RDS uses the MariaDB, MySQL, Oracle, PostgreSQL, and Microsoft SQL Server DB engines' built-in replication functionality to create a special type of DB instance called a read replica from a source DB instance. Updates made to the source DB instance are asynchronously copied to the read replica. You can reduce the load on your source DB instance by routing read queries from your applications to the read replica. https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/USER_ReadRepl.html
    </details>

33. A company has application running on Amazon EC2 instances in a VPC. One of the applications needs to call an Amazon S3 API to store and read objects. The company's security policies restrict any internet-bound traffic from the applications. Which action will fulfill these requirements and maintain security?
    - A. Configure an S3 interface endpoint.
    - B. Configure an S3 gateway endpoint.
    - C. Create an S3 bucket in a private subnet.
    - D. Create an S3 bucket in the same Region as the EC2 instance.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: B
      Explanation: Gateway Endpoint for S3 and DynamoDB https://medium.com/tensult/aws-vpc-endpoints-introduction-ef2bf85c4422 https://docs.aws.amazon.com/vpc/latest/userguide/vpc-endpoints-s3.html https://docs.aws.amazon.com/vpc/latest/userguide/vpce-gateway.html
    </details>

34. A website runs a web application that receives a burst of traffic each day at noon. The users upload new pictures and content daily, but have been complaining of timeouts. The architecture uses Amazon EC2 Auto Scaling groups, and the custom application consistently takes 1 minute to initiate upon boot up before responding to user requests. How should a solutions architect redesign the architecture to better respond to changing traffic?
    - A. Configure a Network Load Balancer with a slow start configuration.
    - B. Configure AWS ElastiCache for Redis to offload direct requests to the servers.
    - C. Configure an Auto Scaling step scaling policy with an instance warmup condition.
    - D. Configure Amazon CloudFront to use an Application Load Balancer as the origin.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: C
      Explanation: If you are creating a step policy, you can specify the number of seconds that it takes for a newly launched instance to warm up. Until its specified warm-up time has expired, an instance is not counted toward the aggregated metrics of the Auto Scaling group. https://docs.aws.amazon.com/autoscaling/ec2/userguide/as-scaling-simple-step.html#as-step- scaling-warmup
    </details>

35. A company hosts its website on Amazon S3. The website serves petabytes of outbound traffic monthly, which accounts for most of the company's AWS costs. What should a solutions architect do to reduce costs?
    - A. Configure Amazon CloudFront with the existing website as the origin.
    - B. Move the website to Amazon EC2 with Amazon EBS volumes for storage.
    - C. Use AWS Global Accelerator and specify the existing website as the endpoint.
    - D. Rearchitect the website to run on a combination of Amazon API Gateway and AWS Lambda.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: A
      Explanation: A textbook case for CloudFront. The data transfer cost in CloudFront is lower than in S3. With heavy read operations of static content, it's more economical to add CloudFront in front of you S3 bucket.
    </details>

36. A company currently stores symmetric encryption keys in a hardware security module (HSM). A solution architect must design a solution to migrate key management to AWS. The solution should
allow for key rotation and support the use of customer provided keys. Where should the key material be stored to meet these requirements?
    - A. Amazon S3
    - B. AWS Secrets Manager
    - C. AWS Systems Manager Parameter store
    - D. AWS Key Management Service (AWS KMS)

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: B
      Explanation: AWS Secrets Manager helps you protect secrets needed to access your applications, services, and IT resources. The service enables you to easily rotate, manage, and retrieve database credentials, API keys, and other secrets throughout their lifecycle. https://aws.amazon.com/secrets-manager/
    </details>

37. A company needs to implement a relational database with a multi-Region disaster recovery Recovery Point Objective (RPO) of 1 second and an Recovery Time Objective (RTO) of 1 minute. Which AWS solution can achieve this?
    - A. Amazon Aurora Global Database
    - B. Amazon DynamoDB global tables.
    - C. Amazon RDS for MySQL with Multi-AZ enabled.
    - D. Amazon RDS for MySQL with a cross-Region snapshot copy.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: A
      Explanation: Cross-Region Disaster Recovery If your primary region suffers a performance degradation or outage, you can promote one of the secondary regions to take read/write responsibilities. An Aurora cluster can recover in less than 1 minute even in the event of a complete regional outage. This provides your application with an effective Recovery Point Objective (RPO) of 1 second and a Recovery Time Objective (RTO) of less than 1 minute, providing a strong foundation for a global business continuity plan.
    </details>

38. A company is designing a new service that will run on Amazon EC2 instance behind an Elastic Load Balancer. However, many of the web service clients can only reach IP addresses whitelisted on their firewalls. What should a solution architect recommend to meet the clients' needs?
    - A. A Network Load Balancer with an associated Elastic IP address.
    - B. An Application Load Balancer with an a associated Elastic IP address
    - C. An A record in an Amazon Route 53 hosted zone pointing to an Elastic IP address
    - D. An EC2 instance with a public IP address running as a proxy in front of the load balancer

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: C
      Explanation: Route 53 routes end users to Internet applications so the correct answer is C. Map one of the whitelisted IP addresses using an A record to the Elastic IP address.
    </details>

39. A company's packaged application dynamically creates and returns single-use text files in response to user requests. The company is using Amazon CloudFront for distribution, but wants to future reduce data transfer costs. The company modify the application's source code. What should a solution architect do to reduce costs?
    - A. Use Lambda@Edge to compress the files as they are sent to users.
    - B. Enable Amazon S3 Transfer Acceleration to reduce the response times.
    - C. Enable caching on the CloudFront distribution to store generated files at the edge.
    - D. Use Amazon S3 multipart uploads to move the files to Amazon S3 before returning them to users.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: A
      Explanation: B seems more expensive; C does not seem right because they are single use files and will not be needed again from the cache; D multipart mainly for large files and will not reduce data and cost; A seems the best: change the application code to compress the files and reduce the amount of data transferred to save costs.
    </details>

40. An application running on an Amazon EC2 instance in VPC-A needs to access files in another EC2 instance in VPC-B. Both are in separate AWS accounts. The network administrator needs to design a solution to enable secure access to EC2 instance in VPC-B from VPC-A. The connectivity should not have a single point of failure or bandwidth concerns. Which solution will meet these requirements?
    - A. Set up a VPC peering connection between VPC-A and VPC-B. - B. Set up VPC gateway endpoints for the EC2 instance running in VPC-B. - C. Attach a virtual private gateway to VPC-B and enable routing from VPC-A. - D. Create a private virtual interface (VIF) for the EC2 instance running in VPC-B and add appropriate routes from VPC-B. 

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: A
      Explanation: A VPC peering connection is a networking connection between two VPCs that enables you to route traffic between them using private IPv4 addresses or IPv6 addresses. Instances in either VPC can communicate with each other as if they are within the same network. You can create a VPC peering connection between your own VPCs, or with a VPC in another AWS account. The traffic remains in the private IP space. All inter-region traffic is encrypted with no single point of failure, or bandwidth bottleneck. https://docs.aws.amazon.com/vpc/latest/peering/what-is-vpc-peering.html
    </details>

41. A company stores user data in AWS. The data is used continuously with peak usage during business hours. Access patterns vary, with some data not being used for months at a time. A solutions architect must choose a cost-effective solution that maintains the highest level of durability while maintaining high availability. Which storage solution meets these requirements?
    - A. Amazon S3
    - B. Amazon S3 Intelligent-Tiering
    - C. Amazon S3 Glacier Deep Archive
    - D. Amazon S3 One Zone-Infequent Access (S3 One Zone-IA)

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: B
      Explanation: Intelligent tearing moves data between storage classes based on its current degree of usage.
    </details>

42. A solutions architect is creating an application that will handle batch processing of large amounts of data. The input data will be held in Amazon S3 and the output data will be stored in a different S3 bucket. For processing, the application will transfer the data over the network between multiple Amazon EC2 instances. What should the solutions architect do to reduce the overall data transfer costs?
    - A. Place all the EC2 instances in an Auto Scaling group.
    - B. Place all the EC2 instances in the same AWS Region.
    - C. Place all the EC2 instances in the same Availability Zone.
    - D. Place all the EC2 instances in private subnets in multiple Availability Zones.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: C
      Explanation: The transfer is between EC2 instances and not just between S3 and EC2. Also, be aware of inter-Availability Zones data transfer charges between Amazon EC2 instances, even within the same region. If possible, the instances in a development or test environment that need to communicate with each other should be co-located within the same Availability Zone to avoid data transfer charges. (This doesn't apply to production workloads which will most likely need to span multiple Availability Zones for high availability.) https://aws.amazon.com/blogs/mt/using-aws-cost-explorer-to-analyze-data-transfer-costs/
    </details>

43. A company has recently updated its internal security standards. The company must now ensure all Amazon S3 buckets and Amazon Elastic Block Store (Amazon EBS) volumes are encrypted with keys created and periodically rotated by internal security specialists. The company is looking for a native, software-based AWS service to accomplish this goal. What should a solutions architect recommend as a solution?
    - A. Use AWS Secrets Manager with customer master keys (CMKs) to store master key material and apply a routine to create a new CMK periodically and replace it in AWS Secrets Manager.
    - B. Use AWS Key Management Service (AWS KMS) with customer master keys (CMKs) to store master key material and apply a routing to re-create a new key periodically and replace it in AWS KMS.
    - C. Use an AWS CloudHSM cluster with customer master keys (CMKs) to store master key material and apply a routine a re-create a new key periodically and replace it in the CloudHSM cluster nodes.
    - D. Use AWS Systems Manager Parameter Store with customer master keys (CMKs) keys to store master key material and apply a routine to re-create a new periodically and replace it in the Parameter Store.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: A
      Explanation: AWS Secrets Manager provides full lifecycle management for secrets within your environment. In this post, Maitreya and I will show you how to use Secrets Manager to store, deliver, and rotate
      SSH keypairs used for communication within compute clusters. Rotation of these keypairs is a security best practice, and sometimes a regulatory requirement. Traditionally, these keypairs have been associated with a number of tough challenges. For example, synchronizing key rotation across all compute nodes, enable detailed logging and auditing, and manage access to users in order to modify secrets.
    </details>

44. A company relies on an application that needs at least 4 Amazon EC2 instances during regular traffic and must scale up to 12 EC2 instances during peak loads. The application is critical to the business and must be highly available. Which solution will meet these requirements?
    - A. Deploy the EC2 instances in an Auto Scaling group. Set the minimum to 4 and the maximum to 12, with 2 in Availability Zone A and 2 in Availability Zone
    - B. - B. Deploy the EC2 instances in an Auto Scaling group. Set the minimum to 4 and the maximum to 12, with all 4 in Availability Zone
    - A. - C. Deploy the EC2 instances in an Auto Scaling group. Set the minimum to 8 and the maximum to 12, with 4 in Availability Zone A and 4 in Availability Zone B
    - D. Deploy the EC2 instances in an Auto Scaling group. Set the minimum to 8 and the maximum to 12 with all 8 in Availability Zone
    - A. 

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: C
      Explanation: It requires HA and if one AZ is down then at least 4 instances will be active in another AZ which is key for this question.
    </details>

45. A company recently deployed a two-tier application in two Availability Zones in the us-east-1 Region. The databases are deployed in a private subnet while the web servers are deployed in a public subnet. An internet gateway is attached to the VPC. The application and database run on Amazon EC2
instances. The database servers are unable to access patches on the internet. A solutions architect needs to design a solution that maintains database security with the least operational overhead. Which solution meets these requirements?
    - A. Deploy a NAT gateway inside the public subnet for each Availability Zone and associate it with an Elastic IP address. Update the routing table of the private subnet to use it as the default route.
    - B. Deploy a NAT gateway inside the private subnet for each Availability Zone and associate it with an Elastic IP address. Update the routing table of the private subnet to use it as the default route.
    - C. Deploy two NAT instances inside the public subnet for each Availability Zone and associate them with Elastic IP addresses. Update the routing table of the private subnet to use it as the default route.
    - D. Deploy two NAT instances inside the private subnet for each Availability Zone and associate them with Elastic IP addresses. Update the routing table of the private subnet to use it as the default route.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: A
      Explanation: VPC with public and private subnets (NAT) The configuration for this scenario includes a virtual private cloud (VPC) with a public subnet and a private subnet. We recommend this scenario if you want to run a public-facing web application, while maintaining back-end servers that aren't publicly accessible. A common example is a multi- tier website, with the web servers in a public subnet and the database servers in a private subnet. You can set up security and routing so that the web servers can communicate with the database servers. The instances in the public subnet can send outbound traffic directly to the Internet, whereas the instances in the private subnet can't. Instead, the instances in the private subnet can access the Internet by using a network address translation (NAT) gateway that resides in the public subnet. The database servers can connect to the Internet for software updates using the NAT gateway, but the Internet cannot establish connections to the database servers. https://docs.aws.amazon.com/vpc/latest/userguide/VPC_Scenario2.html
    </details>

46. A company has an on-premises data center that is running out of storage capacity. The company wants to migrate its storage infrastructure to AWS while minimizing bandwidth costs. The solution must allow for immediate retrieval of data at no additional cost. How can these requirements be met?
    - A. Deploy Amazon S3 Glacier Vault and enable expedited retrieval. Enable provisioned retrieval capacity for the workload
    - B. Deploy AWS Storage Gateway using cached volumes. Use Storage Gateway to store data in Amazon S3 while retaining copies of frequently accessed data subsets locally.
    - C. Deploy AWS Storage Gateway using stored volumes to store data locally. Use Storage Gateway to asynchronously back up point-in-time snapshots of the data to Amazon S3
    - D. Deploy AWS Direct Connect to connect with the on-premises data center. Configure AWS Storage Gateway to store data locally. Use Storage Gateway to asynchronously bacK up potnt-tn-time snapshots of the data to Amazon S3.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: C
      Explanation: Volume Gateway provides an iSCSI target, which enables you to create block storage volumes and mount them as iSCSI devices from your on-premises or EC2 application servers. The Volume Gateway runs in either a cached or stored mode: In the cached mode, your primary data is written to S3, while retaining your frequently accessed data locally in a cache for low-latency access. In the stored mode, your primary data is stored locally and your entire dataset is available for low- latency access while asynchronously backed up to AWS.
    </details>

47. A company recently implemented hybrid cloud connectivity using AWS Direct Connect and is migrating data to Amazon S3. The company is looking for a fully managed solution that will automate and accelerate the replication of data between the on-premises storage systems and AWS storage services. Which solution should a solutions architect recommend to keep the data private?
    - A. Deploy an AWS DataSync agent tor the on-premises environment. Configure a sync job to replicate the data and connect it with an AWS service endpoint.
    - B. Deploy an AWS DataSync agent for the on-premises environment. Schedule a batch job to replicate point-ln-time snapshots to AWS.
    - C. Deploy an AWS Storage Gateway volume gateway for the on-premises environment. Configure it to store data locally, and asynchronously back up point-in-time snapshots to AWS.
    - D. Deploy an AWS Storage Gateway file gateway for the on-premises environment. Configure it to store data locally, and asynchronously back up point-in-lime snapshots to AWS.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: A
      Explanation: You can use AWS DataSync with your Direct Connect link to access public service endpoints or private VPC endpoints. When using VPC endpoints, data transferred between the DataSync agent and AWS services does not traverse the public internet or need public IP addresses, increasing the security of data as it is copied over the network.
    </details>

48. A solutions architect is designing the storage architecture for a new web application used for stonng and viewing engineering drawings. All application components will be deployed on the AWS infrastructure. The application design must support caching to minimize the amount of time that users wait for the engineering drawings to load. The application must be able to store petabytes of data. Which combination of storage and caching should the solutions architect use?
    - A. Amazon S3 with Amazon CloudFront
    - B. Amazon S3 Glacier with Amazon ElastiCache
    - C. Amazon Elastic Block Store (Amazon EBS) volumes with Amazon CloudFront
    - D. AWS Storage Gateway with Amazon ElastiCache

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: A
      Explanation: CloudFront for caching and S3 as the origin. Glacier is used for archiving which is not the case for this scenario.
    </details>

49. An operations team has a standard that states IAM policies should not be applied directly to users.
Some new members have not been following this standard. The operation manager needs a way to easily identify the users with attached policies. What should a solutions architect do to accomplish this?
    - A. Monitor using AWS CloudTrail
    - B. Create an AWS Config rule to run daily
    - C. Publish IAM user changes lo Amazon SNS
    - D. Run AWS Lambda when a user is modified

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: B
      Explanation: A new AWS Config rule is deployed in the account after you enable AWS Security Hub. The AWS Config rule reacts to resource configuration and compliance changes and send these change items to AWS CloudWatch. When AWS CloudWatch receives the compliance change, a CloudWatch event rule triggers the AWS Lambda function.
    </details>

50. A company is building applications in containers. The company wants to migrate its on-premises development and operations services from its on- premises data center to AWS. Management states that production system must be cloud agnostic and use the same configuration and administrator tools across production systems. A solutions architect needs to design a managed solution that will align open-source software. Which solution meets these requirements?
    - A. Launch the containers on Amazon EC2 with EC2 instance worker nodes.
    - B. Launch the containers on Amazon Elastic Kubernetes Service (Amazon EKS) and EKS workers nodes.
    - C. Launch the containers on Amazon Elastic Containers service (Amazon ECS) with AWS Fargate instances.
    - D. Launch the containers on Amazon Elastic Container Service (Amazon EC) with Amazon EC2 instance worker nodes.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: B
      Explanation: When talking about containerized applications, the leading technologies which will always come up during the conversation are Kubernetes and Amazon ECS (Elastic Container Service). While Kubernetes is an open-sourced container orchestration platform that was originally developed by Google, Amazon ECS is AWS' proprietary, managed container orchestration service.
    </details>

51. A solutions architect is performing a security review of a recently migrated workload. The workload is a web application that consists of Amazon EC2 instances in an Auto Scaling group behind an Application Load Balancer. The solutions architect must improve the security posture and minimize the impact of a DDoS attack on resources. Which solution is MOST effective?
    - A. Configure an AWS WAF ACL with rate-based rules. Create an Amazon CloudFront distribution that points to the Application Load Balancer. Enable the WAF ACL on the CloudFront distribution.
    - B. Create a custom AWS Lambda function that adds identified attacks into a common vulnerability
pool to capture a potential DDoS attack. Use the identified information to modify a network ACL to block access.
    - C. Enable VPC Flow Logs and store them in Amazon S3. Create a custom AWS Lambda function that parses the togs looking for a DDoS attack. Modify a network ACL to block identified source IP addresses.
    - D. Enable Amazon GuardDuty and configure findings written to Amazon CloudWatch. Create an event with CloudWatch Events for DDoS alerts that triggers Amazon Simple Notification Service (Amazon SNS) . Have Amazon SNS invoke a custom AWS Lambda function that parses the logs looking for a DDoS attack. Modify a network ACL to block identified source IP addresses.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: A
      Explanation: AWS WAF is a web application firewall that helps detect and mitigate web application layer DDoS attacks by inspecting traffic inline. Application layer DDoS attacks use well-formed but malicious requests to evade mitigation and consume application resources. You can define custom security rules (also called web ACLs) that contain a set of conditions, rules, and actions to block attacking traffic. After you define web ACLs, you can apply them to CloudFront distributions, and web ACLs are evaluated in the priority order you specified when you configured them. Real-time metrics and sampled web requests are provided for each web ACL. https://aws.amazon.com/blogs/security/how-to-protect-dynamic-web-applications-against-ddos- attacks-by-using-amazon-cloudfront-and-amazon-route-53/
    </details>

52. A company is creating a prototype of an ecommerce website on AWS. The website consists of an Application Load Balancer, an Auto Scaling group of Amazon EC2 instances for web servers, and an Amazon RDS for MySQL DB instance that runs with the Single-AZ configuration. The website is slow to respond during searches of the product catalog. The product catalog is a group of tables in the MySQL database that the company does not update frequently. A solutions architect has determined that the CPU utilization on the DB instance is high when product catalog searches occur. What should the solutions architect recommend to improve the performance of the website during searches of the product catalog?
    - A. Migrate the product catalog to an Amazon Redshift database. Use the COPY command to load the product catalog tables.
    - B. Implement an Amazon ElastiCache for Redis cluster to cache the product catalog. Use lazy loading to populate the cache.
    - C. Add an additional scaling policy to the Auto Scaling group to launch additional EC2 instances when database response is slow.
    - D. Turn on the Multi-AZ configuration for the DB instance. Configure the EC2 instances to throttle the product catalog queries that are sent to the database.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: B
      Explanation: Common ElastiCache Use Cases and How ElastiCache Can Help : Whether serving the latest news, a top-10 leaderboard, a product catalog, or selling tickets to an event, speed is the name of the game. The success of your website and business is greatly affected by the speed at which you deliver content. https://docs.aws.amazon.com/AmazonElastiCache/latest/red-ug/elasticache-use-cases.html
    </details>

53. A company's application is running on Amazon EC2 instances within an Auto Scaling group behind an Elastic Load Balancer. Based on the application's history, the company anticipates a spike in traffic during a holiday each year. A solutions architect must design a strategy to ensure that the Auto Scaling group proactively increases capacity to minimize any performance impact on application users. Which solution will meet these requirements?
    - A. Create an Amazon CloudWatch alarm to scale up the EC2 instances when CPU utilization exceeds 90%.
    - B. Create a recurring scheduled action to scale up the Auto Scaling group before the expected period of peak demand.
    - C. Increase the minimum and maximum number of EC2 instances in the Auto Scaling group during the peak demand period.
    - D. Configure an Amazon Simple Notification Service (Amazon SNS) notification to send alerts when there are autoscaling:EC2_INSTANCE_LAUNCH events.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: B
      Explanation: Amazon EC2 Auto Scaling supports sending Amazon SNS notifications when the following events occur. https://docs.aws.amazon.com/autoscaling/ec2/userguide/schedule_time.html
    </details>

54. A solutions architect is tasked with transferring 750 TB of data from an on-premises network- attached file system located at a branch office Amazon S3 Glacier. The migration must not saturate the on-premises 1 Mbps internet connection. Which solution will meet these requirements?
    - A. Create an AWS site-to-site VPN tunnel to an Amazon S3 bucket and transfer the files directly. Transfer the files directly by using the AWS CLI.
    - B. Order 10 AWS Snowball Edge Storage Optimized devices, and select an S3 Glacier vault as the destination.
    - C. Mount the network-attached file system to an S3 bucket, and copy the files directly. Create a lifecycle policy to transition the S3 objects to Amazon S3 Glacier.
    - D. Order 10 AWS Snowball Edge Storage Optimized devices, and select an Amazon S3 bucket as the destination.
Create a lifecycle policy to transition the S3 objects to Amazon S3 Glacier.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: D
      Explanation: To upload existing data to Amazon S3 Glacier (S3 Glacier), you might consider using one of the AWS Snowball device types to import data into Amazon S3, and then move it to the S3 Glacier storage class for archival using lifecycle rules. When you transition Amazon S3 objects to the S3 Glacier storage class, Amazon S3 internally uses S3 Glacier for durable storage at lower cost. Although the objects are stored in S3 Glacier, they remain Amazon S3 objects that you manage in Amazon S3, and you cannot access them directly through S3 Glacier. https://docs.aws.amazon.com/amazonglacier/latest/dev/uploading-an-archive.html
    </details>

55. A company's website handles millions of requests each day, and the number of requests continues to increase. A solutions architect needs to improve the response time of the web application. The solutions architect determines that the application needs to decrease latency when retrieving product details from the Amazon DynamoDB table. Which solution will meet these requirements with the LEAST amount of operational overhead?
    - A. Set up a DynamoDB Accelerator (DAX) cluster. Route all read requests through DAX.
    - B. Set up Amazon ElastiCache for Redis between the DynamoDB table and the web application. Route all read requests through Redis.
    - C. Set up Amazon ElastiCache for Memcached between the DynamoDB table and the web application. Route all read requests through Memcached.
    - D. Set up Amazon DynamoDB Streams on the table, and have AWS Lambda read from the table and populate Amazon ElastiCache. Route all read requests through ElastiCache.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: A
      Explanation: Amazon DynamoDB is designed for scale and performance. In most cases, the DynamoDB response times can be measured in single-digit milliseconds. However, there are certain use cases that require response times in microseconds. For these use cases, DynamoDB Accelerator (DAX) delivers fast response times for accessing eventually consistent data. DAX is a DynamoDB-compatible caching service that enables you to benefit from fast in-memory performance for demanding applications. https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/DAX.html
    </details>

56. A media company collects and analyzes user activity data on premises. The company wants to migrate this capability to AWS. The user activity data store will continue to grow and will be petabytes in size. The company needs to build a highly available data ingestion solution that facilitates on-demand analytics of existing data and new data with SQL. Which solution will meet these requirements with the LEAST operational overhead?
    - A. Send activity data to an Amazon Kinesis data stream. Configure the stream to deliver the data to an Amazon S3 bucket.
    - B. Send activity data to an Amazon Kinesis Data Firehose delivery stream. Configure the stream to deliver the data to an Amazon Redshift cluster.
    - C. Place activity data in an Amazon S3 bucket. Configure Amazon S3 to run an AWS Lambda function on the data as the data arrives in the S3
bucket.
    - D. Create an ingestion service on Amazon EC2 instances that are spread across multiple Availability Zones. Configure the service to forward data to an Amazon RDS Multi-AZ database.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: B
      Explanation: Amazon Kinesis Data Firehose is a data transfer service for loading streaming data into Amazon S3, Splunk, ElasticSearch, and RedShift. https://www.whizlabs.com/blog/aws-kinesis-data-streams-vs-aws-kinesis-data-firehose/
    </details>

57. A company is using a centralized AWS account to store log data in various Amazon S3 buckets. A solutions architect needs to ensure that the data is encrypted at rest before the data is uploaded to the S3 buckets. The data also must be encrypted in transit. Which solution meets these requirements?
    - A. Use client-side encryption to encrypt the data that is being uploaded to the S3 buckets.
    - B. Use server-side encryption to encrypt the data that is being uploaded to the S3 buckets.
    - C. Create bucket policies that require the use of server-side encryption with S3 managed encryption keys (SSE-S3) for S3 uploads.
    - D. Enable the security option to encrypt the S3 buckets through the use of a default AWS Key Management Service (AWS KMS) key.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: A
      Explanation: Data protection refers to protecting data while in-transit (as it travels to and from Amazon S3) and at rest (while it is stored on disks in Amazon S3 data centers). You can protect data in transit using Secure Socket Layer/Transport Layer Security (SSL/TLS) or client-side encryption. https://docs.aws.amazon.com/AmazonS3/latest/userguide/UsingEncryption.html
    </details>

58. A company has an on-premises business application that generates hundreds of files each day. These files are stored on an SMB file share and require a low- latency connection to the application servers. A new company policy states all application-generated files must be copied to AWS. There is already a VPN connection to AWS. The application development team does not have time to make the necessary code modifications to move the application to AWS. Which service should a solutions architect recommend to allow the application to copy files to AWS?
    - A. Amazon Elastic File System (Amazon EFS)
    - B. Amazon FSx for Windows File Server
    - C. AWS Snowball
    - D. AWS Storage Gateway

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: D
      Explanation: The files will be on the storgare gateway with low latency and copied to AWS as a second copy. FSx in AWS will not provide low latency for the on prem apps over a vpn to the FSx file system.
    </details>

59. A company has an ordering application that stores customer information in Amazon RDS for MySQL. During regular business hours, employees run one-time queries for reporting purposes. Timeouts are occurring during order processing because the reporting queries are taking a long time to run. The company needs to eliminate the timeouts without preventing employees from performing queries. What should a solutions architect do to meet these requirements?
    - A. Create a read replica. Move reporting queries to the read replica.
    - B. Create a read replica. Distribute the ordering application to the primary DB instance and the read replica.
    - C. Migrate the ordering application to Amazon DynamoDB with on-demand capacity.
    - D. Schedule the reporting queries for non-peak hours.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: A
      Explanation: Reporting is OK to run on replicated data with some delay in replication.
    </details>

60. A company runs a web application that is backed by Amazon RDS. A new database administrator caused data loss by accidentally editing information in a database table. To help recover from this type of incident, the company wants the ability to restore the database to its state from 5 minutes before any change within the last 30 days. Which feature should the solutions architect include in the design to meet this requirement?
    - A. Read replicas
    - B. Manual snapshots
    - C. Automated backups
    - D. Multi-AZ deployments

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: C
      Explanation: RDS creates automated backups of your volume snapshot in which you can recover to a specific point-in-time recovery. https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/USER_WorkingWithAutomatedBac kups.html
    </details>

61. A company uses Amazon RDS for PostgreSQL databases for its data tier. The company must implement password rotation for the databases. Which solution meets this requirement with the LEAST operational overhead?
    - A. Store the password in AWS Secrets Manager. Enable automatic rotation on the secret.
    - B. Store the password in AWS Systems Manager Parameter Store. Enable automatic rotation on the parameter.
    - C. Store the password in AWS Systems Manager Parameter Store. Write an AWS Lambda function that rotates the password.
    - D. Store the password in AWS Key Management Service (AWS KMS). Enable automatic rotation on the customer master key (CMK).

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: A
      Explanation: Only service that rotates credentials automatically is secrets manager. https://aws.amazon.com/secrets-manager/ https://docs.aws.amazon.com/systems-manager/latest/userguide/systems-manager-parameter- store.html (reference note)
    </details>

62. A company's facility has badge readers at every entrance throughout the building. When badges are scanned, the readers send a message over HTTPS to indicate who attempted to access that particular entrance. A solutions architect must design a system to process these messages from the sensors. The solution must be highly available, and the results must be made available for the company's security team to analyze. Which system architecture should the solutions architect recommend?
    - A. Launch an Amazon EC2 instance to serve as the HTTPS endpoint and to process the messages. Configure the EC2 instance to save the results to an Amazon S3 bucket.
    - B. Create an HTTPS endpoint in Amazon API Gateway. Configure the API Gateway endpoint to invoke an AWS Lambda function to process the messages and save the results to an Amazon DynamoDB table.
    - C. Use Amazon Route 53 to direct incoming sensor messages to an AWS Lambda function. Configure the Lambda function to process the messages and save the results to an Amazon DynamoDB table.
    - D. Create a gateway VPC endpoint for Amazon S3. Configure a Site-to-Site VPN connection from the facility network to the VPC so that sensor data can be written directly to an S3 bucket by way of the VPC endpoint.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: B
      Explanation: Deploy Amazon API Gateway as an HTTPS endpoint and AWS Lambda to process and save the messages to an Amazon DynamoDB table. This option provides a highly available and scalable solution that can easily handle large amounts of data. It also integrates with other AWS services, making it easier to analyze and visualize the data for the security team.
    </details>

63. An Amazon EC2 instance is located in a private subnet in a new VPC. This subnet does not have outbound internet access, but the EC2 instance needs the ability to download monthly security updates from an outside vendor. What should a solutions architect do to meet these requirements?
    - A. Create an internet gateway, and attach it to the VPC. Configure the private subnet route table to use the internet gateway as the default route.
    - B. Create a NAT gateway, and place it in a public subnet. Configure the private subnet route table to use the NAT gateway as the default route.
    - C. Create a NAT instance, and place it in the same subnet where the EC2 instance is located. Configure the private subnet route table to use the NAT instance as the default route.
    - D. Create an internet gateway, and attach it to the VPC. Create a NAT instance, and place it in the same subnet where the EC2 instance is located. Configure the private subnet route table to use the internet gateway as the default route.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: B
      Explanation: This approach will allow the EC2 instance to access the internet and download the monthly security updates while still being located in a private subnet. By creating a NAT gateway and placing it in a public subnet, it will allow the instances in the private subnet to access the internet through the NAT gateway. And then, configure the private subnet route table to use the NAT gateway as the default route. This will ensure that all outbound traffic is directed through the NAT gateway, allowing the EC2 instance to access the internet while still maintaining the security of the private subnet.
    </details>

64. A company has been running a web application with an Oracle relational database in an on- premises data center for the past 15 years. The company must migrate the database to AWS. The company needs to reduce operational overhead without having to modify the application's code. Which solution meets these requirements?
    - A. Use AWS Database Migration Service (AWS DMS) to migrate the database servers to Amazon RDS.
    - B. Use Amazon EC2 instances to migrate and operate the database servers.
    - C. Use AWS Database Migration Service (AWS DMS) to migrate the database servers to Amazon DynamoDB. - D. Use an AWS Snowball Edge Storage Optimized device to migrate the data from Oracle to Amazon Aurora.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: A
      Explanation: DMS can be used for database migration(supports cross database migration too). RDS supports MySQL, PostgreSQL, Microsoft SQL Server, Oracle. https://docs.aws.amazon.com/prescriptive-guidance/latest/patterns/migrate-an-on-premises- oracle-database-to-amazon-rds-for-oracle.html
    </details>

65. A company is running an application on Amazon EC2 instances. Traffic to the workload increases substantially during business hours and decreases afterward. The CPU utilization of an EC2 instance is a strong indicator of end-user demand on the application. The company has configured an Auto Scaling group to have a minimum group size of 2 EC2 instances and a maximum group size of 10 EC2 instances. The company is concerned that the current scaling policy that is associated with the Auto Scaling group might not be correct. The company must avoid over-provisioning EC2 instances and incurring unnecessary costs. What should a solutions architect recommend to meet these requirements?
    - A. Configure Amazon EC2 Auto Scaling to use a scheduled scaling plan and launch an additional 8 EC2 instances during business hours.
    - B. Configure AWS Auto Scaling to use a scaling plan that enables predictive scaling. Configure predictive scaling with a scaling mode of forecast and scale, and to enforce the maximum capacity setting during scaling.
    - C. Configure a step scaling policy to add 4 EC2 instances at 50% CPU utilization and add another 4 EC2 instances at 90% CPU utilization. Configure scale-in policies to perform the reverse and remove EC2 instances based on the two values.
    - D. Configure AWS Auto Scaling to have a desired capacity of 5 EC2 instances, and disable any existing scaling policies. Monitor the CPU utilization metric for 1 week. Then create dynamic scaling policies that are based on the observed values.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: B
      Explanation: Predictive Scaling, now natively supported as an EC2 Auto Scaling policy, uses machine learning to schedule the right number of EC2 instances in anticipation of approaching traffic changes. Predictive Scaling predicts future traffic, including regularly-occurring spikes, and provisions the right number of EC2 instances in advance. Predictive Scaling's machine learning algorithms detect changes in daily and weekly patterns, automatically adjusting their forecasts. This removes the need for manual adjustment of Auto Scaling parameters as cyclicality changes over time, making Auto Scaling simpler to configure. Auto Scaling enhanced with Predictive Scaling delivers faster, simpler, and more accurate capacity provisioning resulting in lower cost and more responsive applications.
    </details>
