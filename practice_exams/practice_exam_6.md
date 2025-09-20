---
layout: exam
---

# Practice Exam 6

1. A company wants to run an in-memory database for a latency-sensitive application that runs on Amazon EC2 instances. The application processes more than 100,000 transactions each minute and requires high network throughput. A solutions architect needs to provide a cost-effective network design that minimizes data transfer charges. Which solution meets these requirements?
    - A. Launch all EC2 instances in the same Availability Zone within the same AWS Region. Specify a placement group with cluster strategy when launching EC2 instances.
    - B. Launch all EC2 instances in different Availability Zones within the same AWS Region. Specify a placement group with partition strategy when launching EC2 instances.
    - C. Deploy an Auto Scaling group to launch EC2 instances in different Availability Zones based on a network utilization target.
    - D. Deploy an Auto Scaling group with a step scaling policy to launch EC2 instances in different Availability Zones.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: A
      Explanation: To achieve low latency, high throughput, and cost-effectiveness, the optimal solution is to launch EC2 instances as a placement group with the cluster strategy within the same Availability Zone.
    </details>

2. A company that primarily runs its application servers on premises has decided to migrate to AWS. The company wants to minimize its need to scale its Internet Small Computer Systems Interface (iSCSI) storage on premises. The company wants only its recently accessed data to remain stored locally.
Which AWS solution should the company use to meet these requirements?
    - A. Amazon S3 File Gateway
    - B. AWS Storage Gateway Tape Gateway
    - C. AWS Storage Gateway Volume Gateway stored volumes
    - D. AWS Storage Gateway Volume Gateway cached volumes

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: D
      Explanation: AWS Storage Gateway Volume Gateway provides two configurations for connecting to iSCSI storage, namely, stored volumes and cached volumes. The stored volume configuration stores the entire data set on-premises and asynchronously backs up the data to AWS. The cached volume configuration stores recently accessed data on-premises, and the remaining data is stored in Amazon S3. Since the company wants only its recently accessed data to remain stored locally, the cached volume configuration would be the most appropriate. It allows the company to keep frequently accessed data on-premises and reduce the need for scaling its iSCSI storage while still providing access to all data through the AWS cloud. This configuration also provides low-latency access to frequently accessed data and cost-effective off-site backups for less frequently accessed data. https://docs.amazonaws.cn/en_us/storagegateway/latest/vgw/StorageGatewayConcepts.html#sto rage-gateway-cached-concepts
    </details>

3. A solutions architect needs to optimize storage costs. The solutions architect must identify any Amazon S3 buckets that are no longer being accessed or are rarely accessed. Which solution will accomplish this goal with the LEAST operational overhead?
    - A. Analyze bucket access patterns by using the S3 Storage Lens dashboard for advanced activity metrics.
    - B. Analyze bucket access patterns by using the S3 dashboard in the AWS Management Console.
    - C. Turn on the Amazon CloudWatch BucketSizeBytes metric for buckets. Analyze bucket access patterns by using the metrics data with Amazon Athena.
    - D. Turn on AWS CloudTrail for S3 object monitoring. Analyze bucket access patterns by using CloudTrail logs that are integrated with Amazon CloudWatch Logs.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: A
      Explanation: S3 Storage Lens is a fully managed S3 storage analytics solution that provides a comprehensive view of object storage usage, activity trends, and recommendations to optimize costs. Storage Lens allows you to analyze object access patterns across all of your S3 buckets and generate detailed metrics and reports. https://aws.amazon.com/blogs/aws/s3-storage-lens/
    </details>

4. A company sells datasets to customers who do research in artificial intelligence and machine learning (AI/ML). The datasets are large, formatted files that are stored in an Amazon S3 bucket in the us-east-1 Region. The company hosts a web application that the customers use to purchase access to a given dataset. The web application is deployed on multiple Amazon EC2 instances behind an Application Load Balancer. After a purchase is made, customers receive an S3 signed URL that allows access to the files. The customers are distributed across North America and Europe. The company wants to reduce the cost that is associated with data transfers and wants to maintain or improve performance. What should a solutions architect do to meet these requirements?
    - A. Configure S3 Transfer Acceleration on the existing S3 bucket. Direct customer requests to the S3 Transfer Acceleration endpoint. Continue to use S3 signed URLs for access control.
    - B. Deploy an Amazon CloudFront distribution with the existing S3 bucket as the origin. Direct customer requests to the CloudFront URL. Switch to CloudFront signed URLs for access control.
    - C. Set up a second S3 bucket in the eu-central-1 Region with S3 Cross-Region Replication between the buckets. Direct customer requests to the closest Region. Continue to use S3 signed URLs for access control.
    - D. Modify the web application to enable streaming of the datasets to end users. Configure the web application to read the data from the existing S3 bucket. Implement access control directly in the application.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: B
      Explanation: To reduce the cost associated with data transfers and maintain or improve performance, a solutions architect should use Amazon CloudFront, a content delivery network (CDN) service that securely delivers data, videos, applications, and APIs to customers globally with low latency and high transfer speeds. Deploying a CloudFront distribution with the existing S3 bucket as the origin will allow the company to serve the data to customers from edge locations that are closer to them, reducing data transfer costs and improving performance. Directing customer requests to the CloudFront URL and switching to CloudFront signed URLs for access control will enable customers to access the data securely and efficiently. https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/PrivateContent.html
    </details>

5. A company is using AWS to design a web application that will process insurance quotes. Users will request quotes from the application. Quotes must be separated by quote type, must be responded to within 24 hours, and must not get lost. The solution must maximize operational efficiency and must minimize maintenance. Which solution meets these requirements?
    - A. Create multiple Amazon Kinesis data streams based on the quote type. Configure the web application to send messages to the proper data stream. Configure each backend group of application servers to use the Kinesis Client Library (KCL) to pool messages from its own data stream.
    - B. Create an AWS Lambda function and an Amazon Simple Notification Service (Amazon SNS) topic for each quote type. Subscribe the Lambda function to its associated SNS topic. Configure the application to publish requests for quotes to the appropriate SNS topic.
    - C. Create a single Amazon Simple Notification Service (Amazon SNS) topic. Subscribe Amazon Simple Queue Service (Amazon SQS) queues to the SNS topic. Configure SNS message filtering to publish messages to the proper SQS queue based on the quote type. Configure each backend application server to use its own SQS queue.
    - D. Create multiple Amazon Kinesis Data Firehose delivery streams based on the quote type to deliver data streams to an Amazon OpenSearch Service cluster. Configure the application to send messages to the proper delivery stream. Configure each backend group of application servers to search for the messages from OpenSearch Service and process them accordingly.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: C
      Explanation: Quote types need to be separated: SNS message filtering can be used to publish messages to the appropriate SQS queue based on the quote type, ensuring that quotes are separated by type. Quotes must be responded to within 24 hours and must not get lost: SQS provides reliable and scalable queuing for messages, ensuring that quotes will not get lost and can be processed in a timely manner. Additionally, each backend application server can use its own SQS queue, ensuring that quotes are processed efficiently without any delay. Operational efficiency and minimizing maintenance: Using a single SNS topic and multiple SQS queues is a scalable and cost-effective approach, which can help to maximize operational efficiency and minimize maintenance. Additionally, SNS and SQS are fully managed services, which means that the company will not need to worry about maintenance tasks such as software updates, hardware upgrades, or scaling the infrastructure. https://aws.amazon.com/getting-started/hands-on/filter-messages-published-to-topics/
    </details>

6. A company has an application that runs on several Amazon EC2 instances. Each EC2 instance has multiple Amazon Elastic Block Store (Amazon EBS) data volumes attached to it. The application's EC2 instance configuration and data need to be backed up nightly. The application also needs to be recoverable in a different AWS Region. Which solution will meet these requirements in the MOST operationally efficient way?
    - A. Write an AWS Lambda function that schedules nightly snapshots of the application's EBS volumes and copies the snapshots to a different Region.
    - B. Create a backup plan by using AWS Backup to perform nightly backups. Copy the backups to another Region. Add the application's EC2 instances as resources.
    - C. Create a backup plan by using AWS Backup to perform nightly backups. Copy the backups to another Region. Add the application's EBS volumes as resources.
    - D. Write an AWS Lambda function that schedules nightly snapshots of the application's EBS volumes
and copies the snapshots to a different Availability Zone.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: B
      Explanation: https://aws.amazon.com/vi/blogs/aws/aws-backup-ec2-instances-efs-single-file-restore-and- cross-region-backup/ When you back up an EC2 instance, AWS Backup will protect all EBS volumes attached to the instance, and it will attach them to an AMI that stores all parameters from the original EC2 instance except for two.
    </details>

7. A company is building a mobile app on AWS. The company wants to expand its reach to millions of users. The company needs to build a platform so that authorized users can watch the company's content on their mobile devices. What should a solutions architect recommend to meet these requirements?
    - A. Publish content to a public Amazon S3 bucket. Use AWS Key Management Service (AWS KMS) keys to stream content.
    - B. Set up IPsec VPN between the mobile app and the AWS environment to stream content.
    - C. Use Amazon CloudFront. Provide signed URLs to stream content.
    - D. Set up AWS Client VPN between the mobile app and the AWS environment to stream content.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: C
      Explanation: Amazon CloudFront is a content delivery network (CDN) that securely delivers data, videos, applications, and APIs to customers globally with low latency and high transfer speeds. CloudFront supports signed URLs that provide authorized access to your content. This feature allows the company to control who can access their content and for how long, providing a secure and scalable solution for millions of users. https://www.amazonaws.cn/en/cloudfront/
    </details>

8. A company experienced a breach that affected several applications in its on-premises data center. The attacker took advantage of vulnerabilities in the custom applications that were running on the servers. The company is now migrating its applications to run on Amazon EC2 instances. The company wants to implement a solution that actively scans for vulnerabilities on the EC2 instances and sends a report that details the findings. Which solution will meet these requirements?
    - A. Deploy AWS Shield to scan the EC2 instances for vulnerabilities. Create an AWS Lambda function to log any findings to AWS CloudTrail.
    - B. Deploy Amazon Macie and AWS Lambda functions to scan the EC2 instances for vulnerabilities. Log any findings to AWS CloudTrail.
    - C. Turn on Amazon GuardDuty. Deploy the GuardDuty agents to the EC2 instances. Configure an AWS Lambda function to automate the generation and distribution of reports that detail the findings.
    - D. Turn on Amazon Inspector. Deploy the Amazon Inspector agent to the EC2 instances. Configure an AWS Lambda function to automate the generation and distribution of reports that detail the findings.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: D
      Explanation: Amazon Inspector is an automated vulnerability management service that continually scans AWS workloads for software vulnerabilities and unintended network exposure. https://aws.amazon.com/inspector/features/?nc=sn&loc=2
    </details>

9. A company uses an Amazon EC2 instance to run a script to poll for and process messages in an Amazon Simple Queue Service (Amazon SQS) queue. The company wants to reduce operational costs while maintaining its ability to process a growing number of messages that are added to the queue. What should a solutions architect recommend to meet these requirements?
    - A. Increase the size of the EC2 instance to process messages faster.
    - B. Use Amazon EventBridge to turn off the EC2 instance when the instance is underutilized.
    - C. Migrate the script on the EC2 instance to an AWS Lambda function with the appropriate runtime.
    - D. Use AWS Systems Manager Run Command to run the script on demand.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: C
      Explanation: By migrating the script to AWS Lambda, the company can take advantage of the auto-scaling feature of the service. AWS Lambda will automatically scale resources to match the size of the workload. This means that the company will not have to worry about provisioning or managing instances as the number of messages increases, resulting in lower operational costs.
    </details>

10. A company uses a legacy application to produce data in CSV format. The legacy application stores the output data in Amazon S3. The company is deploying a new commercial off-the-shelf (COTS) application that can perform complex SQL queries to analyze data that is stored in Amazon Redshift
and Amazon S3 only. However, the COTS application cannot process the .csv files that the legacy application produces. The company cannot update the legacy application to produce data in another format. The company needs to implement a solution so that the COTS application can use the data that the legacy application produces. Which solution will meet these requirements with the LEAST operational overhead?
    - A. Create an AWS Glue extract, transform, and load (ETL) job that runs on a schedule. Configure the ETL job to process the .csv files and store the processed data in Amazon Redshift.
    - B. Develop a Python script that runs on Amazon EC2 instances to convert the .csv files to .sql files. Invoke the Python script on a cron schedule to store the output files in Amazon S3.
    - C. Create an AWS Lambda function and an Amazon DynamoDB table. Use an S3 event to invoke the Lambda function. Configure the Lambda function to perform an extract, transform, and load (ETL) job to process the .csv files and store the processed data in the DynamoDB table.
    - D. Use Amazon EventBridge to launch an Amazon EMR cluster on a weekly schedule. Configure the EMR cluster to perform an extract, transform, and load (ETL) job to process the .csv files and store the processed data in an Amazon Redshift table.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: A
      Explanation: https://docs.aws.amazon.com/glue/latest/dg/aws-glue-programming-etl-format-csv-home.html
    </details>

11. A company has hundreds of Amazon EC2 Linux-based instances in the AWS Cloud. Systems administrators have used shared SSH keys to manage the instances. After a recent audit, the company's security team is mandating the removal of all shared keys. A solutions architect must design a solution that provides secure access to the EC2 instances. Which solution will meet this requirement with the LEAST amount of administrative overhead?
    - A. Use AWS Systems Manager Session Manager to connect to the EC2 instances.
    - B. Use AWS Security Token Service (AWS STS) to generate one-time SSH keys on demand.
    - C. Allow shared SSH access to a set of bastion instances. Configure all other instances to allow only SSH access from the bastion instances.
    - D. Use an Amazon Cognito custom authorizer to authenticate users. Invoke an AWS Lambda function to generate a temporary SSH key.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: A
      Explanation: AWS Systems Manager Session Manager provides secure and auditable instance management without the need for any inbound connections or open ports. It allows you to manage your instances through an interactive one-click browser-based shell or through the AWS CLI. This means that you don't have to manage any SSH keys, and you don't have to worry about securing access to your instances as access is controlled through IAM policies.
    </details>

12. What should a solutions architect do to ensure that all objects uploaded to an Amazon S3 bucket are encrypted?
    - A. Update the bucket policy to deny if the PutObject does not have an s3:x-amz-acl header set.
    - B. Update the bucket policy to deny if the PutObject does not have an s3:x-amz-acl header set to private.
    - C. Update the bucket policy to deny if the PutObject does not have an aws:SecureTransport header set to true.
    - D. Update the bucket policy to deny if the PutObject does not have an x-amz-server-side-encryption header set.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: D
      Explanation: To ensure that all objects uploaded to an Amazon S3 bucket are encrypted, the solutions architect should update the bucket policy to deny any PutObject requests that do not have an x-amz-server- side-encryption header set. This will prevent any objects from being uploaded to the bucket unless they are encrypted using server-side encryption. https://docs.aws.amazon.com/AmazonS3/latest/userguide/amazon-s3-policy-keys.html
    </details>

13. A company is hosting a web application from an Amazon S3 bucket. The application uses Amazon Cognito as an identity provider to authenticate users and return a JSON Web Token (JWT) that provides access to protected resources that are stored in another S3 bucket. Upon deployment of the application, users report errors and are unable to access the protected content. A solutions architect must resolve this issue by providing proper permissions so that users can access the protected content. Which solution meets these requirements?
    - A. Update the Amazon Cognito identity pool to assume the proper IAM role for access to the protected content.
    - B. Update the S3 ACL to allow the application to access the protected content.
    - C. Redeploy the application to Amazon S3 to prevent eventually consistent reads in the S3 bucket from affecting the ability of users to access the protected content.
    - D. Update the Amazon Cognito pool to use custom attribute mappings within the identity pool and grant users the proper permissions to access the protected content.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: A
      Explanation: https://docs.aws.amazon.com/cognito/latest/developerguide/tutorial-create-identity-pool.html You have to create an custom role such as read-only.
    </details>

14. A solutions architect must secure a VPC network that hosts Amazon EC2 instances. The EC2 instances contain highly sensitive data and run in a private subnet. According to company policy, the EC2 instances that run in the VPC can access only approved third-party software repositories on the internet for software product updates that use the third party's URL. Other internet traffic must be blocked. Which solution meets these requirements?
    - A. Update the route table for the private subnet to route the outbound traffic to an AWS Network Firewall firewall. Configure domain list rule groups.
    - B. Set up an AWS WAF web ACL. Create a custom set of rules that filter traffic requests based on source and destination IP address range sets.
    - C. Implement strict inbound security group rules. Configure an outbound rule that allows traffic only to the authorized software repositories on the internet by specifying the URLs.
    - D. Configure an Application Load Balancer (ALB) in front of the EC2 instances. Direct all outbound traffic to the ALB. Use a URL-based rule listener in the ALB's target group for outbound access to the internet.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: A
      Explanation: Send the outbound connection from EC2 to Network Firewall. In Network Firewall, create stateful outbound rules to allow certain domains for software patch download and deny all other domains. https://docs.aws.amazon.com/network-firewall/latest/developerguide/suricata- examples.html#suricata-example-domain-filtering
    </details>

15. A company is hosting a three-tier ecommerce application in the AWS Cloud. The company hosts the website on Amazon S3 and integrates the website with an API that handles sales requests. The company hosts the API on three Amazon EC2 instances behind an Application Load Balancer (ALB). The API consists of static and dynamic front-end content along with backend workers that process sales requests asynchronously. The company is expecting a significant and sudden increase in the number of sales requests during events for the launch of new products. What should a solutions architect recommend to ensure that all the requests are processed successfully?
    - A. Add an Amazon CloudFront distribution for the dynamic content. Increase the number of EC2 instances to handle the increase in traffic.
    - B. Add an Amazon CloudFront distribution for the static content. Place the EC2 instances in an Auto Scaling group to launch new instances based on network traffic.
    - C. Add an Amazon CloudFront distribution for the dynamic content. Add an Amazon ElastiCache instance in front of the ALB to reduce traffic for the API to handle.
    - D. Add an Amazon CloudFront distribution for the static content. Add an Amazon Simple Queue Service (Amazon SQS) queue to receive requests from the website for later processing by the EC2 instances.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: D
      Explanation: Static content can include images and style sheets that are the same across all users and are best cached at the edges of the content distribution network (CDN). Dynamic content includes information that changes frequently or is personalized based on user preferences, behavior, location or other factors - all content is sales requests.
    </details>

16. A security audit reveals that Amazon EC2 instances are not being patched regularly. A solutions architect needs to provide a solution that will run regular security scans across a large fleet of EC2 instances. The solution should also patch the EC2 instances on a regular schedule and provide a report of each instance's patch status. Which solution will meet these requirements?
    - A. Set up Amazon Macie to scan the EC2 instances for software vulnerabilities. Set up a cron job on each EC2 instance to patch the instance on a regular schedule.
    - B. Turn on Amazon GuardDuty in the account. Configure GuardDuty to scan the EC2 instances for software vulnerabilities. Set up AWS Systems Manager Session Manager to patch the EC2 instances on a regular schedule.
    - C. Set up Amazon Detective to scan the EC2 instances for software vulnerabilities. Set up an Amazon EventBridge scheduled rule to patch the EC2 instances on a regular schedule.
    - D. Turn on Amazon Inspector in the account. Configure Amazon Inspector to scan the EC2 instances for software vulnerabilities. Set up AWS Systems Manager Patch Manager to patch the EC2 instances on a regular schedule.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: D
      Explanation: Amazon Inspector is a security assessment service that helps improve the security and compliance of applications deployed on Amazon Web Services (AWS). It automatically assesses applications for vulnerabilities or deviations from best practices. Amazon Inspector can be used to identify security issues and recommend fixes for them. It is an ideal solution for running regular security scans across a large fleet of EC2 instances. AWS Systems Manager Patch Manager is a service that helps you automate the process of patching Windows and Linux instances. It provides a simple, automated way to patch your instances with the latest security patches and updates. Patch Manager helps you maintain compliance with security policies and regulations by providing detailed reports on the patch status of your instances.
    </details>

17. A company is planning to store data on Amazon RDS DB instances. The company must encrypt the data at rest.
What should a solutions architect do to meet this requirement?
    - A. Create a key in AWS Key Management Service (AWS KMS). Enable encryption for the DB instances.
    - B. Create an encryption key. Store the key in AWS Secrets Manager. Use the key to encrypt the DB instances.
    - C. Generate a certificate in AWS Certificate Manager (ACM). Enable SSL/TLS on the DB instances by using the certificate.
    - D. Generate a certificate in AWS Identity and Access Management (IAM). Enable SSL/TLS on the DB instances by using the certificate.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: A
      Explanation: To encrypt data at rest in Amazon RDS, you can use the encryption feature of Amazon RDS, which uses AWS Key Management Service (AWS KMS). With this feature, Amazon RDS encrypts each database instance with a unique key. This key is stored securely by AWS KMS. You can manage your own keys or use the default AWS-managed keys. When you enable encryption for a DB instance, Amazon RDS encrypts the underlying storage, including the automated backups, read replicas, and snapshots.
    </details>

18. A company must migrate 20 TB of data from a data center to the AWS Cloud within 30 days. The company's network bandwidth is limited to 15 Mbps and cannot exceed 70% utilization. What should a solutions architect do to meet these requirements?
    - A. Use AWS Snowball.
    - B. Use AWS DataSync.
    - C. Use a secure VPN connection.
    - D. Use Amazon S3 Transfer Acceleration.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: A
      Explanation: AWS Snowball is a secure data transport solution that accelerates moving large amounts of data into and out of the AWS cloud. It can move up to 80 TB of data at a time, and provides a network bandwidth of up to 50 Mbps, so it is well-suited for the task. Additionally, it is secure and easy to use, making it the ideal solution for this migration. https://docs.aws.amazon.com/snowball/latest/ug/whatissnowball.html
    </details>

19. A company needs to provide its employees with secure access to confidential and sensitive files. The company wants to ensure that the files can be accessed only by authorized users. The files must be downloaded securely to the employees' devices. The files are stored in an on-premises Windows file server. However, due to an increase in remote usage, the file server is running out of capacity. Which solution will meet these requirements?
    - A. Migrate the file server to an Amazon EC2 instance in a public subnet. Configure the security group to limit inbound traffic to the employees' IP addresses.
    - B. Migrate the files to an Amazon FSx for Windows File Server file system. Integrate the Amazon FSx file system with the on-premises Active Directory. Configure AWS Client VPN.
    - C. Migrate the files to Amazon S3, and create a private VPC endpoint. Create a signed URL to allow download.
    - D. Migrate the files to Amazon S3, and create a public VPC endpoint. Allow employees to sign on with AWS IAM Identity Center (AWS Single Sign-On).

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: B
      Explanation: It provides a secure way for employees to access confidential and sensitive files from anywhere using AWS Client VPN. The Amazon FSx for Windows File Server file system is designed to provide native support for Windows file system features such as NTFS permissions, Active Directory integration, and Distributed File System (DFS). This means that the company can continue to use their on-premises Active Directory to manage user access to files.
    </details>

20. A company's application runs on Amazon EC2 instances behind an Application Load Balancer (ALB). The instances run in an Amazon EC2 Auto Scaling group across multiple Availability Zones. On the first day of every month at midnight, the application becomes much slower when the month- end financial calculation batch runs. This causes the CPU utilization of the EC2 instances to immediately peak to 100%, which disrupts the application. What should a solutions architect recommend to ensure the application is able to handle the workload and avoid downtime?
    - A. Configure an Amazon CloudFront distribution in front of the ALB. - B. Configure an EC2 Auto Scaling simple scaling policy based on CPU utilization.
    - C. Configure an EC2 Auto Scaling scheduled scaling policy based on the monthly schedule.
    - D. Configure Amazon ElastiCache to remove some of the workload from the EC2 instances.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: C
      Explanation: https://docs.aws.amazon.com/autoscaling/ec2/userguide/ec2-auto-scaling-scheduled-scaling.html
    </details>

21. A company wants to give a customer the ability to use on-premises Microsoft Active Directory to download files that are stored in Amazon S3. The customer's application uses an SFTP client to download the files. Which solution will meet these requirements with the LEAST operational overhead and no changes to the customer's application?
    - A. Set up AWS Transfer Family with SFTP for Amazon S3. Configure integrated Active Directory authentication.
    - B. Set up AWS Database Migration Service (AWS DMS) to synchronize the on-premises client with Amazon S3. Configure integrated Active Directory authentication.
    - C. Set up AWS DataSync to synchronize between the on-premises location and the S3 location by using AWS IAM Identity Center (AWS Single Sign-On).
    - D. Set up a Windows Amazon EC2 instance with SFTP to connect the on-premises client with Amazon S3. Integrate AWS Identity and Access Management (IAM).

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: A
      Explanation: https://docs.aws.amazon.com/transfer/latest/userguide/directory-services-users.html
    </details>

22. A company is experiencing sudden increases in demand. The company needs to provision large Amazon EC2 instances from an Amazon Machine Image (AMI). The instances will run in an Auto Scaling group. The company needs a solution that provides minimum initialization latency to meet the demand. Which solution meets these requirements?
    - A. Use the aws ec2 register-image command to create an AMI from a snapshot. Use AWS Step Functions to replace the AMI in the Auto Scaling group.
    - B. Enable Amazon Elastic Block Store (Amazon EBS) fast snapshot restore on a snapshot. Provision an AMI by using the snapshot. Replace the AMI in the Auto Scaling group with the new AMI.
    - C. Enable AMI creation and define lifecycle rules in Amazon Data Lifecycle Manager (Amazon DLM). Create an AWS Lambda function that modifies the AMI in the Auto Scaling group.
    - D. Use Amazon EventBridge to invoke AWS Backup lifecycle policies that provision AMIs. Configure Auto Scaling group capacity limits as an event source in EventBridge.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: B
      Explanation: Enabling Amazon Elastic Block Store (Amazon EBS) fast snapshot restore on a snapshot allows you to quickly create a new Amazon Machine Image (AMI) from a snapshot, which can help reduce the initialization latency when provisioning new instances. Once the AMI is provisioned, you can replace the AMI in the Auto Scaling group with the new AMI. This will ensure that new instances are launched from the updated AMI and are able to meet the increased demand quickly.
    </details>

23. A company hosts a multi-tier web application that uses an Amazon Aurora MySQL DB cluster for storage. The application tier is hosted on Amazon EC2 instances. The company's IT security guidelines mandate that the database credentials be encrypted and rotated every 14 days. What should a solutions architect do to meet this requirement with the LEAST operational effort?
    - A. Create a new AWS Key Management Service (AWS KMS) encryption key. Use AWS Secrets Manager to create a new secret that uses the KMS key with the appropriate credentials. Associate the secret with the Aurora DB cluster. Configure a custom rotation period of 14 days.
    - B. Create two parameters in AWS Systems Manager Parameter Store: one for the user name as a string parameter and one that uses the SecureString type for the password. Select AWS Key Management Service (AWS KMS) encryption for the password parameter, and load these parameters in the application tier. Implement an AWS Lambda function that rotates the password every 14 days.
    - C. Store a file that contains the credentials in an AWS Key Management Service (AWS KMS) encrypted Amazon Elastic File System (Amazon EFS) file system. Mount the EFS file system in all EC2 instances of the application tier. Restrict the access to the file on the file system so that the application can read the file and that only super users can modify the file. Implement an AWS Lambda function that rotates the key in Aurora every 14 days and writes new credentials into the file.
    - D. Store a file that contains the credentials in an AWS Key Management Service (AWS KMS) encrypted Amazon S3 bucket that the application uses to load the credentials. Download the file to the application regularly to ensure that the correct credentials are used. Implement an AWS Lambda function that rotates the Aurora credentials every 14 days and uploads these credentials to the file in the S3 bucket.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: A
      Explanation: To implement password rotation lifecycles, use AWS Secrets Manager. You can rotate, manage, and retrieve database credentials, API keys, and other secrets throughout their lifecycle using Secrets Manager. https://aws.amazon.com/blogs/security/how-to-use-aws-secrets-manager-rotate-credentials- amazon-rds-database-types-oracle/
    </details>

24. A company has deployed a web application on AWS. The company hosts the backend database on Amazon RDS for MySQL with a primary DB instance and five read replicas to support scaling needs. The read replicas must lag no more than 1 second behind the primary DB instance. The database routinely runs scheduled stored procedures. As traffic on the website increases, the replicas experience additional lag during periods of peak load. A solutions architect must reduce the replication lag as much as possible. The solutions architect must minimize changes to the application code and must minimize ongoing operational overhead. Which solution will meet these requirements?
    - A. Migrate the database to Amazon Aurora MySQL. Replace the read replicas with Aurora Replicas, and configure Aurora Auto Scaling. Replace the stored procedures with Aurora MySQL native functions.
    - B. Deploy an Amazon ElastiCache for Redis cluster in front of the database. Modify the application to check the cache before the application queries the database. Replace the stored procedures with AWS Lambda functions.
    - C. Migrate the database to a MySQL database that runs on Amazon EC2 instances. Choose large, compute optimized EC2 instances for all replica nodes. Maintain the stored procedures on the EC2 instances.
    - D. Migrate the database to Amazon DynamoDB. Provision a large number of read capacity units (RCUs) to support the required throughput, and configure on-demand capacity scaling. Replace the stored procedures with DynamoDB streams.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: A
      Explanation: You can scale reads for your Amazon RDS for PostgreSQL DB instance by adding read replicas to the instance. As with other Amazon RDS database engines, RDS for PostgreSQL uses the native replication mechanisms of PostgreSQL to keep read replicas up to date with changes on the source DB. For general information about read replicas and Amazon RDS, see Working with read replicas. https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/USER_PostgreSQL.Replication.Re adReplicas.html
    </details>

25. A solutions architect must create a disaster recovery (DR) plan for a high-volume software as a service (SaaS) platform. All data for the platform is stored in an Amazon Aurora MySQL DB cluster. The DR plan must replicate data to a secondary AWS Region. Which solution will meet these requirements MOST cost-effectively?
    - A. Use MySQL binary log replication to an Aurora cluster in the secondary Region. Provision one DB instance for the Aurora cluster in the secondary Region.
    - B. Set up an Aurora global database for the DB cluster. When setup is complete, remove the DB instance from the secondary Region.
    - C. Use AWS Database Migration Service (AWS DMS) to continuously replicate data to an Aurora cluster in the secondary Region. Remove the DB instance from the secondary Region.
    - D. Set up an Aurora global database for the DB cluster. Specify a minimum of one DB instance in the secondary Region.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: D
      Explanation: An Aurora DB cluster can contain up to 15 Aurora Replicas. The Aurora Replicas can be distributed across the Availability Zones that a DB cluster spans WITHIN an AWS Region. https://docs.aws.amazon.com/AmazonRDS/latest/AuroraUserGuide/Aurora.Replication.html You can replicate data across multiple Regions by using an Aurora global database.
    </details>

26. A company has a custom application with embedded credentials that retrieves information from an Amazon RDS MySQL DB instance. Management says the application must be made more secure with the least amount of programming effort. What should a solutions architect do to meet these requirements?
    - A. Use AWS Key Management Service (AWS KMS) to create keys. Configure the application to load the database credentials from AWS KMS. Enable automatic key rotation.
    - B. Create credentials on the RDS for MySQL database for the application user and store the credentials in AWS Secrets Manager. Configure the application to load the database credentials from Secrets Manager. Create an AWS Lambda function that rotates the credentials in Secret Manager.
    - C. Create credentials on the RDS for MySQL database for the application user and store the credentials in AWS Secrets Manager. Configure the application to load the database credentials from Secrets Manager. Set up a credentials rotation schedule for the application user in the RDS for MySQL database using Secrets Manager.
    - D. Create credentials on the RDS for MySQL database for the application user and store the credentials in AWS Systems Manager Parameter Store. Configure the application to load the database credentials from Parameter Store. Set up a credentials rotation schedule for the application user in the RDS for MySQL database using Parameter Store.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: C
      Explanation: https://ws.amazon.com/blogs/security/rotate-amazon-rds-database-credentials-automatically- with-aws-secrets-manager/
    </details>

27. A media company hosts its website on AWS. The website application's architecture includes a fleet of Amazon EC2 instances behind an Application Load Balancer (ALB) and a database that is hosted on Amazon Aurora. The company's cybersecurity team reports that the application is vulnerable to SQL injection. How should the company resolve this issue?
    - A. Use AWS WAF in front of the ALB. Associate the appropriate web ACLs with AWS WAF.
    - B. Create an ALB listener rule to reply to SQL injections with a fixed response.
    - C. Subscribe to AWS Shield Advanced to block all SQL injection attempts automatically.
    - D. Set up Amazon Inspector to block all SQL injection attempts automatically.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: A
      Explanation: Protect against SQL injection and cross-site scripting To protect your applications against SQL injection and cross-site scripting (XSS) attacks, use the built-in SQL injection and cross-site scripting engines. Remember that attacks can be performed on different parts of the HTTP request, such as the HTTP header, query string, or URI. Configure the AWS WAF rules to inspect different parts of the HTTP request against the built-in mitigation engines.
    </details>

28. A company has an Amazon S3 data lake that is governed by AWS Lake Formation. The company wants to create a visualization in Amazon QuickSight by joining the data in the data lake with operational data that is stored in an Amazon Aurora MySQL database. The company wants to enforce column-level authorization so that the company's marketing team can access only a subset of columns in the database. Which solution will meet these requirements with the LEAST operational overhead?
    - A. Use Amazon EMR to ingest the data directly from the database to the QuickSight SPICE engine. Include only the required columns.
    - B. Use AWS Glue Studio to ingest the data from the database to the S3 data lake. Attach an IAM policy to the QuickSight users to enforce column-level access control. Use Amazon S3 as the data source in QuickSight.
    - C. Use AWS Glue Elastic Views to create a materialized view for the database in Amazon S3. Create an S3 bucket policy to enforce column-level access control for the QuickSight users. Use Amazon S3 as the data source in QuickSight.
    - D. Use a Lake Formation blueprint to ingest the data from the database to the S3 data lake. Use Lake Formation to enforce column-level access control for the QuickSight users. Use Amazon Athena as the data source in QuickSight.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: D
      Explanation: This solution leverages AWS Lake Formation to ingest data from the Aurora MySQL database into the S3 data lake, while enforcing column-level access control for QuickSight users. Lake Formation can be used to create and manage the data lake's metadata and enforce security and governance policies, including column-level access control. This solution then uses Amazon Athena as the data source in QuickSight to query the data in the S3 data lake. This solution minimizes operational overhead by leveraging AWS services to manage and secure the data, and by using a standard query service (Amazon Athena) to provide a SQL interface to the data. https://aws.amazon.com/blogs/big-data/enforce-column-level-authorization-with-amazon- quicksight-and-aws-lake-formation/
    </details>

29. A transaction processing company has weekly scripted batch jobs that run on Amazon EC2 instances. The EC2 instances are in an Auto Scaling group. The number of transactions can vary, but the baseline CPU utilization that is noted on each run is at least 60%. The company needs to provision the capacity 30 minutes before the jobs run. Currently, engineers complete this task by manually modifying the Auto Scaling group parameters. The company does not have the resources to analyze the required capacity trends for the Auto Scaling group counts. The company needs an automated way to modify the Auto Scaling group's desired capacity.
Which solution will meet these requirements with the LEAST operational overhead?
    - A. Create a dynamic scaling policy for the Auto Scaling group. Configure the policy to scale based on the CPU utilization metric. Set the target value for the metric to 60%.
    - B. Create a scheduled scaling policy for the Auto Scaling group. Set the appropriate desired capacity, minimum capacity, and maximum capacity. Set the recurrence to weekly. Set the start time to 30 minutes before the batch jobs run.
    - C. Create a predictive scaling policy for the Auto Scaling group. Configure the policy to scale based on forecast. Set the scaling metric to CPU utilization. Set the target value for the metric to 60%. In the policy, set the instances to pre-launch 30 minutes before the jobs run.
    - D. Create an Amazon EventBridge event to invoke an AWS Lambda function when the CPU utilization metric value for the Auto Scaling group reaches 60%. Configure the Lambda function to increase the Auto Scaling group's desired capacity and maximum capacity by 20%.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: C
      Explanation: https://docs.aws.amazon.com/autoscaling/ec2/userguide/ec2-auto-scaling-predictive-scaling.html
    </details>

30. A solutions architect is designing a company's disaster recovery (DR) architecture. The company has a MySQL database that runs on an Amazon EC2 instance in a private subnet with scheduled backup. The DR design needs to include multiple AWS Regions. Which solution will meet these requirements with the LEAST operational overhead?
    - A. Migrate the MySQL database to multiple EC2 instances. Configure a standby EC2 instance in the DR Region. Turn on replication.
    - B. Migrate the MySQL database to Amazon RDS. Use a Multi-AZ deployment. Turn on read replication for the primary DB instance in the different Availability Zones.
    - C. Migrate the MySQL database to an Amazon Aurora global database. Host the primary DB cluster in the primary Region. Host the secondary DB cluster in the DR Region.
    - D. Store the scheduled backup of the MySQL database in an Amazon S3 bucket that is configured for S3 Cross-Region Replication (CRR). Use the data backup to restore the database in the DR Region.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: C
      Explanation: https://docs.aws.amazon.com/AmazonRDS/latest/AuroraUserGuide/Aurora.Replication.html
    </details>

31. A company has a Java application that uses Amazon Simple Queue Service (Amazon SQS) to parse messages. The application cannot parse messages that are larger than 256 KB in size. The company wants to implement a solution to give the application the ability to parse messages as large as 50 MB. Which solution will meet these requirements with the FEWEST changes to the code?
    - A. Use the Amazon SQS Extended Client Library for Java to host messages that are larger than 256 KB in Amazon S3.
    - B. Use Amazon EventBridge to post large messages from the application instead of Amazon SQS.
    - C. Change the limit in Amazon SQS to handle messages that are larger than 256 KB. - D. Store messages that are larger than 256 KB in Amazon Elastic File System (Amazon EFS).
Configure Amazon SQS to reference this location in the messages.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: A
      Explanation: To send messages larger than 256 KiB, you can use the Amazon SQS Extended Client Library for Java. This library allows you to send an Amazon SQS message that contains a reference to a message payload in Amazon S3. The maximum payload size is 2 GB. https://docs.aws.amazon.com/AWSSimpleQueueService/latest/SQSDeveloperGuide/quotas- messages.html
    </details>

32. A company wants to restrict access to the content of one of its main web applications and to protect the content by using authorization techniques available on AWS. The company wants to implement a serverless architecture and an authentication solution for fewer than 100 users. The solution needs to integrate with the main web application and serve web content globally. The solution must also scale as the company's user base grows while providing the lowest login latency possible. Which solution will meet these requirements MOST cost-effectively?
    - A. Use Amazon Cognito for authentication. Use Lambda@Edge for authorization. Use Amazon CloudFront to serve the web application globally.
    - B. Use AWS Directory Service for Microsoft Active Directory for authentication. Use AWS Lambda for authorization. Use an Application Load Balancer to serve the web application globally.
    - C. Use Amazon Cognito for authentication. Use AWS Lambda for authorization. Use Amazon S3 Transfer Acceleration to serve the web application globally.
    - D. Use AWS Directory Service for Microsoft Active Directory for authentication. Use Lambda@Edge for authorization. Use AWS Elastic Beanstalk to serve the web application globally.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: A
      Explanation: Amazon CloudFront is a global content delivery network (CDN) service that can securely deliver web content, videos, and APIs at scale. It integrates with Cognito for authentication and with Lambda@Edge for authorization, making it an ideal choice for serving web content globally. Lambda@Edge is a service that lets you run AWS Lambda functions globally closer to users, providing lower latency and faster response times. It can also handle authorization logic at the edge to secure content in CloudFront. For this scenario, Lambda@Edge can provide authorization for the web application while leveraging the low-latency benefit of running at the edge.
    </details>

33. A company has an aging network-attached storage (NAS) array in its data center. The NAS array presents SMB shares and NFS shares to client workstations. The company does not want to purchase a new NAS array. The company also does not want to incur the cost of renewing the NAS array's support contract. Some of the data is accessed frequently, but much of the data is inactive. A solutions architect needs to implement a solution that migrates the data to Amazon S3, uses S3 Lifecycle policies, and maintains the same look and feel for the client workstations. The solutions architect has identified AWS Storage Gateway as part of the solution. Which type of storage gateway should the solutions architect provision to meet these requirements?
    - A. Volume Gateway
    - B. Tape Gateway
    - C. Amazon FSx File Gateway
    - D. Amazon S3 File Gateway

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: D
      Explanation: Amazon S3 File Gateway provides a file interface to objects stored in S3. It can be used for a file- based interface with S3, which allows the company to migrate their NAS array data to S3 while maintaining the same look and feel for client workstations. Amazon S3 File Gateway supports SMB and NFS protocols, which will allow clients to continue to access the data using these protocols. Additionally, Amazon S3 Lifecycle policies can be used to automate the movement of data to lower- cost storage tiers, reducing the storage cost of inactive data. https://aws.amazon.com/about-aws/whats-new/2018/06/aws-storage-gateway-adds-smb-support- to-store-objects-in-amazon-s3/
    </details>

34. A company has an application that is running on Amazon EC2 instances. A solutions architect has standardized the company on a particular instance family and various instance sizes based on the current needs of the company. The company wants to maximize cost savings for the application over the next 3 years. The company needs to be able to change the instance family and sizes in the next 6 months based on application popularity and usage. Which solution will meet these requirements MOST cost-effectively?
    - A. Compute Savings Plan
    - B. EC2 Instance Savings Plan
    - C. Zonal Reserved Instances
    - D. Standard Reserved Instances

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: A
      Explanation: Compute Savings Plans provide the most flexibility and help to reduce your costs by up to 66%. These plans automatically apply to EC2 instance usage regardless of instance family, size, AZ, Region, OS or tenancy, and also apply to Fargate or Lambda usage. EC2 Instance Savings Plans provide the lowest prices, offering savings up to 72% in exchange for commitment to usage of individual instance families in a Region https://aws.amazon.com/savingsplans/compute-pricing/
    </details>

35. A company collects data from a large number of participants who use wearable devices. The company stores the data in an Amazon DynamoDB table and uses applications to analyze the data. The data workload is constant and predictable. The company wants to stay at or below its forecasted budget for DynamoDB. Which solution will meet these requirements MOST cost-effectively?
    - A. Use provisioned mode and DynamoDB Standard-Infrequent Access (DynamoDB Standard-IA). Reserve capacity for the forecasted workload.
    - B. Use provisioned mode. Specify the read capacity units (RCUs) and write capacity units (WCUs).
    - C. Use on-demand mode. Set the read capacity units (RCUs) and write capacity units (WCUs) high enough to accommodate changes in the workload.
    - D. Use on-demand mode. Specify the read capacity units (RCUs) and write capacity units (WCUs)
with reserved capacity.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: B
      Explanation: "The data workload is constant and predictable." https://docs.aws.amazon.com/wellarchitected/latest/serverless-applications-lens/capacity.html "With provisioned capacity you pay for the provision of read and write capacity units for your DynamoDB tables. Whereas with DynamoDB on-demand you pay per request for the data reads and writes that your application performs on your tables."
    </details>

36. A company stores confidential data in an Amazon Aurora PostgreSQL database in the ap- southeast-3 Region. The database is encrypted with an AWS Key Management Service (AWS KMS) customer managed key. The company was recently acquired and must securely share a backup of the database with the acquiring company's AWS account in ap-southeast-3. What should a solutions architect do to meet these requirements?
    - A. Create a database snapshot. Copy the snapshot to a new unencrypted snapshot. Share the new snapshot with the acquiring company's AWS account.
    - B. Create a database snapshot. Add the acquiring company's AWS account to the KMS key policy. Share the snapshot with the acquiring company's AWS account.
    - C. Create a database snapshot that uses a different AWS managed KMS key. Add the acquiring company's AWS account to the KMS key alias. Share the snapshot with the acquiring company's AWS account.
    - D. Create a database snapshot. Download the database snapshot. Upload the database snapshot to an Amazon S3 bucket. Update the S3 bucket policy to allow access from the acquiring company's AWS account.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: B
      Explanation: https://aws.amazon.com/premiumsupport/knowledge-center/aurora-share-encrypted-snapshot/
    </details>

37. A company is moving its data management application to AWS. The company wants to transition to an event-driven architecture. The architecture needs to be more distributed and to use serverless concepts while performing the different aspects of the workflow. The company also wants to minimize operational overhead. Which solution will meet these requirements?
    - A. Build out the workflow in AWS Glue. Use AWS Glue to invoke AWS Lambda functions to process the workflow steps.
    - B. Build out the workflow in AWS Step Functions. Deploy the application on Amazon EC2 instances. Use Step Functions to invoke the workflow steps on the EC2 instances.
    - C. Build out the workflow in Amazon EventBridge. Use EventBridge to invoke AWS Lambda functions on a schedule to process the workflow steps.
    - D. Build out the workflow in AWS Step Functions. Use Step Functions to create a state machine. Use the state machine to invoke AWS Lambda functions to process the workflow steps.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: D
      Explanation: AWS Step functions is serverless Visual workflows for distributed applications。 https://aws.amazon.com/step-functions/
    </details>

38. A company is designing the network for an online multi-player game. The game uses the UDP networking protocol and will be deployed in eight AWS Regions. The network architecture needs to minimize latency and packet loss to give end users a high-quality gaming experience. Which solution will meet these requirements?
    - A. Setup a transit gateway in each Region. Create inter-Region peering attachments between each transit gateway.
    - B. Set up AWS Global Accelerator with UDP listeners and endpoint groups in each Region.
    - C. Set up Amazon CloudFront with UDP turned on. Configure an origin in each Region.
    - D. Set up a VPC peering mesh between each Region. Turn on UDP for each VPC. 

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: B
      Explanation: Global Accelerator supports the User Datagram Protocol (UDP) and Transmission Control Protocol (TCP), making it an excellent choice for an online multi-player game using UDP networking protocol. By setting up Global Accelerator with UDP listeners and endpoint groups in each Region, the network architecture can minimize latency and packet loss, giving end users a high-quality gaming experience.
    </details>

39. A company hosts a three-tier web application on Amazon EC2 instances in a single Availability Zone. The web application uses a self-managed MySQL database that is hosted on an EC2 instance to store data in an Amazon Elastic Block Store (Amazon EBS) volume. The MySQL database currently uses a 1 TB Provisioned IOPS SSD (io2) EBS volume. The company expects traffic of 1,000 IOPS for both reads and writes at peak traffic.
The company wants to minimize any disruptions, stabilize performance, and reduce costs while retaining the capacity for double the IOPS. The company wants to move the database tier to a fully managed solution that is highly available and fault tolerant. Which solution will meet these requirements MOST cost-effectively?
    - A. Use a Multi-AZ deployment of an Amazon RDS for MySQL DB instance with an io2 Block Express EBS volume.
    - B. Use a Multi-AZ deployment of an Amazon RDS for MySQL DB instance with a General Purpose SSD (gp2) EBS volume.
    - C. Use Amazon S3 Intelligent-Tiering access tiers.
    - D. Use two large EC2 instances to host the database in active-passive mode.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: B
      Explanation: RDS does not support IO2 or IO2express . GP2 can do the required IOPS. RDS supported Storage > https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/CHAP_Storage.html GP2 max IOPS > https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/general-purpose.html#gp2- performance
    </details>

40. A company hosts a serverless application on AWS. The application uses Amazon API Gateway, AWS Lambda, and an Amazon RDS for PostgreSQL database. The company notices an increase in application errors that result from database connection timeouts during times of peak traffic or unpredictable traffic. The company needs a solution that reduces the application failures with the least amount of change to the code. What should a solutions architect do to meet these requirements?
    - A. Reduce the Lambda concurrency rate.
    - B. Enable RDS Proxy on the RDS DB instance.
    - C. Resize the RDS DB instance class to accept more connections.
    - D. Migrate the database to Amazon DynamoDB with on-demand scaling.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: B
      Explanation: https://aws.amazon.com/rds/proxy/
    </details>

41. A company is migrating an old application to AWS. The application runs a batch job every hour and is CPU intensive. The batch job takes 15 minutes on average with an on-premises server. The server has 64 virtual CPU (vCPU) and 512 GiB of memory. Which solution will run the batch job within 15 minutes with the LEAST operational overhead?
    - A. Use AWS Lambda with functional scaling.
    - B. Use Amazon Elastic Container Service (Amazon ECS) with AWS Fargate.
    - C. Use Amazon Lightsail with AWS Auto Scaling.
    - D. Use AWS Batch on Amazon EC2.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: D
      Explanation: AWS Batch is a fully-managed service that can launch and manage the compute resources needed to execute batch jobs. It can scale the compute environment based on the size and timing of the batch jobs.
    </details>

42. A company stores its data objects in Amazon S3 Standard storage. A solutions architect has found that 75% of the data is rarely accessed after 30 days. The company needs all the data to remain immediately accessible with the same high availability and resiliency, but the company wants to minimize storage costs. Which storage solution will meet these requirements?
    - A. Move the data objects to S3 Glacier Deep Archive after 30 days.
    - B. Move the data objects to S3 Standard-Infrequent Access (S3 Standard-IA) after 30 days.
    - C. Move the data objects to S3 One Zone-Infrequent Access (S3 One Zone-IA) after 30 days.
    - D. Move the data objects to S3 One Zone-Infrequent Access (S3 One Zone-IA) immediately.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: B
      Explanation: Move the data objects to S3 Standard-Infrequent Access (S3 Standard-IA) after 30 days - will meet the requirements of keeping the data immediately accessible with high availability and resiliency, while minimizing storage costs. S3 Standard-IA is designed for infrequently accessed data, and it provides a lower storage cost than S3 Standard, while still offering the same low latency, high throughput, and high durability as S3 Standard.
    </details>

43. A company has a three-tier application on AWS that ingests sensor data from its users’ devices. The traffic flows through a Network Load Balancer (NLB), then to Amazon EC2 instances for the web tier, and finally to EC2 instances for the application tier. The application tier makes calls to a database. What should a solutions architect do to improve the security of the data in transit?
    - A. Configure a TLS listener. Deploy the server certificate on the NLB. - B. Configure AWS Shield Advanced. Enable AWS WAF on the NLB. - C. Change the load balancer to an Application Load Balancer (ALB). Enable AWS WAF on the ALB. - D. Encrypt the Amazon Elastic Block Store (Amazon EBS) volume on the EC2 instances by using AWS Key Management Service (AWS KMS).

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: A
      Explanation: Network Load Balancers now support TLS protocol. With this launch, you can now offload resource intensive decryption/encryption from your application servers to a high throughput, and low latency Network Load Balancer. Network Load Balancer is now able to terminate TLS traffic and set up connections with your targets either over TCP or TLS protocol. https://docs.aws.amazon.com/elasticloadbalancing/latest/network/create-tls-listener.html https://exampleloadbalancer.com/nlbtls_demo.html
    </details>

44. A social media company runs its application on Amazon EC2 instances behind an Application Load Balancer (ALB). The ALB is the origin for an Amazon CloudFront distribution. The application has more than a billion images stored in an Amazon S3 bucket and processes thousands of images each second. The company wants to resize the images dynamically and serve appropriate formats to clients. Which solution will meet these requirements with the LEAST operational overhead?
    - A. Install an external image management library on an EC2 instance. Use the image management library to process the images.
    - B. Create a CloudFront origin request policy. Use the policy to automatically resize images and to serve the appropriate format based on the User-Agent HTTP header in the request.
    - C. Use a Lambda@Edge function with an external image management library. Associate the Lambda@Edge function with the CloudFront behaviors that serve the images.
    - D. Create a CloudFront response headers policy. Use the policy to automatically resize images and to serve the appropriate format based on the User-Agent HTTP header in the request.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: C
      Explanation: https://aws.amazon.com/cn/blogs/networking-and-content-delivery/resizing-images-with-amazon- cloudfront-lambdaedge-aws-cdn-blog/
    </details>

45. A hospital needs to store patient records in an Amazon S3 bucket. The hospital's compliance team must ensure that all protected health information (PHI) is encrypted in transit and at rest. The compliance team must administer the encryption key for data at rest. Which solution will meet these requirements?
    - A. Create a public SSL/TLS certificate in AWS Certificate Manager (ACM). Associate the certificate with Amazon S3. Configure default encryption for each S3 bucket to use server-side encryption with AWS KMS keys (SSE-KMS). Assign the compliance team to manage the KMS keys.
    - B. Use the aws:SecureTransport condition on S3 bucket policies to allow only encrypted connections over HTTPS (TLS). Configure default encryption for each S3 bucket to use server-side encryption with S3 managed encryption keys (SSE-S3). Assign the compliance team to manage the SSE-S3 keys.
    - C. Use the aws:SecureTransport condition on S3 bucket policies to allow only encrypted connections over HTTPS (TLS). Configure default encryption for each S3 bucket to use server-side encryption with AWS KMS keys (SSE-KMS). Assign the compliance team to manage the KMS keys.
    - D. Use the aws:SecureTransport condition on S3 bucket policies to allow only encrypted connections over HTTPS (TLS). Use Amazon Macie to protect the sensitive data that is stored in Amazon S3. Assign the compliance team to manage Macie.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: C
      Explanation: It allows the compliance team to manage the KMS keys used for server-side encryption, thereby providing the necessary control over the encryption keys. Additionally, the use of the "aws:SecureTransport" condition on the bucket policy ensures that all connections to the S3 bucket are encrypted in transit.
    </details>

46. A company wants to migrate a Windows-based application from on premises to the AWS Cloud. The application has three tiers, a business tier, and a database tier with Microsoft SQL Server. The company wants to use specific features of SQL Server such as native backups and Data Quality Services. The company also needs to share files for process between the tiers. How should a solution architect design the architecture to meet these requirements?
    - A. Host all three on Amazon instances. Use Mmazon FSx File Gateway for file sharing between tiers.
    - B. Host all three on Amazon EC2 instances. Use Amazon FSx for Windows file sharing between the tiers.
    - C. Host the application tier and the business tier on Amazon EC2 instances. Host the database tier on
Amazon RDS. Use Amazon Elastic File system (Amazon EFS) for file sharing between the tiers.
    - D. Host the application tier and the business tier on Amazon EC2 instances. Host the database tier on Amazon RDS. Use a Provisioned IOPS SSD (io2) Amazon Elastic Block Store (Amazon EBS) volume for file sharing between the tiers.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: B
      Explanation: Data Quality Services: If this feature is critical to your workload, consider choosing Amazon RDS Custom or Amazon EC2. https://docs.aws.amazon.com/prescriptive-guidance/latest/migration-sql-server/comparison.html
    </details>

47. A company uses Amazon EC2 instances and AWS Lambda functions to run its application. The company has VPCs with public subnets and private subnets in its AWS account. The EC2 instances run in a private subnet in one of the VPCs. The Lambda functions need direct network access to the EC2 instances for the application to work. The application will run for at least 1 year. The company expects the number of Lambda functions that the application uses to increase during that time. The company wants to maximize its savings on all application resources and to keep network latency between the services low. Which solution will meet these requirements?
    - A. Purchase on an EC2 instance Savings Plan. Optimize the Lambda functions duration and memory usage and the number of invocations. Connect the Lambda functions to the private subnet that contains the EC2 instances.
    - B. Purchase on an EC2 instance Savings Plan. Optimize the Lambda functions duration and memory usage and the number of invocation, and the amount of data that is transfered. Connect the Lambda functions to a public subnet in the same VPC where the EC2 instances run.
    - C. Purchase a Compute Savings Plan. Optimize the Lambda functions duration and memory usage, the number of invocations, and the amount of data that is transferred. Connect the Lambda function to the Private subnet that contains the EC2 instances.
    - D. Purchase a Compute Savings Plan. Optimize the Lambda functions' duration and memory usage, the number of invocations, and the amount of data that is transferred. Keep the Lambda functions in the Lambda service VPC. 

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: C
      Explanation: By purchasing a Compute Savings Plan, the company can save on the costs of running both EC2 instances and Lambda functions. The Lambda functions can be connected to the private subnet that contains the EC2 instances through a VPC endpoint for AWS services or a VPC peering connection. This provides direct network access to the EC2 instances while keeping the traffic within the private network, which helps to minimize network latency. Optimizing the Lambda functions’ duration, memory usage, number of invocations, and amount of data transferred can help to further minimize costs and improve performance. Additionally, using a private subnet helps to ensure that the EC2 instances are not directly accessible from the public internet, which is a security best practice.
    </details>

48. A company is building a mobile app on AWS. The company wants to expand its reach to millions of users. The company needs to build a platform so that authorized users can watch the company's content on their mobile devices.
What should a solutions architect recommend to meet these requirements?
    - A. Publish content to a public Amazon S3 bucket. Use AWS Key Management Service (AWS KMS) keys to stream content.
    - B. Set up IPsec VPN between the mobile app and the AWS environment to stream content.
    - C. Use Amazon CloudFront Provide signed URLs to stream content.
    - D. Set up AWS Client VPN between the mobile app and the AWS environment to stream content.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: C
      Explanation: Amazon CloudFront is a content delivery network (CDN) that securely delivers data, videos, applications, and APIs to customers globally with low latency and high transfer speeds. CloudFront supports signed URLs that provide authorized access to your content. This feature allows the company to control who can access their content and for how long, providing a secure and scalable solution for millions of users. https://www.amazonaws.cn/en/cloudfront/
    </details>

49. A company is hosting a three-tier ecommerce application in the AWS Cloud. The company hosts the website on Amazon S3 and integrates the website with an API that handles sales requests. The company hosts the API on three Amazon EC2 instances behind an Application Load Balancer (ALB). The API consists of static and dynamic front-end content along with backend workers that process sales requests asynchronously. The company is expecting a significant and sudden increase in the number of sales requests during events for the launch of new products. What should a solutions architect recommend to ensure that all the requests are processed successfully?
    - A. Add an Amazon CloudFront distribution for the dynamic content. Increase the number of EC2 instances to handle the increase in traffic.
    - B. Add an Amazon CloudFront distribution for the static content. Place the EC2 instances in an Auto Scaling group to launch new instances based on network traffic.
    - C. Add an Amazon CloudFront distribution for the dynamic content. Add an Amazon ElastiCache instance in front of the ALB to reduce traffic for the API to handle.
    - D. Add an Amazon CloudFront distribution for the static content. Add an Amazon Simple Queue Service (Amazon SOS) queue to receive requests from the website for later processing by the EC2 instances.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: D
      Explanation: Static content can include images and style sheets that are the same across all users and are best cached at the edges of the content distribution network (CDN). Dynamic content includes information that changes frequently or is personalized based on user preferences, behavior, location or other factors - all content is sales requests.
    </details>

50. A company’s web application consists of an Amazon API Gateway API in front of an AWS Lambda function and an Amazon DynamoDB database. The Lambda function handles the business logic, and the DynamoDB table hosts the data. The application uses Amazon Cognito user pools to
identify the individual users of the application. A solutions architect needs to update the application so that only users who have a subscription can access premium content. Which solution will meet this requirement with the LEAST operational overhead?
    - A. Enable API caching and throttling on the API Gateway API.
    - B. Set up AWS WAF on the API Gateway API Create a rule to filter users who have a subscription.
    - C. Apply fine-grained IAM permissions to the premium content in the DynamoDB table.
    - D. Implement API usage plans and API keys to limit the access of users who do not have a subscription.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: D
      Explanation: To meet the requirement with the least operational overhead, you can implement API usage plans and API keys to limit the access of users who do not have a subscription. This way, you can control access to your API Gateway APIs by requiring clients to submit valid API keys with requests. You can associate usage plans with API keys to configure throttling and quota limits on individual client accounts. https://docs.aws.amazon.com/apigateway/latest/developerguide/api-gateway-api-usage- plans.html
    </details>

51. A company recently created a disaster recovery site in a different AWS Region. The company needs to transfer large amounts of data back and forth between NFS file systems in the two Regions on a periodic basis. Which solution will meet these requirements with the LEAST operational overhead?
    - A. Use AWS DataSync.
    - B. Use AWS Snowball devices
    - C. Set up an SFTP server on Amazon EC2
    - D. Use AWS Database Migration Service (AWS DMS)

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: A
      Explanation: AWS DataSync is a fully managed data transfer service that simplifies moving large amounts of data between on-premises storage systems and AWS services. It can also transfer data between
      different AWS services, including different AWS Regions. DataSync provides a simple, scalable, and automated solution to transfer data, and it minimizes the operational overhead because it is fully managed by AWS.
    </details>

52. A company has an On-premises volume backup solution that has reached its end of life. The company wants to use AWS as part of a new backup solution and wants to maintain local access to all the data while it is backed up on AWS. The company wants to ensure that the data backed up on AWS is automatically and securely transferred. Which solution meets these requirements?
    - A. Use AWS Snowball to migrate data out of the on-premises solution to Amazon S3. Configure on- premises systems to mount the Snowball S3 endpoint to provide local access to the data.
    - B. Use AWS Snowball Edge to migrate data out of the on-premises solution to Amazon S3. Use the Snowball Edge file interface to provide on-premises systems with local access to the data.
    - C. Use AWS Storage Gateway and configure a cached volume gateway. Run the Storage Gateway software application on premises and configure a percentage of data to cache locally. Mount the gateway storage volumes to provide local access to the data.
    - D. Use AWS Storage Gateway and configure a stored volume gateway. Run the Storage software application on premises and map the gateway storage volumes to on-premises storage. Mount the gateway storage volumes to provide local access to the data.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: D
      Explanation: https://docs.aws.amazon.com/storagegateway/latest/vgw/WhatIsStorageGateway.html
    </details>

53. A company runs an application on Amazon EC2 instances. The company needs to implement a disaster recovery (DR) solution for the application. The DR solution needs to have a recovery time objective (RTO) of less than 4 hours. The DR solution also needs to use the fewest possible AWS resources during normal operations. Which solution will meet these requirements in the MOST operationally efficient way?
    - A. Create Amazon Machine Images (AMIs) to back up the EC2 instances. Copy the AMIs to a secondary AWS Region. Automate infrastructure deployment in the secondary Region by using AWS Lambda and custom scripts.
    - B. Create Amazon Machine Images (AMIs) to back up the EC2 instances. Copy the AMIs to a secondary AWS Region. Automate infrastructure deployment in the secondary Region by using AWS CloudFormation.
    - C. Launch EC2 instances in a secondary AWS Region. Keep the EC2 instances in the secondary Region active at all times.
    - D. Launch EC2 instances in a secondary Availability Zone. Keep the EC2 instances in the secondary Availability Zone active at all times.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: B
      Explanation: Option B would be the most operationally efficient solution for implementing a DR solution for the application, meeting the requirement of an RTO of less than 4 hours and using the fewest possible AWS resources during normal operations. By creating Amazon Machine Images (AMIs) to back up the EC2 instances and copying them to a secondary AWS Region, the company can ensure that they have a reliable backup in the event of
      a disaster. By using AWS CloudFormation to automate infrastructure deployment in the secondary Region, the company can minimize the amount of time and effort required to set up the DR solution.
    </details>

54. A company hosts a multiplayer gaming application on AWS. The company wants the application to read data with sub-millisecond latency and run one-time queries on historical data. Which solution will meet these requirements with the LEAST operational overhead?
    - A. Use Amazon RDS for data that is frequently accessed. Run a periodic custom script to export the data to an Amazon S3 bucket.
    - B. Store the data directly in an Amazon S3 bucket. Implement an S3 Lifecycle policy to move older data to S3 Glacier Deep Archive for long-term storage. Run one-time queries on the data in Amazon S3 by using Amazon Athena
    - C. Use Amazon DynamoDB with DynamoDB Accelerator (DAX) for data that is frequently accessed. Export the data to an Amazon S3 bucket by using DynamoDB table export. Run one-time queries on the data in Amazon S3 by using Amazon Athena.
    - D. Use Amazon DynamoDB for data that is frequently accessed. Turn on streaming to Amazon Kinesis Data Streams. Use Amazon Kinesis Data Firehose to read the data from Kinesis Data Streams. Store the records in an Amazon S3 bucket.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: C
      Explanation: DynamoDB supports some of the world's largest scale applications by providing consistent, single- digit millisecond response times at any scale. You can build applications with virtually unlimited throughput and storage. https://aws.amazon.com/dynamodb/dax/?nc1=h_ls
    </details>

55. A solutions architect is designing a company’s disaster recovery (DR) architecture. The company has a MySQL database that runs on an Amazon EC2 instance in a private subnet with scheduled backup. The DR design needs to include multiple AWS Regions. Which solution will meet these requirements with the LEAST operational overhead?
    - A. Migrate the MySQL database to multiple EC2 instances. Configure a standby EC2 instance in the DR Region Turn on replication.
    - B. Migrate the MySQL database to Amazon RDS. Use a Multi-AZ deployment. Turn on read replication for the primary DB instance in the different Availability Zones.
    - C. Migrate the MySQL database to an Amazon Aurora global database. Host the primary DB cluster in the primary Region. Host the secondary DB cluster in the DR Region.
    - D. Store the schedule backup of the MySQL database in an Amazon S3 bucket that is configured for S3 Cross-Region Replication (CRR). Use the data backup to restore the database in the DR Region.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: C
      Explanation: https://docs.aws.amazon.com/AmazonRDS/latest/AuroraUserGuide/Aurora.Replication.html
    </details>

56. A solutions architect wants all new users to have specific complexity requirements and mandatory rotation periods tor IAM user passwords. What should the solutions architect do to accomplish this?
    - A. Set an overall password policy for the entire AWS account.
    - B. Set a password policy for each IAM user in the AWS account.
    - C. Use third-party vendor software to set password requirements.
    - D. Attach an Amazon CloudWatch rule to the Create_newuser event to set the password with the appropriate requirements.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: A
      Explanation: To accomplish this, the solutions architect should set an overall password policy for the entire AWS account. This policy will apply to all IAM users in the account, including new users.
    </details>

57. A company is planning to migrate a commercial off-the-shelf application from is on-premises data center to AWS. The software has a software licensing model using sockets and cores with predictable capacity and uptime requirements. The company wants to use its existing licenses, which were purchased earlier this year. Which Amazon EC2 pricing option is the MOST cost-effective?
    - A. Dedicated Reserved Hosts
    - B. Dedicated On-Demand Hosts
    - C. Dedicated Reserved Instances
    - D. Dedicated On-Demand Instances

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: A
      Explanation: Dedicated Host Reservations provide a billing discount compared to running On-Demand Dedicated Hosts. Reservations are available in three payment options. https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/dedicated-hosts-overview.html
    </details>

58. An ecommerce company is experiencing an increase in user traffic. The company's store is deployed on Amazon EC2 instances as a two-tier web application consisting of a web tier and a separate database tier. As traffic increases, the company notices that the architecture is causing significant delays in sending timely marketing and order confirmation email to users. The company wants to reduce the time it spends resolving complex email delivery issues and minimize operational overhead. What should a solutions architect do to meet these requirements?
    - A. Create a separate application tier using EC2 instances dedicated to email processing.
    - B. Configure the web instance to send email through Amazon Simple Email Service (Amazon SES).
    - C. Configure the web instance to send email through Amazon Simple Notification Service (Amazon SNS).
    - D. Create a separate application tier using EC2 instances dedicated to email processing. Place the instances in an Auto Scaling group.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: B
      Explanation: Amazon SES is a cost-effective and scalable email service that enables businesses to send and receive email using their own email addresses and domains. Configuring the web instance to send email through Amazon SES is a simple and effective solution that can reduce the time spent resolving complex email delivery issues and minimize operational overhead.
    </details>

59. A company is deploying a two-tier web application in a VPC. The web tier is using an Amazon EC2 Auto Scaling group with public subnets that span multiple Availability Zones. The database tier consists of an Amazon RDS for MySQL DB instance in separate private subnets. The web tier requires access to the database to retrieve product information. The web application is not working as intended. The web application reports that it cannot connect to the database. The database is confirmed to be up and running. All configurations for the network ACLs, security groups, and route tables are still in their default states. What should a solutions architect recommend to fix the application?
    - A. Add an explicit rule to the private subnet's network ACL to allow traffic from the web tier's EC2 instances.
    - B. Add a route in the VPC route table to allow traffic between the web tier’s EC2 instances and the database tier.
    - C. Deploy the web tier's EC2 instances and the database tier's RDS instance into two separate VPCs and configure VPC peering.
    - D. Add an inbound rule to the security group of the database tier's RDS instance to allow traffic from the web tier's security group.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: D
      Explanation: By default, all inbound traffic to an RDS instance is blocked. Therefore, an inbound rule needs to be added to the security group of the RDS instance to allow traffic from the security group of the web tier's EC2 instances.
    </details>

60. A company is running a multi-tier ecommerce web application in the AWS Cloud. The application runs on Amazon EC2 instances with an Amazon RDS for MySQL Multi-AZ DB instance. Amazon RDS is configured with the latest generation DB instance with 2,000 GB of storage in a General Purpose SSD (gp3) Amazon Elastic Block Store (Amazon EBS) volume. The database performance affects the application during periods of high demand. A database administrator analyzes the logs in Amazon CloudWatch Logs and discovers that the application performance always degrades when the number of read and write IOPS is higher than 20,000. What should a solutions architect do to improve the application performance?
    - A. Replace the volume with a magnetic volume.
    - B. Increase the number of IOPS on the gp3 volume.
    - C. Replace the volume with a Provisioned IOPS SSD (Io2) volume.
    - D. Replace the 2,000 GB gp3 volume with two 1,000 GB gp3 volumes.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: D
      Explanation: To improve the application performance, you can replace the 2,000 GB gp3 volume with two 1,000 GB gp3 volumes. This will increase the number of IOPS available to the database and improve performance. https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/CHAP_Storage.html
    </details>

61. A company is deploying a new application on Amazon EC2 instances. The application writes data to Amazon Elastic Block Store (Amazon EBS) volumes. The company needs to ensure that all data that is written to the EBS volumes is encrypted at rest. Which solution will meet this requirement?
    - A. Create an IAM role that specifies EBS encryption. Attach the role to the EC2 instances.
    - B. Create the EBS volumes as encrypted volumes. Attach the EBS volumes to the EC2 instances.
    - C. Create an EC2 instance tag that has a key of Encrypt and a value of True. Tag all instances that require encryption at the ESS level.
    - D. Create an AWS Key Management Service (AWS KMS) key policy that enforces EBS encryption in the account Ensure that the key policy is active.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: B
      Explanation: When you create an EBS volume, you can specify whether to encrypt the volume. If you choose to encrypt the volume, all data written to the volume is automatically encrypted at rest using AWS- managed keys. You can also use customer-managed keys (CMKs) stored in AWS KMS to encrypt and protect your EBS volumes. You can create encrypted EBS volumes and attach them to EC2 instances to ensure that all data written to the volumes is encrypted at rest.
    </details>

62. A company is moving its data management application to AWS. The company wants to transition to an event-driven architecture. The architecture needs to be more distributed and to use serverless concepts while performing the different aspects of the workflow. The company also wants to minimize operational overhead. Which solution will meet these requirements?
    - A. Build out the workflow in AWS Glue. Use AWS Glue to invoke AWS Lambda functions to process the workflow slaps.
    - B. Build out the workflow in AWS Step Functions. Deploy the application on Amazon EC2 Instances. Use Step Functions to invoke the workflow steps on the EC2 instances.
    - C. Build out the workflow in Amazon EventBridge. Use EventBridge to invoke AWS Lambda functions on a schedule to process the workflow steps.
    - D. Build out the workflow in AWS Step Functions. Use Step Functions to create a state machine. Use the state machine to invoke AWS Lambda functions to process the workflow steps.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: D
      Explanation: Step 3: Create a State Machine Use the Step Functions console to create a state machine that invokes the Lambda function that you created earlier in Step 1. https://docs.aws.amazon.com/step-functions/latest/dg/tutorial-creating-lambda-state- machine.html In Step Functions, a workflow is called a state machine, which is a series of event-driven steps. Each step in a workflow is called a state.
    </details>

63. An image-hosting company stores its objects in Amazon S3 buckets. The company wants to avoid accidental exposure of the objects in the S3 buckets to the public. All S3 objects in the entire AWS account need to remain private.
Which solution will meal these requirements?
    - A. Use Amazon GuardDuty to monitor S3 bucket policies. Create an automatic remediation action rule that uses an AWS Lambda function to remediate any change that makes the objects public.
    - B. Use AWS Trusted Advisor to find publicly accessible S3 Dockets. Configure email notifications In Trusted Advisor when a change is detected manually change the S3 bucket policy if it allows public access.
    - C. Use AWS Resource Access Manager to find publicly accessible S3 buckets. Use Amazon Simple Notification Service (Amazon SNS) to invoke an AWS Lambda function when a change it detected. Deploy a Lambda function that programmatically remediates the change.
    - D. Use the S3 Block Public Access feature on the account level. Use AWS Organizations to create a service control policy (SCP) that prevents IAM users from changing the setting. Apply tie SCP to tie account.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: D
      Explanation: https://docs.aws.amazon.com/AmazonS3/latest/userguide/access-control-block-public- access.html
    </details>

64. A financial company hosts a web application on AWS. The application uses an Amazon API Gateway Regional API endpoint to give users the ability to retrieve current stock prices. The company's security team has noticed an increase in the number of API requests. The security team is concerned that HTTP flood attacks might take the application offline. A solutions architect must design a solution to protect the application from this type of attack. Which solution meats these requirements with the LEAST operational overhead?
    - A. Create an Amazon CloudFront distribution in front of the API Gateway Regional API endpoint with a maximum TTL of 24 hours.
    - B. Create a Regional AWS WAF web ACL with a rate-based rule. Associate the web ACL with the API Gateway stage.
    - C. Use Amazon CloudWatch metrics to monitor the Count metric and alert the security team when the predefined rate is reached.
    - D. Create an Amazon CloudFront distribution with Lambda@Edge in front of the API Gateway Regional API endpoint. Create an AWS Lambda function to block requests from IP addresses that exceed the predefined rate.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: B
      Explanation: A rate-based rule in AWS WAF allows the security team to configure thresholds that trigger rate- based rules, which enable AWS WAF to track the rate of requests for a specified time period and then block them automatically when the threshold is exceeded. This provides the ability to prevent HTTP flood attacks with minimal operational overhead. https://docs.aws.amazon.com/waf/latest/developerguide/web-acl.html
    </details>

65. A company is migrating its on-premises workload to the AWS Cloud. The company already uses several Amazon EC2 instances and Amazon RDS DB instances. The company wants a solution that automatically starts and stops the EC2 instances and D6 instances outside of business hours. The solution must minimize cost and infrastructure maintenance. Which solution will meet these requirement?
    - A. Scale the EC2 instances by using elastic resize Scale the DB instances to zero outside of business hours.
    - B. Explore AWS Marketplace for partner solutions that will automatically start and stop the EC2 Instances and OB instances on a schedule.
    - C. Launch another EC2 instance. Configure a crontab schedule to run shell scripts that will start and stop the existing EC2 instances and DB instances on a schedule.
    - D. Create an AWS Lambda function that will start and stop the EC2 instances and DB instances. Configure Amazon EventBridge to invoke the Lambda function on a schedule.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: D
      Explanation: The most efficient solution for automatically starting and stopping EC2 instances and DB instances on a schedule while minimizing cost and infrastructure maintenance is to create an AWS Lambda function and configure Amazon EventBridge to invoke the function on a schedule.
    </details>
