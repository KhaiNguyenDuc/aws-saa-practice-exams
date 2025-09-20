---
layout: exam
---

# Practice Exam 2

1. A company runs a high performance computing (HPC) workload on AWS. The workload required low-latency network performance and high network throughput with tightly coupled node-to-node communication. The Amazon EC2 instances are properly sized for compute and storage capacity, and are launched using default options. What should a solutions architect propose to improve the performance of the workload?
    - A. Choose a cluster placement group while launching Amazon EC2 instances.
    - B. Choose dedicated instance tenancy while launching Amazon EC2 instances.
    - C. Choose an Elastic Inference accelerator while launching Amazon EC2 instances.
    - D. Choose the required capacity reservation while launching Amazon EC2 instances.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: A
      Explanation: https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/aws-resource-ec2- placementgroup.html A cluster placement group is a logical grouping of instances within a single Availability Zone that benefit from low network latency, high network throughput.
    </details>

2. A company wants to use the AWS Cloud to make an existing application highly available and resilient. The current version of the application resides in the company's data center. The application recently experienced data loss after a database server crashed because of an unexpected power outage. The company needs a solution that avoids any single points of failure. The solution must give the application the ability to scale to meet user demand. Which solution will meet these requirements?
    - A. Deploy the application servers by using Amazon EC2 instances in an Auto Scaling group across multiple Availability Zones. Use an Amazon RDS DB instance in a Multi-AZ configuration.
    - B. Deploy the application servers by using Amazon EC2 instances in an Auto Scaling group in a single Availability Zone. Deploy the database on an EC2 instance. Enable EC2 Auto Recovery.
    - C. Deploy the application servers by using Amazon EC2 instances in an Auto Scaling group across multiple Availability Zones. Use an Amazon RDS DB instance with a read replica in a single Availability Zone. Promote the read replica to replace the primary DB instance if the primary DB instance fails.
    - D. Deploy the application servers by using Amazon EC2 instances in an Auto Scaling group across multiple Availability Zones. Deploy the primary and secondary database servers on EC2 instances across multiple Availability Zones. Use Amazon Elastic Block Store (Amazon EBS) Multi-Attach to create shared storage between the instances.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: A
      Explanation: To make an existing application highly available and resilient while avoiding any single points of failure and giving the application the ability to scale to meet user demand, the best solution would be to deploy the application servers using Amazon EC2 instances in an Auto Scaling group across multiple Availability Zones and use an Amazon RDS DB instance in a Multi-AZ configuration. By using an Amazon RDS DB instance in a Multi-AZ configuration, the database is automatically replicated across multiple Availability Zones, ensuring that the database is highly available and can withstand the failure of a single Availability Zone. This provides fault tolerance and avoids any single points of failure.
    </details>

3. A company has an ecommerce checkout workflow that writes an order to a database and calls a service to process the payment. Users are experiencing timeouts during the checkout process. When users resubmit the checkout form, multiple unique orders are created for the same desired transaction. How should a solutions architect refactor this workflow to prevent the creation of multiple orders?
    - A. Configure the web application to send an order message to Amazon Kinesis Data Firehose. Set the payment service to retrieve the message from Kinesis Data Firehose and process the order.
    - B. Create a rule in AWS CloudTrail to invoke an AWS Lambda function based on the logged application path request. Use Lambda to query the database, call the payment service, and pass in the order information.
    - C. Store the order in the database. Send a message that includes the order number to Amazon Simple Notification Service (Amazon SNS). Set the payment service to poll Amazon SNS. retrieve the message, and process the order.
    - D. Store the order in the database. Send a message that includes the order number to an Amazon Simple Queue Service (Amazon SQS) FIFO queue.
Set the payment service to retrieve the message and process the order. Delete the message from the queue.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: D
      Explanation: This approach ensures that the order creation and payment processing steps are separate and atomic. By sending the order information to an SQS FIFO queue, the payment service can process the order one at a time and in the order they were received. If the payment service is unable to process an order, it can be retried later, preventing the creation of multiple orders. The deletion of the message from the queue after it is processed will prevent the same message from being processed multiple times. It's worth noting that FIFO queues guarantee that messages are processed in the order they are received, and prevent duplicates.
    </details>

4. A company is building a containerized application on premises and decides to move the application to AWS. The application will have thousands of users soon after li is deployed. The company Is unsure how to manage the deployment of containers at scale. The company needs to deploy the containerized application in a highly available architecture that minimizes operational overhead. Which solution will meet these requirements?
    - A. Store container images In an Amazon Elastic Container Registry (Amazon ECR) repository. Use an Amazon Elastic Container Service (Amazon ECS) cluster with the AWS Fargate launch type to run the containers. Use target tracking to scale automatically based on demand.
    - B. Store container images in an Amazon Elastic Container Registry (Amazon ECR) repository. Use an Amazon Elastic Container Service (Amazon ECS) cluster with the Amazon EC2 launch type to run the containers. Use target tracking to scale automatically based on demand.
    - C. Store container images in a repository that runs on an Amazon EC2 instance. Run the containers on EC2 instances that are spread across multiple Availability Zones. Monitor the average CPU utilization in Amazon CloudWatch. Launch new EC2 instances as needed.
    - D. Create an Amazon EC2 Amazon Machine Image (AMI) that contains the container image. Launch EC2 Instances in an Auto Scaling group across multiple Availability Zones. Use an Amazon CloudWatch alarm to scale out EC2 instances when the average CPU utilization threshold is breached.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: A
      Explanation: AWS Fargate is a technology that you can use with Amazon ECS to run containers without having to manage servers or clusters of Amazon EC2 instances. With Fargate, you no longer have to provision, configure, or scale clusters of virtual machines to run containers. This removes the need to choose server types, decide when to scale your clusters, or optimize cluster packing.
    </details>

5. A company's application Is having performance issues. The application staleful and needs to complete m-memory tasks on Amazon EC2 instances. The company used AWS CloudFormation to deploy infrastructure and used the M5 EC2 Instance family. As traffic increased, the application performance degraded. Users are reporting delays when the users attempt to access the application. Which solution will resolve these issues in the MOST operationally efficient way?
    - A. Replace the EC2 Instances with T3 EC2 instances that run in an Auto Scaling group. Made the changes by using the AWS Management Console.
    - B. Modify the CloudFormation templates to run the EC2 instances in an Auto Scaling group. Increase the desired capacity and the maximum capacity of the Auto Scaling group manually when an increase is necessary.
    - C. Modify the CloudFormation templates.
Replace the EC2 instances with R5 EC2 instances. Use Amazon CloudWatch built-in EC2 memory metrics to track the application performance for future capacity planning.
    - D. Modify the CloudFormation templates. Replace the EC2 instances with R5 EC2 instances. Deploy the Amazon CloudWatch agent on the EC2 instances to generate custom application latency metrics for future capacity planning.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: D
      Explanation: EC2 do not provide by default memory metrics to CloudWatch and require the CloudWatch Agent to be installed on the monitored instances. https://aws.amazon.com/premiumsupport/knowledge-center/cloudwatch-memory-metrics-ec2/
    </details>

6. An ecommerce company has an order-processing application that uses Amazon API Gateway and an AWS Lambda function. The application stores data in an Amazon Aurora PostgreSQL database. During a recent sales event, a sudden surge in customer orders occurred. Some customers experienced timeouts and the application did not process the orders of those customers. A solutions architect determined that the CPU utilization and memory utilization were high on the database because of a large number of open connections. The solutions architect needs to prevent the timeout errors while making the least possible changes to the application. Which solution will meet these requirements?
    - A. Configure provisioned concurrency for the Lambda function. Modify the database to be a global database in multiple AWS Regions.
    - B. Use Amazon RDS Proxy to create a proxy for the database. Modify the Lambda function to use the RDS Proxy endpoint instead of the database endpoint.
    - C. Create a read replica for the database in a different AWS Region. Use query string parameters in API Gateway to route traffic to the read replica.
    - D. Migrate the data from Aurora PostgreSQL to Amazon DynamoDB by using AWS Database. Migration Service (AWS DMS) Modify the Lambda function to use the OynamoDB table.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: B
      Explanation: Many applications, including those built on modern serverless architectures, can have a large number of open connections to the database server and may open and close database connections at a high rate, exhausting database memory and compute resources. Amazon RDS Proxy allows applications to pool and share connections established with the database, improving database efficiency and application scalability. https://aws.amazon.com/id/rds/proxy/
    </details>

7. A company runs a global web application on Amazon EC2 instances behind an Application Load Balancer. The application stores data in Amazon Aurora. The company needs to create a disaster recovery solution and can tolerate up to 30 minutes of downtime and potential data loss. The solution does not need to handle the load when the primary infrastructure is healthy. What should a solutions architect do to meet these requirements?
    - A. Deploy the application with the required infrastructure elements in place. Use Amazon Route 53 to configure active-passive failover. Create an Aurora Replica in a second AWS Region.
    - B. Host a scaled-down deployment of the application in a second AWS Region. Use Amazon Route 53 to configure active-active failover. Create an Aurora Replica in the second Region.
    - C. Replicate the primary infrastructure in a second AWS Region. Use Amazon Route 53 to configure active-active failover. Create an Aurora database that is restored from the latest snapshot.
    - D. Back up data with AWS Backup. Use the backup to create the required infrastructure in a second AWS Region. Use Amazon Route 53 to configure active-passive failover. Create an Aurora second primary instance in the second Region.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: A
      Explanation: https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/dns-failover-types.html
    </details>

8. A company is running several business applications in three separate VPCs within the us-east-1 Region. The applications must be able to communicate between VPCs. The applications also must be able to consistently send hundreds of gigabytes of data each day to a latency-sensitive application that runs in a single on- premises data center. A solutions architect needs to design a network connectivity solution that maximizes cost- effectiveness. Which solution meets these requirements?
    - A. Configure three AWS Site-to-Site VPN connections from the data center to AWS. Establish connectivity by configuring one VPN connection for each VPC. - B. Launch a third-party virtual network appliance in each VPC. Establish an iPsec VPN tunnel between the Data center and each virtual appliance.
    - C. Set up three AWS Direct Connect connections from the data center to a Direct Connect gateway
in us-east-1. Establish connectivity by configuring each VPC to use one of the Direct Connect connections.
    - D. Set up one AWS Direct Connect connection from the data center to AWS. Create a transit gateway, and attach each VPC to the transit gateway. Establish connectivity between the Direct Connect connection and the transit gateway.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: D
      Explanation: https://docs.aws.amazon.com/whitepapers/latest/aws-vpc-connectivity-options/aws-direct- connect-aws-transit-gateway.html
    </details>

9. An online photo application lets users upload photos and perform image editing operations. The application offers two classes of service free and paid Photos submitted by paid users are processed before those submitted by free users Photos are uploaded to Amazon S3 and the job information is sent to Amazon SQS. Which configuration should a solutions architect recommend?
    - A. Use one SQS FIFO queue. Assign a higher priority to the paid photos so they are processed first
    - B. Use two SQS FIFO queues: one for paid and one for free. Set the free queue to use short polling and the paid queue to use long polling
    - C. Use two SQS standard queues one for paid and one for free. Configure Amazon EC2 instances to prioritize polling for the paid queue over the free queue.
    - D. Use one SQS standard queue. Set the visibility timeout of the paid photos to zero. Configure Amazon EC2 instances to prioritize visibility settings so paid photos are processed first

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: C
      Explanation: Priority: Use separate queues to provide prioritization of work.
    </details>

10. A company hosts its product information webpages on AWS. The existing solution uses multiple Amazon EC2 instances behind an Application Load Balancer in an Auto Scaling group. The website also uses a custom DNS name and communicates with HTTPS only using a dedicated SSL certificate. The company is planning a new product launch and wants to be sure that users from around the world have the best possible experience on the new website. What should a solutions architect do to meet these requirements?
    - A. Redesign the application to use Amazon CloudFront
    - B. Redesign the application to use AWS Elastic Beanstalk
    - C. Redesign the application to use a Network Load Balancer.
    - D. Redesign the application to use Amazon S3 static website hosting

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: A
      Explanation: as CloudFront can help provide the best experience for global users. CloudFront integrates seamlessly with ALB and provides and option to use custom DNS and SSL certs.
    </details>

11. A company has 150 TB of archived image data stored on-premises that needs to be moved to the AWS Cloud within the next month. The company's current network connection allows up to 100 Mbps uploads for this purpose during the night only. What is the MOST cost-effective mechanism to move this data and meet the migration deadline?
    - A. Use AWS Snowmobile to ship the data to AWS.
    - B. Order multiple AWS Snowball devices to ship the data to AWS.
    - C. Enable Amazon S3 Transfer Acceleration and securely upload the data.
    - D. Create an Amazon S3 VPC endpoint and establish a VPN to upload the data

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: B
      Explanation: eg.6 hrs night 6 hrs*60min/hr=360 min 360 min*60 sec/min=21600 sec 100 Mbps*21600 s=2160000Mb or 2160 Gb or 2.1 TB can only be done So, for 150 TB, we can use 2 X Snowball Edge Storage Optimised devices. Size of Snowball Edge Storage Optimised device=80 TB Size of Snowball Edge Compute Optimised device= 40 TB Size of Snowcone =8 TB Size of Snowmobile =100 PB (1 PB=1000 TB) Q: How should I choose between Snowmobile and Snowball? To migrate large datasets of 10PB or more in a single location, you should use Snowmobile. For datasets less than 10PB or distributed in multiple locations, you should use Snowball. In addition, you should evaluate the amount of available bandwidth in your network backbone. If you have a high speed backbone with hundreds of Gb/s of spare throughput, then you can use Snowmobile to migrate the large datasets all at once. If you have limited bandwidth on your backbone, you should consider using multiple Snowballs to migrate the data incrementally.
    </details>

12. A company hosts its web application on AWS using seven Amazon EC2 instances. The company requires that the IP addresses of all healthy EC2 instances be returned in response to DNS queries. Which policy should be used to meet this requirement?
    - A. Simple routing policy
    - B. Latency routing policy
    - C. Multivalue routing policy
    - D. Geolocation routing policy

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: C
      Explanation: https://aws.amazon.com/premiumsupport/knowledge-center/multivalue-versus-simple-policies/ "Use a multivalue answer routing policy to help distribute DNS responses across multiple resources. For example, use multivalue answer routing when you want to associate your routing records with a Route 53 health check." https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/routing-policy.html#routing-policy- multivalue
    </details>

13. A company wants to use AWS Systems Manager to manage a fleet of Amazon EC2 instances. According to the company's security requirements, no EC2 instances can have internet access. A solutions architect needs to design network connectivity from the EC2 instances to Systems Manager while fulfilling this security obligation. Which solution will meet these requirements?
    - A. Deploy the EC2 instances into a private subnet with no route to the internet.
    - B. Configure an interface VPC endpoint for Systems Manager. Update routes to use the endpoint.
    - C. Deploy a NAT gateway into a public subnet. Configure private subnets with a default route to the NAT gateway.
    - D. Deploy an internet gateway. Configure a network ACL to deny traffic to all destinations except Systems Manager.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: B
      Explanation: VPC Peering connections VPC interface endpoints can be accessed through both intra-Region and inter-Region VPC peering connections. VPC Gateway Endpoint connections can't be extended out of a VPC. Resources on the other side of a VPC peering connection in your VPC can't use the gateway endpoint to communicate with resources in the gateway endpoint service. Reference: https://docs.aws.amazon.com/systems-manager/latest/userguide/setup-create- vpc.html
    </details>

14. A company needs to build a reporting solution on AWS. The solution must support SQL queries that data analysts run on the data. The data analysts will run lower than 10 total queries each day. The company generates 3 GB of new data daily in an on-premises relational database. This data needs to be transferred to AWS to perform reporting tasks. What should a solutions architect recommend to meet these requirements at the LOWEST cost?
    - A. Use AWS Database Migration Service (AWS DMS) to replicate the data from the on-premises database into Amazon S3. Use Amazon Athena to query the data.
    - B. Use an Amazon Kinesis Data Firehose delivery stream to deliver the data into an Amazon Elasticsearch Service (Amazon ES) cluster Run the queries in Amazon ES.
    - C. Export a daily copy of the data from the on-premises database. Use an AWS Storage Gateway file gateway to store and copy the export into Amazon S3. Use an Amazon EMR cluster to query the data.
    - D. Use AWS Database Migration Service (AWS DMS) to replicate the data from the on-premises database and load it into an Amazon Redshift cluster. Use the Amazon Redshift cluster to query the data.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: D
      Explanation: https://docs.aws.amazon.com/dms/latest/userguide/CHAP_Target.Redshift.html AWS DMS cannot migrate or replicate changes to a schema with a name that begins with underscore (_). If you have schemas that have a name that begins with an underscore, use mapping transformations to rename the schema on the target. Amazon Redshift doesn't support VARCHARs larger than 64 KB. LOBs from traditional databases can't be stored in Amazon Redshift. Applying a DELETE statement to a table with a multi-column primary key is not supported when
      any of the primary key column names use a reserved word. Go here to see a list of Amazon Redshift reserved words. You may experience performance issues if your source system performs UPDATE operations on the primary key of a source table. These performance issues occur when applying changes to the target. This is because UPDATE (and DELETE) operations depend on the primary key value to identify the target row. If you update the primary key of a source table, your task log will contain messages like the following: Update on table 1 changes PK to a PK that was previously updated in the same bulk update. DMS doesn't support custom DNS names when configuring an endpoint for a Redshift cluster, and you need to use the Amazon provided DNS name. Since the Amazon Redshift cluster must be in the same AWS account and Region as the replication instance, validation fails if you use a custom DNS endpoint.
    </details>

15. A company wants to monitor its AWS costs for financial review. The cloud operations team is designing an architecture in the AWS Organizations management account to query AWS Cost and Usage Reports for all member accounts. The team must run this query once a month and provide a detailed analysis of the bill. Which solution is the MOST scalable and cost-effective way to meet these requirements?
    - A. Enable Cost and Usage Reports in the management account. Deliver reports to Amazon Kinesis. Use Amazon EMR for analysis.
    - B. Enable Cost and Usage Reports in the management account. Deliver the reports to Amazon S3. Use Amazon Athena for analysis.
    - C. Enable Cost and Usage Reports for member accounts. Deliver the reports to Amazon S3. Use Amazon Redshift for analysis.
    - D. Enable Cost and Usage Reports for member accounts. Deliver the reports to Amazon Kinesis. Use Amazon QuickSight for analysis.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: C
      Explanation: https://docs.aws.amazon.com/cur/latest/userguide/what-is-cur.html If you are an administrator of an AWS Organizations management account and do not want any of the member accounts in your Organization to set-up a CUR you can do one of the following: (Recommended) If you've opted into Organizations with all features enabled, you can apply a Service Control Policy (SCP). Note that SCPs only apply to member accounts and if you want to restrict any IAM users associated with the management account from setting up a CUR, you'll need to adjust their specific IAM permissions. SCPs also are not retroactive, so they will not de-activate any CURs a member account may have set-up prior to the SCP being applied. Submit a customer support case to block access to billing data in the Billing console for member accounts. This is a list of organizations where the payer account prevents member accounts in its organization from viewing billing data on the Bills and Invoices pages. This also prevents those accounts from setting up Cost and Usage Reports. This option is only available for organizations without all features enabled. Please note that if you have already opted into this to prevent member accounts from viewing bills and invoices in the Billing Console, you do not need to request this access again. Those same member accounts will also be prevented from setting up a Cost and Usage Report.
    </details>

16. A company collects data for temperature, humidity, and atmospheric pressure in cities across multiple continents. The average volume of data that the company collects from each site daily is 500 GB. Each site has a high-speed Internet connection. The company wants to aggregate the data from all these global sites as quickly as possible in a single Amazon S3 bucket. The solution must minimize operational complexity. Which solution meets these requirements?
    - A. Turn on S3 Transfer Acceleration on the destination S3 bucket. Use multipart uploads to directly upload site data to the destination S3 bucket.
    - B. Upload the data from each site to an S3 bucket in the closest Region. Use S3 Cross-Region Replication to copy objects to the destination S3 bucket. Then remove the data from the origin S3 bucket.
    - C. Schedule AWS Snowball Edge Storage Optimized device jobs daily to transfer data from each site to the closest Region. Use S3 Cross-Region Replication to copy objects to the destination S3 bucket.
    - D. Upload the data from each site to an Amazon EC2 instance in the closest Region. Store the data in an Amazon Elastic Block Store (Amazon EBS) volume. At regular intervals, take an EBS snapshot and copy it to the Region that contains the destination S3 bucket. Restore the EBS volume in that Region.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: A
      Explanation: You might want to use Transfer Acceleration on a bucket for various reasons, including the following: - You have customers that upload to a centralized bucket from all over the world. - You transfer gigabytes to terabytes of data on a regular basis across continents. - You are unable to utilize all of your available bandwidth over the Internet when uploading to Amazon S3. https://docs.aws.amazon.com/AmazonS3/latest/dev/transfer-acceleration.html https://aws.amazon.com/s3/transfer- acceleration/#:~:text=S3%20Transfer%20Acceleration%20(S3TA)%20reduces,to%20S3%20for% 20remote%20applications "Amazon S3 Transfer Acceleration can speed up content transfers to and from Amazon S3 by as much as 50-500% for long-distance transfer of larger objects. Customers who have either web or mobile applications with widespread users or applications hosted far away from their S3 bucket can experience long and variable upload and download speeds over the Internet" https://docs.aws.amazon.com/AmazonS3/latest/userguide/mpuoverview.html "Improved throughput -You can upload parts in parallel to improve throughput."
    </details>

17. A company needs the ability to analyze the log files of its proprietary application. The logs are stored in JSON format in an Amazon S3 bucket Queries will be simple and will run on-demand. A solutions architect needs to perform the analysis with minimal changes to the existing architecture. What should the solutions architect do to meet these requirements with the LEAST amount of operational overhead?
    - A. Use Amazon Redshift to load all the content into one place and run the SQL queries as needed
    - B. Use Amazon CloudWatch Logs to store the logs Run SQL queries as needed from the Amazon CloudWatch console
    - C. Use Amazon Athena directly with Amazon S3 to run the queries as needed
    - D. Use AWS Glue to catalog the logs
Use a transient Apache Spark cluster on Amazon EMR to run the SQL queries as needed

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: C
      Explanation: Amazon Athena is an interactive query service that makes it easy to analyze data directly in Amazon Simple Storage Service (Amazon S3) using standard SQL. With a few actions in the AWS Management Console, you can point Athena at your data stored in Amazon S3 and begin using standard SQL to run ad-hoc queries and get results in seconds. https://docs.aws.amazon.com/athena/latest/ug/what-is.html
    </details>

18. A company uses AWS Organizations to manage multiple AWS accounts for different departments. The management account has an Amazon S3 bucket that contains project reports. The company wants to limit access to this S3 bucket to only users of accounts within the organization in AWS Organizations. Which solution meets these requirements with the LEAST amount of operational overhead?
    - A. Add the aws:PrincipalOrgID global condition key with a reference to the organization ID to the S3 bucket policy.
    - B. Create an organizational unit (OU) for each department. Add the aws:PrincipalOrgPaths global condition key to the S3 bucket policy.
    - C. Use AWS CloudTrail to monitor the CreateAccount, InviteAccountToOrganization, LeaveOrganization, and RemoveAccountFromOrganization events. Update the S3 bucket policy accordingly.
    - D. Tag each user that needs access to the S3 bucket. Add the aws:PrincipalTag global condition key to the S3 bucket policy.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: A
      Explanation: https://aws.amazon.com/blogs/security/control-access-to-aws-resources-by-using-the-aws- organization-of-iam-principals/ The aws:PrincipalOrgID global key provides an alternative to listing all the account IDs for all AWS accounts in an organization. For example, the following Amazon S3 bucket policy allows members of any account in the XXX organization to add an object into the examtopics bucket. {"Version": "2020-09-10", "Statement": { "Sid": "AllowPutObject", "Effect": "Allow", "Principal": "*", "Action": "s3:PutObject", "Resource": "arn:aws:s3:::examtopics/*", "Condition": {"StringEquals": {"aws:PrincipalOrgID":["XXX"]}}}} https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_condition-keys.html
    </details>

19. An application runs on an Amazon EC2 instance in a VPC. The application processes logs that are stored in an Amazon S3 bucket. The EC2 instance needs to access the S3 bucket without connectivity to the internet.
Which solution will provide private network connectivity to Amazon S3?
    - A. Create a gateway VPC endpoint to the S3 bucket.
    - B. Stream the logs to Amazon CloudWatch Logs. Export the logs to the S3 bucket.
    - C. Create an instance profile on Amazon EC2 to allow S3 access.
    - D. Create an Amazon API Gateway API with a private link to access the S3 endpoint.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: A
      Explanation: You can access Amazon S3 from your VPC using gateway VPC endpoints. After you create the gateway endpoint, you can add it as a target in your route table for traffic destined from your VPC to Amazon S3. You can create a policy that restricts access to specific IP address ranges by using the aws:VpcSourceIp condition key. https://docs.aws.amazon.com/vpc/latest/privatelink/vpc-endpoints-s3.html
    </details>

20. A company is hosting a web application on AWS using a single Amazon EC2 instance that stores user-uploaded documents in an Amazon EBS volume. For better scalability and availability, the company duplicated the architecture and created a second EC2 instance and EBS volume in another Availability Zone, placing both behind an Application Load Balancer. After completing this change, users reported that, each time they refreshed the website, they could see one subset of their documents or the other, but never all of the documents at the same time. What should a solutions architect propose to ensure users see all of their documents at once?
    - A. Copy the data so both EBS volumes contain all the documents.
    - B. Configure the Application Load Balancer to direct a user to the server with the documents
    - C. Copy the data from both EBS volumes to Amazon EFS. Modify the application to save new documents to Amazon EFS
    - D. Configure the Application Load Balancer to send the request to both servers. Return each document from the correct server.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: C
      Explanation: Amazon EFS provides file storage in the AWS Cloud. With Amazon EFS, you can create a file system, mount the file system on an Amazon EC2 instance, and then read and write data to and from your file system. You can mount an Amazon EFS file system in your VPC, through the Network File System versions 4.0 and 4.1 (NFSv4) protocol. We recommend using a current generation Linux NFSv4.1 client, such as those found in the latest Amazon Linux, Redhat, and Ubuntu AMIs, in conjunction with the Amazon EFS Mount Helper. For instructions, see Using the amazon-efs- utils Tools. For a list of Amazon EC2 Linux Amazon Machine Images (AMIs) that support this protocol, see NFS Support. For some AMIs, you'll need to install an NFS client to mount your file system on your Amazon EC2 instance. For instructions, see Installing the NFS Client. You can access your Amazon EFS file system concurrently from multiple NFS clients, so applications that scale beyond a single connection can access a file system. Amazon EC2 instances running in multiple Availability Zones within the same AWS Region can access the file system, so that many users can access and share a common data source.
    </details>

21. A company uses NFS to store large video files in on-premises network attached storage. Each video file ranges in size from 1 MB to 500 GB. The total storage is 70 TB and is no longer growing.
The company decides to migrate the video files to Amazon S3. The company must migrate the video files as soon as possible while using the least possible network bandwidth. Which solution will meet these requirements?
    - A. Create an S3 bucket. Create an IAM role that has permissions to write to the S3 bucket. Use the AWS CLI to copy all files locally to the S3 bucket.
    - B. Create an AWS Snowball Edge job. Receive a Snowball Edge device on premises. Use the Snowball Edge client to transfer data to the device. Return the device so that AWS can import the data into Amazon S3.
    - C. Deploy an S3 File Gateway on premises. Create a public service endpoint to connect to the S3 File Gateway. Create an S3 bucket. Create a new NFS file share on the S3 File Gateway. Point the new file share to the S3 bucket. Transfer the data from the existing NFS file share to the S3 File Gateway.
    - D. Set up an AWS Direct Connect connection between the on-premises network and AWS. Deploy an S3 File Gateway on premises. Create a public virtual interlace (VIF) to connect to the S3 File Gateway. Create an S3 bucket. Create a new NFS file share on the S3 File Gateway. Point the new file share to the S3 bucket. Transfer the data from the existing NFS file share to the S3 File Gateway.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: B
      Explanation: Option B: As using the least possible network bandwidth. On a Snowball Edge device you can copy files with a speed of up to 100 Gbps. 70 TB will take around 5600 seconds, so very quickly, less than 2 hours. The downside is that it'll take between 4- 6 working days to receive the device and then another 2-3 working days to send it back and for AWS to move the data onto S3 once it reaches them. Total time: 6-9 working days. Bandwidth used: 0.
    </details>

22. A company has an application that ingests incoming messages. Dozens of other applications and microservices then quickly consume these messages. The number of messages varies drastically and sometimes increases suddenly to 100,000 each second. The company wants to decouple the solution and increase scalability. Which solution meets these requirements?
    - A. Persist the messages to Amazon Kinesis Data Analytics. Configure the consumer applications to read and process the messages.
    - B. Deploy the ingestion application on Amazon EC2 instances in an Auto Scaling group to scale the number of EC2 instances based on CPU metrics.
    - C. Write the messages to Amazon Kinesis Data Streams with a single shard. Use an AWS Lambda function to preprocess messages and store them in Amazon DynamoDB. Configure the consumer applications to read from DynamoDB to process the messages.
    - D. Publish the messages to an Amazon Simple Notification Service (Amazon SNS) topic with multiple Amazon Simple Queue Service (Amazon SOS) subscriptions. Configure the consumer applications to process the messages from the queues.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: D
      Explanation: "SNS Standard Topic" Maximum throughput: Standard topics support a nearly unlimited number of messages per second. https://aws.amazon.com/sns/features/ "SQS Standard Queue" Unlimited Throughput: Standard queues support a nearly unlimited number of transactions per second (TPS) per API action. https://aws.amazon.com/sqs/features/
    </details>

23. A company is migrating a distributed application to AWS. The application serves variable workloads. The legacy platform consists of a primary server that coordinates jobs across multiple compute nodes. The company wants to modernize the application with a solution that maximizes resiliency and scalability. How should a solutions architect design the architecture to meet these requirements?
    - A. Configure an Amazon Simple Queue Service (Amazon SQS) queue as a destination for the jobs. Implement the compute nodes with Amazon EC2 instances that are managed in an Auto Scaling group. Configure EC2 Auto Scaling to use scheduled scaling.
    - B. Configure an Amazon Simple Queue Service (Amazon SQS) queue as a destination for the jobs. Implement the compute nodes with Amazon EC2 Instances that are managed in an Auto Scaling group. Configure EC2 Auto Scaling based on the size of the queue.
    - C. Implement the primary server and the compute nodes with Amazon EC2 instances that are managed in an Auto Scaling group. Configure AWS CloudTrail as a destination for the fobs . Configure EC2 Auto Scaling based on the load on the primary server.
    - D. implement the primary server and the compute nodes with Amazon EC2 instances that are managed in an Auto Scaling group. Configure Amazon EventBridge (Amazon CloudWatch Events) as a destination for the jobs. Configure EC2 Auto Scaling based on the load on the compute nodes.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: B
      Explanation: Amazon SQS is a fully managed message queue service that enables you to decouple and scale microservices, distributed systems, and serverless applications. By using SQS as the destination for the jobs, you can decouple the primary server from the compute nodes, which will increase resiliency and scalability. Amazon EC2 Auto Scaling is a service that automatically increases or decreases the number of EC2 instances in your application based on demand. By configuring EC2 Auto Scaling to scale based on the size of the SQS queue, you can ensure that the number of compute nodes is sufficient to handle the workload. https://docs.aws.amazon.com/autoscaling/ec2/userguide/as-using-sqs-queue.html
    </details>

24. A company is running an SMB file server in its data center. The file server stores large files that are accessed frequently for the first few days after the files are created. After 7 days the files are rarely accessed. The total data size is increasing and is close to the company's total storage capacity. A solutions architect must increase the company's available storage space without losing low-latency access to the most recently accessed files. The solutions architect must also provide file lifecycle management to avoid future storage issues.
Which solution will meet these requirements?
    - A. Use AWS DataSync to copy data that is older than 7 days from the SMB file server to AWS.
    - B. Create an Amazon S3 File Gateway to extend the company's storage space. Create an S3 Lifecycle policy to transition the data to S3 Glacier Deep Archive after 7 days.
    - C. Create an Amazon FSx for Windows File Server file system to extend the company's storage space.
    - D. Install a utility on each user's computer to access Amazon S3. Create an S3 Lifecycle policy to transition the data to S3 Glacier Flexible Retrieval after 7 days.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: B
      Explanation: Amazon S3 File Gateway offers SMB or NFS-based access to data in Amazon S3 with local caching. https://docs.aws.amazon.com/filegateway/latest/files3/CreatingAnSMBFileShare.html
    </details>

25. A company is building an ecommerce web application on AWS. The application sends information about new orders to an Amazon API Gateway REST API to process. The company wants to ensure that orders are processed in the order that they are received. Which solution will meet these requirements?
    - A. Use an API Gateway integration to publish a message to an Amazon Simple Notification Service (Amazon SNS) topic when the application receives an order. Subscribe an AWS Lambda function to the topic to perform processing.
    - B. Use an API Gateway integration to send a message to an Amazon Simple Queue Service (Amazon SQS) FIFO queue when the application receives an order. Configure the SQS FIFO queue to invoke an AWS Lambda function for processing.
    - C. Use an API Gateway authorizer to block any requests while the application processes an order.
    - D. Use an API Gateway integration to send a message to an Amazon Simple Queue Service (Amazon SQS) standard queue when the application receives an order. Configure the SQS standard queue to invoke an AWS Lambda function for processing.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: B
      Explanation: SQS FIFO queue guarantees message order. https://docs.aws.amazon.com/AWSSimpleQueueService/latest/SQSDeveloperGuide/FIFO- queues.html
    </details>

26. A company has an application that runs on Amazon EC2 instances and uses an Amazon Aurora database. The EC2 instances connect to the database by using user names and passwords that are stored locally in a file. The company wants to minimize the operational overhead of credential management. What should a solutions architect do to accomplish this goal?
    - A. Use AWS Secrets Manager. Turn on automatic rotation.
    - B. Use AWS Systems Manager Parameter Store. Turn on automatic rotation.
    - C. Create an Amazon S3 bucket lo store objects that are encrypted with an AWS Key. Management Service (AWS KMS) encryption key. Migrate the credential file to the S3 bucket. Point the application to the S3 bucket.
    - D. Create an encrypted Amazon Elastic Block Store (Amazon EBS) volume or each EC2 instance. Attach the new EBS volume to each EC2 instance. Migrate the credential file to the new EBS volume. Point the application to the new EBS volume.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: A
      Explanation: AWS Secrets Manager is a secrets management service that helps you protect access to your applications, services, and IT resources. This service enables you to rotate, manage, and retrieve database credentials, API keys, and other secrets throughout their lifecycle. https://aws.amazon.com/cn/blogs/security/how-to-connect-to-aws-secrets-manager-service- within-a-virtual-private-cloud/ https://aws.amazon.com/blogs/security/rotate-amazon-rds-database-credentials-automatically- with-aws-secrets-manager/
    </details>

27. A global company hosts its web application on Amazon EC2 instances behind an Application Load Balancer (ALB). The web application has static data and dynamic data. The company stores its static data in an Amazon S3 bucket. The company wants to improve performance and reduce latency for the static data and dynamic data. The company is using its own domain name registered with Amazon Route 53. What should a solutions architect do to meet these requirements?
    - A. Create an Amazon CloudFront distribution that has the S3 bucket and the ALB as origins. Configure Route 53 to route traffic to the CloudFront distribution.
    - B. Create an Amazon CloudFront distribution that has the ALB as an origin. Create an AWS Global Accelerator standard accelerator that has the S3 bucket as an endpoint. Configure Route 53 to route traffic to the CloudFront distribution.
    - C. Create an Amazon CloudFront distribution that has the S3 bucket as an origin. Create an AWS Global Accelerator standard accelerator that has the ALB and the CloudFront distribution as endpoints. Create a custom domain name that points to the accelerator DNS name. Use the custom domain name as an endpoint for the web application.
    - D. Create an Amazon CloudFront distribution that has the ALB as an origin. Create an AWS Global Accelerator standard accelerator that has the S3 bucket as an endpoint. Create two domain names. Point one domain name to the CloudFront DNS name for dynamic content. Point the other domain name to the accelerator DNS name for static content. Use the domain names as endpoints for the web application.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: A
      Explanation: AWS Global Accelerator vs CloudFront • They both use the AWS global network and its edge locations around the world • Both services integrate with AWS Shield for DDoS protection. • CloudFront • Improves performance for both cacheable content (such as images and videos) • Dynamic content (such as API acceleration and dynamic site delivery) • Content is served at the edge • Global Accelerator
      • Improves performance for a wide range of applications over TCP or UDP • Proxying packets at the edge to applications running in one or more AWS Regions. • Good fit for non-HTTP use cases, such as gaming (UDP), IoT (MQTT), or Voice over IP • Good for HTTP use cases that require static IP addresses • Good for HTTP use cases that required deterministic, fast regional failover
    </details>

28. A company performs monthly maintenance on its AWS infrastructure. During these maintenance activities, the company needs to rotate the credentials tor its Amazon ROS tor MySQL databases across multiple AWS Regions. Which solution will meet these requirements with the LEAST operational overhead?
    - A. Store the credentials as secrets in AWS Secrets Manager. Use multi-Region secret replication for the required Regions. Configure Secrets Manager to rotate the secrets on a schedule.
    - B. Store the credentials as secrets in AWS Systems Manager by creating a secure string parameter. Use multi-Region secret replication for the required Regions. Configure Systems Manager to rotate the secrets on a schedule.
    - C. Store the credentials in an Amazon S3 bucket that has server-side encryption (SSE) enabled. Use Amazon EventBridge (Amazon CloudWatch Events) to invoke an AWS Lambda function to rotate the credentials.
    - D. Encrypt the credentials as secrets by using AWS Key Management Service (AWS KMS) multi- Region customer managed keys. Store the secrets in an Amazon DynamoDB global table. Use an AWS Lambda function to retrieve the secrets from DynamoDB. Use the RDS API to rotate the secrets.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: A
      Explanation: AWS Secrets Manager meant for storing secrets, Capability to force rotation of secrets every X days, Automate generation of secrets on rotation (uses Lambda), Integration with Amazon RDS (MySQL, PostgreSQL, Aurora). https://aws.amazon.com/blogs/security/how-to-replicate-secrets-aws-secrets-manager-multiple- regions/
    </details>

29. A company is planning to run a group of Amazon EC2 instances that connect to an Amazon Aurora database. The company has built an AWS CloudFormation template to deploy the EC2 instances and the Aurora DB cluster. The company wants to allow the instances to authenticate to the database in a secure way. The company does not want to maintain static database credentials. Which solution meets these requirements with the LEAST operational effort?
    - A. Create a database user with a user name and password. Add parameters for the database user name and password to the CloudFormation template. Pass the parameters to the EC2 instances when the instances are launched.
    - B. Create a database user with a user name and password. Store the user name and password in AWS Systems Manager Parameter Store. Configure the EC2 instances to retrieve the database credentials from Parameter Store.
    - C. Configure the DB cluster to use IAM database authentication. Create a database user to use with IAM authentication. Associate a role with the EC2 instances to allow applications on the instances to access the database.
    - D. Configure the DB cluster to use IAM database authentication with an IAM user.
Create a database user that has a name that matches the IAM user. Associate the IAM user with the EC2 instances to allow applications on the instances to access the database.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: A
      Explanation: Finally, you need a way to instruct CloudFormation to complete stack creation only after all the services (such as Apache and MySQL) are running and not after all the stack resources are created. In other words, if you use the template from the earlier section to launch a stack, CloudFormation sets the status of the stack as CREATE_COMPLETE after it successfully creates all the resources. However, if one or more services failed to start, CloudFormation still sets the stack status as CREATE_COMPLETE. To prevent the status from changing to CREATE_COMPLETE until all the services have successfully started, you can add a CreationPolicy attribute to the instance. This attribute puts the instance's status in CREATE_IN_PROGRESS until CloudFormation receives the required number of success signals or the timeout period is exceeded, so you can control when the instance has been successfully created. Reference: https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/deploying.applications.html
    </details>

30. A company that operates a web application on premises is preparing to launch a newer version of the application on AWS. The company needs to route requests to either the AWS-hosted or the on-premises-hosted application based on the URL query string. The on-premises application is not available from the internet, and a VPN connection is established between Amazon VPC and the company's data center. The company wants to use an Application Load Balancer (ALB) for this launch. Which solution meets these requirements?
    - A. Use two ALBs: one for on-premises and one for the AWS resource. Add hosts to each target group of each ALB. Route with Amazon Route 53 based on the URL query string.
    - B. Use two ALBs: one for on-premises and one for the AWS resource. Add hosts to the target group of each ALB. Create a software router on an EC2 instance based on the URL query string.
    - C. Use one ALB with two target groups: one for the AWS resource and one for on premises. Add hosts to each target group of the ALB. Configure listener rules based on the URL query string.
    - D. Use one ALB with two AWS Auto Scaling groups: one for the AWS resource and one for on premises. Add hosts to each Auto Scaling group. Route with Amazon Route 53 based on the URL query string.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: C
      Explanation: https://aws.amazon.com/blogs/aws/new-advanced-request-routing-for-aws-application-load- balancers/ The host-based routing feature allows you to write rules that use the Host header to route traffic to the desired target group. Today we are extending and generalizing this feature, giving you the ability to write rules (and route traffic) based on standard and custom HTTP headers and methods, the query string, and the source IP address.
    </details>

31. An entertainment company is using Amazon DynamoDB to store media metadata. The application is read intensive and experiencing delays. The company does not have staff to handle additional operational overhead and needs to improve the performance efficiency of DynamoDB without reconfiguring the application. What should a solutions architect recommend to meet this requirement?
    - A. Use Amazon ElastiCache for Redis
    - B. Use Amazon DynamoDB Accelerate (DAX)
    - C. Replicate data by using DynamoDB global tables
    - D. Use Amazon ElastiCache for Memcached with Auto Discovery enabled

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: B
      Explanation: Though DynamoDB offers consistent single-digit-millisecond latency, DynamoDB + DAX takes performance to the next level with response times in microseconds for millions of requests per second for read-heavy workloads. With DAX, your applications remain fast and responsive, even when a popular event or news story drives unprecedented request volumes your way. No tuning required.
    </details>

32. A company has an application that provides marketing services to stores. The services are based on previous purchases by store customers. The stores upload transaction data to the company through SFTP, and the data is processed and analyzed to generate new marketing offers. Some of the files can exceed 200 GB in size. Recently, the company discovered that some of the stores have uploaded files that contain personally identifiable information (PII) that should not have been included. The company wants administrators to be alerted if PII is shared again. The company also wants to automate remediation. What should a solutions architect do to meet these requirements with the LEAST development effort?
    - A. Use an Amazon S3 bucket as a secure transfer point. Use Amazon Inspector to scan me objects in the bucket. If objects contain Pll, trigger an S3 Lifecycle policy to remove the objects that contain Pll.
    - B. Use an Amazon S3 bucket as a secure transfer point. Use Amazon Macie to scan the objects in the bucket. If objects contain Pll, use Amazon Simple Notification Service (Amazon SNS) to trigger a notification to the administrators to remove the objects mat contain Pll.
    - C. Implement custom scanning algorithms in an AWS Lambda function. Trigger the function when objects are loaded into the bucket. If objects contain PII, use Amazon Simple Notification Service (Amazon SNS) to trigger a notification to the administrators to remove the objects that contain PII.
    - D. Implement custom scanning algorithms in an AWS Lambda function. Trigger the function when objects are loaded into the bucket. If objects contain Pll, use Amazon Simple Email Service (Amazon STS) to trigger a notification to the administrators and trigger on S3 Lifecycle policy to remove the objects mot contain PII.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: B
      Explanation: To support integration with other services and systems, Macie publishes findings to Amazon EventBridge as finding events. https://aws.amazon.com/es/macie/faq/
    </details>

33. A company needs guaranteed Amazon EC2 capacity in three specific Availability Zones in a specific AWS Region for an upcoming event that will last 1 week. What should the company do to guarantee the EC2 capacity?
    - A. Purchase Reserved instances that specify the Region needed
    - B. Create an On Demand Capacity Reservation that specifies the Region needed
    - C. Purchase Reserved instances that specify the Region and three Availability Zones needed
    - D. Create an On-Demand Capacity Reservation that specifies the Region and three Availability Zones needed

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: D
      Explanation: https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ec2-capacity-reservations.html "When you create a Capacity Reservation, you specify: The Availability Zone in which to reserve the capacity"
    </details>

34. A company's website uses an Amazon EC2 instance store for its catalog of items. The company wants to make sure that the catalog is highly available and that the catalog is stored in a durable location. What should a solutions architect do to meet these requirements?
    - A. Move the catalog to Amazon ElastiCache for Redis.
    - B. Deploy a larger EC2 instance with a larger instance store.
    - C. Move the catalog from the instance store to Amazon S3 Glacier Deep Archive.
    - D. Move the catalog to an Amazon Elastic File System (Amazon EFS) file system.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: D
      Explanation: Instance store is not durable, if it goes down then instance store data is lost. EFS is the only option here that will provide high availability and durability, plus it can be accessed by multiple instances at the same time.
    </details>

35. A company stores call transcript files on a monthly basis. Users access the files randomly within 1 year of the call, but users access the files infrequently after 1 year. The company wants to optimize its solution by giving users the ability to query and retrieve files that are less than 1-year-old as quickly as possible. A delay in retrieving older files is acceptable. Which solution will meet these requirements MOST cost-effectively?
    - A. Store individual files with tags in Amazon S3 Glacier Instant Retrieval. Query the tags to retrieve the files from S3 Glacier Instant Retrieval.
    - B. Store individual files in Amazon S3 Intelligent-Tiering. Use S3 Lifecycle policies to move the files to S3 Glacier Flexible Retrieval after 1 year. Query and retrieve the files that are in Amazon S3 by using Amazon Athena. Query and retrieve the files that are in S3 Glacier by using S3 Glacier Select.
    - C. Store individual files with tags in Amazon S3 Standard storage. Store search metadata for each archive in Amazon S3 Standard storage. Use S3 Lifecycle policies to move the files to S3 Glacier Instant Retrieval after 1 year. Query and retrieve the files by searching for metadata from Amazon S3.
    - D. Store individual files in Amazon S3 Standard storage. Use S3 Lifecycle policies to move the files to S3 Glacier Deep Archive after 1 year. Store search metadata in Amazon RDS. Query the files from Amazon RDS. Retrieve the files from S3 Glacier Deep Archive.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: B
      Explanation: Users access the files randomly S3 Intelligent-Tiering is the ideal storage class for data with unknown, changing, or unpredictable access patterns, independent of object size or retention period. You can use S3 Intelligent-Tiering as the default storage class for virtually any workload, especially data lakes, data analytics, new applications, and user-generated content. https://aws.amazon.com/fr/s3/storage-classes/intelligent-tiering/
    </details>

36. A company has a production workload that runs on 1,000 Amazon EC2 Linux instances. The workload is powered by third-party software. The company needs to patch the third-party software on all EC2 instances as quickly as possible to remediate a critical security vulnerability. What should a solutions architect do to meet these requirements?
    - A. Create an AWS Lambda function to apply the patch to all EC2 instances.
    - B. Configure AWS Systems Manager Patch Manager to apply the patch to all EC2 instances.
    - C. Schedule an AWS Systems Manager maintenance window to apply the patch to all EC2 instances.
    - D. Use AWS Systems Manager Run Command to run a custom command that applies the patch to all EC2 instances.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: D
      Explanation: For Linux-based operating system types that report a severity level for patches, Patch Manager uses the severity level reported by the software publisher for the update notice or individual patch. Patch Manager doesn't derive severity levels from third-party sources, such as the Common Vulnerability Scoring System (CVSS), or from metrics released by the National Vulnerability Database (NVD). https://docs.aws.amazon.com/systems-manager/latest/userguide/systems-manager-patch.html
    </details>

37. A company wants to migrate its on-premises application to AWS. The application produces output files that vary in size from tens of gigabytes to hundreds of terabytes The application data must be stored in a standard file system structure. The company wants a solution that scales automatically, is highly available, and requires minimum operational overhead. Which solution will meet these requirements?
    - A. Migrate the application to run as containers on Amazon Elastic Container Service (Amazon ECS). Use Amazon S3 for storage.
    - B. Migrate the application to run as containers on Amazon Elastic Kubernetes Service (Amazon EKS). Use Amazon Elastic Block Store (Amazon EBS) for storage.
    - C. Migrate the application to Amazon EC2 instances in a Multi-AZ Auto Scaling group. Use Amazon Elastic File System (Amazon EFS) for storage.
    - D. Migrate the application to Amazon EC2 instances in a Multi-AZ Auto Scaling group. Use Amazon Elastic Block Store (Amazon EBS) for storage.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: C
      Explanation: EFS is a standard file system, it scales automatically and is highly available.
    </details>

38. A company runs multiple Windows workloads on AWS. The company's employees use Windows file shares that are hosted on two Amazon EC2 instances. The file shares synchronize data between themselves and maintain duplicate copies. The company wants a highly available and durable storage solution that preserves how users currently access the files. What should a solutions architect do to meet these requirements?
    - A. Migrate all the data to Amazon S3. Set up IAM authentication for users to access files
    - B. Set up an Amazon S3 File Gateway. Mount the S3 File Gateway on the existing EC2 Instances.
    - C. Extend the file share environment to Amazon FSx for Windows File Server with a Multi-AZ configuration. Migrate all the data to FSx for Windows File Server.
    - D. Extend the file share environment to Amazon Elastic File System (Amazon EFS) with a Multi-AZ configuration. Migrate all the data to Amazon EFS.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: C
      Explanation: Windows file shares = Amazon FSx for Windows File Server https://docs.aws.amazon.com/fsx/latest/WindowsGuide/managing-file-shares.html
    </details>

39. A solutions architect is developing a multiple-subnet VPC architecture. The solution will consist of six subnets in two Availability Zones. The subnets are defined as public, private and dedicated for databases. Only the Amazon EC2 instances running in the private subnets should be able to
access a database. Which solution meets these requirements?
    - A. Create a now route table that excludes the route to the public subnets' CIDR blocks. Associate the route table to the database subnets.
    - B. Create a security group that denies ingress from the security group used by instances in the public subnets. Attach the security group to an Amazon RDS DB instance.
    - C. Create a security group that allows ingress from the security group used by instances in the private subnets. Attach the security group to an Amazon RDS DB instance.
    - D. Create a new peering connection between the public subnets and the private subnets. Create a different peering connection between the private subnets and the database subnets.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: C
      Explanation: Security groups are stateful. All inbound traffic is blocked by default. If you create an inbound rule allowing traffic in, that traffic is automatically allowed back out again. You cannot block specific IP address using Security groups (instead use Network Access Control Lists). "You can specify allow rules, but not deny rules." "When you first create a security group, it has no inbound rules. Therefore, no inbound traffic originating from another host to your instance is allowed until you add inbound rules to the security group." Source: https://docs.aws.amazon.com/vpc/latest/userguide/VPC_SecurityGroups.html#VPCSecurityGrou ps
    </details>

40. A company has registered its domain name with Amazon Route 53. The company uses Amazon API Gateway in the ca-central-1 Region as a public interface for its backend microservice APIs. Third-party services consume the APIs securely. The company wants to design its API Gateway URL with the company's domain name and corresponding certificate so that the third-party services can use HTTPS. Which solution will meet these requirements?
    - A. Create stage variables in API Gateway with Name="Endpoint-URL" and Value="Company Domain Name" to overwrite the default URL. Import the public certificate associated with the company's domain name into AWS Certificate Manager (ACM).
    - B. Create Route 53 DNS records with the company's domain name. Point the alias record to the Regional API Gateway stage endpoint. Import the public certificate associated with the company's domain name into AWS Certificate Manager (ACM) in the us-east-1 Region.
    - C. Create a Regional API Gateway endpoint. Associate the API Gateway endpoint with the company's domain name. Import the public certificate associated with the company's domain name into AWS Certificate Manager (ACM) in the same Region. Attach the certificate to the API Gateway endpoint. Configure Route 53 to route traffic to the API Gateway endpoint.
    - D. Create a Regional API Gateway endpoint. Associate the API Gateway endpoint with the company's domain name. Import the public certificate associated with the company's domain name into AWS Certificate Manager (ACM) in the us-east-1 Region. Attach the certificate to the API Gateway APIs. Create Route 53 DNS records with the company's domain name. Point an A record to the company's domain name.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: C
      Explanation: Regional custom domain names must use an SSL/TLS certificate that's in the same AWS Region as your API. Edge-optimized custom domain names must use a certificate that's in the following Region: US East (N. Virginia) (us-east-1). https://docs.aws.amazon.com/apigateway/latest/developerguide/apigateway-regional-api-custom- domain-create.html
    </details>

41. A company is running a popular social media website. The website gives users the ability to upload images to share with other users. The company wants to make sure that the images do not contain inappropriate content. The company needs a solution that minimizes development effort. What should a solutions architect do to meet these requirements?
    - A. Use Amazon Comprehend to detect inappropriate content. Use human review for low-confidence predictions.
    - B. Use Amazon Rekognition to detect inappropriate content. Use human review for low-confidence predictions.
    - C. Use Amazon SageMaker to detect inappropriate content. Use ground truth to label low-confidence predictions.
    - D. Use AWS Fargate to deploy a custom machine learning model to detect inappropriate content. Use ground truth to label low-confidence predictions.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: B
      Explanation: https://docs.aws.amazon.com/rekognition/latest/dg/moderation.html?pg=ln&sec=ft
    </details>

42. A company wants to run its critical applications in containers to meet requirements tor scalability and availability The company prefers to focus on maintenance of the critical applications. The company does not want to be responsible for provisioning and managing the underlying infrastructure that runs the containerized workload. What should a solutions architect do to meet those requirements?
    - A. Use Amazon EC2 Instances, and Install Docker on the Instances
    - B. Use Amazon Elastic Container Service (Amazon ECS) on Amazon EC2 worker nodes
    - C. Use Amazon Elastic Container Service (Amazon ECS) on AWS Fargate
    - D. Use Amazon EC2 instances from an Amazon Elastic Container Service (Amazon ECS)-op6mized Amazon Machine Image (AMI).

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: C
      Explanation: AWS Fargate is a serverless, pay-as-you-go compute engine that lets you focus on building applications without having to manage servers. AWS Fargate is compatible with Amazon Elastic Container Service (ECS) and Amazon Elastic Kubernetes Service (EKS). https://aws.amazon.com/fr/fargate/
    </details>

43. A company hosts more than 300 global websites and applications. The company requires a platform to analyze more than 30 TB of clickstream data each day. What should a solutions
architect do to transmit and process the clickstream data?
    - A. Design an AWS Data Pipeline to archive the data to an Amazon S3 bucket and run an Amazon EMR duster with the data to generate analytics
    - B. Create an Auto Scaling group of Amazon EC2 instances to process the data and send it to an Amazon S3 data lake for Amazon Redshift to use tor analysis
    - C. Cache the data to Amazon CloudFron. Store the data in an Amazon S3 bucket. When an object is added to the S3 bucket, run an AWS Lambda function to process the data tor analysis.
    - D. Collect the data from Amazon Kinesis Data Streams. Use Amazon Kinesis Data Firehose to transmit the data to an Amazon S3 data lake Load the data in Amazon Redshift for analysis

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: D
      Explanation: https://aws.amazon.com/es/blogs/big-data/real-time-analytics-with-amazon-redshift-streaming- ingestion/
    </details>

44. A company is running a multi-tier ecommerce web application in the AWS Cloud. The web application is running on Amazon EC2 instances. The database tier Is on a provisioned Amazon Aurora MySQL DB cluster with a writer and a reader in a Multi-AZ environment. The new requirement for the database tier is to serve the application to achieve continuous write availability through an Instance failover. What should a solutions architect do to meet this new requirement?
    - A. Add a new AWS Region to the DB cluster for multiple writes
    - B. Add a new reader In the same Availability Zone as the writer.
    - C. Migrate the database tier to an Aurora multi-master cluster.
    - D. Migrate the database tier to an Aurora DB cluster with parallel query enabled.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: C
      Explanation: Bring-your-own-shard (BYOS) A situation where you already have a database schema and associated applications that use sharding. You can transfer such deployments relatively easily to Aurora multi-master clusters. In this case, you can devote your effort to investigating the Aurora benefits such as server consolidation and high availability. You don't need to create new application logic to handle multiple connections for write requests. Global read-after-write (GRAW) A setting that introduces synchronization so that any read operations always see the most current state of the data. By default, the data seen by a read operation in a multi-master cluster is subject to replication lag, typically a few milliseconds. During this brief interval, a query on one DB instance might retrieve stale data if the same data is modified at the same time by a different DB instance. To enable this setting, change aurora_mm_session_consistency_level from its default setting of INSTANCE_RAW to REGIONAL_RAW. Doing so ensures cluster-wide consistency for read operations regardless of the DB instances that perform the reads and writes. Reference: https://docs.aws.amazon.com/AmazonRDS/latest/AuroraUserGuide/aurora-multi- master.html
    </details>

45. A solutions architect observes that a nightly batch processing job is automatically scaled up for 1 hour before the desired Amazon EC2 capacity is reached. The peak capacity is the ‘same every night and the batch jobs always start at 1 AM. The solutions architect needs to find a cost-effective solution that will allow for the desired EC2 capacity to be reached quickly and allow the Auto Scaling group to scale down after the batch jobs are complete. What should the solutions architect do to meet these requirements?
    - A. Increase the minimum capacity for the Auto Scaling group.
    - B. Increase the maximum capacity for the Auto Scaling group.
    - C. Configure scheduled scaling to scale up to the desired compute level.
    - D. Change the scaling policy to add more EC2 instances during each scaling operation.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: C
      Explanation: By configuring scheduled scaling, the solutions architect can set the Auto Scaling group to automatically scale up to the desired compute level at a specific time (IAM) when the batch job starts and then automatically scale down after the job is complete. This will allow the desired EC2 capacity to be reached quickly and also help in reducing the cost.
    </details>

46. A company runs an application in the AWS Cloud and uses Amazon DynamoDB as the database. The company deploys Amazon EC2 instances to a private network to process data from the database. The company uses two NAT instances to provide connectivity to DynamoDB. The company wants to retire the NAT instances. A solutions architect must implement a solution that provides connectivity to DynamoDB and that does not require ongoing management. What is the MOST cost-effective solution that meets these requirements?
    - A. Create a gateway VPC endpoint to provide connectivity to DynamoDB
    - B. Configure a managed NAT gateway to provide connectivity to DynamoDB
    - C. Establish an AWS Direct Connect connection between the private network and DynamoDB
    - D. Deploy an AWS PrivateLink endpoint service between the private network and DynamoDB

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: A
      Explanation: AWS recommends changing from NAT Gateway to VPC endpoints to access S3 or DynamoDB. "Determine whether the majority of your NAT gateway charges are from traffic to Amazon Simple Storage Service or Amazon DynamoDB in the same Region. If they are, set up a gateway VPC endpoint. Route traffic to and from the AWS resource through the gateway VPC endpoint, rather than through the NAT gateway. There's no data processing or hourly charges for using gateway VPC endpoints." https://aws.amazon.com/premiumsupport/knowledge-center/vpc-reduce-nat-gateway-transfer- costs/
    </details>

47. A company has an on-premises business application that generates hundreds of files each day. These files are stored on an SMB file share and require a low-latency connection to the application servers. A new company policy states all application-generated files must be copied to AWS. There is already a VPN connection to AWS. The application development team does not have time to make the necessary code modifications to move the application to AWS.
Which service should a solutions architect recommend to allow the application to copy files to AWS?
    - A. Amazon Elastic File System (Amazon EFS)
    - B. Amazon FSx for Windows File Server
    - C. AWS Snowball
    - D. AWS Storage Gateway

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: D
      Explanation: The files will be on the storgare gateway with low latency and copied to AWS as a second copy. FSx in AWS will not provide low latency for the on prem apps over a vpn to the FSx file system.
    </details>

48. A company has an automobile sales website that stores its listings in an database on Amazon RDS. When an automobile is sold, the listing needs to be removed from the website and the data must be sent to multiple target systems. Which design should a solutions architect recommend?
    - A. Create an AWS Lambda function triggered when the database on Amazon RDS is updated to send the information to an Amazon Simple Queue Service (Amazon SOS) queue for the targets to consume.
    - B. Create an AWS Lambda function triggered when the database on Amazon RDS is updated to send the information to an Amazon Simple Queue Service (Amazon SQS) FIFO queue for the targets to consume.
    - C. Subscribe to an RDS event notification and send an Amazon Simple Queue Service (Amazon SQS) queue fanned out to multiple Amazon Simple Notification Service (Amazon SNS) topics. Use AWS Lambda functions to update the targets.
    - D. Subscribe to an RDS event notification and send an Amazon Simple Notification Service (Amazon SNS) topic fanned out to multiple Amazon Simple Queue Service (Amazon SQS) queues. Use AWS Lambda functions to update the targets.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: A
      Explanation: You can use AWS Lambda to process event notifications from an Amazon Relational Database Service (Amazon RDS) database. Amazon RDS sends notifications to an Amazon Simple Notification Service (Amazon SNS) topic, which you can configure to invoke a Lambda function. Amazon SNS wraps the message from Amazon RDS in its own event document and sends it to your function. https://docs.aws.amazon.com/lambda/latest/dg/with-sns.html https://aws.amazon.com/blogs/compute/messaging-fanout-pattern-for-serverless-architectures- using-amazon-sns/
    </details>

49. A company is developing a video conversion application hosted on AWS. The application will be available in two tiers: a free tier and a paid tier. Users in the paid tier will have their videos converted first and then the tree tier users will have their videos converted. Which solution meets these requirements and is MOST cost-effective?
    - A. One FIFO queue for the paid tier and one standard queue for the free tier
    - B. A single FIFO Amazon Simple Queue Service (Amazon SQS) queue for all file types
    - C. A single standard Amazon Simple Queue Service (Amazon SQS) queue for all file types
    - D. Two standard Amazon Simple Queue Service (Amazon SQS) queues with one for the paid tier and one for the free tier

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: D
      Explanation: In AWS, the queue service is the Simple Queue Service (SQS). Multiple SQS queues may be prepared to prepare queues for individual priority levels (with a priority queue and a secondary queue). Moreover, you may also use the message Delayed Send function to delay process execution.
    </details>

50. A company runs an ecommerce application on Amazon EC2 instances behind an Application Load Balancer. The instances run in an Amazon EC2 Auto Scaling group across multiple Availability Zones. The Auto Scaling group scales based on CPU utilization metrics. The ecommerce application stores the transaction data in a MySQL 8.0 database that is hosted on a large EC2 instance. The database's performance degrades quickly as application load increases. The application handles more read requests than write transactions. The company wants a solution that will automatically scale the database to meet the demand of unpredictable read workloads while maintaining high availability. Which solution will meet these requirements?
    - A. Use Amazon Redshift with a single node for leader and compute functionality.
    - B. Use Amazon RDS with a Single-AZ deployment. Configure Amazon RDS to add reader instances in a different Availability Zone.
    - C. Use Amazon Aurora with a Multi-AZ deployment. Configure Aurora Auto Scaling with Aurora Replicas.
    - D. Use Amazon ElastiCache for Memcached with EC2 Spot Instances.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: C
      Explanation: AURORA is 5x performance improvement over MySQL on RDS and handles more read requests than write, maintaining high availability = Multi-AZ deployment
    </details>

51. A company recently migrated to AWS and wants to implement a solution to protect the traffic that flows in and out of the production VPC. The company had an inspection server in its on-premises data center. The inspection server performed specific operations such as traffic flow inspection and traffic filtering. The company wants to have the same functionalities in the AWS Cloud. Which solution will meet these requirements?
    - A. Use Amazon GuardDuty for traffic inspection and traffic filtering in the production VPC
    - B. Use Traffic Mirroring to mirror traffic from the production VPC for traffic inspection and filtering.
    - C. Use AWS Network Firewall to create the required rules for traffic inspection and traffic filtering for the production VPC. - D. Use AWS Firewall Manager to create the required rules for traffic inspection and traffic filtering for the production VPC. 

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: C
      Explanation: AWS Network Firewall is a stateful, managed network firewall and intrusion detection and prevention service for your virtual private cloud (VPC) that you created in Amazon Virtual Private Cloud (Amazon VPC). With Network Firewall, you can filter traffic at the perimeter of your VPC. This includes filtering traffic going to and coming from an internet gateway, NAT gateway, or over VPN or AWS Direct Connect.
    </details>

52. A company hosts a data lake on AWS. The data lake consists of data in Amazon S3 and Amazon RDS for PostgreSQL. The company needs a reporting solution that provides data visualization and includes all the data sources within the data lake. Only the company's management team should have full access to all the visualizations. The rest of the company should have only limited access. Which solution will meet these requirements?
    - A. Create an analysis in Amazon QuickSight. Connect all the data sources and create new datasets. Publish dashboards to visualize the data. Share the dashboards with the appropriate IAM roles.
    - B. Create an analysis in Amazon OuickSighl. Connect all the data sources and create new datasets. Publish dashboards to visualize the data. Share the dashboards with the appropriate users and groups.
    - C. Create an AWS Glue table and crawler for the data in Amazon S3. Create an AWS Glue extract, transform, and load (ETL) job to produce reports. Publish the reports to Amazon S3. Use S3 bucket policies to limit access to the reports.
    - D. Create an AWS Glue table and crawler for the data in Amazon S3. Use Amazon Athena Federated Query to access data within Amazon RDS for PoslgreSQL. Generate reports by using Amazon Athena. Publish the reports to Amazon S3. Use S3 bucket policies to limit access to the reports.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: B
      Explanation: https://docs.aws.amazon.com/quicksight/latest/user/sharing-a-dashboard.html https://docs.aws.amazon.com/quicksight/latest/user/share-a-dashboard-grant-access-users.html
    </details>

53. A company is implementing a new business application. The application runs on two Amazon EC2 instances and uses an Amazon S3 bucket for document storage. A solutions architect needs to ensure that the EC2 instances can access the S3 bucket. What should the solutions architect do to meet this requirement?
    - A. Create an IAM role that grants access to the S3 bucket. Attach the role to the EC2 instances.
    - B. Create an IAM policy that grants access to the S3 bucket. Attach the policy to the EC2 instances.
    - C. Create an IAM group that grants access to the S3 bucket. Attach the group to the EC2 instances.
    - D. Create an IAM user that grants access to the S3 bucket. Attach the user account to the EC2 instances.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: A
      Explanation: Always remember that you should associate IAM roles to EC2 instances. https://aws.amazon.com/premiumsupport/knowledge-center/ec2-instance-access-s3-bucket/
    </details>

54. A company has a three-tier web application that is deployed on AWS. The web servers are deployed in a public subnet in a VPC. The application servers and database servers are deployed in private subnets in the same VPC. The company has deployed a third-party virtual firewall appliance from AWS Marketplace in an inspection VPC. The appliance is configured with an IP interface that can accept IP packets. A solutions architect needs to Integrate the web application with the appliance to inspect all traffic to the application before the traffic teaches the web server. Which solution will moot these requirements with the LEAST operational overhead?
    - A. Create a Network Load Balancer the public subnet of the application's VPC to route the traffic to the appliance for packet inspection.
    - B. Create an Application Load Balancer in the public subnet of the application's VPC to route the traffic to the appliance for packet inspection.
    - C. Deploy a transit gateway in the inspection VPC. Configure route tables to route the incoming pockets through the transit gateway.
    - D. Deploy a Gateway Load Balancer in the inspection VPC. Create a Gateway Load Balancer endpoint to receive the incoming packets and forward the packets to the appliance.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: D
      Explanation: Gateway Load Balancer is a new type of load balancer that operates at layer 3 of the OSI model and is built on Hyperplane, which is capable of handling several thousands of connections per second. Gateway Load Balancer endpoints are configured in spoke VPCs originating or receiving traffic from the Internet. This architecture allows you to perform inline inspection of traffic from multiple spoke VPCs in a simplified and scalable fashion while still centralizing your virtual appliances. https://aws.amazon.com/blogs/networking-and-content-delivery/scaling-network-traffic-inspection- using-aws-gateway-load-balancer/
    </details>

55. A company wants to improve its ability to clone large amounts of production data into a test environment in the same AWS Region. The data is stored in Amazon EC2 instances on Amazon Elastic Block Store (Amazon EBS) volumes. Modifications to the cloned data must not affect the production environment. The software that accesses this data requires consistently high I/O performance. A solutions architect needs to minimize the time that is required to clone the production data into the test environment. Which solution will meet these requirements?
    - A. Take EBS snapshots of the production EBS volumes. Restore the snapshots onto EC2 instance store volumes in the test environment.
    - B. Configure the production EBS volumes to use the EBS Multi-Attach feature. Take EBS snapshots of the production EBS volumes. Attach the production EBS volumes to the EC2 instances in the test environment.
    - C. Take EBS snapshots of the production EBS volumes. Create and initialize new EBS volumes. Attach the new EBS volumes to EC2 instances in the test environment before restoring the volumes from the production EBS snapshots.
    - D. Take EBS snapshots of the production EBS volumes. Turn on the EBS fast snapshot restore feature on the EBS snapshots. Restore the snapshots into new EBS volumes. Attach the new EBS volumes to EC2 instances in the test environment.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: D
      Explanation: Amazon EBS fast snapshot restore (FSR) enables you to create a volume from a snapshot that is fully initialized at creation. This eliminates the latency of I/O operations on a block when it is accessed for the first time. Volumes that are created using fast snapshot restore instantly deliver all of their provisioned performance. https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ebs-fast-snapshot-restore.html https://aws.amazon.com/cn/about-aws/whats-new/2020/11/amazon-ebs-fast-snapshot-restore- now-available-us-govcloud-regions/
    </details>

56. An ecommerce company wants to launch a one-deal-a-day website on AWS. Each day will feature exactly one product on sale for a period of 24 hours. The company wants to be able to handle
millions of requests each hour with millisecond latency during peak hours. Which solution will meet these requirements with the LEAST operational overhead?
    - A. Use Amazon S3 to host the full website in different S3 buckets. Add Amazon CloudFront distributions. Set the S3 buckets as origins for the distributions. Store the order data in Amazon S3.
    - B. Deploy the full website on Amazon EC2 instances that run in Auto Scaling groups across multiple Availability Zones. Add an Application Load Balancer (ALB) to distribute the website traffic. Add another ALB for the backend APIs. Store the data in Amazon RDS for MySQL.
    - C. Migrate the full application to run in containers. Host the containers on Amazon Elastic Kubernetes Service (Amazon EKS). Use the Kubernetes Cluster Autoscaler to increase and decrease the number of pods to process bursts in traffic. Store the data in Amazon RDS for MySQL.
    - D. Use an Amazon S3 bucket to host the website's static content. Deploy an Amazon CloudFront distribution. Set the S3 bucket as the origin. Use Amazon API Gateway and AWS Lambda functions for the backend APIs. Store the data in Amazon DynamoDB. 

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: D
      Explanation: All of the components are infinitely scalable dynamoDB, API Gateway, Lambda, and of course s3+cloudfront.
    </details>

57. A solutions architect is using Amazon S3 to design the storage architecture of a new digital media application. The media files must be resilient to the loss of an Availability Zone Some files are accessed frequently while other files are rarely accessed in an unpredictable pattern. The solutions architect must minimize the costs of storing and retrieving the media files. Which storage option meets these requirements?
    - A. S3 Standard
    - B. S3 Intelligent-Tiering
    - C. S3 Standard-Infrequent Access {S3 Standard-IA)
    - D. S3 One Zone-Infrequent Access (S3 One Zone-IA)

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: B
      Explanation: S3 Intelligent-Tiering -Perfect use case when you don't know the frequency of access or irregular patterns of usage. Amazon S3 offers a range of storage classes designed for different use cases. These include S3 Standard for general-purpose storage of frequently accessed data; S3 Intelligent-Tiering for data with unknown or changing access patterns; S3 Standard-Infrequent Access (S3 Standard-IA) and S3 One Zone-Infrequent Access (S3 One Zone-IA) for long-lived, but less frequently accessed data; and Amazon S3 Glacier (S3 Glacier) and Amazon S3 Glacier Deep Archive (S3 Glacier Deep Archive) for long-term archive and digital preservation. If you have data residency requirements that can't be met by an existing AWS Region, you can use the S3 Outposts storage class to store your S3 data on-premises. Amazon S3 also offers capabilities to manage your data throughout its
      lifecycle. Once an S3 Lifecycle policy is set, your data will automatically transfer to a different storage class without any changes to your application. https://docs.aws.amazon.com/AmazonS3/latest/userguide/DataDurability.html
    </details>

58. A company has an on-premises MySQL database used by the global sales team with infrequent access patterns. The sales team requires the database to have minimal downtime. A database administrator wants to migrate this database to AWS without selecting a particular instance type in anticipation of more users in the future. Which service should a solution architect recommend?
    - A. Amazon Aurora MySQL
    - B. Amazon Aurora Serverless for MySQL
    - C. Amazon Redshift Spectrum
    - D. Amazon RDS for MySQL

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: B
      Explanation: A database administrator wants to migrate this database to AWS without selecting a particular instance type in anticipation of more users in the future" Serverless sounds right, and it's compatible with MySQL and PostgreSQL. https://aws.amazon.com/rds/aurora/serverless/
    </details>

59. A company is building an application on Amazon EC2 instances that generates temporary transactional data. The application requires access to data storage that can provide configurable and consistent IOPS. What should a solutions architect recommend?
    - A. Provision an EC2 instance with a Throughput Optimized HDD (st1) root volume and a Cold HDD (sc1) data volume.
    - B. Provision an EC2 instance with a Throughput Optimized HDD (st1) volume that will serve as the root and data volume.
    - C. Provision an EC2 instance with a General Purpose SSD (gp2) root volume and Provisioned IOPS SSD (io1) data volume.
    - D. Provision an EC2 instance with a General Purpose SSD (gp2) root volume. Configure the application to store its data in an Amazon S3 bucket.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: C
      Explanation: Only gp3, io1, or io2 Volumes have configurable IOPS. You cannot add HDD in root volume. SSD needs to be selected as root volume and HDD as Data Volume. https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ebs-volumes.html
    </details>

60. A company is hosting 60 TB of production-level data in an Amazon S3 bucket. A solution architect needs to bring that data on premises for quarterly audit requirements. This export of data must be encrypted while in transit. The company has low network bandwidth in place between AWS and its on-premises data center.
What should the solutions architect do to meet these requirements?
    - A. Deploy AWS Migration Hub with 90-day replication windows for data transfer.
    - B. Deploy an AWS Storage Gateway volume gateway on AWS. Enable a 90-day replication window to transfer the data.
    - C. Deploy Amazon Elastic File System (Amazon EFS), with lifecycle policies enabled, on AWS. Use it to transfer the data.
    - D. Deploy an AWS Snowball device in the on-premises data center after completing an export job request in the AWS Snowball console.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: D
      Explanation: AWS Snowball with the Snowball device has the following features: 80 TB and 50 TB models are available in US Regions; 50 TB model available in all other AWS Regions. https://docs.aws.amazon.com/snowball/latest/ug/whatissnowball.html
    </details>

61. A solutions architect is designing the cloud architecture for a company that needs to host hundreds of machine learning models for its users. During startup, the models need to load up to 10 GB of data from Amazon S3 into memory, but they do not need disk access. Most of the models are used sporadically, but the users expect all of them to be highly available and accessible with low latency. Which solution meets the requirements and is MOST cost-effective?
    - A. Deploy models as AWS Lambda functions behind an Amazon API Gateway for each model.
    - B. Deploy models as Amazon Elastic Container Service (Amazon ECS) services behind an Application Load Balancer for each model.
    - C. Deploy models as AWS Lambda functions behind a single Amazon API Gateway with path-based routing where one path corresponds to each model.
    - D. Deploy models as Amazon Elastic Container Service (Amazon ECS) services behind a single Application Load Balancer with path-based routing where one path corresponds to each model.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: C
      Explanation: AWS just update Lambda to support 10G memory and helping compute intensive applications like machine learning. No disk access, lowest cost. https://aws.amazon.com/about-aws/whats-new/2020/12/aws-lambda-supports-10gb-memory-6- vcpu-cores-lambda-functions/
    </details>

62. A company has an ecommerce application that stores data in an on-premises SQL database. The company has decided to migrate this database to AWS. However, as part of the migration, the company wants to find a way to attain sub-millisecond responses to common read requests. A solutions architect knows that the increase in speed is paramount and that a small percentage of stale data returned in the database reads is acceptable. What should the solutions architect recommend?
    - A. Build Amazon RDS read replicas.
    - B. Build the database as a larger instance type.
    - C. Build a database cache using Amazon ElastiCache.
    - D. Build a database cache using Amazon Elasticsearch Service (Amazon ES).

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: C
      Explanation: To attain sub-millisecond responses to common read requests. https://aws.amazon.com/redis/ REDIS (REmote DIctionary Server) delivers sub-millisecond response times enabling millions of requests per second for real-time applications.
    </details>

63. A company is designing an application where users upload small files into Amazon S3. After a user uploads a file, the file requires one-time simple processing to transform the data and save the data in JSON format for later analysis. Each file must be processed as quickly as possible after it is uploaded. Demand will vary. On some days, users will upload a high number of files. On other days, users will upload a few files or no files. Which solution meets these requirements with the LEAST operational overhead?
    - A. Configure Amazon EMR to read text files from Amazon S3.
Run processing scripts to transform the data. Store the resulting JSON file in an Amazon Aurora DB cluster.
    - B. Configure Amazon S3 to send an event notification to an Amazon Simple Queue Service (Amazon SQS) queue. Use Amazon EC2 instances to read from the queue and process the data. Store the resulting JSON file in Amazon DynamoDB. - C. Configure Amazon S3 to send an event notification to an Amazon Simple Queue Service (Amazon SQS) queue. Use an AWS Lambda function to read from the queue and process the data. Store the resulting JSON file in Amazon DynamoDB. - D. Configure Amazon EventBridge (Amazon CloudWatch Events) to send an event to Amazon Kinesis Data Streams when a new file is uploaded. Use an AWS Lambda function to consume the event from the stream and process the data. Store the resulting JSON file in Amazon Aurora DB cluster.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: C
      Explanation: Amazon S3 sends event notifications about S3 buckets (for example, object created, object removed, or object restored) to an SNS topic in the same Region. The SNS topic publishes the event to an SQS queue in the central Region. The SQS queue is configured as the event source for your Lambda function and buffers the event messages for the Lambda function. The Lambda function polls the SQS queue for messages and processes the Amazon S3 event notifications according to your application's requirements. https://docs.aws.amazon.com/prescriptive-guidance/latest/patterns/subscribe-a-lambda-function- to-event-notifications-from-s3-buckets-in-different-aws-regions.html
    </details>

64. An application allows users at a company's headquarters to access product data. The product data is stored in an Amazon RDS MySQL DB instance. The operations team has isolated an application performance slowdown and wants to separate read traffic from write traffic. A solutions architect needs to optimize the application's performance quickly. What should the solutions architect recommend?
    - A. Change the existing database to a Multi-AZ deployment. Serve the read requests from the primary Availability Zone.
    - B. Change the existing database to a Multi-AZ deployment. Serve the read requests from the secondary Availability Zone.
    - C. Create read replicas for the database. Configure the read replicas with half of the compute and storage resources as the source database.
    - D. Create read replicas for the database. Configure the read replicas with the same compute and storage resources as the source database.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: D
      Explanation: For replication to operate effectively, each read replica should have the same amount of compute and storage resources as the source DB instance. https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/USER_MySQL.Replication.ReadRe plicas.html
    </details>

65. An Amazon EC2 administrator created the following policy associated with an IAM group containing several users. What is the effect of this policy?
    - A. Users can terminate an EC2 instance in any AWS Region except us-east-1.
    - B. Users can terminate an EC2 instance with the IP address 10 100 100 1 in the us-east-1 Region
    - C. Users can terminate an EC2 instance in the us-east-1 Region when the user's source IP is 10.100.100.254.
    - D. Users cannot terminate an EC2 instance in the us-east-1 Region when the user's source IP is 10.100 100 254

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: C
      Explanation: As the policy prevents anyone from doing any EC2 action on any region except us-east-1 and allows only users with source ip 10.100.100.0/24 to terminate instances. So user with source ip 10.100.100.254 can terminate instances in us-east-1 region.
    </details>
