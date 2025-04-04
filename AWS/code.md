AWS provides compute, storage, databases, analytics, networking, developer and management tools, IoT, Security, enterprise applications - on-demand, pay-as-you-go pricing.
Cloud Computing is delivery of computing services over Internet instead of local servers. Scalable and inexpensive services for the above, and virtual servers.
Cloud Service Models - 
1. IaaS : Provides users resource-based service such as VM's for computing infrastructure. eg - Storage, Networking, Servers for computing, Virtualization
2. PaaS : Provides runtime environments to develop, test and manage applications, mainly for software development. eg - OS, Middleware, Runtime
3. SaaS : On-demand software solution such as Data and Apps, i.e., Application data.
Cloud Deployment Models -
1. Public - Service Provider offers resources to general public over the Internet. eg - AWS, GCP, Azure
2. Private - Similar to Public, but through proprietary architecture dedicated to single organization or third-party vendor, based on their needs and goals, such as Virtualization Layer by VMWare. eg - OpenStack, Azure Stack, OpenShift
3. Hybrid - Combine private with one or more public cloud services, with software enabling communication between distinct services. eg - AWS outposts

AWS Global Infrastructure - Layout of AWS Regions and availability zones around the world. Region is geographical Area having two or more availability zones(isolated from failures in AZ's) AZ provide inexpensive, low-latency network connectivity to AZ's in same region. 
AWS also have edge locations for content delivery and caches, further reducing latency. eg - CloudFront
Local Zones give ability to place/extend resources in locations near to end users for low latency.(us-west-2-lax-1)
We can launch EC2 instances by slecting the region(us-west-2), Virtual Private Cloud(VPC), then subnet from the Availability Zones(us-west-2a) or automatically set it. If Instance fails, instance from another AZ will handle request.

Shared Responsibility Model - Between AWS and user/client for security and compilance responsibilities. AWS handles security "OF" the cloud - what helps run the AWS cloud services via host OS such as gloabl infrastructure, and user handles security "IN" the cloud - customer controlled services vs guest OS such as AWS provided security group firewall.

Well Architected Framework - Set of strategic guidelines to provide high performing and resilient systems, being cost efficient. Best practices across SIX principles/pillars : Operational Excellence, Security, Reliability, Performance Efficiency, Cost Optimization, Sustainability.

1. EC2 - Web service that provides secure, resizable compute capacity such as virtual servers/instances. The interface helps obtain and configure capacity with minimal friction to develop, deploy and run applications. Access CPU(Compute), Memory, Storage, Netowrking capacity for the instances.
EC2 provides Instances, AMI, types, EBS Volumes(persistent storage volumes), Instance store volumes(temp data for instances), Security groups(Virtual firewall for source and destination IP ranges)
-> Instance Types - For use cases, grouped into categories such as General Purpose(m8g), Compute Optimized(C8g), Memory Optimized(R8g), Storage Optmized(I8g), Accelerated Computing Instances(GPU's or hardware accelerators such as P5), further divided into instance types. eg - t2.micro
-> CPU Credits - Earn when idle OR below baseline level, and consume when active. One CPU Credit gives performance of full CPU Core for 1 minute. T2 and T3 accrue these credits, saved for 7 days. Burstable performance instances can burst CPU utilization above baseline level BY using these credits.
-> Storage/Volumes - Elastic Block Store(EBS) used by EC2 for data durability. Automatically replicate (EBS Snapshots) within AZ in case of failure to avoid data loss. Appear as network/hard drive that can be mounted and formatted using file system of our choice.
Volume Types(SSD or HDD), scalable, backup, data protection.
-> Keypairs - Used to login to Instances. Public private key, where EC2 gives us private key, and stores public key. Lanch by specifying the keypair name. Region-specific.
-> Elastic IP - Static IPv4 address fetched from pool for dynamic cloud computing, associated with AWS account. This can mask failure of an instance by rapidly remapping address to another instance in account.
-> User Data Scripts - Run as root user for common automated configuration tasks, such as software/file downloads from S3. Ran ONLY once when instance is launched or rebooted, not when stop/start. **AWS CloudFormation** for more complex Automations.
-> Purchasing options - 
On-Demand allows clients to pay for compute capacity per hour with no long term commitments.
Reserved Instances are cheaper, for steady state usage.
Spot Instances to bid unused Amazon EC2 Capacity, with start stop time flexibility.
Dedicated Hosts are physical EC2 servers for specific clients with regulatory license and requirements.
Savings Plan offer reduced rates for consistent usage for 1-3 years.

2. VPC (Virtual private Cloud) service helps launch AWS resources in a logically isolated virtual network. It has advanced security features and Network Access Control Lists to enable inbound and outbound filtering at instance and subnet level. Can create VPN between VPC and corporate datacente  r.  
-> CIDR Blocks (Classless Inter-Domain Routing) is IP Address block which allocates private and public IPV4 addresses. Associated with Network boundary, and can't be changed or overlapped if VPC created, but can be added.
-> Subnets - Divisions of VPC's IP address range under unique availability Zones. EC2 can be launched in selected subnet. When created, specify the CIDR block which is subset of VPC CIDR block. Each subnet has route table for traffic flow between subnets. Public subnet has route table directing to Internet Gateway, and Private subnet doesn't, hence no route to Internet.
-> Route Tables - Set of rules/routes which determine network traffic direction. Each subnet has one at a time.
-> Security Groups - Virtual firewall for instance, can have upto 5 security groups and stateful. Responses for EC2 requests allowed for inflow irrespective of inbound security group rules. Can configure seperate rules for inbound and outbound traffic.
-> Internet Gateway - Horizontally scalable, redundant component that performs bi-directional routing between VPC and Internet. Outbound traffic(NAT) and inbound traffic from Internet. Provides bandwidth and redundancy across all AWS Regions. Associated with VPC upon creation, and can't be detached or attached to another. Security handled using Security groups and Route Tables.
-> NAT Gateway - Managed Service that provides Network Address Translation for instances in private subnet for Internet Access. Automatically handles bandwidth scaling, failover, managing carrier IP Addresses for software updates, patches etc. NO inbound traffic. Supports TCP, UDP, ICMP Protocols and port Address translation.

3. IAM(Identity Access Management) enables to manage access to AWS Services securely. Create AWS Users and Groups, and use permissions, shared access, MFA, granular permissions, temporary access.
Initially, root user for authentication, and for services, check if user is authorized. Eventually Consistent across multiple servers with replication.
-> Policies - Documents that cast as permission containers. JSON Format that define actions, effects, resources, optional conditions. 
Identity based policies are attached to IAM identity - Inline policies created and amanged individually, managed policies are standalone policies attached to multiple identities.
Resource based policies to Resource, specifying the actions that are allowed or denied. Principal element indicates IAM users or roles that are granted the permissions. S3 Buckets, KMS for keys, SNS for topics.
-> User/User Groups - Collection of IAM users, such as Developers.
-> Roles - Secure Access Control for trusted entities to gain temporary security credentials for making AWS API requests - with defined permissions.
Instance Profiles are IAM entities used to GRANT permissions to applications running on EC2 instances for API requests. Basically a container for an IAM role that passes the roles to EC2 instances at launch time.
Assuming Roles allow one AWS Identity to perform actions and access resources in another AWS account, without sharing security credentials. This is using AWS Security Token Service(STS) that passes temporary security credentials. User can switch between these roles usig Management Console.

4. Auto-Scaling - Services that automatically scales resources to meet demands of applications. Check policies, health status and schedules to decide when to add more instances. Using CloudWatch, can optimize cost and performance. Collection of EC2 instances can be called as Auto-Scaling groups, which can have limit on instances.
-> AMIs - Pre-configured templates used as setups for EC2 instances, having OS, apps to install, volume type and size. Public and Private AMI's exist.
-> Launch Templates - Auto Scaling group uses configurations to launch EC2 Instances, including the ID of the AMI, instance type, key pair, security groups, storage configuration.
-> Auto Scaling Groups - Colletion of EC2 Instances treated as logical group for automatic scaling. Instances spread across Availability Zones in region. Each group has min, max and desired number of EC2 Instances.
-> Scaling Policies - How and when to scale. Target tracking scaling policies adjust capacity based on dynamic conditions of metric. Step scaling policies adjust capacity based on set of scaling adjustments of min and max capacity. Simple scaling policies adjust capacity based on single alarm.
-> Elastic Load Balancers - Distributes incoming traffic to EC2 Instances and scales resources to meet traffic demands. Supports routing and LB for HTTP/HTTPS, and TCP traffic. 
Application LB(HTTP/HTTPS), Network LB(TCP), Classic LB(Basic across EC2 instances)

5. S3 - Simple Storage Service is scalable and secure to store data.
-> Buckets/Objects - Bucket is container for data that stores objects(files, folders, object keys and metadata).
-> Lifecycle Configuration - Objects automatically transition to other storage classes or expiration/get cleared at the end of their lifetimes.
Storage Types/Classes - 
1. S3 Standard - General-purpose and frequent access, low latency and high throughput.
2. S3 Intelligent Tiering - Automated to optimize costs by moving objects between access tiers such as frequent and infrequent based on changing access patterns.
3. S3 Glacier - Extremely low-cost storage device for long-term backup and archives. Retrieval modes are expedited(quick access) and Bulk(large and less time-sensitive)
4. S3 Infrequent Access - Lower cost than S3 Standard for data accessed less frequently, but requires rapid access.

6. SES - Simple Email Service is scalable and cheap email sending service for sending notifications, emails, marketing communications. Removes complexity of building in-house email solution, rather easily integrated into existing applications.
-> When account is in Sandbox, emails can be sent to verified ones at max rate of 1 per sec. Move out of sandbox and increase sending limits using SES Sending Limit Increase case to AWS Support.
-> Identity Verification - Ensure user owns address used in From, Source, Sender or Return-path addresses. Verify email address and domain after creating identity. AWS generates DNS Records for Domain and adds to DNS Provider(Route 53, CloudFlare)
-> DKIM Setup - Domain Keys Identified Mail Standard prevents email spoofing on enable. Message transferred such that its verified by mailbox providers via cryptographic authentication. Setup DKIM by adding set of three CNAME records to DNS configuration of sending domain.
-> Feedback Handling - Process to handle bounces, complaints, delivery notifications recieved by email, SNS Topic, CloudWatch.
-> Configuration Sets - Publish email sending events such as ones mentioned above. The set groups similar rules applied to SES mails via its header.
-> Sender Reputation - Measure of sending practices, if it aligns with ISP's expectations and email recipients. Determined by above factors. Helps impact email deliverability rate. 
-> Dedicated IP - Unique IP address that can be used exclusively by a single AWS SES customer for sending emails. 

7. Route53 - DNS service that routes users to Internet Applications. User requests connect to Infra (EC2, S3, ELB) on and outside AWS. Conceals complexities of underlying DNS protocol. Features domain transfer capabilities, DNS failover, health check, customizable TTL.
1. Hosted Zone: Container holding information about how to route traffic on Internet for domain. Has set of DNS Records that control flow of traffic for that domain. A set of DNS record has Name server(NS) record, start of authority(SOA) record. 
a. Private HZ are DNS name spaces that exist within one or more Amazon VPCs. The domain and subdomain in private hosted zone resolvable to private IP addresses on Amzon VPC backends.
b. Public HZ route has its DNS namespace exposed to Internet. Route 53 creates 4 name servers (delegation set), and the corresponding domain's NS records set to it. These zones also include Resources Records Sets, with records like A(address), CNAME(canonical name), MX(mail exchange)
2. Routing Policies: Simple Routing Policy(Single resource)
Weighted Routing Policy(Multiple resources with certain percentage)
Latency Routing Policy(Allows to route based on lowest latency for user based on region)
Failover Routing Policy(Active/Passive based on if primary resource fails to reroute to backup)
Geo location Routing Policy(Based on Geographic location of users)
Geo Proximity Routing Policy(Based on Geographic location of resources, and shift to closer location)
Multi Value Answer Routing Policy(Respond to DNS queries with upto 8 healthy DNS Records)
3. Health Checks - Verify status of resources periodically such as web server or email server, and reroutes if unhealthy after notifying alarms. Integrated with CloudWatch for metrics.

8. Cloudwatch - AWS Resources monitoring. Track metrics, log files, respond to system-wide performance changes.
a. Metrics - Time-ordered set of data points published to cloudwatch. Metric is similar to variable that has to be monitored, and data points is values of those variables with timestamps.
b. Events - Service that provides systematic method to respond to system events. Stop EC2 Instance, monitor AWS Resources, schedule cron jobs, SNS Notification.
c. Logs - Monitor, store and access log files from EC2 Instances, CloudTrail etc. Centralised log from all services into single, highly scalable service. Also integrates with AWS Lambda to respond to critical operational events.

9. CloudFront - CDN service to deliver data to customers globally with low latency, high transfer speeds and developer-friendly environment. Integrates with AWS Shield for DDos mitigation, S3, ELB, EC2, Lambda@Edge to run custom code closer to customers users.
a. Distributions - Globally distributed network system to accelerate distribution of website, API, video content, assets. Specifies where Cloudfront gets files. Web distributions and RTMP Distributions(Media streaming)
b. Policies - Works with IAM to give options to implement fine grained access control over resources in distributions. IAM user can create, delete distribution, create origin access identity, or update settings for a distribution.
c. Invalidations - Remove objects from Cloudfront cache before hitting expiration date. Like other CDNs, store website static file in cache until TTL, but might have to change aspects of the assets, in which case remove objects from these edge locations.

10. RDS - Relational Database Service simplifies setup, operation and scaling of relational databases in the cloud. Provides resizable capacity and admin tasks. Supports database engines such as Aurora, PostgreSQL, MySQL, MariaDB, Oracle and SQL Server. Instances ranging between 5GB to 6GB memory.
1. DB Instance - Isolated database environment that can host a database engine. Can have multiple databases, and DB instances can be managed via AWS Management console, RDS CLI, API Calls.
Each has instance identifier, part of DNS hostname allocated to instance by RDS.
2. Storage Types - 
-> General purpose (SSD) gives consistent baseline of 3 IOPS/GB and burst upto 3000 IOPS. Amazon Elastic Block Store(EBS) gp3 volumes.
-> Provisioned IOPS (SSD) meets needs of I/O intensive workloads that are sensitive to storage performance and consistency. User specifies IOPS rate when volume is created, and AWS will provision it.
-> Magnetic storage is perfect for applications where the lowest storage cost is important, infrequent data access. Poorest perfromance capability and high latency.
3. Backup/Restore - Restore DB instance to specific point in time. Hence new DB instance is created upto that point. The time differenc is restore intiation to time being restored to. We can also have Multi-AZ DB cluster, which is having Instances in different AZ's for recovery during failover.

11. DynamoDB - NoSQL database solution for fast and predictable performances with seamless scalability and no schema. Key-value and document database with single-digit millisecond performance. High durability since automatic replication across three zones in a region.
 -> Tables are collection of items/rows. An item is group of attributes identified by primary key. Key can be simple (partition key) or composite (partition and sort key). Every attribute has name and value of types.
 -> Primary leys/Secondary Indexes -> Hash key/partition key is a simple primary key with scalar value. Helps distribute data across multiple partitions for scalable performance. Composite key has even sort key to store items in sorted order within the partitions.
-> Data Modelling - Determine how to organize, access and understand data stored in database. Primary components include the above. 
Secondary Indexes help query data without disrupting data structure. Global Secondary Index has different partition key and sort key from the main table.
Local Secondary Index has same partition key and different sort key.
-> Streams - Time-ordered sequence of item-level modifications such as Insert, Modify, Remove. Has to be enabled to capture modification information. Helps set up AWS Lambda functions immediately. The stream record is organized into stream view type, where applications can access upto 24 hours of data modification history.
-> Capactiy Settings - Read/Write capacity. Measure of number of strong consistent reads per second, and measure of number of writes per second. Provisioned capacity is specifying the expectation the application requires to handle. On-demand allows DynamoDB to automatically manage capacity to meet needs of workload.
-> Limits - Provisioned has 40000 read capacity units and 40000 write capacity units for on-demand mode per table. Partition key value and sort key value can be 2048 bytes and 1024 bytes respectively.
Backup/Restore - Again, on-demand backups create complete backups for long-term retention and archival. Continuous backups enable to restore data to any point in time in last 35 days, which offers protection from accidental writes or deletes.
Restore data to new DynamoDB table or overwrite data in existing table with metadata and GSI's too.
-> DynamoDB Local - Can download to write and test apps without accessing real AWS Service. Data persists between sessions.

14. ElastiCache - Fully managed in-memory data store from Amazon to speed up dynamic web applications by reducing latency and throughput. Supports two open-source in-memory engines - Redis(database) and Memecached(datasets). Uniform performance and scalability.
-> Serverless caching allows to create a highly available cache in under a minute, without provisioning instances or manage caching capacity. OR choose to design yourself with single or multi-AZ availability.
-> Quotas - Limit on clusters, nodes, groups and subnets in an AWS account. Implemented on Elasticache to prevent overconsumption of resources.

15. ECS - Elastic Container Service is container orchestration service. Supports Docker containers and allow to run and scale containerized applications. API calls can launch and stop Docker enabled apps, query state of application, and access features like EC2 security groups, EBS Volumes, IAM roles.
Elastic Container Registry is a Docker container registry which ensures developers can store, manage and deploy Docker container Images. No need to handle container repositories or scaling underlying architecture. Integrate with AWS IAM for resource-level control of the repository.
Clusters/ECS Container Agents - Cluster is logical grouping of tasks or services. Building block of ECS infrastructure. Serves namespace for tasks and services, since they can't span multiple clusters.
ECS Container Agent registers the EC2 instance with the ECS. Recieves commands from ECS scheduler, telling which Docker containers to run and where to pplace in EC2 instance. Then it also launches the containers.
Tasks are instantiation of task definition within cluster.(Like class objects) Specify Docker Image, CPU needed, launch type.
Services are set of task definitions that run and maintain instances of the definition simultaneously in a ECS Cluster. If a task definiton fails, scheduler launches another instance.
Launch Config/Autoscaling Groups is template that Auto Scaling group uses to launch EC2 instances. It includes AMI, Instance Types, Security Groups. Helps scale up or down.
Fargate is serverless service(no EC2 instance needed) to run containers or host them. AWS takes care of that instead.

16. ECK - Elastic Kubernetes Service simplifies deployment, management and scaling of containerized applications using Kubernetes.
EKS provides infrastructure for Pods and clusters.

17. Lambda - Serverless computing service that runs code based on triggers. No idle charges, great for quick tasks, automation. Upload code, set trigger, AWS executes it.
Triggers can also be HTTP Requests using Amazon API Gateway. Can scale automaically in response to incoming requests.
-> Create/Invoke Functions - Lambda, compute, Create function after Author from scratch. API gateway can trigger when endpoint hits, or periodically using CloudWatch.
-> Layers - Distribution mechanism for artifacts(libraries, runtimes, dependencies) that can be versioned and immutable. It's a ZIP archive. Hence Lambda functions can reference those layers
-> Custom Runtimes - Used when preferred programming language isn't supported. A linus executable file(bootstrap) that handles invocations and communicates with the Lambda service.
-> Versioning - Manage iterations of Lambda function. Alias is a pointer to a specific Lambda function version. Aliases are mutable and addressed using an alias ARN.
-> Event Bridge/Scheduled Execution - Serverless event bus to connect apps together using application data, SaaS apps and AWS Services. Build bridge that helps ingest, filter, transform and deliver events. Trigger lambda for small S3 images, or S3 upload triggers Lambda and SNS topic, or S3 in Region A triggers Lambda in Region B. Event bus and pipes used.
-> Cold start and Limitations - Delay when Lambda invokes function first time, or once code is updated. This is because initial setup of runtine before execution. If not triggered for long, resources might be taken away and would take long again to set up.

18. API Gateway - Create, publish, maintain, monitor, and secure API's at any scale. Apps can access data, business logic from backend services running on EC2, Lambda or web apps. Accepts hundreds of thousands of concurrent API calls. Traffic management, authorization and access control. throttling, API Version management.

19. Lambda Edge - Run functions at AWS Edge locations. Lower latency response times. Can customize cloudfront content by executing code after its response or request.