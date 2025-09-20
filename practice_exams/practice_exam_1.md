---
layout: exam
---

# Practice Exam 1

1. A company has a website hosted on AWS The website is behind an Application Load Balancer (ALB) that is configured to handle HTTP and HTTPS separately. The company wants to forward all requests to the website so that the requests will use HTTPS. What should a solutions architect do to meet this requirement?
    - A. Update the ALB's network ACL to accept only HTTPS traffic
    - B. Create a rule that replaces the HTTP in the URL with HTTPS.
    - C. Create a listener rule on the ALB to redirect HTTP traffic to HTTPS.
    - D. Replace the ALB with a Network Load Balancer configured to use Server Name Indication (SNI).

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: C
      Explanation: To redirect HTTP traffic to HTTPS, a solutions architect should create a listener rule on the ALB to redirect HTTP traffic to HTTPS. Option A is not correct because network ACLs do not have the ability to redirect traffic. Option B is not correct because it does not redirect traffic, it only replaces the URL. Option D is not correct because a Network Load Balancer does not have the ability to handle HTTPS traffic. https://docs.aws.amazon.com/fr_fr/elasticloadbalancing/latest/application/create-https- listener.html https://aws.amazon.com/fr/premiumsupport/knowledge-center/elb-redirect-http-to-https-using-alb/
    </details>

2. A company is developing a two-tier web application on AWS. The company's developers have deployed the application on an Amazon EC2 instance that connects directly to a backend Amazon RDS database. The company must not hardcode database credentials in the application. The company must also implement a solution to automatically rotate the database credentials on a regular basis. Which solution will meet these requirements with the LEAST operational overhead?
    - A. Store the database credentials in the instance metadata. Use Amazon EventBridge (Amazon CloudWatch Events) rules to run a scheduled AWS Lambda function that updates the RDS credentials and instance metadata at the same time.
    - B. Store the database credentials in a configuration file in an encrypted Amazon S3 bucket. Use Amazon EventBridge (Amazon CloudWatch Events) rules to run a scheduled AWS Lambda function that updates the RDS credentials and the credentials in the configuration file at the same time. Use S3 Versioning to ensure the ability to fall back to previous values.
    - C. Store the database credentials as a secret in AWS Secrets Manager. Turn on automatic rotation for the secret. Attach the required permission to the EC2 role to grant access to the secret.
    - D. Store the database credentials as encrypted parameters in AWS Systems Manager Parameter Store. Turn on automatic rotation for the encrypted parameters. Attach the required permission to the EC2 role to grant access to the encrypted parameters.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: C
      Explanation: Secrets manager supports Autorotation unlike Parameter store. AWS Secrets Manager is a service that enables you to easily rotate, manage, and retrieve database credentials, API keys, and other secrets throughout their lifecycle. By storing the database credentials as a secret in Secrets Manager, you can ensure that they are not hardcoded
      in the application and that they are automatically rotated on a regular basis. To grant the EC2 instance access to the secret, you can attach the required permission to the EC2 role. This will allow the application to retrieve the secret from Secrets Manager as needed. https://docs.aws.amazon.com/secretsmanager/latest/userguide/create_database_secret.html
    </details>

3. A company is deploying a new public web application to AWS. The application will run behind an Application Load Balancer (ALB). The application needs to be encrypted at the edge with an SSL/TLS certificate that is issued by an external certificate authority (CA). The certificate must be rotated each year before the certificate expires. What should a solutions architect do to meet these requirements?
    - A. Use AWS Certificate Manager (ACM) to issue an SSL/TLS certificate. Apply the certificate to the ALB. Use the managed renewal feature to automatically rotate the certificate.
    - B. Use AWS Certificate Manager (ACM) to issue an SSL/TLS certificate. Import the key material from the certificate. Apply the certificate to the ALB. Use the managed renewal feature to automatically rotate the certificate.
    - C. Use AWS Certificate Manager (ACM) Private Certificate Authority to issue an SSL/TLS certificate from the root CA. Apply the certificate to the ALB. Use the managed renewal feature to automatically rotate the certificate.
    - D. Use AWS Certificate Manager (ACM) to import an SSL/TLS certificate. Apply the certificate to the ALB. Use Amazon EventBridge (Amazon CloudWatch Events) to send a notification when the certificate is nearing expiration. Rotate the certificate manually.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: D
      Explanation: ACM does not manage the renewal process for imported certificates. You are responsible for monitoring the expiration date of your imported certificates and for renewing them before they expire. Check this question on the link below: Q: What types of certificates can I create and manage with ACM? https://www.amazonaws.cn/en/certificate-manager/faqs/#Managed_renewal_and_deployment
    </details>

4. A company runs its infrastructure on AWS and has a registered base of 700,000 users for its document management application. The company intends to create a product that converts large .pdf files to .jpg image files. The .pdf files average 5 MB in size. The company needs to store the original files and the converted files. A solutions architect must design a scalable solution to accommodate demand that will grow rapidly over time. Which solution meets these requirements MOST cost-effectively?
    - A. Save the .pdf files to Amazon S3. Configure an S3 PUT event to invoke an AWS Lambda function to convert the files to .jpg format and store them back in Amazon S3.
    - B. Save the .pdf files to Amazon DynamoDUse the DynamoDB Streams feature to invoke an AWS Lambda function to convert the files to .jpg format and store them back in DynamoDB. - C. Upload the .pdf files to an AWS Elastic Beanstalk application that includes Amazon EC2 instances, Amazon Elastic Block Store (Amazon EBS) storage, and an Auto Scaling group. Use a program in the EC2 instances to convert the files to .jpg format. Save the .pdf files and the .jpg files in the EBS store.
    - D. Upload the .pdf files to an AWS Elastic Beanstalk application that includes Amazon EC2 instances, Amazon Elastic File System (Amazon EFS) storage, and an Auto Scaling group. Use a program in the EC2 instances to convert the file to .jpg format. Save the .pdf files and the .jpg files in the EBS store.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: A
      Explanation: Elastic BeanStalk is expensive, and DocumentDB has a 400KB max to upload files. So Lambda and S3 should be the one.
    </details>

5. A company has more than 5 TB of file data on Windows file servers that run on premises. Users and applications interact with the data each day. The company is moving its Windows workloads to AWS. As the company continues this process, the company requires access to AWS and on-premises file storage with minimum latency. The company needs a solution that minimizes operational overhead and requires no significant changes to the existing file access patterns. The company uses an AWS Site-to-Site VPN connection for connectivity to AWS. What should a solutions architect do to meet these requirements?
    - A. Deploy and configure Amazon FSx for Windows File Server on AWS. Move the on-premises file data to FSx for Windows File Server. Reconfigure the workloads to use FSx for Windows File Server on AWS.
    - B. Deploy and configure an Amazon S3 File Gateway on premises. Move the on-premises file data to the S3 File Gateway. Reconfigure the on-premises workloads and the cloud workloads to use the S3 File Gateway
    - C. Deploy and configure an Amazon S3 File Gateway on premises. Move the on-premises file data to Amazon S3. Reconfigure the workloads to use either Amazon S3 directly or the S3 File Gateway, depending on each workload's location.
    - D. Deploy and configure Amazon FSx for Windows File Server on AWS. Deploy and configure an Amazon FSx File Gateway on premises. Move the on-premises file data to the FSx File Gateway. Configure the cloud workloads to use FSx for Windows File Server on AWS. Configure the on-premises workloads to use the FSx File Gateway.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: D
      Explanation: Amazon FSx File Gateway (FSx File Gateway) is a new File Gateway type that provides low latency and efficient access to in-cloud FSx for Windows File Server file shares from your on-premises facility. If you maintain on-premises file storage because of latency or bandwidth requirements, you can instead use FSx File Gateway for seamless access to fully managed, highly reliable, and virtually unlimited Windows file shares provided in the AWS Cloud by FSx for Windows File Server. https://docs.aws.amazon.com/filegateway/latest/filefsxw/what-is-file-fsxw.html
    </details>

6. A hospital recently deployed a RESTful API with Amazon API Gateway and AWS Lambda. The hospital uses API Gateway and Lambda to upload reports that are in PDF format and JPEG format. The hospital needs to modify the Lambda code to identify protected health information (PHI) in the
reports. Which solution will meet these requirements with the LEAST operational overhead?
    - A. Use existing Python libraries to extract the text from the reports and to identify the PHI from the extracted text.
    - B. Use Amazon Textract to extract the text from the reports. Use Amazon SageMaker to identify the PHI from the extracted text.
    - C. Use Amazon Textract to extract the text from the reports. Use Amazon Comprehend Medical to identify the PHI from the extracted text.
    - D. Use Amazon Rekognition to extract the text from the reports. Use Amazon Comprehend Medical to identify the PHI from the extracted text.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: C
      Explanation: Using Amazon Textract to extract the text from the reports, and Amazon Comprehend Medical to identify the PHI from the extracted text, would be the most efficient solution as it would involve the least operational overhead. Textract is specifically designed for extracting text from documents, and Comprehend Medical is a fully managed service that can accurately identify PHI in medical text. This solution would require minimal maintenance and would not incur any additional costs beyond the usage fees for Textract and Comprehend Medical.
    </details>

7. A company has an application that generates a large number of files, each approximately 5 MB in size. The files are stored in Amazon S3. Company policy requires the files to be stored for 4 years before they can be deleted. Immediate accessibility is always required as the files contain critical business data that is not easy to reproduce. The files are frequently accessed in the first 30 days of the object creation but are rarely accessed after the first 30 days. Which storage solution is MOST cost-effective?
    - A. Create an S3 bucket lifecycle policy to move Mm from S3 Standard to S3 Glacier 30 days from object creation. Delete the Tiles 4 years after object creation
    - B. Create an S3 bucket lifecycle policy to move tiles from S3 Standard to S3 One Zone-infrequent Access (S3 One Zone-IA) 30 days from object creation. Delete the fees 4 years after object creation
    - C. Create an S3 bucket lifecycle policy to move files from S3 Standard-infrequent Access (S3 Standard -lA) 30 from object creation. Delete the ties 4 years after object creation
    - D. Create an S3 bucket Lifecycle policy to move files from S3 Standard to S3 Standard-Infrequent Access (S3 Standard-IA) 30 days from object creation. Move the files to S3 Glacier 4 years after object carton.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: C
      Explanation: Immediate accessibility is always required as the files contain critical business data that is not easy to reproduce. If they do not explicitly mention that they are using Glacier Instant Retrieval, we should assume that Glacier -> takes more time to retrieve and may not meet the requirements.
    </details>

8. A company hosts an application on multiple Amazon EC2 instances. The application processes messages from an Amazon SQS queue writes to an Amazon RDS table and deletes the message from the queue Occasional duplicate records are found in the RDS table. The SQS queue does not contain any duplicate messages.
What should a solutions architect do to ensure messages are being processed once only?
    - A. Use the CreateQueue API call to create a new queue
    - B. Use the Add Permission API call to add appropriate permissions
    - C. Use the ReceiveMessage API call to set an appropriate wail time
    - D. Use the ChangeMessageVisibility APi call to increase the visibility timeout

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: D
      Explanation: The visibility timeout begins when Amazon SQS returns a message. During this time, the consumer processes and deletes the message. However, if the consumer fails before deleting the message and your system doesn't call the DeleteMessage action for that message before the visibility timeout expires, the message becomes visible to other consumers and the message is received again. If a message must be received only once, your consumer should delete it within the duration of the visibility timeout. https://docs.aws.amazon.com/AWSSimpleQueueService/latest/SQSDeveloperGuide/sqs- visibility-timeout.html Keyword: SQS queue writes to an Amazon RDS From this, Option D best suite &amp; other Options ruled out [Option A -You can't intruduce one more Queue in the existing one; Option B - only Permission &amp; Option C -Only Retrieves Messages] FIF O queues are designed to never introduce duplicate messages. However, your message producer might introduce duplicates in certain scenarios: for example, if the producer sends a message, does not receive a response, and then resends the same message. Amazon SQS APIs provide deduplication functionality that prevents your message producer from sending duplicates. Any duplicates introduced by the message producer are removed within a 5-minute deduplication interval. For standard queues, you might occasionally receive a duplicate copy of a message (at-least-once delivery). If you use a standard queue, you must design your applications to be idempotent (that is, they must not be affected adversely when processing the same message more than once).
    </details>

9. A solutions architect is designing a new hybrid architecture to extend a company s on-premises infrastructure to AWS. The company requires a highly available connection with consistent low latency to an AWS Region. The company needs to minimize costs and is willing to accept slower traffic if the primary connection fails. What should the solutions architect do to meet these requirements?
    - A. Provision an AWS Direct Connect connection to a Region. Provision a VPN connection as a backup if the primary Direct Connect connection fails.
    - B. Provision a VPN tunnel connection to a Region for private connectivity. Provision a second VPN tunnel for private connectivity and as a backup if the primary VPN connection fails.
    - C. Provision an AWS Direct Connect connection to a Region. Provision a second Direct Connect connection to the same Region as a backup if the primary Direct Connect connection fails.
    - D. Provision an AWS Direct Connect connection to a Region. Use the Direct Connect failover attribute from the AWS CLI to automatically create a backup connection if the primary Direct Connect connection fails.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: A
      Explanation: "In some cases, this connection alone is not enough. It is always better to guarantee a fallback connection as the backup of DX. There are several options, but implementing it with an AWS Site-
      To-Site VPN is a real cost-effective solution that can be exploited to reduce costs or, in the meantime, wait for the setup of a second DX." https://www.proud2becloud.com/hybrid-cloud-networking-backup-aws-direct-connect-network- connection-with-aws-site-to-site-vpn/
    </details>

10. A company is running a business-critical web application on Amazon EC2 instances behind an Application Load Balancer. The EC2 instances are in an Auto Scaling group. The application uses an Amazon Aurora PostgreSQL database that is deployed in a single Availability Zone. The company wants the application to be highly available with minimum downtime and minimum loss of data. Which solution will meet these requirements with the LEAST operational effort?
    - A. Place the EC2 instances in different AWS Regions. Use Amazon Route 53 health checks to redirect traffic. Use Aurora PostgreSQL Cross-Region Replication.
    - B. Configure the Auto Scaling group to use multiple Availability Zones. Configure the database as Multi-AZ. Configure an Amazon RDS Proxy instance for the database.
    - C. Configure the Auto Scaling group to use one Availability Zone. Generate hourly snapshots of the database. Recover the database from the snapshots in the event of a failure.
    - D. Configure the Auto Scaling group to use multiple AWS Regions. Write the data from the application to Amazon S3. Use S3 Event Notifications to launch an AWS Lambda function to write the data to the database.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: B
      Explanation: By configuring the Auto Scaling group to use multiple Availability Zones, the application will be able to continue running even if one Availability Zone goes down. Configuring the database as Multi-AZ will also ensure that the database remains available in the event of a failure in one Availability Zone. Using an Amazon RDS Proxy instance for the database will allow the application to automatically route traffic to healthy database instances, further increasing the availability of the application. This solution will meet the requirements for high availability with minimal operational effort. https://docs.aws.amazon.com/AmazonRDS/latest/AuroraUserGuide/rds-proxy.html
    </details>

11. A company's HTTP application is behind a Network Load Balancer (NLB). The NLB's target group is configured to use an Amazon EC2 Auto Scaling group with multiple EC2 instances that run the web service. The company notices that the NLB is not detecting HTTP errors for the application. These errors require a manual restart of the EC2 instances that run the web service. The company needs to improve the application's availability without writing custom scripts or code. What should a solutions architect do to meet these requirements?
    - A. Enable HTTP health checks on the NLB. supplying the URL of the company's application.
    - B. Add a cron job to the EC2 instances to check the local application's logs once each minute. If HTTP errors are detected, the application will restart.
    - C. Replace the NLB with an Application Load Balancer. Enable HTTP health checks by supplying the URL of the company's application.
Configure an Auto Scaling action to replace unhealthy instances.
    - D. Create an Amazon Cloud Watch alarm that monitors the UnhealthyHostCount metric for the NLB. Configure an Auto Scaling action to replace unhealthy instances when the alarm is in the ALARM state.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: C
      Explanation: NLB does not handle HTTP (layer 7) listerns errors only TCP (layer 4) listeners. https://docs.aws.amazon.com/elasticbeanstalk/latest/dg/environments-cfg-nlb.html
    </details>

12. A company runs a shopping application that uses Amazon DynamoDB to store customer information. In case of data corruption, a solutions architect needs to design a solution that meets a recovery point objective (RPO) of 15 minutes and a recovery time objective (RTO) of 1 hour. What should the solutions architect recommend to meet these requirements?
    - A. Configure DynamoDB global tables. For RPO recovery, point the application to a different AWS Region.
    - B. Configure DynamoDB point-in-time recovery. For RPO recovery, restore to the desired point in time.
    - C. Export the DynamoDB data to Amazon S3 Glacier on a daily basis. For RPO recovery, import the data from S3 Glacier to DynamoDB. - D. Schedule Amazon Elastic Block Store (Amazon EBS) snapshots for the DynamoDB table every 15 minutes. For RPO recovery, restore the DynamoDB table by using the EBS snapshot.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: B
      Explanation: Point in Time Recovery is designed as a continuous backup juts to recover it fast. It covers perfectly the RPO, and probably the RTO. https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/PointInTimeRecovery.ht ml
    </details>

13. A company wants to move a multi-tiered application from on premises to the AWS Cloud to improve the application's performance. The application consists of application tiers that communicate with each other by way of RESTful services. Transactions are dropped when one tier becomes overloaded. A solutions architect must design a solution that resolves these issues and modernizes the application. Which solution meets these requirements and is the MOST operationally efficient?
    - A. Use Amazon API Gateway and direct transactions to the AWS Lambda functions as the application layer. Use Amazon Simple Queue Service (Amazon SQS) as the communication layer between application services.
    - B. Use Amazon CloudWatch metrics to analyze the application performance history to determine the server's peak utilization during the performance failures. Increase the size of the application server's Amazon EC2 instances to meet the peak requirements.
    - C. Use Amazon Simple Notification Service (Amazon SNS) to handle the messaging between application servers running on Amazon EC2 in an Auto Scaling group. Use Amazon CloudWatch to monitor the SNS queue length and scale up and down as required.
    - D. Use Amazon Simple Queue Service (Amazon SQS) to handle the messaging between application servers running on Amazon EC2 in an Auto Scaling group. Use Amazon CloudWatch to monitor the SQS queue length and scale up when communication failures are detected.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: A
      Explanation: Lambda = serverless + autoscale (modernize), SQS= decouple (no more drops) https://aws.amazon.com/getting-started/hands-on/build-serverless-web-app-lambda-apigateway- s3-dynamodb-cognito/module-4/
    </details>

14. A company receives 10 TB of instrumentation data each day from several machines located at a single factory. The data consists of JSON files stored on a storage area network (SAN) in an on- premises data center located within the factory. The company wants to send this data to Amazon S3 where it can be accessed by several additional systems that provide critical near-real-lime analytics. A secure transfer is important because the data is considered sensitive. Which solution offers the MOST reliable data transfer?
    - A. AWS DataSync over public internet
    - B. AWS DataSync over AWS Direct Connect
    - C. AWS Database Migration Service (AWS DMS) over public internet
    - D. AWS Database Migration Service (AWS DMS) over AWS Direct Connect

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: B
      Explanation: These are some of the main use cases for AWS DataSync: - Data migration - Move active datasets rapidly over the network into Amazon S3, Amazon EFS, or FSx for Windows File Server. DataSync includes automatic encryption and data integrity validation to help make sure that your data arrives securely, intact, and ready to use. DataSync includes encryption and integrity validation to help make sure your data arrives securely, intact, and ready to use. https://aws.amazon.com/datasync/faqs/
    </details>

15. A company needs to configure a real-time data ingestion architecture for its application. The company needs an API, a process that transforms data as the data is streamed, and a storage solution for the data. Which solution will meet these requirements with the LEAST operational overhead?
    - A. Deploy an Amazon EC2 instance to host an API that sends data to an Amazon Kinesis data stream. Create an Amazon Kinesis Data Firehose delivery stream that uses the Kinesis data stream as a data source. Use AWS Lambda functions to transform the data. Use the Kinesis Data Firehose delivery stream to send the data to Amazon S3.
    - B. Deploy an Amazon EC2 instance to host an API that sends data to AWS Glue. Stop source/destination checking on the EC2 instance. Use AWS Glue to transform the data and to send the data to Amazon S3.
    - C. Configure an Amazon API Gateway API to send data to an Amazon Kinesis data stream. Create an Amazon Kinesis Data Firehose delivery stream that uses the Kinesis data stream as a data source. Use AWS Lambda functions to transform the data. Use the Kinesis Data Firehose delivery stream to send the data to Amazon S3.
    - D. Configure an Amazon API Gateway API to send data to AWS Glue. Use AWS Lambda functions to transform the data. Use AWS Glue to send the data to Amazon S3.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: C
      Explanation: It uses fully managed services for the API, data transformation, and data delivery, which minimizes operational overhead.
    </details>

16. A company needs to keep user transaction data in an Amazon DynamoDB table. The company must retain the data for 7 years. What is the MOST operationally efficient solution that meets these requirements?
    - A. Use DynamoDB point-in-time recovery to back up the table continuously.
    - B. Use AWS Backup to create backup schedules and retention policies for the table.
    - C. Create an on-demand backup of the table by using the DynamoDB console. Store the backup in an Amazon S3 bucket. Set an S3 Lifecycle configuration for the S3 bucket.
    - D. Create an Amazon EventBridge (Amazon CloudWatch Events) rule to invoke an AWS Lambda function.
Configure the Lambda function to back up the table and to store the backup in an Amazon S3 bucket. Set an S3 Lifecycle configuration for the S3 bucket.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: B
      Explanation: We recommend you use AWS Backup to automatically delete the backups that you no longer need by configuring your lifecycle when you created your backup plan. https://docs.aws.amazon.com/aws-backup/latest/devguide/deleting-backups.html
    </details>

17. A company is planning to use an Amazon DynamoDB table for data storage. The company is concerned about cost optimization. The table will not be used on most mornings. In the evenings, the read and write traffic will often be unpredictable. When traffic spikes occur, they will happen very quickly. What should a solutions architect recommend?
    - A. Create a DynamoDB table in on-demand capacity mode.
    - B. Create a DynamoDB table with a global secondary index.
    - C. Create a DynamoDB table with provisioned capacity and auto scaling.
    - D. Create a DynamoDB table in provisioned capacity mode, and configure it as a global table.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: A
      Explanation: On-demand mode is a good option if any of the following are true: - You create new tables with unknown workloads. - You have unpredictable application traffic. - You prefer the ease of paying for only what you use.
    </details>

18. A company recently signed a contract with an AWS Managed Service Provider (MSP) Partner for help with an application migration initiative. A solutions architect needs to share an Amazon Machine Image (AMI) from an existing AWS account with the MSP Partner's AWS account. The AMI is backed by Amazon Elastic Block Store (Amazon EBS) and uses a customer managed customer master key (CMK) to encrypt EBS volume snapshots. What is the MOST secure way for the solutions architect to share the AMI with the MSP Partner's AWS account?
    - A. Make the encrypted AMI and snapshots publicly available. Modify the CMK's key policy to allow the MSP Partner's AWS account to use the key
    - B. Modify the launchPermission property of the AMI. Share the AMI with the MSP Partner's AWS account only. Modify the CMK's key policy to allow the MSP Partner's AWS account to use the key.
    - C. Modify the launchPermission property of the AMI. Share the AMI with the MSP Partner's AWS account only. Modify the CMK's key policy to trust a new CMK that is owned by the MSP Partner for encryption.
    - D. Export the AMI from the source account to an Amazon S3 bucket in the MSP Partner's AWS account. Encrypt the S3 bucket with a CMK that is owned by the MSP Partner. Copy and launch the AMI in the MSP Partner's AWS account.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: B
      Explanation: Share the existing KMS key with the MSP external account because it has already been used to encrypt the AMI snapshot. https://docs.aws.amazon.com/kms/latest/developerguide/key-policy-modifying-external- accounts.html
    </details>

19. A solutions architect is designing the cloud architecture for a new application being deployed on AWS. The process should run in parallel while adding and removing application nodes as needed based on the number of jobs to be processed. The processor application is stateless. The solutions architect must ensure that the application is loosely coupled and the job items are durably stored. Which design should the solutions architect use?
    - A. Create an Amazon SNS topic to send the jobs that need to be processed. Create an Amazon Machine Image (AMI) that consists of the processor application. Create a launch configuration that uses the AMI. Create an Auto Scaling group using the launch configuration. Set the scaling policy for the Auto Scaling group to add and remove nodes based on CPU usage.
    - B. Create an Amazon SQS queue to hold the jobs that need to be processed. Create an Amazon Machine image (AMI) that consists of the processor application. Create a launch configuration that uses the AMI. Create an Auto Scaling group using the launch configuration. Set the scaling policy for the Auto Scaling group to add and remove nodes based on network usage.
    - C. Create an Amazon SQS queue to hold the jobs that needs to be processed. Create an Amazon Machine image (AMI) that consists of the processor application. Create a launch template that uses the AMI. Create an Auto Scaling group using the launch template. Set the scaling policy for the Auto Scaling group to add and remove nodes based on the number of items in the SQS queue.
    - D. Create an Amazon SNS topic to send the jobs that need to be processed. Create an Amazon Machine Image (AMI) that consists of the processor application. Create a launch template that uses the AMI. Create an Auto Scaling group using the launch template. Set the scaling policy for the Auto Scaling group to add and remove nodes based on the number of messages published to the SNS topic

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: C
      Explanation: "Create an Amazon SQS queue to hold the jobs that needs to be processed. Create an Amazon EC2 Auto Scaling group for the compute application. Set the scaling policy for the Auto Scaling group to add and remove nodes based on the number of items in the SQS queue" In this case we need to find a durable and loosely coupled solution for storing jobs. Amazon SQS is ideal for this use case and can be configured to use dynamic scaling based on the number of jobs waiting in the queue.To configure this scaling you can use the backlog per instance metric with the target value being the acceptable backlog per instance to maintain. You can calculate these numbers as follows: Backlog per instance: To calculate your backlog per instance, start with the ApproximateNumberOfMessages queue attribute to determine the length of the SQS queue
    </details>

20. A company hosts its web applications in the AWS Cloud. The company configures Elastic Load
Balancers to use certificate that are imported into AWS Certificate Manager (ACM). The company's security team must be notified 30 days before the expiration of each certificate. What should a solutions architect recommend to meet the requirement?
    - A. Add a rule in ACM to publish a custom message to an Amazon Simple Notification Service (Amazon SNS) topic every day beginning 30 days before any certificate will expire.
    - B. Create an AWS Config rule that checks for certificates that will expire within 30 days. Configure Amazon EventBridge (Amazon CloudWatch Events) to invoke a custom alert by way of Amazon Simple Notification Service (Amazon SNS) when AWS Config reports a noncompliant resource
    - C. Use AWS trusted Advisor to check for certificates that will expire within to days. Create an Amazon CloudWatch alarm that is based on Trusted Advisor metrics for check status changes. Configure the alarm to send a custom alert by way of Amazon Simple rectification Service (Amazon SNS)
    - D. Create an Amazon EventBridge (Amazon CloudWatch Events) rule to detect any certificates that will expire within 30 days. Configure the rule to invoke an AWS Lambda function. Configure the Lambda function to send a custom alert by way of Amazon Simple Notification Service (Amazon SNS).

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: B
      Explanation: https://aws.amazon.com/premiumsupport/knowledge-center/acm-certificate-expiration/
    </details>

21. A company's dynamic website is hosted using on-premises servers in the United States. The company is launching its product in Europe, and it wants to optimize site loading times for new European users. The site's backend must remain in the United States. The product is being launched in a few days, and an immediate solution is needed. What should the solutions architect recommend?
    - A. Launch an Amazon EC2 instance in us-east-1 and migrate the site to it.
    - B. Move the website to Amazon S3. Use cross-Region replication between Regions.
    - C. Use Amazon CloudFront with a custom origin pointing to the on-premises servers.
    - D. Use an Amazon Route 53 geo-proximity routing policy pointing to on-premises servers.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: C
      Explanation: https://aws.amazon.com/pt/blogs/aws/amazon-cloudfront-support-for-custom-origins/ You can now create a CloudFront distribution using a custom origin. Each distribution will can point to an S3 or to a custom origin. This could be another storage service, or it could be something more interesting and more dynamic, such as an EC2 instance or even an Elastic Load Balancer.
    </details>

22. A company wants to reduce the cost of its existing three-tier web architecture. The web, application, and database servers are running on Amazon EC2 instances for the development, test, and production environments. The EC2 instances average 30% CPU utilization during peak hours and 10% CPU utilization during non-peak hours. The production EC2 instances run 24 hours a day. The development and test EC2 instances run for at least 8 hours each day. The company plans to implement automation to stop the development
and test EC2 instances when they are not in use. Which EC2 instance purchasing solution will meet the company's requirements MOST cost- effectively?
    - A. Use Spot Instances for the production EC2 instances. Use Reserved Instances for the development and test EC2 instances.
    - B. Use Reserved Instances for the production EC2 instances. Use On-Demand Instances for the development and test EC2 instances.
    - C. Use Spot blocks for the production EC2 instances. Use Reserved Instances for the development and test EC2 instances.
    - D. Use On-Demand Instances for the production EC2 instances. Use Spot blocks for the development and test EC2 instances.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: B
      Explanation: Spot blocks are not longer available, and you can't use spot instances on Prod machines 24x7.
    </details>

23. A company has a production web application in which users upload documents through a web interlace or a mobile app. According to a new regulatory requirement, new documents cannot be modified or deleted after they are stored. What should a solutions architect do to meet this requirement?
    - A. Store the uploaded documents in an Amazon S3 bucket with S3 Versioning and S3 Object Lock enabled
    - B. Store the uploaded documents in an Amazon S3 bucket. Configure an S3 Lifecycle policy to archive the documents periodically.
    - C. Store the uploaded documents in an Amazon S3 bucket with S3 Versioning enabled. Configure an ACL to restrict all access to read-only.
    - D. Store the uploaded documents on an Amazon Elastic File System (Amazon EFS) volume. Access the data by mounting the volume in read-only mode.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: A
      Explanation: You can use S3 Object Lock to store objects using a write-once-read-many (WORM) model. Object Lock can help prevent objects from being deleted or overwritten for a fixed amount of time or indefinitely. You can use S3 Object Lock to meet regulatory requirements that require WORM storage, or add an extra layer of protection against object changes and deletion. Versioning is required and automatically activated as Object Lock is enabled. https://docs.aws.amazon.com/AmazonS3/latest/userguide/object-lock-overview.html
    </details>

24. A company has several web servers that need to frequently access a common Amazon RDS MySQL Multi-AZ DB instance. The company wants a secure method for the web servers to connect to the database while meeting a security requirement to rotate user credentials frequently. Which solution meets these requirements?
    - A. Store the database user credentials in AWS Secrets Manager. Grant the necessary IAM permissions to allow the web servers to access AWS Secrets Manager.
    - B. Store the database user credentials in AWS Systems Manager OpsCenter.
Grant the necessary IAM permissions to allow the web servers to access OpsCenter.
    - C. Store the database user credentials in a secure Amazon S3 bucket. Grant the necessary IAM permissions to allow the web servers to retrieve credentials and access the database.
    - D. Store the database user credentials in files encrypted with AWS Key Management Service (AWS KMS) on the web server file system. The web server should be able to decrypt the files and access the database.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: A
      Explanation: Secrets Manager enables you to replace hardcoded credentials in your code, including passwords, with an API call to Secrets Manager to retrieve the secret programmatically. This helps ensure the secret can't be compromised by someone examining your code, because the secret no longer exists in the code. Also, you can configure Secrets Manager to automatically rotate the secret for you according to a specified schedule. This enables you to replace long-term secrets with short- term ones, significantly reducing the risk of compromise. https://docs.aws.amazon.com/secretsmanager/latest/userguide/intro.html
    </details>

25. A company hosts an application on AWS Lambda functions mat are invoked by an Amazon API Gateway API. The Lambda functions save customer data to an Amazon Aurora MySQL database. Whenever the company upgrades the database, the Lambda functions fail to establish database connections until the upgrade is complete. The result is that customer data Is not recorded for some of the event. A solutions architect needs to design a solution that stores customer data that is created during database upgrades. Which solution will meet these requirements?
    - A. Provision an Amazon RDS proxy to sit between the Lambda functions and the database. Configure the Lambda functions to connect to the RDS proxy.
    - B. Increase the run time of me Lambda functions to the maximum. Create a retry mechanism in the code that stores the customer data in the database.
    - C. Persist the customer data to Lambda local storage. Configure new Lambda functions to scan the local storage to save the customer data to the database.
    - D. Store the customer data in an Amazon Simple Queue Service (Amazon SOS) FIFO queue. Create a new Lambda function that polls the queue and stores the customer data in the database.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: D
      Explanation: SQS maintains the data if the lambda function fails, RDS Proxy just reuses db connections for performance.
    </details>

26. A survey company has gathered data for several years from areas m\ the United States. The company hosts the data in an Amazon S3 bucket that is 3 TB in size and growing. The company has started to share the data with a European marketing firm that has S3 buckets. The company wants to ensure that its data transfer costs remain as low as possible. Which solution will meet these requirements?
    - A. Configure the Requester Pays feature on the company's S3 bucket
    - B. Configure S3 Cross-Region Replication from the company's S3 bucket to one of the marketing
firm's S3 buckets.
    - C. Configure cross-account access for the marketing firm so that the marketing firm has access to the company's S3 bucket.
    - D. Configure the company's S3 bucket to use S3 Intelligent-Tiering Sync the S3 bucket to one of the marketing firm's S3 buckets

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: A
      Explanation: Typically, you configure buckets to be Requester Pays buckets when you want to share data but not incur charges associated with others accessing the data. For example, you might use Requester Pays buckets when making available large datasets, such as zip code directories, reference data, geospatial information, or web crawling data. https://docs.aws.amazon.com/AmazonS3/latest/userguide/RequesterPaysBuckets.html
    </details>

27. A company uses Amazon S3 to store its confidential audit documents. The S3 bucket uses bucket policies to restrict access to audit team IAM user credentials according to the principle of least privilege. Company managers are worried about accidental deletion of documents in the S3 bucket and want a more secure solution. What should a solutions architect do to secure the audit documents?
    - A. Enable the versioning and MFA Delete features on the S3 bucket.
    - B. Enable multi-factor authentication (MFA) on the IAM user credentials for each audit team IAM user account.
    - C. Add an S3 Lifecycle policy to the audit team's IAM user accounts to deny the s3:DeleteObject action during audit dates.
    - D. Use AWS Key Management Service (AWS KMS) to encrypt the S3 bucket and restrict audit team IAM user accounts from accessing the KMS key.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: A
      Explanation: This will secure the audit documents by providing an additional layer of protection against accidental deletion. With versioning enabled, any deleted or overwritten objects in the S3 bucket will be preserved as previous versions, allowing the company to recover them if needed. With MFA Delete enabled, any delete request made to the S3 bucket will require the use of an MFA code, which provides an additional layer of security.
    </details>

28. A company is using a SQL database to store movie data that is publicly accessible. The database runs on an Amazon RDS Single-AZ DB instance. A script runs queries at random intervals each day to record the number of new movies that have been added to the database. The script must report a final total during business hours. The company's development team notices that the database performance is inadequate for development tasks when the script is running. A solutions architect must recommend a solution to resolve this issue. Which solution will meet this requirement with the LEAST operational overhead?
    - A. Modify the DB instance to be a Multi-AZ deployment
    - B. Create a read replica of the database. Configure the script to query only the read replica.
    - C. Instruct the development team to manually export the entries in the database at the end of each day
    - D. Use Amazon ElastiCache to cache the common queries that the script runs against the database

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: B
      Explanation: Elasti Cache if for reading common results. The script is looking for new movies added. Read replica would be the best choice.
    </details>

29. A company has applications that run on Amazon EC2 instances in a VPC. One of the applications needs to call the Amazon S3 API to store and read objects. According to the company's security regulations, no traffic from the applications is allowed to travel across the internet. Which solution will meet these requirements?
    - A. Configure an S3 interface endpoint.
    - B. Configure an S3 gateway endpoint.
    - C. Create an S3 bucket in a private subnet.
    - D. Create an S3 bucket in the same Region as the EC2 instance.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: B
      Explanation: Gateway endpoints provide reliable connectivity to Amazon S3 and DynamoDB without requiring an internet gateway or a NAT device for your VPC. https://docs.aws.amazon.com/vpc/latest/privatelink/gateway-endpoints.html
    </details>

30. A company runs an on-premises application that is powered by a MySQL database. The company is migrating the application to AWS to Increase the application's elasticity and availability. The current architecture shows heavy read activity on the database during times of normal operation. Every 4 hours the company's development team pulls a full export of the production database to populate a database in the staging environment. During this period, users experience unacceptable application latency. The development team is unable to use the staging environment until the procedure completes. A solutions architect must recommend replacement architecture that alleviates the application
latency issue. The replacement architecture also must give the development team the ability to continue using the staging environment without delay. Which solution meets these requirements?
    - A. Use Amazon Aurora MySQL with Multi-AZ Aurora Replicas for production. Populate the staging database by implementing a backup and restore process that uses the mysqldump utility.
    - B. Use Amazon Aurora MySQL with Multi-AZ Aurora Replicas for production. Use database cloning to create the staging database on-demand
    - C. Use Amazon RDS for MySQL with a Mufti AZ deployment and read replicas for production. Use the standby instance tor the staging database.
    - D. Use Amazon RDS for MySQL with a Multi-AZ deployment and read replicas for production. Populate the staging database by implementing a backup and restore process that uses the mysqldump utility.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: B
      Explanation: To alleviate the application latency issue, the recommended solution is to use Amazon Aurora MySQL with Multi-AZ Aurora Replicas for production, and use database cloning to create the staging database on-demand. This allows the development team to continue using the staging environment without delay, while also providing elasticity and availability for the production application.
    </details>

31. A company is preparing to store confidential data in Amazon S3. For compliance reasons the data must be encrypted at rest Encryption key usage must be logged tor auditing purposes. Keys must be rotated every year. Which solution meets these requirements and the MOST operationally efferent?
    - A. Server-side encryption with customer-provided keys (SSE-C)
    - B. Server-side encryption with Amazon S3 managed keys (SSE-S3)
    - C. Server-side encryption with AWS KMS (SSE-KMS) customer master keys (CMKs) with manual rotation
    - D. Server-side encryption with AWS KMS (SSE-KMS) customer master keys (CMKs) with automate rotation

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: D
      Explanation: When you enable automatic key rotation for a customer managed key, AWS KMS generates new cryptographic material for the KMS key every year. AWS KMS also saves the KMS key's older cryptographic material in perpetuity so it can be used to decrypt data that the KMS key encrypted. Key rotation in AWS KMS is a cryptographic best practice that is designed to be transparent and easy to use. AWS KMS supports optional automatic key rotation only for customer managed CMKs. Enable and disable key rotation. Automatic key rotation is disabled by default on customer managed CMKs. When you enable (or re-enable) key rotation, AWS KMS automatically rotates the CMK 365 days after the enable date and every 365 days thereafter. https://docs.aws.amazon.com/kms/latest/developerguide/rotate-keys.html
    </details>

32. A bicycle sharing company is developing a multi-tier architecture to track the location of its bicycles during peak operating hours. The company wants to use these data points in its existing analytics
platform. A solutions architect must determine the most viable multi-tier option to support this architecture. The data points must be accessible from the REST API. Which action meets these requirements for storing and retrieving location data?
    - A. Use Amazon Athena with Amazon S3
    - B. Use Amazon API Gateway with AWS Lambda
    - C. Use Amazon QuickSight with Amazon Redshift.
    - D. Use Amazon API Gateway with Amazon Kinesis Data Analytics

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: B
      Explanation: Kinesis Data Streams does not persist data. It also only ingests data from Kinesis Data Stream and Firehose, and outputs to Kinesis Data Stream, Firehose and Lambda.
    </details>

33. A company has an automobile sales website that stores its listings in a database on Amazon RDS. When an automobile is sold the listing needs to be removed from the website and the data must be sent to multiple target systems. Which design should a solutions architect recommend?
    - A. Create an AWS Lambda function triggered when the database on Amazon RDS is updated to send the information to an Amazon Simple Queue Service (Amazon SQS> queue for the targets to consume
    - B. Create an AWS Lambda function triggered when the database on Amazon RDS is updated to send the information to an Amazon Simple Queue Service (Amazon SQS) FIFO queue for the targets to consume
    - C. Subscribe to an RDS event notification and send an Amazon Simple Queue Service (Amazon SQS) queue fanned out to multiple Amazon Simple Notification Service (Amazon SNS) topics Use AWS Lambda functions to update the targets
    - D. Subscribe to an RDS event notification and send an Amazon Simple Notification Service (Amazon SNS) topic fanned out to multiple Amazon Simple Queue Service (Amazon SQS) queues Use AWS Lambda functions to update the targets

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: D
      Explanation: Amazon RDS uses the SNS to provide notification when an Amazon event occurs. https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/USER_Events.html
    </details>

34. A company needs to store data in Amazon S3 and must prevent the data from being changed. The company wants new objects that are uploaded to Amazon S3 to remain unchangeable for a nonspecific amount of time until the company decides to modify the objects. Only specific users in the company's AWS account can have the ability 10 delete the objects. What should a solutions architect do to meet these requirements?
    - A. Create an S3 Glacier vault. Apply a write-once, read-many (WORM) vault lock policy to the objects.
    - B. Create an S3 bucket with S3 Object Lock enabled. Enable versioning. Set a retention period of 100 years. Use governance mode as the S3 bucket’s default retention mode for new objects.
    - C. Create an S3 bucket.
Use AWS CloudTrail to track any S3 API events that modify the objects. Upon notification, restore the modified objects from any backup versions that the company has.
    - D. Create an S3 bucket with S3 Object Lock enabled. Enable versioning. Add a legal hold to the objects. Add the s3:PutObjectLegalHold permission to the IAM policies of users who need to delete the objects.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: D
      Explanation: "The Object Lock legal hold operation enables you to place a legal hold on an object version. Like setting a retention period, a legal hold prevents an object version from being overwritten or deleted. However, a legal hold doesn't have an associated retention period and remains in effect until removed." https://docs.aws.amazon.com/AmazonS3/latest/userguide/batch-ops-legal-hold.html
    </details>

35. A company recently migrated a message processing system to AWS. The system receives messages into an ActiveMQ queue running on an Amazon EC2 instance. Messages are processed by a consumer application running on Amazon EC2. The consumer application processes the messages and writes results to a MySQL database running on Amazon EC2. The company wants this application to be highly available with low operational complexity. Which architecture offers the HIGHEST availability?
    - A. Add a second ActiveMQ server to another Availably Zone.
Add an additional consumer EC2 instance in another Availability Zone. Replicate the MySQL database to another Availability Zone.
    - B. Use Amazon MO with active/standby brokers configured across two Availability Zones. Add an additional consumer EC2 instance in another Availability Zone. Replicate the MySQL database to another Availability Zone.
    - C. Use Amazon MO with active/standby blotters configured across two Availability Zones. Add an additional consumer EC2 instance in another Availability Zone. Use Amazon ROS tor MySQL with Multi-AZ enabled.
    - D. Use Amazon MQ with active/standby brokers configured across two Availability Zones. Add an Auto Scaling group for the consumer EC2 instances across two Availability Zones. Use Amazon RDS for MySQL with Multi-AZ enabled.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: D
      Explanation: Amazon MQ with active/standby brokers configured across two Availability Zones ensures that the message queue is available even if one Availability Zone experiences an outage. An Auto Scaling group for the consumer EC2 instances across two Availability Zones ensures that the consumer application is able to continue processing messages even if one Availability Zone experiences an outage. Amazon RDS for MySQL with Multi-AZ enabled ensures that the database is available even if one Availability Zone experiences an outage.
    </details>

36. A company hosts a containerized web application on a fleet of on-premises servers that process incoming requests. The number of requests is growing quickly. The on-premises servers cannot handle the increased number of requests. The company wants to move the application to AWS with minimum code changes and minimum development effort. Which solution will meet these requirements with the LEAST operational overhead?
    - A. Use AWS Fargate on Amazon Elastic Container Service (Amazon ECS) to run the containerized web application with Service Auto Scaling. Use an Application Load Balancer to distribute the incoming requests.
    - B. Use two Amazon EC2 instances to host the containerized web application. Use an Application Load Balancer to distribute the incoming requests.
    - C. Use AWS Lambda with a new code that uses one of the supported languages. Create multiple Lambda functions to support the load. Use Amazon API Gateway as an entry point to the Lambda functions.
    - D. Use a high performance computing (HPC) solution such as AWS ParallelClusterto establish an HPC cluster that can process the incoming requests at the appropriate scale.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: A
      Explanation: Less operational overhead means A: Fargate (no EC2), move the containers on ECS, autoscaling for growth and ALB to balance consumption.
    </details>

37. A company uses 50 TB of data for reporting. The company wants to move this data from on premises to AWS A custom application in the company's data center runs a weekly data transformation job. The company plans to pause the application until the data transfer is complete and needs to begin the transfer process as soon as possible. The data center does not have any available network bandwidth for additional workloads. A solutions architect must transfer the data and must configure the transformation job to continue
to run in the AWS Cloud. Which solution will meet these requirements with the LEAST operational overhead?
    - A. Use AWS DataSync to move the data. Create a custom transformation job by using AWS Glue.
    - B. Order an AWS Snowcone device to move the data. Deploy the transformation application to the device.
    - C. Order an AWS Snowball Edge Storage Optimized device. Copy the data to the device. Create a custom transformation job by using AWS Glue.
    - D. Order an AWS
    - D. Snowball Edge Storage Optimized device that includes Amazon EC2 compute. Copy the data to the device. Create a new EC2 instance on AWS to run the transformation application.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: C
      Explanation: SnowBall can store 80TB (ok), takes around 1 week to move the device (faster than A), and AWS Glue allows to do ETL jobs.
    </details>

38. A company has created an image analysis application in which users can upload photos and add photo frames to their images. The users upload images and metadata to indicate which photo frames they want to add to their images. The application uses a single Amazon EC2 instance and Amazon DynamoDB to store the metadata. The application is becoming more popular, and the number of users is increasing. The company expects the number of concurrent users to vary significantly depending on the time of day and day of week. The company must ensure that the application can scale to meet the needs of the growing user base. Which solution meats these requirements?
    - A. Use AWS Lambda to process the photos. Store the photos and metadata in DynamoDB. - B. Use Amazon Kinesis Data Firehose to process the photos and to store the photos and metadata.
    - C. Use AWS Lambda to process the photos. Store the photos in Amazon S3. Retain DynamoDB to store the metadata.
    - D. Increase the number of EC2 instances to three. Use Provisioned IOPS SSD (io2) Amazon Elastic Block Store (Amazon EBS) volumes to store the photos and metadata.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: C
      Explanation: Storing image in DB won’t be very scalable compared to S3 metadata does not take up much space and is more efficiently stored in DB.
    </details>

39. A medical records company is hosting an application on Amazon EC2 instances. The application processes customer data files that are stored on Amazon S3. The EC2 instances are hosted in public subnets. The EC2 instances access Amazon S3 over the internet, but they do not require any other network access. A new requirement mandates that the network traffic for file transfers take a private route and not
be sent over the internet. Which change to the network architecture should a solutions architect recommend to meet this requirement?
    - A. Create a NAT gateway. Configure the route table for the public subnets to send traffic to Amazon S3 through the NAT gateway.
    - B. Configure the security group for the EC2 instances to restrict outbound traffic so that only traffic to the S3 prefix list is permitted.
    - C. Move the EC2 instances to private subnets. Create a VPC endpoint for Amazon S3, and link the endpoint to the route table for the private subnets
    - D. Remove the internet gateway from the VPC. Set up an AWS Direct Connect connection, and route traffic to Amazon S3 over the Direct Connect connection.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: C
      Explanation: VPC endpoint is the best choice to route S3 traffic without traversing internet.
    </details>

40. A company stores its application logs in an Amazon CloudWatch Logs log group. A new policy requires the company to store all application logs in Amazon OpenSearch Service (Amazon Elasticsearch Service) in near-real time. Which solution will meet this requirement with the LEAST operational overhead?
    - A. Configure a CloudWatch Logs subscription to stream the logs to Amazon OpenSearch Service (Amazon Elasticsearch Service).
    - B. Create an AWS Lambda function. Use the log group to invoke the function to write the logs to Amazon OpenSearch Service (Amazon Elasticsearch Service).
    - C. Create an Amazon Kinesis Data Firehose delivery stream. Configure the log group as the delivery stream's source. Configure Amazon OpenSearch Service (Amazon Elasticsearch Service) as the delivery stream's destination.
    - D. Install and configure Amazon Kinesis Agent on each application server to deliver the logs to Amazon Kinesis Data Streams. Configure Kinesis Data Streams to deliver the logs to Amazon OpenSearch Service (Amazon Elasticsearch Service)

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: A
      Explanation: CloudWatch has a native feature to stream logs to OpenSearch, when you enable this setting it creates a Lambda Function automatically with pre-populated code which streams the logs to OpenSearch Cluster. https://docs.aws.amazon.com/AmazonCloudWatch/latest/logs/CWL_OpenSearch_Stream.html
    </details>

41. A company is building a web-based application running on Amazon EC2 instances in multiple Availability Zones. The web application will provide access to a repository of text documents totaling about 900 TB in size. The company anticipates that the web application will experience periods of high demand. A solutions architect must ensure that the storage component for the text documents can scale to meet the demand of the application at all times. The company is concerned about the overall cost of the solution. Which storage solution meets these requirements MOST cost-effectively?
    - A. Amazon Elastic Block Store (Amazon EBS)
    - B. Amazon Elastic File System (Amazon EFS)
    - C. Amazon Elasticsearch Service (Amazon ES)
    - D. Amazon S3

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: D
      Explanation: Amazon S3 is an object storage service that can store and retrieve large amounts of data at any time, from anywhere on the web. It is designed for high durability, scalability, and cost-effectiveness, making it a suitable choice for storing a large repository of text documents. With S3, you can store and retrieve any amount of data, at any time, from anywhere on the web, and you can scale your storage up or down as needed, which will help to meet the demand of the web application. Additionally, S3 allows you to choose between different storage classes, such as standard, infrequent access, and archive, which will enable you to optimize costs based on your specific use case.
    </details>

42. A global company is using Amazon API Gateway to design REST APIs for its loyalty club users in the us-east-1 Region and the ap-southeast-2 Region. A solutions architect must design a solution to protect these API Gateway managed REST APIs across multiple accounts from SQL injection and cross-site scripting attacks.
Which solution will meet these requirements with the LEAST amount of administrative effort?
    - A. Set up AWS WAF in both Regions. Associate Regional web ACLs with an API stage.
    - B. Set up AWS Firewall Manager in both Regions. Centrally configure AWS WAF rules.
    - C. Set up AWS Shield in bath Regions. Associate Regional web ACLs with an API stage.
    - D. Set up AWS Shield in one of the Regions. Associate Regional web ACLs with an API stage.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: B
      Explanation: Using AWS WAF has several benefits. Additional protection against web attacks using criteria that you specify. You can define criteria using characteristics of web requests such as the following: - Presence of SQL code that is likely to be malicious (known as SQL injection). - Presence of a script that is likely to be malicious (known as cross-site scripting). AWS Firewall Manager simplifies your administration and maintenance tasks across multiple accounts and resources for a variety of protections. https://docs.aws.amazon.com/waf/latest/developerguide/what-is-aws-waf.html
    </details>

43. A company has implemented a self-managed DNS solution on three Amazon EC2 instances behind a Network Load Balancer (NLB) in the us-west-2 Region. Most of the company's users are located in the United States and Europe. The company wants to improve the performance and availability of the solution. The company launches and configures three EC2 instances in the eu-west-1 Region and adds the EC2 instances as targets for a new NLB. Which solution can the company use to route traffic to all the EC2 instances?
    - A. Create an Amazon Route 53 geolocation routing policy to route requests to one of the two NLBs. Create an Amazon CloudFront distribution. Use the Route 53 record as the distribution's origin.
    - B. Create a standard accelerator in AWS Global Accelerator. Create endpoint groups in us-west-2 and eu-west-1. Add the two NLBs as endpoints for the endpoint groups.
    - C. Attach Elastic IP addresses to the six EC2 instances. Create an Amazon Route 53 geolocation routing policy to route requests to one of the six EC2 instances. Create an Amazon CloudFront distribution. Use the Route 53 record as the distribution's origin.
    - D. Replace the two NLBs with two Application Load Balancers (ALBs). Create an Amazon Route 53 latency routing policy to route requests to one of the two ALBs. Create an Amazon CloudFront distribution. Use the Route 53 record as the distribution's origin.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: B
      Explanation: WS Global Accelerator is a networking service that helps you improve the availability and performance of the applications that you offer to your global users. AWS Global Accelerator is easy to set up, configure, and manage. It provides static IP addresses that provide a fixed entry point to your applications and eliminate the complexity of managing specific IP addresses for different AWS Regions and Availability Zones. AWS Global Accelerator always routes user traffic to the optimal
      endpoint based on performance, reacting instantly to changes in application health, your user’s location, and policies that you configure. https://aws.amazon.com/global-accelerator/faqs/
    </details>

44. A company is running an online transaction processing (OLTP) workload on AWS. This workload uses an unencrypted Amazon RDS DB instance in a Multi-AZ deployment. Daily database snapshots are taken from this instance. What should a solutions architect do to ensure the database and snapshots are always encrypted moving forward?
    - A. Encrypt a copy of the latest DB snapshot. Replace existing DB instance by restoring the encrypted snapshot
    - B. Create a new encrypted Amazon Elastic Block Store (Amazon EBS) volume and copy the snapshots to it. Enable encryption on the DB instance.
    - C. Copy the snapshots and enable encryption using AWS Key Management Service (AWS KMS). Restore encrypted snapshot to an existing DB instance.
    - D. Copy the snapshots to an Amazon S3 bucket that is encrypted using server-side encryption with AWS Key Management Service (AWS KMS) managed keys (SSE-KMS)

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: A
      Explanation: You can enable encryption for an Amazon RDS DB instance when you create it, but not after it's created. However, you can add encryption to an unencrypted DB instance by creating a snapshot of your DB instance, and then creating an encrypted copy of that snapshot. You can then restore a DB instance from the encrypted snapshot to get an encrypted copy of your original DB instance. https://docs.aws.amazon.com/prescriptive-guidance/latest/patterns/encrypt-an-existing-amazon- rds-for-postgresql-db-instance.html
    </details>

45. A company wants to build a scalable key management Infrastructure to support developers who need to encrypt data in their applications. What should a solutions architect do to reduce the operational burden?
    - A. Use multifactor authentication (MFA) to protect the encryption keys.
    - B. Use AWS Key Management Service (AWS KMS) to protect the encryption keys
    - C. Use AWS Certificate Manager (ACM) to create, store, and assign the encryption keys
    - D. Use an IAM policy to limit the scope of users who have access permissions to protect the encryption keys

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: B
      Explanation: If you are responsible for securing your data across AWS services, you should use it to centrally manage the encryption keys that control access to your data. If you are a developer who needs to encrypt data in your applications, you should use the AWS Encryption SDK with AWS KMS to easily generate, use and protect symmetric encryption keys in your code.
    </details>

46. A company has a dynamic web application hosted on two Amazon EC2 instances. The company has its own SSL certificate, which is on each instance to perform SSL termination.
There has been an increase in traffic recently, and the operations team determined that SSL encryption and decryption is causing the compute capacity of the web servers to reach their maximum limit. What should a solutions architect do to increase the application's performance?
    - A. Create a new SSL certificate using AWS Certificate Manager (ACM) install the ACM certificate on each instance.
    - B. Create an Amazon S3 bucket Migrate the SSL certificate to the S3 bucket. Configure the EC2 instances to reference the bucket for SSL termination.
    - C. Create another EC2 instance as a proxy server Migrate the SSL certificate to the new instance and configure it to direct connections to the existing EC2 instances
    - D. Import the SSL certificate into AWS Certificate Manager (ACM). Create an Application Load Balancer with an HTTPS listener that uses the SSL certificate from ACM.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: D
      Explanation: https://aws.amazon.com/certificate-manager/: "With AWS Certificate Manager, you can quickly request a certificate, deploy it on ACM-integrated AWS resources, such as Elastic Load Balancers, Amazon CloudFront distributions, and APIs on API Gateway, and let AWS Certificate Manager handle certificate renewals. It also enables you to create private certificates for your internal resources and manage the certificate lifecycle centrally."
    </details>

47. A company has a highly dynamic batch processing job that uses many Amazon EC2 instances to complete it. The job is stateless in nature, can be started and stopped at any given time with no negative impact, and typically takes upwards of 60 minutes total to complete. The company has asked a solutions architect to design a scalable and cost-effective solution that meets the requirements of the job. What should the solutions architect recommend?
    - A. Implement EC2 Spot Instances
    - B. Purchase EC2 Reserved Instances
    - C. Implement EC2 On-Demand Instances
    - D. Implement the processing on AWS Lambda

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: A
      Explanation: EC2 Spot Instances allow users to bid on spare Amazon EC2 computing capacity and can be a cost-effective solution for stateless, interruptible workloads that can be started and stopped at any time. Since the batch processing job is stateless, can be started and stopped at any time, and typically takes upwards of 60 minutes to complete, EC2 Spot Instances would be a good fit for this workload.
    </details>

48. A company runs its ecommerce application on AWS. Every new order is published as a message in a RabbitMQ queue that runs on an Amazon EC2 instance in a single Availability Zone. These messages are processed by a different application that runs on a separate EC2 instance. This application stores the details in a PostgreSQL database on another EC2 instance. All the EC2 instances are in the same Availability Zone. The company needs to redesign its architecture to provide the highest availability with the least operational overhead. What should a solutions architect do to meet these requirements?
    - A. Migrate the queue to a redundant pair (active/standby) of RabbitMQ instances on Amazon MQ.
Create a Multi-AZ Auto Scaling group (or EC2 instances that host the application. Create another Multi-AZ Auto Scaling group for EC2 instances that host the PostgreSQL database.
    - B. Migrate the queue to a redundant pair (active/standby) of RabbitMQ instances on Amazon MQ. Create a Multi-AZ Auto Scaling group for EC2 instances that host the application. Migrate the database to run on a Multi-AZ deployment of Amazon RDS for PostgreSQL.
    - C. Create a Multi-AZ Auto Scaling group for EC2 instances that host the RabbitMQ queue. Create another Multi-AZ Auto Scaling group for EC2 instances that host the application. Migrate the database to run on a Multi-AZ deployment of Amazon RDS fqjPostgreSQL.
    - D. Create a Multi-AZ Auto Scaling group for EC2 instances that host the RabbitMQ queue. Create another Multi-AZ Auto Scaling group for EC2 instances that host the application. Create a third Multi-AZ Auto Scaling group for EC2 instances that host the PostgreSQL database.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: B
      Explanation: Migrating to Amazon MQ reduces the overhead on the queue management. C and D are dismissed. Deciding between A and B means deciding to go for an AutoScaling group for EC2 or an RDS for Postgress (both multi- AZ). The RDS option has less operational impact, as provide as a service the tools and software required. Consider for instance, the effort to add an additional node like a read replica, to the DB. https://docs.aws.amazon.com/amazon-mq/latest/developer-guide/active-standby-broker- deployment.html https://aws.amazon.com/rds/postgresql/
    </details>

49. A reporting team receives files each day in an Amazon S3 bucket. The reporting team manually reviews and copies the files from this initial S3 bucket to an analysis S3 bucket each day at the same time to use with Amazon QuickSight. Additional teams are starting to send more files in larger sizes to the initial S3 bucket. The reporting team wants to move the files automatically analysis S3 bucket as the files enter the initial S3 bucket. The reporting team also wants to use AWS Lambda functions to run pattern- matching code on the copied data. In addition, the reporting team wants to send the data files to a pipeline in Amazon SageMaker Pipelines. What should a solutions architect do to meet these requirements with the LEAST operational overhead?
    - A. Create a Lambda function to copy the files to the analysis S3 bucket. Create an S3 event notification for the analysis S3 bucket. Configure Lambda and SageMaker Pipelines as destinations of the event notification. Configure s30bjectCreated:Put as the event type.
    - B. Create a Lambda function to copy the files to the analysis S3 bucket. Configure the analysis S3 bucket to send event notifications to Amazon EventBridge (Amazon CloudWatch Events). Configure an ObjectCreated rule in EventBridge (CloudWatch Events). Configure Lambda and SageMaker Pipelines as targets for the rule.
    - C. Configure S3 replication between the S3 buckets. Create an S3 event notification for the analysis S3 bucket. Configure Lambda and SageMaker Pipelines as destinations of the event notification. Configure s30bjectCreated:Put as the event type.
    - D. Configure S3 replication between the S3 buckets. Configure the analysis S3 bucket to send event notifications to Amazon EventBridge (Amazon CloudWatch Events).
Configure an ObjectCreated rule in EventBridge (CloudWatch Events). Configure Lambda and SageMaker Pipelines as targets for the rule.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: D
      Explanation: The files are getting large, less operational overhead - so will choose S3 replication. Event bridge is far more advanced than S3 event notification and they support multiple targets. S3 Event notification may not support Sagemaker. Also filtering and pattern matching available in Event bridge.
    </details>

50. A company runs a web-based portal that provides users with global breaking news, local alerts, and weather updates. The portal delivers each user a personalized view by using mixture of static and dynamic content. Content is served over HTTPS through an API server running on an Amazon EC2 instance behind an Application Load Balancer (ALB). The company wants the portal to provide this content to its users across the world as quickly as possible. How should a solutions architect design the application to ensure the LEAST amount of latency for all users?
    - A. Deploy the application stack in a single AWS Region. Use Amazon CloudFront to serve all static and dynamic content by specifying the ALB as an origin.
    - B. Deploy the application stack in two AWS Regions.
Use an Amazon Route 53 latency routing policy to serve all content from the ALB in the closest Region.
    - C. Deploy the application stack in a single AWS Region. Use Amazon CloudFront to serve the static content. Serve the dynamic content directly from the ALB. - D. Deploy the application stack in two AWS Regions. Use an Amazon Route 53 geolocation routing policy to serve all content from the ALB in the closest Region.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: A
      Explanation: Amazon CloudFront is a web service that speeds up distribution of your static and dynamic web content. https://aws.amazon.com/blogs/networking-and-content-delivery/deliver-your-apps-dynamic- content-using-amazon-cloudfront-getting-started-template/
    </details>

51. A gaming company is designing a highly available architecture. The application runs on a modified Linux kernel and supports only UDP-based traffic. The company needs the front-end tier to provide the best possible user experience. That tier must have low latency, route traffic to the nearest edge location, and provide static IP addresses for entry into the application endpoints. What should a solutions architect do to meet these requirements?
    - A. Configure Amazon Route 53 to forward requests to an Application Load Balancer. Use AWS Lambda for the application in AWS Application Auto Scaling.
    - B. Configure Amazon CloudFront to forward requests to a Network Load Balancer. Use AWS Lambda for the application in an AWS Application Auto Scaling group.
    - C. Configure AWS Global Accelerator to forward requests to a Network Load Balancer. Use Amazon EC2 instances for the application in an EC2 Auto Scaling group.
    - D. Configure Amazon API Gateway to forward requests to an Application Load Balancer. Use Amazon EC2 instances for the application in an EC2 Auto Scaling group.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: C
      Explanation: AWS Global Accelerator and Amazon CloudFront are separate services that use the AWS global network and its edge locations around the world. CloudFront improves performance for both cacheable content (such as images and videos) and dynamic content (such as API acceleration and dynamic site delivery). Global Accelerator improves performance for a wide range of applications over TCP or UDP by proxying packets at the edge to applications running in one or more AWS Regions. Global Accelerator is a good fit for non-HTTP use cases, such as gaming (UDP), IoT (MQTT), or Voice over IP, as well as for HTTP use cases that specifically require static IP addresses or deterministic, fast regional failover. Both services integrate with AWS Shield for DDoS protection.
    </details>

52. A company wants to migrate its existing on-premises monolithic application to AWS. The company wants to keep as much of the front-end code and the backend code as possible. However, the company wants to break the application into smaller applications. A different team will manage each application. The company needs a highly scalable solution that minimizes operational overhead. Which solution will meet these requirements?
    - A. Host the application on AWS Lambda Integrate the application with Amazon API Gateway.
    - B. Host the application with AWS Amplify. Connect the application to an Amazon API Gateway API that is integrated with AWS Lambda.
    - C. Host the application on Amazon EC2 instances. Set up an Application Load Balancer with EC2 instances in an Auto Scaling group as targets.
    - D. Host the application on Amazon Elastic Container Service (Amazon ECS) Set up an Application Load Balancer with Amazon ECS as the target.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: D
      Explanation: https://aws.amazon.com/blogs/compute/microservice-delivery-with-amazon-ecs-and-application- load-balancers/
    </details>

53. A company recently started using Amazon Aurora as the data store for its global ecommerce application. When large reports are run developers report that the ecommerce application is performing poorly After reviewing metrics in Amazon CloudWatch, a solutions architect finds that the ReadlOPS and CPUUtilization metrics are spiking when monthly reports run. What is the MOST cost-effective solution?
    - A. Migrate the monthly reporting to Amazon Redshift.
    - B. Migrate the monthly reporting to an Aurora Replica
    - C. Migrate the Aurora database to a larger instance class
    - D. Increase the Provisioned IOPS on the Aurora instance

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: B
      Explanation: https://docs.aws.amazon.com/AmazonRDS/latest/AuroraUserGuide/Aurora.Replication.html #Aurora.Replication.Replicas Aurora Replicas have two main purposes. You can issue queries to them to scale the read operations for your application. You typically do so by connecting to the reader endpoint of the cluster. That way, Aurora can spread the load for read-only connections across as many Aurora Replicas as you have in the cluster. Aurora Replicas also help to increase availability. If the writer instance in a cluster becomes unavailable, Aurora automatically promotes one of the reader instances to take its place as the new writer. https://docs.aws.amazon.com/AmazonRDS/latest/AuroraUserGuide/Aurora.Overview.html
    </details>

54. A company hosts a website analytics application on a single Amazon EC2 On-Demand Instance. The analytics software is written in PHP and uses a MySQL database. The analytics software, the web server that provides PHP, and the database server are all hosted on the EC2 instance. The application is showing signs of performance degradation during busy times and is presenting 5xx errors. The company needs to make the application scale seamlessly. Which solution will meet these requirements MOST cost-effectively?
    - A. Migrate the database to an Amazon RDS for MySQL DB instance. Create an AMI of the web application. Use the AMI to launch a second EC2 On-Demand Instance. Use an Application Load Balancer to distribute the load to each EC2 instance.
    - B. Migrate the database to an Amazon RDS for MySQL DB instance.
Create an AMI of the web application. Use the AMI to launch a second EC2 On-Demand Instance. Use Amazon Route 53 weighted routing to distribute the load across the two EC2 instances.
    - C. Migrate the database to an Amazon Aurora MySQL DB instance. Create an AWS Lambda function to stop the EC2 instance and change the instance type. Create an Amazon CloudWatch alarm to invoke the Lambda function when CPU utilization surpasses 75%.
    - D. Migrate the database to an Amazon Aurora MySQL DB instance. Create an AMI of the web application. Apply the AMI to a launch template. Create an Auto Scaling group with the launch template. Configure the launch template to use a Spot Fleet. Attach an Application Load Balancer to the Auto Scaling group.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: D
      Explanation: Spot Fleet can leverage both spot+on-demand instances, it should be the most cost-effective.
    </details>

55. A company runs a stateless web application in production on a group of Amazon EC2 On-Demand Instances behind an Application Load Balancer. The application experiences heavy usage during an 8-hour period each business day. Application usage is moderate and steady overnight Application usage is low during weekends. The company wants to minimize its EC2 costs without affecting the availability of the application. Which solution will meet these requirements?
    - A. Use Spot Instances for the entire workload.
    - B. Use Reserved instances for the baseline level of usage. Use Spot Instances for any additional capacity that the application needs.
    - C. Use On-Demand Instances for the baseline level of usage. Use Spot Instances for any additional capacity that the application needs.
    - D. Use Dedicated Instances for the baseline level of usage. Use On-Demand Instances for any additional capacity that the application needs.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: B
      Explanation: They are currently using On Demand instances, so option C is out. A uses Spot instances which is not recommended for PROD and D uses Dedicated instances which are expensive. So option B should be the one.
    </details>

56. A company needs to retain application logs files for a critical application for 10 years. The application team regularly accesses logs from the past month for troubleshooting, but logs older than 1 month are rarely accessed. The application generates more than 10 TB of logs per month. Which storage option meets these requirements MOST cost-effectively?
    - A. Store the Iogs in Amazon S3. Use AWS Backup to move logs more than 1 month old to S3 Glacier Deep Archive.
    - B. Store the logs in Amazon S3. Use S3 Lifecycle policies to move logs more than 1 month old to S3 Glacier Deep Archive.
    - C. Store the logs in Amazon CloudWatch Logs.
Use AWS Backup to move logs more then 1 month old to S3 Glacier Deep Archive.
    - D. Store the logs in Amazon CloudWatch Logs. Use Amazon S3 Lifecycle policies to move logs more than 1 month old to S3 Glacier Deep Archive.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: B
      Explanation: You need S3 to be able to archive the logs after one month. Cannot do that with CloudWatch Logs.
    </details>

57. A company has a data ingestion workflow that includes the following components: - An Amazon Simple Notation Service (Amazon SNS) topic that receives notifications about new data deliveries. - An AWS Lambda function that processes and stores the data The ingestion workflow occasionally fails because of network connectivity issues. When tenure occurs the corresponding data is not ingested unless the company manually reruns the job. What should a solutions architect do to ensure that all notifications are eventually processed?
    - A. Configure the Lambda function for deployment across multiple Availability Zones
    - B. Modify me Lambda functions configuration to increase the CPU and memory allocations tor the function
    - C. Configure the SNS topic's retry strategy to increase both the number of retries and the wait time between retries
    - D. Configure an Amazon Simple Queue Service (Amazon SQS) queue as the on failure destination. Modify the Lambda function to process messages in the queue.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: D
      Explanation: To ensure that all notifications are eventually processed, the best solution would be to configure an Amazon Simple Queue Service (SQS) queue as the on-failure destination for the SNS topic. This will allow the notifications to be retried until they are successfully processed. The Lambda function can then be modified to process messages in the queue, ensuring that all notifications are eventually processed. Option D, "Configure an Amazon Simple Queue Service (Amazon SQS) queue as the on-failure destination. Modify the Lambda function to process messages in the queue," is the correct answer.
    </details>

58. A company has a service that produces event data. The company wants to use AWS to process the event data as it is received. The data is written in a specific order that must be maintained throughout processing. The company wants to implement a solution that minimizes operational overhead. How should a solutions architect accomplish this?
    - A. Create an Amazon Simple Queue Service (Amazon SQS) FIFO queue to hold messages. Set up an AWS Lambda function to process messages from the queue.
    - B. Create an Amazon Simple Notification Service (Amazon SNS) topic to deliver notifications containing payloads to process. Configure an AWS Lambda function as a subscriber.
    - C. Create an Amazon Simple Queue Service (Amazon SQS) standard queue to hold messages. Set up an AWS Lambda function to process messages from the queue independently.
    - D. Create an Amazon Simple Notification Service (Amazon SNS) topic to deliver notifications containing payloads to process. Configure an Amazon Simple Queue Service (Amazon SQS) queue as a subscriber.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: A
      Explanation: https://docs.aws.amazon.com/AWSSimpleQueueService/latest/SQSDeveloperGuide/FIFO- queues.html FIFO (First-In-First-Out) queues are designed to enhance messaging between applications when the order of operations and events is critical, or where duplicates can't be tolerated. Examples of situations where you might use FIFO queues include the following: To make sure that user-entered commands are run in the right order. To display the correct product price by sending price modifications in the right order. To prevent a student from enrolling in a course before registering for an account.
    </details>

59. A company is migrating an application from on-premises servers to Amazon EC2 instances. As part of the migration design requirements, a solutions architect must implement infrastructure metric alarms. The company does not need to take action if CPU utilization increases to more than 50% for a short burst of time. However, if the CPU utilization increases to more than 50% and read IOPS on the disk are high at the same time, the company needs to act as soon as possible. The solutions architect also must reduce false alarms. What should the solutions architect do to meet these requirements?
    - A. Create Amazon CloudWatch composite alarms where possible.
    - B. Create Amazon CloudWatch dashboards to visualize the metrics and react to issues quickly.
    - C. Create Amazon CloudWatch Synthetics canaries to monitor the application and raise an alarm.
    - D. Create single Amazon CloudWatch metric alarms with multiple metric thresholds where possible.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: A
      Explanation: Composite alarms determine their states by monitoring the states of other alarms. You can **use composite alarms to reduce alarm noise**. For example, you can create a composite alarm where the underlying metric alarms go into ALARM when they meet specific conditions. You then can set up your composite alarm to go into ALARM and send you notifications when the underlying metric alarms go into ALARM by configuring the underlying metric alarms never to take actions. Currently, composite alarms can take the following actions: https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/Create_Composite_Alarm.ht ml
    </details>

60. A company uses a three-tier web application to provide training to new employees. The application is accessed for only 12 hours every day. The company is using an Amazon RDS for MySQL DB instance to store information and wants to minimize costs. What should a solutions architect do to meet these requirements?
    - A. Configure an IAM policy for AWS Systems Manager Session Manager. Create an IAM role for the policy. Update the trust relationship of the role. Set up automatic start and stop for the DB instance.
    - B. Create an Amazon ElastiCache for Redis cache cluster that gives users the ability to access the data from the cache when the DB instance is stopped. Invalidate the cache after the DB instance is started.
    - C. Launch an Amazon EC2 instance. Create an IAM role that grants access to Amazon RDS. Attach the role to the EC2 instance. Configure a cron job to start and stop the EC2 instance on the desired schedule.
    - D. Create AWS Lambda functions to start and stop the DB instance. Create Amazon EventBridge (Amazon CloudWatch Events) scheduled rules to invoke the Lambda functions. Configure the Lambda functions as event targets for the rules

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: D
      Explanation: AWS Lambda and Amazon EventBridge that allows you to schedule a Lambda function to stop and start the idle databases with specific tags to save on compute costs. https://aws.amazon.com/blogs/database/schedule-amazon-rds-stop-and-start-using-aws-lambda/
    </details>

61. A company sells ringtones created from clips of popular songs. The files containing the ringtones are stored in Amazon S3 Standard and are at least 128 KB in size. The company has millions of files, but downloads are infrequent for ringtones older than 90 days. The company needs to save money on storage while keeping the most accessed files readily available for its users. Which action should the company take to meet these requirements MOST cost-effectively?
    - A. Configure S3 Standard-Infrequent Access (S3 Standard-IA) storage for the initial storage tier of the objects.
    - B. Move the files to S3 Intelligent-Tiering and configure it to move objects to a less expensive storage tier after 90 days.
    - C. Configure S3 inventory to manage objects and move them to S3 Standard-Infrequent Access (S3 Standard-1A) after 90 days.
    - D. Implement an S3 Lifecycle policy that moves the objects from S3 Standard to S3 Standard- Infrequent Access (S3 Standard-1A) after 90 days.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: D
      Explanation: The Question talks about downloads are infrequent older than 90 days which means files less than 90 days are accessed frequently. Standard-Infrequent Access (S3 Standard-IA) needs a minimum 30 days if accessed before, it costs more. So to access the files frequently you need a S3 Standard. After 90 days you can move it to Standard-Infrequent Access (S3 Standard-IA) as its going to be less frequently accessed.
    </details>

62. A company needs to save the results from a medical trial to an Amazon S3 repository. The repository must allow a few scientists to add new files and must restrict all other users to read-only access. No users can have the ability to modify or delete any files in the repository. The company must keep every file in the repository for a minimum of 1 year after its creation date. Which solution will meet these requirements?
    - A. Use S3 Object Lock in governance mode with a legal hold of 1 year
    - B. Use S3 Object Lock in compliance mode with a retention period of 365 days.
    - C. Use an IAM role to restrict all users from deleting or changing objects in the S3 bucket Use an S3 bucket policy to only allow the IAM role
    - D. Configure the S3 bucket to invoke an AWS Lambda function every tune an object is added Configure the function to track the hash of the saved object to that modified objects can be marked accordingly

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: B
      Explanation: Compliance mode is more restrictive. https://docs.aws.amazon.com/AmazonS3/latest/userguide/object-lock-overview.html
    </details>

63. A large media company hosts a web application on AWS. The company wants to start caching confidential media files so that users around the world will have reliable access to the files. The content is stored in Amazon S3 buckets. The company must deliver the content quickly, regardless of where the requests originate geographically. Which solution will meet these requirements?
    - A. Use AWS DataSync to connect the S3 buckets to the web application.
    - B. Deploy AWS Global Accelerator to connect the S3 buckets to the web application.
    - C. Deploy Amazon CloudFront to connect the S3 buckets to CloudFront edge servers.
    - D. Use Amazon Simple Queue Service (Amazon SQS) to connect the S3 buckets to the web application.

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: C
      Explanation: CloudFront uses a local cache to provide the response, AWS Global accelerator proxies requests and connects to the application all the time for the response. https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/private-content- restricting-access-to-s3.html#private-content-granting-permissions-to-oai
    </details>

64. A gaming company has a web application that displays scores. The application runs on Amazon EC2 instances behind an Application Load Balancer. The application stores data in an Amazon RDS for MySQL database. Users are starting to experience long delays and interruptions that are caused by database read performance. The company wants to improve the user experience while minimizing changes to the application's architecture. What should a solutions architect do to meet these requirements?
    - A. Use Amazon ElastiCache in front of the database.
    - B. Use RDS Proxy between the application and the database.
    - C. Migrate the application from EC2 instances to AWS Lambda.
    - D. Migrate the database from Amazon RDS for MySQL to Amazon DynamoDB. 

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: A
      Explanation: Amazon ElastiCache is a web service that makes it easy to deploy, operate, and scale an in- memory data store or cache in the cloud. The service improves the performance of web applications by allowing you to retrieve information from fast, managed, in-memory data stores, instead of relying entirely on slower disk-based databases. https://aws.amazon.com/caching/
    </details>

65. A corporation has recruited a new cloud engineer who should not have access to the CompanyConfidential Amazon S3 bucket. The cloud engineer must have read and write permissions on an S3 bucket named AdminTools. Which IAM policy will satisfy these criteria?
    - A. - B. - C. - D. 

    <details markdown=1><summary markdown='span'>Answer</summary>
      Correct answer: A
      Explanation: https://docs.amazonaws.cn/en_us/IAM/latest/UserGuide/reference_policies_examples_s3_rw- bucket.html
    </details>
