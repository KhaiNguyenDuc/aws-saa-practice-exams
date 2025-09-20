---
layout: exam
---

# Practice Exam 8

1. A company is developing a microservices application that will provide a search catalog for
customers. The company must use REST APIs to present the frontend of the application to users. The REST APIs must access the backend services that the company hosts in containers in private VPC subnets. Which solution will meet these requirements?
    - A. Design a WebSocket API by using Amazon API Gateway. Host the application in Amazon Elastic Container Service (Amazon ECS) in a private subnet. Create a private VPC link for API Gateway to access Amazon ECS.
    - B. Design a REST API by using Amazon API Gateway. Host the application in Amazon Elastic Container Service (Amazon ECS) in a private subnet. Create a private VPC link for API Gateway to access Amazon ECS.
    - C. Design a WebSocket API by using Amazon API Gateway. Host the application in Amazon Elastic Container Service (Amazon ECS) in a private subnet. Create a security group for API Gateway to access Amazon ECS.
    - D. Design a REST API by using Amazon API Gateway. Host the application in Amazon Elastic Container Service (Amazon ECS) in a private subnet. Create a security group for API Gateway to access Amazon ECS.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: B
      Explanation: https://docs.aws.amazon.com/apigateway/latest/developerguide/http-api-private-integration.html
    </details>

2. A company has applications hosted on Amazon EC2 instances with IPv6 addresses. The applications must initiate communications with other external applications using the internet. However the company's security policy states that any external service cannot initiate a connection to the EC2 instances. What should a solutions architect recommend to resolve this issue?
    - A. Create a NAT gateway and make it the destination of the subnet's route table
    - B. Create an internet gateway and make it the destination of the subnet's route table
    - C. Create a virtual private gateway and make it the destination of the subnet's route table
    - D. Create an egress-only internet gateway and make it the destination of the subnet's route table

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: D
      Explanation: An egress-only internet gateway (EIGW) is specifically designed for IPv6-only VPCs and provides outbound IPv6 internet access while blocking inbound IPv6 traffic. It satisfies the requirement of preventing external services from initiating connections to the EC2 instances while allowing the instances to initiate outbound communications.
    </details>

3. A company is creating an application that runs on containers in a VPC. The application stores and accesses data in an Amazon S3 bucket. During the development phase, the application will store and access 1 TB of data in Amazon S3 each day. The company wants to minimize costs and wants to prevent traffic from traversing the internet whenever possible. Which solution will meet these requirements?
    - A. Enable S3 Intelligent-Tiering for the S3 bucket
    - B. Enable S3 Transfer Acceleration for the S3 bucket
    - C. Create a gateway VPC endpoint for Amazon S3. Associate this endpoint with all route tables in the VPC
    - D. Create an interface endpoint for Amazon S3 in the VPC. Associate this endpoint with all route tables in the VPC

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: C
      Explanation: Prevent traffic from traversing the internet = Gateway VPC endpoint for S3.
    </details>

4. A company hosts a website on Amazon EC2 instances behind an Application Load Balancer (ALB). The website serves static content. Website traffic is increasing, and the company is concerned
about a potential increase in cost.
    - A. Create an Amazon CloudFront distribution to cache state files at edge locations
    - B. Create an Amazon ElastiCache cluster. Connect the ALB to the ElastiCache cluster to serve cached files
    - C. Create an AWS WAF web ACL and associate it with the ALB. Add a rule to the web ACL to cache static files
    - D. Create a second ALB in an alternative AWS Region. Route user traffic to the closest Region to minimize data transfer costs

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: A
      Explanation: Amazon CloudFront: CloudFront is a content delivery network (CDN) service that caches content at edge locations worldwide. By creating a CloudFront distribution, static content from the website can be cached at edge locations, reducing the load on the EC2 instances and improving the overall performance. Caching Static Files: Since the website serves static content, caching these files at CloudFront edge locations can significantly reduce the number of requests forwarded to the EC2 instances. This helps to lower the overall cost by offloading traffic from the instances and reducing the data transfer costs.
    </details>

5. A company has multiple VPCs across AWS Regions to support and run workloads that are isolated from workloads in other Regions. Because of a recent application launch requirement, the company's VPCs must communicate with all other VPCs across all Regions. Which solution will meet these requirements with the LEAST amount of administrative effort?
    - A. Use VPC peering to manage VPC communication in a single Region. Use VPC peering across Regions to manage VPC communications.
    - B. Use AWS Direct Connect gateways across all Regions to connect VPCs across regions and manage VPC communications.
    - C. Use AWS Transit Gateway to manage VPC communication in a single Region and Transit Gateway peering across Regions to manage VPC communications.
    - D. Use AWS PrivateLink across all Regions to connect VPCs across Regions and manage VPC communications

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: C
      Explanation: AWS Transit Gateway: Transit Gateway is a highly scalable service that simplifies network connectivity between VPCs and on-premises networks. By using a Transit Gateway in a single Region, you can centralize VPC communication management and reduce administrative effort. Transit Gateway Peering: Transit Gateway supports peering connections across AWS Regions, allowing you to establish connectivity between VPCs in different Regions without the need for complex VPC peering configurations. This simplifies the management of VPC communications across Regions.
    </details>

6. A company is designing a containerized application that will use Amazon Elastic Container Service (Amazon ECS). The application needs to access a shared file system that is highly durable and can recover data to another AWS Region with a recovery point objective (RPO) of 8 hours. The file system needs to provide a mount target m each Availability Zone within a Region.
A solutions architect wants to use AWS Backup to manage the replication to another Region. Which solution will meet these requirements?
    - A. Amazon FSx for Windows File Server with a Multi-AZ deployment
    - B. Amazon FSx for NetApp ONTAP with a Multi-AZ deployment
    - C. Amazon Elastic File System (Amazon EFS) with the Standard storage class
    - D. Amazon FSx for OpenZFS

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: C
      Explanation: https://aws.amazon.com/efs/faq/ Q: What is Amazon EFS Replication? EFS Replication can replicate your file system data to another Region or within the same Region without requiring additional infrastructure or a custom process. Amazon EFS Replication automatically and transparently replicates your data to a second file system in a Region or AZ of your choice. You can use the Amazon EFS console, AWS CLI, and APIs to activate replication on an existing file system. EFS Replication is continual and provides a recovery point objective (RPO) and a recovery time objective (RTO) of minutes, helping you meet your compliance and business continuity goals.
    </details>

7. A company is expecting rapid growth in the near future. A solutions architect needs to configure existing users and grant permissions to new users on AWS. The solutions architect has decided to create IAM groups. The solutions architect will add the new users to IAM groups based on department. Which additional action is the MOST secure way to grant permissions to the new users?
    - A. Apply service control policies (SCPs) to manage access permissions
    - B. Create IAM roles that have least privilege permission. Attach the roles to the IAM groups
    - C. Create an IAM policy that grants least privilege permission. Attach the policy to the IAM groups
    - D. Create IAM roles. Associate the roles with a permissions boundary that defines the maximum permissions

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: C
      Explanation: https://docs.aws.amazon.com/IAM/latest/UserGuide/id_groups_manage_attach-policy.html Attaching a policy to an IAM user group.
    </details>

8. A law firm needs to share information with the public. The information includes hundreds of files that must be publicly readable. Modifications or deletions of the files by anyone before a designated future date are prohibited. Which solution will meet these requirements in the MOST secure way?
    - A. Upload all files to an Amazon S3 bucket that is configured for static website hosting. Grant read- only IAM permissions to any AWS principals that access the S3 bucket until the designated date.
    - B. Create a new Amazon S3 bucket with S3 Versioning enabled. Use S3 Object Lock with a retention period in accordance with the designated date. Configure the S3 bucket for static website hosting. Set an S3 bucket policy to allow read-only access to the objects.
    - C. Create a new Amazon S3 bucket with S3 Versioning enabled. Configure an event trigger to run an AWS Lambda function in case of object modification or deletion. Configure the Lambda function to replace the objects with the original versions from a private S3 bucket.
    - D. Upload all files to an Amazon S3 bucket that is configured for static website hosting. Select the folder that contains the files. Use S3 Object Lock with a retention period in accordance with the designated date. Grant read-only IAM permissions to any AWS principals that access the S3 bucket.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: B
      Explanation: https://docs.aws.amazon.com/AmazonS3/latest/userguide/object-lock.html
    </details>

9. A company is making a prototype of the infrastructure for its new website by manually provisioning the necessary infrastructure. This infrastructure includes an Auto Scaling group, an Application Load Balancer and an Amazon RDS database. After the configuration has been thoroughly validated, the company wants the capability to immediately deploy the infrastructure for development and production use in two Availability Zones in an automated fashion. What should a solutions architect recommend to meet these requirements?
    - A. Use AWS Systems Manager to replicate and provision the prototype infrastructure in two Availability Zones
    - B. Define the infrastructure as a template by using the prototype infrastructure as a guide. Deploy the infrastructure with AWS CloudFormation.
    - C. Use AWS Config to record the inventory of resources that are used in the prototype infrastructure. Use AWS Config to deploy the prototype infrastructure into two Availability Zones.
    - D. Use AWS Elastic Beanstalk and configure it to use an automated reference to the prototype infrastructure to automatically deploy new environments in two Availability Zones.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: B
      Explanation: AWS CloudFormation is a service that allows you to define and provision infrastructure as code. This means that you can create a template that describes the resources you want to create, and then use CloudFormation to deploy those resources in an automated fashion. In this case, the solutions architect should define the infrastructure as a template by using the prototype infrastructure as a guide. The template should include resources for an Auto Scaling group, an Application Load Balancer, and an Amazon RDS database. Once the template is created, the solutions architect can use CloudFormation to deploy the infrastructure in two Availability Zones.
    </details>

10. A business application is hosted on Amazon EC2 and uses Amazon S3 for encrypted object storage. The chief information security officer has directed that no application traffic between the two services should traverse the public internet. Which capability should the solutions architect use to meet the compliance requirements?
    - A. AWS Key Management Service (AWS KMS)
    - B. VPC endpoint
    - C. Private subnet
    - D. Virtual private gateway

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: B
      Explanation: A VPC endpoint enables you to privately access AWS services without requiring internet gateways, NAT gateways, VPN connections, or AWS Direct Connect connections. It allows you to connect your VPC directly to supported AWS services, such as Amazon S3, over a private connection within the AWS network. By creating a VPC endpoint for Amazon S3, the traffic between your EC2 instances and S3 will stay within the AWS network and won't traverse the public internet. This provides a more secure and compliant solution, as the data transfer remains within the private network boundaries.
    </details>

11. A company hosts a three-tier web application in the AWS Cloud. A Multi-AZAmazon RDS for MySQL server forms the database layer Amazon ElastiCache forms the cache layer. The company wants a caching strategy that adds or updates data in the cache when a customer adds an item to the database. The data in the cache must always match the data in the database. Which solution will meet these requirements?
    - A. Implement the lazy loading caching strategy
    - B. Implement the write-through caching strategy
    - C. Implement the adding TTL caching strategy
    - D. Implement the AWS AppConfig caching strategy

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: B
      Explanation: In the write-through caching strategy, when a customer adds or updates an item in the database, the application first writes the data to the database and then updates the cache with the same data.
      This ensures that the cache is always synchronized with the database, as every write operation triggers an update to the cache.
    </details>

12. A company wants to migrate 100 GB of historical data from an on-premises location to an Amazon S3 bucket. The company has a 100 megabits per second (Mbps) internet connection on premises. The company needs to encrypt the data in transit to the S3 bucket. The company will store new data directly in Amazon S3. Which solution will meet these requirements with the LEAST operational overhead?
    - A. Use the s3 sync command in the AWS CLI to move the data directly to an S3 bucket
    - B. Use AWS DataSync to migrate the data from the on-premises location to an S3 bucket
    - C. Use AWS Snowball to move the data to an S3 bucket
    - D. Set up an IPsec VPN from the on-premises location to AWS. Use the s3 cp command in the AWS CLI to move the data directly to an S3 bucket

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: B
      Explanation: AWS DataSync is a fully managed data transfer service that simplifies and automates the process of moving data between on-premises storage and Amazon S3. It provides secure and efficient data transfer with built-in encryption, ensuring that the data is encrypted in transit. By using AWS DataSync, the company can easily migrate the 100 GB of historical data from their on-premises location to an S3 bucket. DataSync will handle the encryption of data in transit and ensure secure transfer.
    </details>

13. A company containerized a Windows job that runs on .NET 6 Framework under a Windows container. The company wants to run this job in the AWS Cloud. The job runs every 10 minutes. The job's runtime varies between 1 minute and 3 minutes. Which solution will meet these requirements MOST cost-effectively?
    - A. Create an AWS Lambda function based on the container image of the job. Configure Amazon EventBridge to invoke the function every 10 minutes.
    - B. Use AWS Batch to create a job that uses AWS Fargate resources. Configure the job scheduling to run every 10 minutes.
    - C. Use Amazon Elastic Container Service (Amazon ECS) on AWS Fargate to run the job. Create a scheduled task based on the container image of the job to run every 10 minutes.
    - D. Use Amazon Elastic Container Service (Amazon ECS) on AWS Fargate to run the job. Create a standalone task based on the container image of the job. Use Windows task scheduler to run the job every 10 minutes.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: C
      Explanation: By leveraging AWS Fargate and ECS, you can achieve cost-effective scaling and resource allocation for your containerized Windows job running on .NET 6 Framework in the AWS Cloud. The serverless nature of Fargate ensures that you only pay for the actual resources consumed by your containers, allowing for efficient cost management.
    </details>

14. A company is looking for a solution that can store video archives in AWS from old news footage. The company needs to minimize costs and will rarely need to restore these files. When the files are needed, they must be available in a maximum of five minutes. What is the MOST cost-effective solution?
    - A. Store the video archives in Amazon S3 Glacier and use Expedited retrievals.
    - B. Store the video archives in Amazon S3 Glacier and use Standard retrievals.
    - C. Store the video archives in Amazon S3 Standard-Infrequent Access (S3 Standard-IA).
    - D. Store the video archives in Amazon S3 One Zone-Infrequent Access (S3 One Zone-IA).

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: A
      Explanation: By choosing Expedited retrievals in Amazon S3 Glacier, you can reduce the retrieval time to minutes, making it suitable for scenarios where quick access is required. Expedited retrievals come with a higher cost per retrieval compared to standard retrievals but provide faster access to your archived data.
    </details>

15. A company is building a three-tier application on AWS. The presentation tier will serve a static
website The logic tier is a containerized application. This application will store data in a relational database. The company wants to simplify deployment and to reduce operational costs. Which solution will meet these requirements?
    - A. Use Amazon S3 to host static content. Use Amazon Elastic Container Service (Amazon ECS) with AWS Fargate for compute power. Use a managed Amazon RDS cluster for the database.
    - B. Use Amazon CloudFront to host static content. Use Amazon Elastic Container Service (Amazon ECS) with Amazon EC2 for compute power. Use a managed Amazon RDS cluster for the database.
    - C. Use Amazon S3 to host static content. Use Amazon Elastic Kubernetes Service (Amazon EKS) with AWS Fargate for compute power. Use a managed Amazon RDS cluster for the database.
    - D. Use Amazon EC2 Reserved Instances to host static content. Use Amazon Elastic Kubernetes Service (Amazon EKS) with Amazon EC2 for compute power. Use a managed Amazon RDS cluster for the database.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: A
      Explanation: Amazon S3 is a highly scalable and cost-effective storage service that can be used to host static website content. It provides durability, high availability, and low latency access to the static files. Amazon ECS with AWS Fargate eliminates the need to manage the underlying infrastructure. It allows you to run containerized applications without provisioning or managing EC2 instances. This reduces operational overhead and provides scalability. By using a managed Amazon RDS cluster for the database, you can offload the management tasks such as backups, patching, and monitoring to AWS. This reduces the operational burden and ensures high availability and durability of the database.
    </details>

16. A company seeks a storage solution for its application. The solution must be highly available and scalable. The solution also must function as a file system be mountable by multiple Linux instances in AWS and on premises through native protocols, and have no minimum size requirements. The company has set up a Site-to-Site VPN for access from its on-premises network to its VPC. Which storage solution meets these requirements?
    - A. Amazon FSx Multi-AZ deployments
    - B. Amazon Elastic Block Store (Amazon EBS) Multi-Attach volumes
    - C. Amazon Elastic File System (Amazon EFS) with multiple mount targets
    - D. Amazon Elastic File System (Amazon EFS) with a single mount target and multiple access points

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: C
      Explanation: Amazon EFS is a fully managed file system service that provides scalable, shared storage for Amazon EC2 instances. It supports the Network File System version 4 (NFSv4) protocol, which is a native protocol for Linux-based systems. EFS is designed to be highly available, durable, and scalable.
    </details>

17. A 4-year-old media company is using the AWS Organizations all features feature set to organize its AWS accounts. According to the company's finance team, the billing information on the member accounts must not be accessible to anyone, including the root user of the member accounts. Which solution will meet these requirements?
    - A. Add all finance team users to an IAM group. Attach an AWS managed policy named Billing to the group.
    - B. Attach an identity-based policy to deny access to the billing information to all users, including the root user.
    - C. Create a service control policy (SCP) to deny access to the billing information. Attach the SCP to the root organizational unit (OU).
    - D. Convert from the Organizations all features feature set to the Organizations consolidated billing feature set.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: C
      Explanation: Service control policy are a type of organization policy that you can use to manage permissions in your organization. SCPs offer central control over the maximum available permissions for all accounts in your organization. SCPs help you to ensure your accounts stay within your organization's access control guidelines. SCPs are available only in an organization that has all features enabled.
    </details>

18. An ecommerce company runs an application in the AWS Cloud that is integrated with an on- premises warehouse solution. The company uses Amazon Simple Notification Service (Amazon SNS) to send order messages to an on-premises HTTPS endpoint so the warehouse application can process the orders. The local data center team has detected that some of the order messages were not received. A solutions architect needs to retain messages that are not delivered and analyze the messages for up to 14 days. Which solution will meet these requirements with the LEAST development effort?
    - A. Configure an Amazon SNS dead letter queue that has an Amazon Kinesis Data Stream target with a retention period of 14 days.
    - B. Add an Amazon Simple Queue Service (Amazon SQS) queue with a retention period of 14 days between the application and Amazon SNS.
    - C. Configure an Amazon SNS dead letter queue that has an Amazon Simple Queue Service (Amazon SQS) target with a retention period of 14 days.
    - D. Configure an Amazon SNS dead letter queue that has an Amazon DynamoDB target with a TTL attribute set for a retention period of 14 days.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: C
      Explanation: The message retention period in Amazon SQS can be set between 1 minute and 14 days (the default is 4 days). Therefore, you can configure your SQS DLQ to retain undelivered SNS messages for 14 days. This will enable you to analyze undelivered messages with the least development effort.
    </details>

19. A gaming company uses Amazon DynamoDB to store user information such as geographic location, player data, and leaderboards. The company needs to configure continuous backups to an Amazon S3 bucket with a minimal amount of coding. The backups must not affect availability of the application and must not affect the read capacity units (RCUs) that are defined for the table. Which solution meets these requirements?
    - A. Use an Amazon EMR cluster. Create an Apache Hive job to back up the data to Amazon S3.
    - B. Export the data directly from DynamoDB to Amazon S3 with continuous backups. Turn on point-in- time recovery for the table.
    - C. Configure Amazon DynamoDB Streams. Create an AWS Lambda function to consume the stream and export the data to an Amazon S3 bucket.
    - D. Create an AWS Lambda function to export the data from the database tables to Amazon S3 on a regular basis. Turn on point-in-time recovery for the table.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: B
      Explanation: Continuous backups is a native feature of DynamoDB, it works at any scale without having to manage servers or clusters and allows you to export data across AWS Regions and accounts to any point-in-time in the last 35 days at a per-second granularity. Plus, it doesn't affect the read capacity or the availability of your production tables. https://aws.amazon.com/blogs/aws/new-export-amazon-dynamodb-table-data-to-data-lake- amazon-s3/
    </details>

20. A solutions architect is designing an asynchronous application to process credit card data validation requests for a bank. The application must be secure and be able to process each request at least once. Which solution will meet these requirements MOST cost-effectively?
    - A. Use AWS Lambda event source mapping. Set Amazon Simple Queue Service (Amazon SQS) standard queues as the event source. Use AWS Key Management Service (SSE-KMS) for encryption. Add the kms:Decrypt permission for the Lambda execution role.
    - B. Use AWS Lambda event source mapping. Use Amazon Simple Queue Service (Amazon SQS) FIFO queues as the event source. Use SQS managed encryption keys (SSE-SQS) for encryption. Add the encryption key invocation permission for the Lambda function.
    - C. Use the AWS Lambda event source mapping. Set Amazon Simple Queue Service (Amazon SQS) FIFO queues as the event source. Use AWS KMS keys (SSE-KMS). Add the kms:Decrypt permission for the Lambda execution role.
    - D. Use the AWS Lambda event source mapping. Set Amazon Simple Queue Service (Amazon SQS) standard queues as the event source. Use AWS KMS keys (SSE-KMS) for encryption. Add the encryption key invocation permission for the Lambda function.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: A
      Explanation: https://docs.aws.amazon.com/zh_tw/AWSSimpleQueueService/latest/SQSDeveloperGuide/sqs- least-privilege-policy.html
    </details>

21. A company has multiple AWS accounts for development work. Some staff consistently use oversized Amazon EC2 instances, which causes the company to exceed the yearly budget for the development accounts. The company wants to centrally restrict the creation of AWS resources in these accounts. Which solution will meet these requirements with the LEAST development effort?
    - A. Develop AWS Systems Manager templates that use an approved EC2 creation process. Use the approved Systems Manager templates to provision EC2 instances.
    - B. Use AWS Organizations to organize the accounts into organizational units (OUs). Define and attach a service control policy (SCP) to control the usage of EC2 instance types.
    - C. Configure an Amazon EventBridge rule that invokes an AWS Lambda function when an EC2 instance is created. Stop disallowed EC2 instance types.
    - D. Set up AWS Service Catalog products for the staff to create the allowed EC2 instance types. Ensure that staff can deploy EC2 instances only by using the Service Catalog products.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: B
      Explanation: AWS Organizations: AWS Organizations is a service that helps you centrally manage multiple AWS accounts. It enables you to group accounts into organizational units (OUs) and apply policies across those accounts. Service Control Policies (SCPs): SCPs in AWS Organizations allow you to define fine-grained permissions and restrictions at the account or OU level. By attaching an SCP to the development accounts, you can control the creation and usage of EC2 instance types. Least Development Effort: Option B requires minimal development effort as it leverages the built- in features of AWS Organizations and SCPs. You can define the SCP to restrict the use of oversized EC2 instance types and apply it to the appropriate OUs or accounts.
    </details>

22. A company is conducting an internal audit. The company wants to ensure that the data in an Amazon S3 bucket that is associated with the company's AWS Lake Formation data lake does not contain sensitive customer or employee data. The company wants to discover personally identifiable information (PII) or financial information, including passport numbers and credit card numbers. Which solution will meet these requirements?
    - A. Configure AWS Audit Manager on the account. Select the Payment Card Industry Data Security Standards (PCI DSS) for auditing.
    - B. Configure Amazon S3 Inventory on the S3 bucket Configure Amazon Athena to query the inventory.
    - C. Configure Amazon Macie to run a data discovery job that uses managed identifiers for the required data types.
    - D. Use Amazon S3 Select to run a report across the S3 bucket.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: C
      Explanation: Amazon Macie is a service that helps discover, classify, and protect sensitive data stored in AWS. It uses machine learning algorithms and managed identifiers to detect various types of sensitive information, including personally identifiable information (PII) and financial information. By configuring Amazon Macie to run a data discovery job with the appropriate managed identifiers for the required data types (such as passport numbers and credit card numbers), the company can identify and classify any sensitive data present in the S3 bucket.
    </details>

23. A company has a service that reads and writes large amounts of data from an Amazon S3 bucket in the same AWS Region. The service is deployed on Amazon EC2 instances within the private subnet of a VPC. The service communicates with Amazon S3 over a NAT gateway in the public subnet. However, the company wants a solution that will reduce the data output costs. Which solution will meet these requirements MOST cost-effectively?
    - A. Provision a dedicated EC2 NAT instance in the public subnet. Configure the route table for the private subnet to use the elastic network interface of this instance as the destination for all S3 traffic.
    - B. Provision a dedicated EC2 NAT instance in the private subnet. Configure the route table for the public subnet to use the elastic network interface of this instance as the destination for all S3 traffic.
    - C. Provision a VPC gateway endpoint. Configure the route table for the private subnet to use the gateway endpoint as the route for all S3 traffic.
    - D. Provision a second NAT gateway. Configure the route table for the private subnet to use this NAT gateway as the destination for all S3 traffic.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: C
      Explanation: A VPC gateway endpoint allows you to privately access Amazon S3 from within your VPC without using a NAT gateway or NAT instance. By provisioning a VPC gateway endpoint for S3, the service in the private subnet can directly communicate with S3 without incurring data transfer costs for traffic going through a NAT gateway.
    </details>

24. A company uses Amazon S3 to store high-resolution pictures in an S3 bucket. To minimize application changes, the company stores the pictures as the latest version of an S3 object. The company needs to retain only the two most recent versions of the pictures. The company wants to reduce costs. The company has identified the S3 bucket as a large expense. Which solution will reduce the S3 costs with the LEAST operational overhead?
    - A. Use S3 Lifecycle to delete expired object versions and retain the two most recent versions.
    - B. Use an AWS Lambda function to check for older versions and delete all but the two most recent versions.
    - C. Use S3 Batch Operations to delete noncurrent object versions and retain only the two most recent versions.
    - D. Deactivate versioning on the S3 bucket and retain the two most recent versions.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: A
      Explanation: S3 Lifecycle policies allow you to define rules that automatically transition or expire objects based on their age or other criteria. By configuring an S3 Lifecycle policy to delete expired object versions and retain only the two most recent versions, you can effectively manage the storage costs while maintaining the desired retention policy. This solution is highly automated and requires minimal operational overhead as the lifecycle management is handled by S3 itself.
    </details>

25. A company needs to minimize the cost of its 1 Gbps AWS Direct Connect connection. The company's average connection utilization is less than 10%. A solutions architect must recommend a solution that will reduce the cost without compromising security. Which solution will meet these requirements?
    - A. Set up a new 1 Gbps Direct Connect connection. Share the connection with another AWS account.
    - B. Set up a new 200 Mbps Direct Connect connection in the AWS Management Console.
    - C. Contact an AWS Direct Connect Partner to order a 1 Gbps connection. Share the connection with another AWS account.
    - D. Contact an AWS Direct Connect Partner to order a 200 Mbps hosted connection for an existing AWS account.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: D
      Explanation: For Dedicated Connections, 1 Gbps, 10 Gbps, and 100 Gbps ports are available. For Hosted Connections, connection speeds of 50 Mbps, 100 Mbps, 200 Mbps, 300 Mbps, 400 Mbps, 500
      Mbps, 1 Gbps, 2 Gbps, 5 Gbps and 10 Gbps may be ordered from approved AWS Direct Connect Partners.
    </details>

26. A company wants to ingest customer payment data into the company's data lake in Amazon S3. The company receives payment data every minute on average. The company wants to analyze the payment data in real time. Then the company wants to ingest the data into the data lake. Which solution will meet these requirements with the MOST operational efficiency?
    - A. Use Amazon Kinesis Data Streams to ingest data. Use AWS Lambda to analyze the data in real time.
    - B. Use AWS Glue to ingest data. Use Amazon Kinesis Data Analytics to analyze the data in real time.
    - C. Use Amazon Kinesis Data Firehose to ingest data. Use Amazon Kinesis Data Analytics to analyze the data in real time.
    - D. Use Amazon API Gateway to ingest data. Use AWS Lambda to analyze the data in real time.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: C
      Explanation: By leveraging the combination of Amazon Kinesis Data Firehose and Amazon Kinesis Data Analytics, you can efficiently ingest and analyze the payment data in real time without the need for
      manual processing or additional infrastructure management. This solution provides a streamlined and scalable approach to handle continuous data ingestion and analysis requirements.
    </details>

27. A company runs an infrastructure monitoring service. The company is building a new feature that will enable the service to monitor data in customer AWS accounts. The new feature will call AWS APIs in customer accounts to describe Amazon EC2 instances and read Amazon CloudWatch metrics. What should the company do to obtain access to customer accounts in the MOST secure way?
    - A. Ensure that the customers create an IAM role in their account with read-only EC2 and CloudWatch permissions and a trust policy to the company's account.
    - B. Create a serverless API that implements a token vending machine to provide temporary AWS credentials for a role with read-only EC2 and CloudWatch permissions.
    - C. Ensure that the customers create an IAM user in their account with read-only EC2 and CloudWatch permissions. Encrypt and store customer access and secret keys in a secrets management system.
    - D. Ensure that the customers create an Amazon Cognito user in their account to use an IAM role with read-only EC2 and CloudWatch permissions. Encrypt and store the Amazon Cognito user and password in a secrets management system.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: A
      Explanation: By having customers create an IAM role with the necessary permissions in their own accounts, the
      company can use AWS Identity and Access Management (IAM) to establish cross-account access. The trust policy allows the company's AWS account to assume the customer's IAM role temporarily, granting access to the specified resources (EC2 instances and CloudWatch metrics) within the customer's account. This approach follows the principle of least privilege, as the company only requests the necessary permissions and does not require long-term access keys or user credentials from the customers.
    </details>

28. A company needs to connect several VPCs in the us-east-1 Region that span hundreds of AWS accounts. The company's networking team has its own AWS account to manage the cloud network. What is the MOST operationally efficient solution to connect the VPCs?
    - A. Set up VPC peering connections between each VPC. Update each associated subnet's route table
    - B. Configure a NAT gateway and an internet gateway in each VPC to connect each VPC through the internet
    - C. Create an AWS Transit Gateway in the networking team's AWS account. Configure static routes from each VPC. - D. Deploy VPN gateways in each VPC. Create a transit VPC in the networking team's AWS account to connect to each VPC. 

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: C
      Explanation: WS Transit Gateway is a highly scalable and centralized hub for connecting multiple VPCs, on- premises networks, and remote networks. It simplifies network connectivity by providing a single entry point and reducing the number of connections required. In this scenario, deploying an AWS Transit Gateway in the networking team's AWS account allows for efficient management and control over the network connectivity across multiple VPCs.
    </details>

29. A company has Amazon EC2 instances that run nightly batch jobs to process data. The EC2 instances run in an Auto Scaling group that uses On-Demand billing. If a job fails on one instance, another instance will reprocess the job. The batch jobs run between 12:00 AM and 06:00 AM local time every day. Which solution will provide EC2 instances to meet these requirements MOST cost-effectively?
    - A. Purchase a 1-year Savings Plan for Amazon EC2 that covers the instance family of the Auto Scaling group that the batch job uses.
    - B. Purchase a 1-year Reserved Instance for the specific instance type and operating system of the instances in the Auto Scaling group that the batch job uses.
    - C. Create a new launch template for the Auto Scaling group. Set the instances to Spot Instances. Set a policy to scale out based on CPU usage.
    - D. Create a new launch template for the Auto Scaling group. Increase the instance size. Set a policy to scale out based on CPU usage.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: C
      Explanation: Purchasing a 1-year Savings Plan (option A) or a 1-year Reserved Instance (option B) may provide cost savings, but they are more suitable for long-running, steady-state workloads. Since your batch jobs run for a specific period each day, using Spot Instances with the ability to scale out based on CPU usage is a more cost-effective choice.
    </details>

30. A social media company is building a feature for its website. The feature will give users the ability to upload photos. The company expects significant increases in demand during large events and must ensure that the website can handle the upload traffic from users. Which solution meets these requirements with the MOST scalability?
    - A. Upload files from the user's browser to the application servers. Transfer the files to an Amazon S3 bucket.
    - B. Provision an AWS Storage Gateway file gateway. Upload files directly from the user's browser to the file gateway.
    - C. Generate Amazon S3 presigned URLs in the application. Upload files directly from the user's browser into an S3 bucket.
    - D. Provision an Amazon Elastic File System (Amazon EFS) file system. Upload files directly from the user's browser to the file system.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: C
      Explanation: This approach allows users to upload files directly to S3 without passing through the application servers, reducing the load on the application and improving scalability. It leverages the client-side capabilities to handle the file uploads and offloads the processing to S3.
    </details>

31. A company has a web application for travel ticketing. The application is based on a database that runs in a single data center in North America. The company wants to expand the application to serve a global user base. The company needs to deploy the application to multiple AWS Regions. Average latency must be less than 1 second on updates to the reservation database. The company wants to have separate deployments of its web platform across multiple Regions. However, the company must maintain a single primary reservation database that is globally consistent. Which solution should a solutions architect recommend to meet these requirements?
    - A. Convert the application to use Amazon DynamoDB. Use a global table for the center reservation table. Use the correct Regional endpoint in each Regional deployment.
    - B. Migrate the database to an Amazon Aurora MySQL database. Deploy Aurora Read Replicas in each Region. Use the correct Regional endpoint in each Regional deployment for access to the database.
    - C. Migrate the database to an Amazon RDS for MySQL database. Deploy MySQL read replicas in each Region. Use the correct Regional endpoint in each Regional deployment for access to the database.
    - D. Migrate the application to an Amazon Aurora Serverless database. Deploy instances of the database to each Region. Use the correct Regional endpoint in each Regional deployment to access the database. Use AWS Lambda functions to process event streams in each Region to synchronize the databases.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: A
      Explanation: Using DynamoDB's global tables feature, you can achieve a globally consistent reservation database with low latency on updates, making it suitable for serving a global user base. The automatic replication provided by DynamoDB eliminates the need for manual synchronization between Regions.
    </details>

32. A company operates a two-tier application for image processing. The application uses two Availability Zones, each with one public subnet and one private subnet. An Application Load Balancer (ALB) for the web tier uses the public subnets. Amazon EC2 instances for the application tier use the private subnets. Users report that the application is running more slowly than expected. A security audit of the web server log files shows that the application is receiving millions of illegitimate requests from a small number of IP addresses. A solutions architect needs to resolve the immediate performance problem while the company investigates a more permanent solution. What should the solutions architect recommend to meet this requirement?
    - A. Modify the inbound security group for the web tier. Add a deny rule for the IP addresses that are consuming resources.
    - B. Modify the network ACL for the web tier subnets. Add an inbound deny rule for the IP addresses that are consuming resources.
    - C. Modify the inbound security group for the application tier. Add a deny rule for the IP addresses that are consuming resources.
    - D. Modify the network ACL for the application tier subnets. Add an inbound deny rule for the IP addresses that are consuming resources.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: B
      Explanation: In this scenario, the security audit reveals that the application is receiving millions of illegitimate requests from a small number of IP addresses. To address this issue, it is recommended to modify the network ACL (Access Control List) for the web tier subnets. By adding an inbound deny rule specifically targeting the IP addresses that are consuming resources, the network ACL can block the illegitimate traffic at the subnet level before it reaches the web servers. This will help alleviate the excessive load on the web tier and improve the application's performance.
    </details>

33. A global marketing company has applications that run in the ap-southeast-2 Region and the eu- west-1 Region. Applications that run in a VPC in eu-west-1 need to communicate securely with databases that run in a VPC in ap-southeast-2. Which network design will meet these requirements?
    - A. Create a VPC peering connection between the eu-west-1 VPC and the ap-southeast-2 VPC. Create an inbound rule in the eu-west-1 application security group that allows traffic from the database server IP addresses in the ap-southeast-2 security group.
    - B. Configure a VPC peering connection between the ap-southeast-2 VPC and the eu-west-1 VPC. Update the subnet route tables. Create an inbound rule in the ap-southeast-2 database security group that references the security group ID of the application servers in eu-west-1.
    - C. Configure a VPC peering connection between the ap-southeast-2 VPC and the eu-west-1 VPUpdate the subnet route tables. Create an inbound rule in the ap-southeast-2 database security group that allows traffic from the eu-west-1 application server IP addresses.
    - D. Create a transit gateway with a peering attachment between the eu-west-1 VPC and the ap- southeast-2 VPC. After the transit gateways are properly peered and routing is configured, create an inbound rule in the database security group that references the security group ID of the application servers in eu-west-1.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: C
      Explanation: You cannot reference the security group of a peer VPC that's in a different Region. Instead, use the CIDR block of the peer VPC. https://docs.aws.amazon.com/vpc/latest/peering/vpc-peering-security-groups.html
    </details>

34. A company is developing software that uses a PostgreSQL database schema. The company needs to configure multiple development environments and databases for the company's developers. On average, each development environment is used for half of the 8-hour workday. Which solution will meet these requirements MOST cost-effectively?
    - A. Configure each development environment with its own Amazon Aurora PostgreSQL database
    - B. Configure each development environment with its own Amazon RDS for PostgreSQL Single-AZ DB instances
    - C. Configure each development environment with its own Amazon Aurora On-Demand PostgreSQL- Compatible database
    - D. Configure each development environment with its own Amazon S3 bucket by using Amazon S3 Object Select

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: C
      Explanation: With Aurora Serverless, you create a database, specify the desired database capacity range, and connect your applications. You pay on a per-second basis for the database capacity that you use when the database is active, and migrate between standard and serverless configurations with a few steps in the Amazon Relational Database Service (Amazon RDS) console.
    </details>

35. A company uses AWS Organizations with resources tagged by account. The company also uses AWS Backup to back up its AWS infrastructure resources. The company needs to back up all AWS resources. Which solution will meet these requirements with the LEAST operational overhead?
    - A. Use AWS Config to identify all untagged resources. Tag the identified resources programmatically. Use tags in the backup plan.
    - B. Use AWS Config to identify all resources that are not running. Add those resources to the backup vault.
    - C. Require all AWS account owners to review their resources to identify the resources that need to be backed up.
    - D. Use Amazon Inspector to identify all noncompliant resources.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: A
      Explanation: This solution allows you to leverage AWS Config to identify any untagged resources within your AWS Organizations accounts. Once identified, you can programmatically apply the necessary tags to indicate the backup requirements for each resource. By using tags in the backup plan configuration, you can ensure that only the tagged resources are included in the backup process, reducing operational overhead and ensuring all necessary resources are backed up.
    </details>

36. A social media company wants to allow its users to upload images in an application that is hosted in the AWS Cloud. The company needs a solution that automatically resizes the images so that the images can be displayed on multiple device types. The application experiences unpredictable traffic patterns throughout the day. The company is seeking a highly available solution that maximizes scalability. What should a solutions architect do to meet these requirements?
    - A. Create a static website hosted in Amazon S3 that invokes AWS Lambda functions to resize the images and store the images in an Amazon S3 bucket.
    - B. Create a static website hosted in Amazon CloudFront that invokes AWS Step Functions to resize the images and store the images in an Amazon RDS database.
    - C. Create a dynamic website hosted on a web server that runs on an Amazon EC2 instance. Configure a process that runs on the EC2 instance to resize the images and store the images in an Amazon S3 bucket.
    - D. Create a dynamic website hosted on an automatically scaling Amazon Elastic Container Service (Amazon ECS) cluster that creates a resize job in Amazon Simple Queue Service (Amazon SQS). Set up an image-resizing program that runs on an Amazon EC2 instance to process the resize jobs.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: A
      Explanation: By using Amazon S3 and AWS Lambda together, you can create a serverless architecture that provides highly scalable and available image resizing capabilities. Here's how the solution would
      work: Set up an Amazon S3 bucket to store the original images uploaded by users. Configure an event trigger on the S3 bucket to invoke an AWS Lambda function whenever a new image is uploaded. The Lambda function can be designed to retrieve the uploaded image, perform the necessary resizing operations based on device requirements, and store the resized images back in the S3 bucket or a different bucket designated for resized images. Configure the Amazon S3 bucket to make the resized images publicly accessible for serving to users.
    </details>

37. A company is running a microservices application on Amazon EC2 instances. The company wants to migrate the application to an Amazon Elastic Kubernetes Service (Amazon EKS) cluster for scalability. The company must configure the Amazon EKS control plane with endpoint private access set to true and endpoint public access set to false to maintain security compliance. The company must also put the data plane in private subnets. However, the company has received error notifications because the node cannot join the cluster. Which solution will allow the node to join the cluster?
    - A. Grant the required permission in AWS Identity and Access Management (IAM) to the AmazonEKSNodeRole IAM role.
    - B. Create interface VPC endpoints to allow nodes to access the control plane.
    - C. Recreate nodes in the public subnet. Restrict security groups for EC2 nodes.
    - D. Allow outbound traffic in the security group of the nodes.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: B
      Explanation: By creating interface VPC endpoints, you can enable the necessary communication between the Amazon EKS control plane and the nodes in private subnets. This solution ensures that the control plane maintains endpoint private access (set to true) and endpoint public access (set to false) for security compliance.
    </details>

38. A company provides an API interface to customers so the customers can retrieve their financial information. 舎e company expects a larger number of requests during peak usage times of the year. The company requires the API to respond consistently with low latency to ensure customer satisfaction. The company needs to provide a compute host for the API. Which solution will meet these requirements with the LEAST operational overhead?
    - A. Use an Application Load Balancer and Amazon Elastic Container Service (Amazon ECS).
    - B. Use Amazon API Gateway and AWS Lambda functions with provisioned concurrency.
    - C. Use an Application Load Balancer and an Amazon Elastic Kubernetes Service (Amazon EKS) cluster.
    - D. Use Amazon API Gateway and AWS Lambda functions with reserved concurrency.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: B
      Explanation: In the context of the given scenario, where the company wants low latency and consistent performance for their API during peak usage times, it would be more suitable to use provisioned concurrency. By allocating a specific number of concurrent executions, the company can ensure that there are enough function instances available to handle the expected load and minimize the impact of cold starts. This will result in lower latency and improved performance for the API.
    </details>

39. A company wants to send all AWS Systems Manager Session Manager logs to an Amazon S3 bucket for archival purposes. Which solution will meet this requirement with the MOST operational efficiency?
    - A. Enable S3 logging in the Systems Manager console. Choose an S3 bucket to send the session data to.
    - B. Install the Amazon CloudWatch agent. Push all logs to a CloudWatch log group. Export the logs to an S3 bucket from the group for archival purposes.
    - C. Create a Systems Manager document to upload all server logs to a central S3 bucket. Use Amazon EventBridge to run the Systems Manager document against all servers that are in the account daily.
    - D. Install an Amazon CloudWatch agent. Push all logs to a CloudWatch log group. Create a CloudWatch logs subscription that pushes any incoming log events to an Amazon Kinesis Data Firehose delivery stream. Set Amazon S3 as the destination.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: A
      Explanation: https://docs.aws.amazon.com/systems-manager/latest/userguide/session-manager-logging.html
    </details>

40. An application uses an Amazon RDS MySQL DB instance. The RDS database is becoming low on
disk space. A solutions architect wants to increase the disk space without downtime. Which solution meets these requirements with the LEAST amount of effort?
    - A. Enable storage autoscaling in RDS
    - B. Increase the RDS database instance size
    - C. Change the RDS database instance storage type to Provisioned IOPS
    - D. Back up the RDS database, increase the storage capacity, restore the database, and stop the previous instance

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: A
      Explanation: Enabling storage autoscaling allows RDS to automatically adjust the storage capacity based on the application's needs. When the storage usage exceeds a predefined threshold, RDS will automatically increase the allocated storage without requiring manual intervention or causing downtime. This ensures that the RDS database has sufficient disk space to handle the increasing storage requirements.
    </details>

41. A consulting company provides professional services to customers worldwide. The company provides solutions and tools for customers to expedite gathering and analyzing data on AWS. The company needs to centrally manage and deploy a common set of solutions and tools for customers to use for self-service purposes. Which solution will meet these requirements?
    - A. Create AWS CloudFormation templates for the customers.
    - B. Create AWS Service Catalog products for the customers.
    - C. Create AWS Systems Manager templates for the customers.
    - D. Create AWS Config items for the customers.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: B
      Explanation: AWS Service Catalog allows you to create and manage catalogs of IT services that can be deployed within your organization. With Service Catalog, you can define a standardized set of products (solutions and tools in this case) that customers can self-service provision. By creating Service Catalog products, you can control and enforce the deployment of approved and validated solutions and tools.
    </details>

42. A company is designing a new web application that will run on Amazon EC2 Instances. The application will use Amazon DynamoDB for backend data storage. The application traffic will be unpredictable. The company expects that the application read and write throughput to the database will be moderate to high. The company needs to scale in response to application traffic. Which DynamoDB table configuration will meet these requirements MOST cost-effectively?
    - A. Configure DynamoDB with provisioned read and write by using the DynamoDB Standard table class. Set DynamoDB auto scaling to a maximum defined capacity.
    - B. Configure DynamoDB in on-demand mode by using the DynamoDB Standard table class.
    - C. Configure DynamoDB with provisioned read and write by using the DynamoDB Standard Infrequent Access (DynamoDB Standard-IA) table class. Set DynamoDB auto scaling to a maximum defined
capacity.
    - D. Configure DynamoDB in on-demand mode by using the DynamoDB Standard Infrequent Access (DynamoDB Standard-IA) table class.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: B
      Explanation: AWS Service Catalog allows you to create and manage catalogs of IT services that can be deployed within your organization. With Service Catalog, you can define a standardized set of products (solutions and tools in this case) that customers can self-service provision. By creating Service Catalog products, you can control and enforce the deployment of approved and validated solutions and tools.
    </details>

43. A retail company has several businesses. The IT team for each business manages its own AWS account. Each team account is part of an organization in AWS Organizations. Each team monitors its product inventory levels in an Amazon DynamoDB table in the team's own AWS account. The company is deploying a central inventory reporting application into a shared AWS account. The application must be able to read items from all the teams' DynamoDB tables. Which authentication option will meet these requirements MOST securely?
    - A. Integrate DynamoDB with AWS Secrets Manager in the inventory application account. Configure the application to use the correct secret from Secrets Manager to authenticate and read the DynamoDB table. Schedule secret rotation for every 30 days.
    - B. In every business account, create an IAM user that has programmatic access. Configure the application to use the correct IAM user access key ID and secret access key to authenticate and read the DynamoDB table. Manually rotate IAM access keys every 30 days.
    - C. In every business account, create an IAM role named BU_ROLE with a policy that gives the role access to the DynamoDB table and a trust policy to trust a specific role in the inventory application account. In the inventory account, create a role named APP_ROLE that allows access to the STS AssumeRole API operation. Configure the application to use APP_ROLE and assume the crossaccount role BU_ROLE to read the DynamoDB table.
    - D. Integrate DynamoDB with AWS Certificate Manager (ACM). Generate identity certificates to authenticate DynamoDB. Configure the application to use the correct certificate to authenticate and read the DynamoDB table.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: C
      Explanation: IAM Roles: IAM roles provide a secure way to grant permissions to entities within AWS. By creating an IAM role in each business account named BU_ROLE with the necessary permissions to access the DynamoDB table, the access can be controlled at the IAM role level. Cross-Account Access: By configuring a trust policy in the BU_ROLE that trusts a specific role in the inventory application account (APP_ROLE), you establish a trusted relationship between the two accounts. Least Privilege: By creating a specific IAM role (BU_ROLE) in each business account and granting it access only to the required DynamoDB table, you can ensure that each team's table is accessed with the least privilege principle. Security Token Service (STS): The use of STS AssumeRole API operation in the inventory application account allows the application to assume the cross-account role (BU_ROLE) in each business account.
    </details>

44. A company runs a microservice-based serverless web application. The application must be able to retrieve data from multiple Amazon DynamoDB tables A solutions architect needs to give the application the ability to retrieve the data with no impact on the baseline performance of the application. Which solution will meet these requirements in the MOST operationally efficient way?
    - A. AWS AppSync pipeline resolvers
    - B. Amazon CloudFront with Lambda@Edge functions
    - C. Edge-optimized Amazon API Gateway with AWS Lambda functions
    - D. Amazon Athena Federated Query with a DynamoDB connector

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: D
      Explanation: The Amazon Athena DynamoDB connector enables Amazon Athena to communicate with DynamoDB so that you can query your tables with SQL. Write operations like INSERT INTO are not supported.
    </details>

45. A company wants to analyze and troubleshoot Access Denied errors and Unauthorized errors that are related to IAM permissions. The company has AWS CloudTrail turned on. Which solution will meet these requirements with the LEAST effort?
    - A. Use AWS Glue and write custom scripts to query CloudTrail logs for the errors.
    - B. Use AWS Batch and write custom scripts to query CloudTrail logs for the errors.
    - C. Search CloudTrail logs with Amazon Athena queries to identify the errors.
    - D. Search CloudTrail logs with Amazon QuickSight. Create a dashboard to identify the errors.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: C
      Explanation: "Using Athena with CloudTrail logs is a powerful way to enhance your analysis of AWS service activity." https://docs.aws.amazon.com/athena/latest/ug/cloudtrail-logs.html
    </details>

46. A company wants to add its existing AWS usage cost to its operation cost dashboard. A solutions architect needs to recommend a solution that will give the company access to its usage cost programmatically. The company must be able to access cost data for the current year and forecast costs for the next 12 months. Which solution will meet these requirements with the LEAST operational overhead?
    - A. Access usage cost-related data by using the AWS Cost Explorer API with pagination.
    - B. Access usage cost-related data by using downloadable AWS Cost Explorer report .csv files.
    - C. Configure AWS Budgets actions to send usage cost data to the company through FTP.
    - D. Create AWS Budgets reports for usage cost data. Send the data to the company through SMTP.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: A
      Explanation: You can view your costs and usage using the Cost Explorer user interface free of charge. You can also access your data programmatically using the Cost Explorer API. Each paginated API request incurs a charge of $0.01. You can't disable Cost Explorer after you enable it. https://docs.aws.amazon.com/cost-management/latest/userguide/ce-what-is.html https://docs.aws.amazon.com/AWSJavaScriptSDK/v3/latest/clients/client-cost- explorer/interfaces/costexplorerpaginationconfiguration.html
    </details>

47. A solutions architect is reviewing the resilience of an application. The solutions architect notices that a database administrator recently failed over the application's Amazon Aurora PostgreSQL database writer instance as part of a scaling exercise. The failover resulted in 3 minutes of downtime for the application. Which solution will reduce the downtime for scaling exercises with the LEAST operational overhead?
    - A. Create more Aurora PostgreSQL read replicas in the cluster to handle the load during failover.
    - B. Set up a secondary Aurora PostgreSQL cluster in the same AWS Region. During failover, update the application to use the secondary cluster's writer endpoint.
    - C. Create an Amazon ElastiCache for Memcached cluster to handle the load during failover.
    - D. Set up an Amazon RDS proxy for the database. Update the application to use the proxy endpoint.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: D
      Explanation: Amazon RDS proxy allows you to automatically route write request to the healthy writer, minimizing downtime.
    </details>

48. A company has a regional subscription-based streaming service that runs in a single AWS Region. The architecture consists of web servers and application servers on Amazon EC2 instances. The EC2 instances are in Auto Scaling groups behind Elastic Load Balancers. The architecture includes an Amazon Aurora global database cluster that extends across multiple Availability Zones.
The company wants to expand globally and to ensure that its application has minimal downtime. Which solution will provide the MOST fault tolerance?
    - A. Extend the Auto Scaling groups for the web tier and the application tier to deploy instances in Availability Zones in a second Region. Use an Aurora global database to deploy the database in the primary Region and the second Region. Use Amazon Route 53 health checks with a failover routing policy to the second Region.
    - B. Deploy the web tier and the application tier to a second Region. Add an Aurora PostgreSQL cross- Region Aurora Replica in the second Region. Use Amazon Route 53 health checks with a failover routing policy to the second Region. Promote the secondary to primary as needed.
    - C. Deploy the web tier and the application tier to a second Region. Create an Aurora PostgreSQL database in the second Region. Use AWS Database Migration Service (AWS DMS) to replicate the primary database to the second Region. Use Amazon Route 53 health checks with a failover routing policy to the second Region.
    - D. Deploy the web tier and the application tier to a second Region. Use an Amazon Aurora global database to deploy the database in the primary Region and the second Region. Use Amazon Route 53 health checks with a failover routing policy to the second Region. Promote the secondary to primary as needed.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: D
      Explanation: Aws Aurora Global Database allows you to read and write from any region in the global cluster. This enables you to distribute read and write workloads globally, improving performance and reducing latency. Data is replicated synchronously across regions, ensuring strong consistency.
    </details>

49. A company needs to integrate with a third-party data feed. The data feed sends a webhook to notify an external service when new data is ready for consumption. A developer wrote an AWS Lambda function to retrieve data when the company receives a webhook callback. The developer must make the Lambda function available for the third party to call. Which solution will meet these requirements with the MOST operational efficiency?
    - A. Create a function URL for the Lambda function. Provide the Lambda function URL to the third party for the webhook.
    - B. Deploy an Application Load Balancer (ALB) in front of the Lambda function. Provide the ALB URL to the third party for the webhook.
    - C. Create an Amazon Simple Notification Service (Amazon SNS) topic. Attach the topic to the Lambda function. Provide the public hostname of the SNS topic to the third party for the webhook.
    - D. Create an Amazon Simple Queue Service (Amazon SQS) queue. Attach the queue to the Lambda function. Provide the public hostname of the SQS queue to the third party for the webhook.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: A
      Explanation: https://docs.aws.amazon.com/lambda/latest/dg/lambda-urls.html
    </details>

50. A company is building an Amazon Elastic Kubernetes Service (Amazon EKS) cluster for its workloads. All secrets that are stored in Amazon EKS must be encrypted in the Kubernetes etcd key-value store. Which solution will meet these requirements?
    - A. Create a new AWS Key Management Service (AWS KMS) key. Use AWS Secrets Manager to manage, rotate, and store all secrets in Amazon EKS.
    - B. Create a new AWS Key Management Service (AWS KMS) key. Enable Amazon EKS KMS secrets encryption on the Amazon EKS cluster.
    - C. Create the Amazon EKS cluster with default options. Use the Amazon Elastic Block Store (Amazon EBS) Container Storage Interface (CSI) driver as an add-on.
    - D. Create a new AWS Key Management Service (AWS KMS) key with the alias/aws/ebs alias. Enable default Amazon Elastic Block Store (Amazon EBS) volume encryption for the account.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: B
      Explanation: https://docs.aws.amazon.com/eks/latest/userguide/enable-kms.html
    </details>

51. A company wants to provide data scientists with near real-time read-only access to the company's production Amazon RDS for PostgreSQL database. The database is currently configured as a Single-AZ database. The data scientists use complex queries that will not affect the production database. The company needs a solution that is highly available. Which solution will meet these requirements MOST cost-effectively?
    - A. Scale the existing production database in a maintenance window to provide enough power for the
data scientists.
    - B. Change the setup from a Single-AZ to a Multi-AZ instance deployment with a larger secondary standby instance. Provide the data scientists access to the secondary instance.
    - C. Change the setup from a Single-AZ to a Multi-AZ instance deployment. Provide two additional read replicas for the data scientists.
    - D. Change the setup from a Single-AZ to a Multi-AZ cluster deployment with two readable standby instances. Provide read endpoints to the data scientists.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: D
      Explanation: Multi-AZ instance: the standby instance doesn't serve any read or write traffic. Multi-AZ DB cluster: consists of primary instance running in one AZ serving read-write traffic and two other standby running in two different AZs serving read traffic. https://aws.amazon.com/blogs/database/choose-the-right-amazon-rds-deployment-option-single- az-instance-multi-az-instance-or-multi-az-database-cluster/
    </details>

52. A company runs a three-tier web application in the AWS Cloud that operates across three Availability Zones. The application architecture has an Application Load Balancer, an Amazon EC2 web server that hosts user session states, and a MySQL database that runs on an EC2 instance. The company expects sudden increases in application traffic. The company wants to be able to scale to meet future application capacity demands and to ensure high availability across all three Availability Zones. Which solution will meet these requirements?
    - A. Migrate the MySQL database to Amazon RDS for MySQL with a Multi-AZ DB cluster deployment. Use Amazon ElastiCache for Redis with high availability to store session data and to cache reads. Migrate the web server to an Auto Scaling group that is in three Availability Zones.
    - B. Migrate the MySQL database to Amazon RDS for MySQL with a Multi-AZ DB cluster deployment. Use Amazon ElastiCache for Memcached with high availability to store session data and to cache reads. Migrate the web server to an Auto Scaling group that is in three Availability Zones.
    - C. Migrate the MySQL database to Amazon DynamoDB Use DynamoDB Accelerator (DAX) to cache reads. Store the session data in DynamoDB. Migrate the web server to an Auto Scaling group that is in three Availability Zones.
    - D. Migrate the MySQL database to Amazon RDS for MySQL in a single Availability Zone. Use Amazon ElastiCache for Redis with high availability to store session data and to cache reads. Migrate the web server to an Auto Scaling group that is in three Availability Zones.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: A
      Explanation: Memcached is best suited for caching data, while Redis is better for storing data that needs to be persisted. If you need to store data that needs to be accessed frequently, such as user profiles, session data, and application settings, then Redis is the better choice.
    </details>

53. A global video streaming company uses Amazon CloudFront as a content distribution network (CDN). The company wants to roll out content in a phased manner across multiple countries. The company needs to ensure that viewers who are outside the countries to which the company rolls out content are not able to view the content. Which solution will meet these requirements?
    - A. Add geographic restrictions to the content in CloudFront by using an allow list. Set up a custom error message.
    - B. Set up a new URL tor restricted content. Authorize access by using a signed URL and cookies. Set up a custom error message.
    - C. Encrypt the data for the content that the company distributes. Set up a custom error message.
    - D. Create a new URL for restricted content. Set up a time-restricted access policy for signed URLs.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: A
      Explanation: https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/georestrictions.html
    </details>
