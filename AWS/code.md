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
-> AMIs - Pre-configured templates for EC2 instances, having OS, apps to install, volume type and size. Public and Private AMI's exist.