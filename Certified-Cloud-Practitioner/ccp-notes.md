# Certified Cloud Pracitioner
Resources used:  
1. https://www.udemy.com/course/aws-certified-cloud-practitioner-new/

---

## Cloud Computing Basics
Cloud computing is the on-demand delivery of compute power database storage, applications, and other IT resources.

- Through a cloud services platform with **pay-as-you-go pricing**
- You can **provision exactly the right type and size of computing resources** you need
- You can access as many resources as you need, almost **instantly**
- Simple way to access **servers, storage, databases and a set of application services**

#### Private Cloud:
- Cloud services used by a single organization, not exposed to the public.
- Complete control
- Security for sensitive applications
- Meet specific business needs

#### Public Cloud:
- Cloud resources owned and operated by a third- party cloud service provider delivered over the Internet.
- Six Advantages of Cloud Computing

#### Hybrid Cloud:
- Keep some servers on premises and extend some capabilities to the Cloud
- Control over sensitive assets in your private infrastructure
- Flexibility and cost- effectiveness of the public cloud

#### Five Characteristics of Cloud Computing:
1. On-demand self service:
2. Broad network access:
3. Multi-tenancy and resource pooling:
4. Rapid elasticity and scalability:
5. Measured service

#### Six Advantages of Cloud Computing:
1. Trade capital expense (CAPEX) for operational expense (OPEX) 
    - Pay On-Demand: don’t own hardware
    - ReducedTotal Cost of Ownership (TCO) & Operational Expense (OPEX)
2. Benefit from massive economies of scale
3. Stop guessing capacity
4. Increase speed and agility
5. Stop spending money running and maintaining data centers 
6. Go global in minutes

#### Problems solved by the Cloud:
- Flexibility
- Cost-Effectiveness
- Scalability
- Elasticity
- High Availability and fault tolerance

#### Types of Cloud Computing:
- ![Cloud Computing Types](images/cloud-computing-types.png)

#### 3 Pricing of the Cloud:
- AWS follows pay-as-you-go principle
    - Compute
      - Pay for compute time
    - Storage
      - Pay for data storage in the Cloud
    - Data
      - Pay for data transfer **OUT NOT IN** in Cloud. (*IN IS FREE*)

---

## AWS Infrastructure

#### Consists of:
- Regions
- Availability Zones (AZ)
- Data Centers
- Edge Locations / Point of Presence

#### Choose AWS Regions by:
- **Compliance** with data governance and legal requirements
- **Proximity** to customers
- **Available** services within a Region
- **Pricing**

#### Availability Zones (AZ):
- region has multiple AZs
- each AZ 
  - has one or more discrete data centers
  - separate from each other to isolate disasters
  - high bandwidth, ultra-low latency networking

#### Points of Presence (Edge Locations):
- Content is delivered to end users with lower latency

#### Shared Responsibility Model:
- ![Shared Responsibility Model](images/shared-responsibility.png)

---

## Identity Access Management (IAM)

#### Users & Groups:
- global service
- users are people
- groups only contain people, not other groups

#### Permissions:
- Users or Groups can be assigned **JSON documents called policies**
- In AWS you apply the **least privilege principle**: don’t give more permissions than a user needs

#### Policies:
- ![Policies Inheritance](images/policies-inheritance.png)

#### MFA:
- MFA = password you know + security device you own
- Example: phone app, physical hardware MFA device

#### Access Keys, CLI and SDK:
Access Keys:
- AWS Management Console (protected by password + MFA)
- AWS Command Line Interface (CLI): protected by access keys
- AWS Software Developer Kit (SDK) - for code: protected by access keys
- Access Keys are secret, just like a password. Don’t share them
  - Access Key ID = username
  - Secret Access Key = password

CLI:
- A tool that enables you to interact with AWS services using commands in your command-line shell

SDK:
- Software Development Kit
- Enables you to access and manage AWS services programmatically


#### IAM Roles for Services:


#### Security Tools:
IAM Credentials Report (account-level)
- a report that lists all your account's users and the status of their various credentials

IAM Access Advisor (user-level)
- Access advisor shows the service permissions granted to a user and when those services were last accessed.

#### Best Practices:
- Don’t use the root account except for AWS account setup
- One physical user = One AWS user
- Assign users to groups and assign permissions to groups
- Create a strong password policy
- Use Multi Factor Authentication (MFA)
- Create and use Roles for giving permissions to AWS services
- Use Access Keys for Programmatic Access (CLI / SDK)
- Audit permissions of your account using IAM Credentials Report & IAM Access Advisor
- Never share IAM users & Access Keys

#### Shared Responsibility Model for IAM:
AWS:
- Infrastructure (global network security)
- Configuration and vulnerability analysis
- Compliance validation

YOU:
- Users, Groups, Roles, Policies management and monitoring
- Enable MFA on all accounts
- Rotate all your keys often
- Use IAM tools to apply appropriate permissions
- Analyze access patterns & review permissions

#### IAM - Summary
- **Users:** mapped to a physical user, has a password for AWS Console
- **Groups:** contains users only
- **Policies:** JSON document that outlines permissions for users or groups 
- **Roles:** for EC2 instances or AWS services
- **Security:** MFA + Password Policy
- **AWS CLI:** manage your AWS services using the command-line
- **AWS SDK:** manage your AWS services using a programming language 
- **Access Keys:** access AWS using the CLI or SDK
- **Audit:** IAM Credential Reports & IAM Access Advisor

---

## Elastic Compute Cloud (EC2)
- Infrastructure as a Service
- Mainly consists in the capability of: 
  - Renting virtual machines (EC2)
  - Storing data on virtual drives (EBS)
  - Distributing load across machines (ELB)
  - Scaling the services using an auto-scaling group (ASG)

#### EC2 User Data
- EC2 user data is used to automate boot tasks such as: 
  - Installing updates
  - Installing software
  - Downloading common files from the internet
  - Anything you can think of
- Only run once at the instance first start

#### EC2 Instant Types

**General Purpose:**
- Great for a diversity of workloads such as web servers or code repositories
- Balance between: 
  - Compute
  - Memory
  - Networking
- Example: t2.micro

**Compute Optimized:**
- Great for compute-intensive tasks that require **high performance** processors:
  - Batch processing workloads
  - Media transcoding
  - High performance web servers
  - High performance computing (HPC)
  - Scientific modeling & machine learning
  - Dedicated gaming servers

**Memory Optimized:**
- Fast performance for workloads that process **large data sets** in memory:
  - High performance, relational/non-relational databases
  - Distributed web scale cache stores
  - In-memory databases optimized for BI (business intelligence)
  - Applications performing real-time processing of big unstructured data

**Storage Optimized:**
- Great for storage-intensive tasks that require **high, sequential read and write access to large data sets on local storage**:
  - High frequency online transaction processing (OLTP) systems
  - Relational & NoSQL databases
  - Cache for in-memory databases (for example, Redis)
  - Data warehousing applications
  - Distributed file systems

#### EC2 Security Groups
- Acts as a Firewall for EC2 instances
- Security groups only contain **ALLOW** rules
- Security groups rules can reference by IP or by security group
- Can be attached to multiple instances
- If your application is not accessible (time out), then it’s a security group issue
- If your application gives a “connection refused“ error, then it’s an application error or it’s not launched
- All inbound traffic is blocked by default
- All outbound traffic is authorized by default


#### Port Numbers
- **22 = SSH (Secure Shell)** - log into a Linux instance
- **21 = FTP (File Transfer Protocol)** – upload files into a file share
- **22 = SFTP (Secure File Transfer Protocol)** – upload files using SSH
- **80 = HTTP** – access unsecured websites
- **443 = HTTPS** – access secured websites
- **3389 = RDP (Remote Desktop Protocol)** – log into a Windows instance

#### EC2 Purchasing Options
- **On-Demand Instances** – short workload, predictable pricing, pay by second
- **Reserved (1 & 3 years)**
  - Reserved Instances – long workloads
  - Convertible Reserved Instances – long workloads with flexible instances
- **Savings Plans (1 & 3 years)** –commitment to an amount of usage, long workload 
- **Spot Instances** – short workloads, cheap, can lose instances (less reliable)
- **Dedicated Hosts** – book an entire physical server, control instance placement
- **Dedicated Instances** – no other customers will share your hardware
- **Capacity Reservations** – reserve capacity in a specific AZ for any duration

**EC2 On Demand:**
- Pay for what you use:
  - Linux or Windows - billing per second, after the first minute 
  - All other operating systems - billing per hour
- Has the highest cost but no upfront payment
- No long-term commitment
- Recommended for short-term and un-interrupted workloads, where you can't predict how the application will behave

**EC2 Reserved Instances:**
- Up to 72% discount compared to On-demand
- You reserve a specific instance attributes (Instance Type, Region,Tenancy, OS)
- Reservation Period – 1 year (+discount) or 3 years (+++discount)
- Payment Options – No Upfront (+), Par tial Upfront (++), All Upfront (+++) 
- Reserved Instance’s Scope – Regional or Zonal (reserve capacity in an AZ)

**EC2 Savings Plans:**
- discount based on long-term usage
- Locked to a specific instance family & AWS region

**EC2 Spot Instances:**
- discount of up to 90% compared to On-demand
- Instances that you can “lose” at any point of time if your max price is less than the current spot price
- MOST cost-efficient instances in AWS
- Useful for workloads that are resilient to failure: 
  - Batch jobs
  - Data analysis
  - Image processing
  - Any distributed workloads
  - Workloads with a flexible start and end time
- Not suitable for critical jobs or databases

**EC2 Dedicated Hosts:**
- A physical server with EC2 instance capacity fully dedicated to your use
- Allows you address **compliance requirements and use your existing server- bound software licenses** (per-socket, per-core, pe—VM software licenses)
- Purchasing Options:
  - On-demand – pay per second for active Dedicated Host
  - Reserved - 1 or 3 years (No Upfront, Partial Upfront,All Upfront)
- The most expensive option
- Useful for software that have complicated licensing model (BYOL – Bring Your Own License)
- Or for companies that have strong regulatory or compliance needs

**EC2 Dedicated Instances:**
- Instances run on hardware that’s dedicated to you
- May share hardware with other instances in same account
- No control over instance placement (can move hardware after Stop / Start)

**EC2 Capacity Reservations:**
- Reserve On-Demand instances capacity in a specific AZ for any
duration
- No time commitment (create/cancel anytime), no billing discounts
- Combine with Regional Reserved Instances and Savings Plans to benefit from billing discounts
- Suitable for short-term, uninterrupted workloads that needs to be in a specific AZ

**EC2 Purchasing Options Comparison:**
- **On Demand:** coming and staying in resort whenever we like, we pay the full price
- **Reserved:** like planning ahead and if we plan to stay for a long time, we may get a good discount.
- **Savings Plans:** pay a certain amount per hour for certain period and stay in any room type (e.g., King, Suite, Sea View, ...)
- **Spot instances:** the hotel allows people to bid for the empty rooms and the highest bidder keeps the rooms.You can get kicked out at any time
- **Dedicated Hosts:** We book an entire building of the resort
- **Capacity Reservations:** you book a room for a period with full price even you don’t stay in it

#### Shared Responsibility Model for EC2
**AWS:**
- Infrastructure (global network security)
- Isolation on physical hosts
- Replacing faulty hardware
- Compliance validation

**YOU**
- Security Groups rules
- Operating-system patches and
- Software and utilities installed on the EC2 instance
- IAM Roles assigned to EC2 & IAM user access management
- Data security on your instance

#### EC2 - Summary
- **EC2 Instance:** AMI (OS) + Instance Size (CPU + RAM) + Storage + security groups + EC2 User Data
- **Security Groups:** Firewall attached to the EC2 instance
- **EC2 User Data:** Script launched at the first start of an instance
- **SSH:** start a terminal into our EC2 Instances (port 22)
- **EC2 Instance Role:** link to IAM roles
- **Purchasing Options:** On-Demand, Spot, Reserved (Standard + Convertible), Dedicated Host, Dedicated Instance

---

## EC2 Instances Storage

#### Elastic Block Store (EBS) Volumes
- it's a network drive
- locked to AZ
- can only be mounted to one instance at a time
- provisioned capacity
- By default, the root EBS volume is deleted (attribute enabled)
- By default, any other attached EBS volume is not deleted (attribute disabled)
- <img src="images/ebs-volume.png" height="200">

#### EBS Snapshots
- backup (snapshot) of your EBS volume at a point in time
- copy snapshots across AZ or Region
- ![EBS Snapshots](images/ebs-snapshots.png)

- EBS Snapshot Archive
  - Move a Snapshot to an ”archive tier” that is
75% cheaper
  - Takes within 24 to 72 hours for restoring the archive
  - <img src="images/ebs-snapshots3.png" height="150">

- Recycle Bin for EBS Snapshots
  - Setup rules to retain deleted snapshots so you can recover them after an accidental deletion
  - Specify retention (from 1 day to 1 year)
  - <img src="images/ebs-snapshots2.png" height="150">

#### Amazon Machine Image (AMI)
- customization of an EC2 instance
  - You add your own software, configuration, operating system, monitoring... 
  - Faster boot / configuration time because all your software is pre-packaged
- built for a specific region
- EC2 instances from:
  - A Public AMI: AWS provided
  - Your own AMI: you make and maintain them yourself
  - An AWS Marketplace AMI: an AMI someone else made (and potentially sells)
- ![AMI](images/ami.png)

#### EC2 Image Builder
- automate the creation ofVirtual Machines or container images
- Automate the creation, maintain, validate and test EC2 AMIs
- Can be run on a schedule 
- ![EC2 Image Builder](images/ec2-image-builder.png)

#### EC2 Instance Store
- EBS has limited performance so, if you need a high-performance hardware disk, use EC2 Instance Store.
- Better I/O performance
- EC2 Instance Store lose their storage if they’re stopped (ephemeral)
- Good for buffer / cache / scratch data / temporary content
- Risk of data loss if hardware fails
- Backups and Replication are your responsibility

#### Elastic File System (EFS)
- Managed NFS (network file system) that can be mounted on 100s of EC2
- EFS works with Linux EC2 instances in multi-AZ
- Highly available, scalable, expensive (3x gp2), pay per use, no capacity planning
- <img src="images/efs.png" height="250">

#### EBS vs EFS
- <img src="images/ebs-efs.png" height="250">

#### EFS Infrequent Access (EFS-IA)
- Storage class that is cost-optimized for files not accessed every day
- EFS will automatically move your files to EFS-IA
based on the last time they were accessed
- Example: move files that are not accessed for 60 days to EFS-IA
- <img src="images/efs-ia.png" height="308">

#### Shared Responsibility Model for EC2 Storage
**AWS:**
- Infrastructure
- Replication for data for EBS
volumes & EFS drives
- Replacing faulty hardware
- Ensuring their employees cannot access your data

**YOU:**
- Setting up backup / snapshot procedures
- Setting up data encryption
- Responsibility of any data on
the drives
- Understanding the risk of using EC2 Instance Store

#### Amazon FSx
- 3rd party high-performance file systems on AWS
- FSx for Lustre, Windows File Server, NetApp ONTAP

**FSx for Windows File Server**
- Windows native shared file system
- Windows File Server

**FSx for Lustre**
- A fully managed, high-performance, scalable file storage for High Performance Computing (HPC)
- Lustre is derived from “Linux” and “cluster”.

#### EC2 Instance Storage - Summary
- **EBS volumes:**
  - network drives attached to one EC2 instance at a time
  - MappedtoanAvailabilityZones
  - Can use EBS Snapshots for backups / transferring EBS volumes across AZ
- **AMI:** create ready-to-use EC2 instances with our customizations
- **EC2 Image Builder:** automatically build, test and distribute AMIs
- **EC2 Instance Store:**
  - High performance hardware disk attached to our EC2 instance 
  - Lost if our instance is stopped / terminated
- **EFS:** network file system, can be attached to 100s of instances in a region 
- **EFS-IA:** cost-optimized storage class for infrequent accessed files
- **FSx for Windows:** Network File System for Windows servers
- **FSx for Lustre:** High Performance Computing Linux file system

---

## Elastic Load Balancer (ELB) & Auto Scaling Groups (ASG)

**Vertical Scalability**
- means increasing the size of the instance
- example: t2.micro -> t2.large

**Horizontal Scalability**
- means increasing the number of instances / systems for your application
- Auto Scaling Group
- Load Balancer

**High Availability**
- means running your application / system in at least 2 

**Availability Zones**
- avoids disaster situations
- Auto Scaling Group multi AZ
- Load Balancer multi AZ

**Scalability:**
- ability to accommodate a larger load by making the hardware stronger (scale up), or by adding nodes (scale out)

**Elasticity:** 
- once a system is scalable, elasticity means that there will be some “auto-scaling” so that the system can scale based on the load.This is “cloud-friendly”: pay-per-use, match demand, optimize costs

**Agility:**
- (not related to scalability - distractor) new IT resources are only a click away, which means that you reduce the time to make those resources available to your developers from weeks to just minutes.

**Load Balancer:**
- Spread load across multiple downstream instances
- Do regular health checks to your instances
- <img src="images/load-balancer.png" height="150">

#### Elastic Load Balancer (ELB)
- managed load balancer
- 4 Types:
  - Application Load Balancer (HTTP / HTTPS only) – Layer 7
  - Network Load Balancer (TCP) – Layer 4
  - Gateway Load Balancer – Layer 3
  - Classic Load Balancer (retired in 2023) – Layer 4 & 7
  - ![Load Balancer Types](images/load-balancer-types.png)

#### Auto Scaling Groups (ASG)
- Scale out (add EC2 instances) to match an increased load
- Scale in (remove EC2 instances) to match a decreased load

**Manual Scaling:**
- Update the size of an ASG manually

**Dynamic Scaling:**
- Simple / Step Scaling
  - When a CloudWatch alarm is triggered (example CPU > 70%), then add 2 units 
  - When a CloudWatch alarm is triggered (example CPU < 30%), then remove 1
- Target Tracking Scaling
  - Example: I want the average ASG CPU to stay at around 40%
- Scheduled Scaling
  - Anticipate a scaling based on known usage patterns
  - Example: increase the min. capacity to 10 at 5 pm on Fridays
- Predictive Scaling
  - Uses Machine Learning to predict future traffic ahead of time


#### ELB & ALB - Summary
- High Availability vs Scalability (vertical and horizontal) vs Elasticity vs Agility in the Cloud
- Elastic Load Balancers (ELB)
  - Distribute traffic across backend EC2 instances, can be Multi-AZ
  - Supports health checks
  - 4 types: Classic (old), Application (HTTP – L7), Network (TCP – L4), Gateway (L3)
- Auto Scaling Groups (ASG)
  - Implement Elasticity for your application, across multiple AZ
  - Scale EC2 instances based on the demand on your system, replace unhealthy
  - Integrated with the ELB

---

## Amazon S3
- ”infinitely scaling” storage
- Backup and storage
- Disaster Recovery
- Archive
- Hybrid Cloud storage • Application hosting
- Media hosting
- Data lakes & big data analytics • Software delivery
- Static website

#### S3 Buckets
- allows people to store objects (files) in “buckets” (directories)
- buckets must have a globally unique name (across all regions all accounts)
- defined at region-level

**S3 Bucket Objects:**
- Objects (files) have a Key
- key is composed of prefix + object name
- Metadata
- Tags
- Version ID

**S3 Bucket Security:**
- User-Based
  - IAM Policies – which API calls should be allowed for a specific user from IAM
- Resource-Based
  - Bucket Policies – bucket wide rules from the S3 console - allows cross account 
  - Object Access Control List (ACL) – finer grain (can be disabled)
  - Bucket Access Control List (ACL) – less common (can be disabled)
- Encryption: encrypt objects in Amazon S3 using encryption keys

**S3 Bucket Policies:**
- JSON based policies
- By default, blocks all public access

#### S3 - Static Website Hosting
- S3 can host static websites and have them accessible on the Internet
- 403 Forbidden error, make sure the bucket policy allows public reads!

#### S3 - Versioning
- version your files in Amazon S3
- Protect against unintended deletes (ability to restore a version) - Easy roll back to previous version

#### S3 - Replication (CRR & SRR)
- Must enable Versioning in source and destination buckets 
- Cross-Region Replication (CRR)
  - compliance, lower latency access, replication across
accounts
- Same-Region Replication (SRR)
  - log aggregation, live replication between production and test accounts

#### S3 - Storage Classes
**General Purpose:**
- Used for frequently accessed data
- Low latency and high throughput
- Use Cases: Big Data analytics, mobile & gaming applications, content distribution

**Infrequent Access:**
- data that is less frequently accessed, but requires rapid access when needed
- **Standard-Infrequent Access (S3 Standard-IA):**
  - Use cases: Disaster Recovery, backups
- **One Zone-Infrequent Access (S3 One Zone-IA):**
  - Use Cases: Storing secondary backup copies of on-premise data, or data you can recreate

**Glacier Storage:**
- Low-cost object storage meant for archiving / backup
- **Glacier Instant Retrieval:**
  - Millisecond retrieval, great for data accessed once a quarter 
  - Minimum storage duration of 90 days
- **Glacier Flexible Retrieval:**
  - Expedited (1 to 5 minutes), Standard (3 to 5 hours), Bulk (5 to 12 hours) – free 
  - Minimum storage duration of 90 days
- **Glacier Deep Archive:**
  - long term storage
  - Standard (12 hours), Bulk (48 hours)
  - Minimum storage duration of 180 days

**Intelligent-Tiering:**
- Small monthly monitoring and auto-tiering fee
- Frequent Access tier (automatic): 
  - default tier
- Infrequent Access tier (automatic): 
  - objects not accessed for 30 days
- Archive Instant Access tier (automatic): 
  - objects not accessed for 90 days 
- Archive Access tier (optional): 
  - configurable from 90 days to 700+ days 
- Deep Archive Access tier (optional): 
  - config. from 180 days to 700+ days

#### Encryption
- server side:
  - server encrypts the file after receiving it
- client side:
  - client encrypted the file before sending it

#### IAM Access Analyzer
- Ensures that only intended people have access to your S3 buckets

#### Shared Responsibility Model for S3
**AWS:**
- Infrastructure (global security, durability, availability, sustain concurrent loss of data in two facilities)
- Configuration and vulnerability analysis
- Compliance validation

**YOU:**
- S3 Versioning
- S3 Bucket Policies
- S3 Replication Setup
- Logging and Monitoring • S3 Storage Classes
- Data encryption at rest and in transit

#### Snow Family
- Highly-secure, physical portable devices to collect and process data at the
edge, and migrate data into and out of AWS
- Data migration:
  - Snowcone
  - Snowball Edge
  - Snowmobile
- Edge computing:
  - Snowcone
  - Snowball Edge

**Snowcone:**
- Small, portable computing, anywhere, rugged & secure, withstands harsh environments
- Must provide your own battery / cables
- Snowcone 
  - 8 TB of HDD Storage
- Snowcone SSD 
  - 14 TB of SSD Storage

**Snowball Edge:**
- move TBs or PBs of data in or out of AWS
- Alternative to moving data over the network (and paying network fees)
- Storage Optimized
  - 80 TB of HDD capacity
- Compute Optimized
  - 42 TB of HDD or 28TB NVMe capacity
- Use cases: 
  - large data cloud migrations, DC decommission, disaster recovery

Pricing:
- You pay for device usage and data transfer **OUT** of AWS
- IN to AWS is FREE

**Snowmobile:**
- Transfer exabytes of data (1 EB = 1,000 PB = 1,000,000 TBs)
- Each Snowmobile has 100 PB of capacity (use multiple in parallel)
- High security: temperature controlled, GPS, 24/7 video surveillance 
- Better than Snowball if you transfer more than 10 PB

#### Edge Computing
- Process data while it’s being created on an Edge Location.
- Edge Location means
  - Limited / no internet access
  - Limited / no easy access to computing power
- Only Snowcone or Snowball Edge devices
- Use cases:
  -  Preprocess data, Machine learning at the edge, Transcoding media streams
- Long-term deployment options: 1 and 3 years discounted pricing

#### OpsHub
- software to manage Snow Family Device

#### Storage Gateway
- Bridge between on-premise data and cloud data in S3
- Hybrid storage service to allow on- premises to seamlessly use the AWS Cloud
- Use cases: 
  - disaster recovery, backup & restore, tiered storage

#### Amazon S3 - Summary
- **Buckets vs Objects:** 
  - global unique name, tied to a region
- **S3 security:** 
  - IAM policy, S3 Bucket Policy (public access), S3 Encryption
- **S3 Websites:** 
  - host a static website on Amazon S3
- **S3 Versioning:** 
  - multiple versions for files, prevent accidental deletes
- **S3 Replication:** 
  - same-region or cross-region, must enable versioning
- **S3 Storage Classes:** 
  - Standard, IA, 1Z-IA, Intelligent, Glacier (Instant, Flexible, Deep) 
- **Snow Family:** 
  - import data onto S3 through a physical device, edge computing
- **OpsHub:** 
  - desktop application to manage Snow Family devices
- **Storage Gateway:** 
  - hybrid solution to extend on-premises storage to S3

---

## Databases & Analytics
- You can **structure** the data
- You build **indexes** to efficiently **query / search** through the data
- You define **relationships** between your datasets
- Databases are optimized for a purpose and come with different
features, shapes and constraints

**Relational Databases:**
- databases that are linked

**NoSQL Databases:**
- non relational databases
- Benefits:
  - Flexibility: easy to evolve data model
  - Scalability: designed to scale-out by using distributed clusters • High-performance: optimized for a specific data model
  - Highly functional: types optimized for the data model
- Examples: Key-value, document, graph, in-memory, search databases
- JSON

#### Relational Database Service (RDS)
- managed DB service for DB use **SQL** as a query language
- create databases in the cloud that are managed by AWS 
  - Postgres
  - MySQL
  - MariaDB
  - Oracle
  - Microsoft SQL Server
  - Aurora (AWS Proprietary database)

**RDS versus deploying DB on EC:**

  - PROS:
    - Automated provisioning, OS patching
    - Continuous backups and restore to specific timestamp (Point in Time Restore)! • Monitoring dashboards
    - Read replicas for improved read performance
    - Multi AZ setup for DR (Disaster Recovery)
    - Maintenance windows for upgrades
    - Scaling capability (vertical and horizontal) 
    - Storage backed by EBS (gp2 or io1)

  - CONS:
    - cant SSH

#### Amazon Aurora
- proprietary technology from AWS (not open sourced)
- PostgreSQL and MySQL
- claims 5x performance improvement over MySQL on RDS, over 3x the performance of Postgres on RDS
- costs more than RDS (20% more) – but is more efficient

**Serverless:**
- Automated database instantiation and auto-scaling based on actual usage
- No capacity planning needed
- Least management overhead
- Use cases: 
  - good for infrequent, intermittent or unpredictable workloads

#### Deployments
**Read Replicas:**
- Scale the read workload of your DB
- Can create up to 15 Read Replicas 
- Data is only written to the main DB
- <img src="images/rds-read-replicas.png" height="200">

**Multi-AZ:**
- Failover in case of AZ outage (high availability) 
- Data is only read/written to the main database 
- Can only have 1 other AZ as failover
- <img src="images/rds-multi-az.png" height="200">

**Multi-Region:**
- Disaster recovery in case of region
issue
- Local performance for global reads 
- Replication cost
- <img src="images/rds-multi-region.png" height="200">

#### ElastiCache
- managed Redis or Memcached
- Caches are in-memory databases with high performance, low latency
- Helps reduce load off databases for read intensive workloads

#### DynamoDB
- NoSQL database - not a relational database
- key/value database

**DynamoDB Accelerator (DAX):**
- Fully Managed in-memory cache for
DynamoDB
- 10x performance improvement
- DAX is only used for and is integrated with DynamoDB, while ElastiCache can be used for other databases

#### Redshift
- PostgreSQL, but it’s not used for OLTP
- it is OLAP – online analytical processing (analytics and data warehousing)
- Load data once every hour, not every second

**Serverless:**
- Automatically provisions and scales data warehouse underlying capacity
- Run analytics workloads without managing data warehouse infrastructure • Pay only for what you use (save costs)
- Use cases
  - Reporting, dashboarding applications, real-time analytics

#### Elastic MapReduce (EMR)
- helps creating **Hadoop clusters (Big Data)** to analyze and process vast amount of data

#### Athena
- Serverless query service to analyze data stored in Amazon S3
- SQL
- analyze data in S3 using serverless SQL, use Athena

#### QuickSight
- Serverless machine learning-powered business intelligence service to create **interactive dashboards**

#### DocumentDB
- Aurora is an “AWS-implementation” of PostgreSQL / MySQL
- DocumentDB is the same for MongoDB (which is a NoSQL database)

#### Neptune
- Fully managed graph database
- Examples; Wikipedia, social media

#### Quantum Ledger Database (QLDB)
- Used to review history of all the changes made to your application data over time
- Immutable system: no entry can be removed or modified, cryptographically verifiable
- centralization component

#### Managed Blockchain
- decentralization component
- Blockchain makes it possible to build applications where multiple parties can execute transactions without the need for a trusted, central authority.

#### Glue
- Managed extract, transform, and load (ETL) service

#### Database Migration Service (DMS)
- Quickly and securely migrate databases to AWS, resilient, self healing
- The source database remains available during the migration

#### Databases & Analytics - Summary
- Relational Databases - OLTP:
  - RDS & Aurora (SQL)
- Differences between Multi-AZ, Read Replicas, Multi-Region
- In-memory Database: 
  - ElastiCache
- Key/Value Database: 
  - DynamoDB (serverless) & DAX (cache for DynamoDB)
- Warehouse - OLAP: 
  - Redshift (SQL)
- Hadoop Cluster: 
  - EMR
- Athena: 
  - query data on Amazon S3 (serverless & SQL)
- QuickSight: 
  - dashboards on your data (serverless)
- DocumentDB:
  - “Aurora for MongoDB”(JSON – NoSQL database)
- Amazon QLDB:
  - Financial Transactions Ledger(immutable journal, cryptographically verifiable)
- Amazon Managed Blockchain: 
  - managed Hyperledger Fabric & Ethereum blockchains
- Glue: 
  - Managed ETL (Extract Transform Load) and Data Catalog service
- Database Migration: 
  - DMS
- Neptune: 
  - graph database

---

## Other Compute Services

### Docker
- software development platform to deploy apps
- Apps are packaged in containers that can be run on any OS
- Apps run the same, regardless of where they’re run: 
  - Any machine
  - No compatibility issues
  - Predictable behavior
  - Less work
  - Easier to maintain and deploy
  - Works with any language, any OS, any technology
  - Scale containers up and down very quickly (seconds)

**Docker Images:**
- stored in Docker Repositories
- Public: Docker Hub  
- Private: Amazon ECR (Elastic Container Registry)

**Virtualization:**
- Docker is ”sort of” a virtualization technology, but not exactly
- Resources are shared with the host => many containers on one server

#### Elastic Container Service (ECS)
- Launch Docker containers on AWS
- **You DO provision & maintain the infrastructure** (the EC2 instances)
- <img src="images/ecs.png" height="250">

#### Fargate
- Launch Docker containers on AWS
- **You DO NOT provision & maintain the infrastructure** (the EC2 instances)
- serverless
- <img src="images/fargate.png" height="250">

#### Elastic Container Registry (ECR)
- Private Docker Registry on AWS
- store your Docker images so they can be run by ECS or Fargate

#### Lambda
- Virtual functions – no servers to manage! 
- Limited by time - short executions
- Run on-demand
- Scaling is automated!
- Event-Driven: functions get invoked by AWS when needed
- many programming languages
- Lambda Container Image
  - The container image must implement the Lambda Runtime API 
  - ECS / Fargate is preferred for running arbitrary Docker images
- It is usually very cheap to run AWS Lambda so it’s very popular
- Use cases:
  - Create Thumbnails for images uploaded onto S3 
  - Run a Serverless cron job

#### API Gateway
- if you want to build a serverless API
- Serverless and scalable
- Supports RESTful APIs and WebSocket APIs
- <img src="images/api-gateway.png">

#### Batch
- Fully managed batch processing at any scale
- Batch will dynamically launch EC2 instances or Spot Instances
- Batch jobs are defined as Docker images and run on ECS
- <img src="images/batch.png" height="150">

#### Batch vs Lambda
- Lambda:
  - Time limit
  - Limited runtimes
  - Limited temporary disk space 
  - Serverless

- Batch:
  - No time limit
  - Any runtime as long as it’s packaged as a Docker image
  - Rely on EBS / instance store for disk space
  - Relies on EC2 (can be managed by AWS)

#### Lightsail
- low price
- Simpler alternative to using EC2, RDS, ELB, EBS, Route 53, etc etc
- for noobies with little to no cloud experience
- use case: Simple web applications, web sites

#### Other Compute Services - Summary
- Docker:
  - container technology to run applications
- ECS: 
  - run Docker containers on EC2 instances
- Fargate:
  - Run Docker containers without provisioning the infrastructure 
  - Serverless offering (no EC2 instances)
- ECR: 
  - Private Docker Images Repository
- Batch: 
  - run batch jobs on AWS across managed EC2 instances
- Lightsail: 
  - predictable & low pricing for simple application & DB stacks

---

## Deploying and Managing Infrastructure at Scale

#### CloudFormation
- creating your AWS infrastructure in a 'template'
- allows you to creates in the right order, with the exact configuration that you specify
- example template:
  - I want a security group
  - I want two EC2 instances using this security group
  - I want an S3 bucket
  - I want a load balancer (ELB) in front of these machines

**Benefits:**
- Infrastructure as code
- Cost Effective
- Productivity
  - Declarative programming
- Don’t re-invent the wheel
  - use existing templates
- Supports (almost) all AWS resources

#### Cloud Development Kit (CDK)
- Define your cloud infrastructure using a programming language, then it will compile to a CloudFormation template
- meaning y ou can therefore deploy infrastructure and application runtime code together 
  - Great for Lambda functions
  - Great for Docker containers in ECS / EKS

#### Developers using AWS
- Devs using AWS ONLY care about **DEPLOYING AND RUNNING YOUR  CODE**.
- Devs don't care about:
  - Managing infrastructure
  - Configuring all the databases, load balancers, etc 
  - Scaling concerns
- Most web apps have the same architecture (ALB + ASG)


#### Beanstalk
- developer centric view of deploying an application on AWS
- Platform as a Service (PaaS)
- Managed service:
  - Instance configuration / OS is handled by Beanstalk
  - Deployment strategy is configurable but performed by Elastic Beanstalk 
  - Capacity provisioning
  - Load balancing & auto-scaling
  - Application health-monitoring & responsiveness
- Just the application code is the responsibility of the developer
- Example models:
  - Single Instance deployment: good for dev
  - LB + ASG: great for production or pre-production web applications 
  - ASG only: great for non-web apps in production (workers, etc..)

#### CodeDeploy
- We want to upgrade our application automatically
- Works with:
  - ECS 2 instances
  - on prem services
  - hybrid

#### CodeCommit
- AWS' version of GitHub

#### CodeBuild
- Compiles source code, run tests, and produces packages that are ready to be deployed
- <img src="images/codebuild.png">

#### CodePipeline
- CICD (Continuous Integration & Continuous Delivery)
- Fully managed, compatible with CodeCommit, CodeBuild,CodeDeploy, ElasticBeanstalk, CloudFormation, GitHub, 3rd-party services (GitHub...) & custom plugins...
- <img src="images/codepipeline.png">

#### CodeArtifact
- Artifacts are software packages depend on each other to be built (also called **code dependencies**)
- Developers and CodeBuild can then retrieve dependencies straight from CodeArtifact

#### CodeStar
- Unified UI to easily manage software development activities in one place

#### Cloud9
- cloud IDE

#### Systems Manager (SSM)
- Hybrid AWS service
- Helps you manage your EC2 and On-Premises systems at scale

**Session Manager:**
- Allows you to start a secure shell on your EC2 and on-premises servers
- No need for SSH or port 22 open

**Parameter Store:**
- Secure storage for configuration and secrets 
- API Keys, passwords, configurations

#### OpsWorks
- if you need **Chef & Puppet** to help you perform server configuration automatically, or repetitive actions

#### Deployment - Summary
- CloudFormation: (AWS only)
  - Infrastructure as Code, works with almost all of AWS resources 
  - Repeat across Regions & Accounts
- Beanstalk: (AWS only)
  - Platform as a Service (PaaS), limited to certain programming languages or Docker 
  - Deploy code consistently with a known architecture: ex, ALB + EC2 + RDS
- CodeDeploy (hybrid): 
  - deploy & upgrade any application onto servers 
- Systems Manager (hybrid): 
  - patch, configure and run commands at scale 
- OpsWorks (hybrid): 
  - managed Chef and Puppet in AWS

#### Developer Services - Summary
- CodeCommit:
  - Store code in private git repository (version controlled) 
- CodeBuild: 
  - Build & test code in AWS
- CodeDeploy: 
  - Deploy code onto servers
- CodePipeline: 
  - Orchestration of pipeline (from code to build to deploy) 
- CodeArtifact: 
  - Store software packages / dependencies on AWS
- CodeStar: 
  - Unified view for allowing developers to do CICD and code
- Cloud9:
  - Cloud IDE (Integrated Development Environment) with collab
- AWS CDK: 
  - Define your cloud infrastructure using a programming language

---

## Global Infrastructure

**Global Application**
- an application deployed in multiple geographies
- Why do we need one?
  - Decreased Latency
  - Disaster Recovery (DR)
  - Attack protection

**Global Applications in AWS:**
- Global DNS: Route 53
- Global Content Delivery Network (CDN): CloudFront
- S3 Transfer Acceleration
- AWS Global Accelerator:

#### Route 53
- Managed DNS (Domain Name System)
- DNS is a collection of rules and records which helps clients understand how to reach a server through URLs.
- <img src="images/route53.png" height="250">

**Routing Policies:**
- <img src="images/route53policies.png" height="170">
- <img src="images/route53policies2.png" height="170">

#### CloudFront
- Content Delivery Network (CDN)
- Improves read performance, content is cached at the edge
- Improves users experience
- DDoS protection (because worldwide), integration with Shield, AWS Web Application Firewall

**Origins:**
- S3 bucket:
  - For distributing files and caching them at the edge
  - Enhanced security with CloudFront Origin Access Control (OAC)
- Custom Origin (HTTP):
  - Application Load Balancer
  - EC2 instance
  - S3 website
  - Any HTTP backend you want

**CloudFront vs S3 Cross Region Replication:**
- CloudFront:
  - Global Edge network
  - Files are cached for a TTL (maybe a day)
  - **Great for static content that must be available everywhere**
- S3 Cross Region Replication:
  - Must be setup for each region you want replication to happen
  - Files are updated in near real-time
  - Read only
  - **Great for dynamic content that needs to be available at low-latency in few regions**

#### S3 Transfer Acceleration
- Increase transfer speed by transferring file to an AWS edge location which will forward the data to the S3 bucket in the target region
- <img src="images/transfer-acceleration.png" height="100">

#### Global Accelerator
- Improve global application availability and performance using the AWS global network
- Leverage the AWS internal network to optimize the route to your application (60% improvement)
- Edge locations send the traffic to your application
- <img src="images/global-accelerator.png" height="200">
- <img src="images/global-accelerator2.png" height="210">

#### Outposts
- solve the issue of hybrid cloud environments
- Outposts are “server racks”
  - that offers the same AWS infrastructure, services, APIs & tools to build your own applications on-premises just as in the cloud
- AWS will setup and manage “Outposts Racks” within your on-premises infrastructure and you can start leveraging AWS services on-premises
- You are responsible for the Outposts Rack physical security
- <img src="images/outposts.png" height="180">

#### Wavelengths
- Brings AWS services to the edge of the **5G networks**
- Ultra-low latency applications through 5G networks

#### Local Zones
- Places AWS services closer to end users to run latency-sensitive applications
- Example:
  - AWS Region: N.Virginia (us-east-1)
  - AWS Local Zones: Boston, Chicago, Dallas, Houston, Miami, etc.

#### Global Applications Architecture
- <img src="images/global-apps1.png" height="180">
- <img src="images/global-apps2.png" height="180">

#### Global Applications in AWS - Summary
- **Global DNS: Route 53:**
  - Great to route users to the closest deployment with least latency 
  - Great for disaster recovery strategies
- **Global Content Delivery Network (CDN): CloudFront**
  - Replicate part of your application to AWS Edge Locations – decrease latency 
  - Cache common requests – improved user experience and decreased latency
- **S3 Transfer Acceleration:**
  - Accelerate global uploads & downloads into Amazon S3
- **AWS Global Accelerator:**
  - Improve global application availability and performance using the AWS global network
- **AWS Outposts:**
  - Deploy Outposts Racks in your own Data Centers to extend AWS services
- **AWS WaveLength:**
  - Brings AWS services to the edge of the 5G networks • Ultra-low latency applications
- **AWS Local Zones:**
  - Bring AWS resources (compute, database, storage, ...) closer to your users 
  - Good for latency-sensitive applications

---

## Cloud Integration

#### Simple Queue Service (SQS)
- What's a queue?
- <img src="images/sqs.png" height="180">

**Standard Queue:**
- Fully managed service (serverless)
- use to **decouple** applications
- Default retention of messages: 4 days, maximum of 14 days
- No limit to how many messages can be in the queue
- Messages are deleted after they’re read by consumers
- Low latency (<10 ms on publish and receive)
- Consumers share the work to read messages & scale horizontally
- <img src="images/sqs2.png" height="180">

**FIFO Queue:**
- First In First Out (ordering of messages in the queue)
- Messages are processed in order by the consumer
- <img src="images/sqs-fifo.png" height="60">

#### Kinesis
- Kinesis = **real-time big data streaming**
- Managed service to collect, process, and analyze real-time streaming data at any scale

#### Simple Notification Services (SNS)
- “**event publishers**” only sends message to one SNS topic
- “**event subscribers**” as we want to listen to the SNS topic notifications 
- Each subscriber to the topic will get all the messages
- <img src="images/sns.png" height="150">

#### MQ
- managed message broker service
- When migrating to the cloud, instead of re-engineering the application to use SQS and SNS, we can use Amazon MQ
- on-premises may use open protocols such as:
  - MQTT, AMQP, STOMP, Openwire, WSS
- doesn’t “scale” as much as SQS / SNS

#### Cloud Integration - Summary
**SQS:**
- Queue service in AWS
- Multiple Producers, messages are kept up to 14 days
- Multiple Consumers share the read and delete messages when done 
- Used to **decouple** applications in AWS
- It uses a pull-based system.

**SNS:**
- Notification service in AWS
- Subscribers: Email,Lambda,SQS,HTTP,Mobile...
- Multiple Subscribers, send all messages to all of them - No message retention

**Kinesis:** 
- real-time data streaming, persistence and analysis

**Amazon MQ:**
- managed message broker for ActiveMQ and RabbitMQ in the
cloud (MQTT, AMQP.. protocols)

---

## Cloud Monitoring

#### CloudWatch
- provides metrics for every services in AWS

**Important Metrics:**
- EC2 instances: 
  - CPU Utilization, Status Checks, Network (not RAM) 
  - Default metrics every 5 minutes
  - Option for Detailed Monitoring ($$$): metrics every 1 minute
- EBS volumes: 
  - Disk Read/Writes
- S3 buckets: 
  - BucketSizeBytes, NumberOfObjects, AllRequests 
- Billing: 
  - Total Estimated Charge (only in us-east-1)
- Service Limits: 
  - how much you’ve been using a service API
- Custom metrics: 
  - push your own metrics

**Alarms:**
- used to trigger notifications for any metric
- Example: create a billing alarm on the CloudWatch Billing metric

**Logs:**
- real-time monitoring of logs
- AWS services:
  - Elastic Beanstalk: 
    - collection of logs from application
  - ECS: 
    - collection from containers
  - AWS Lambda: 
    - collection from function logs
  - CloudTrail 
    - based on filter
  - CloudWatch log agents: 
    - on EC2 machines or on-premises servers 
  - Route53: 
    - Log DNS queries

**Logs on EC2:**
- By default, no logs from your EC2 instance will go to CloudWatch
- CloudWatch log agent can be setup on-premises too

#### EventBridge / CloudWatch Events
- react to events on your AWS account
- Schedule:
  - Cron jobs (scheduled scripts)
  - Example:
    - Schedule Every hour -> Trigger script on Lambda function
- Event Pattern: 
  - Event rules to react to a service doing something
  - Example:
    - IAM Root User Sign in Event -> SNS Topic with Email Notification
- can react to events to outside apps or custom
- <img src="images/event-bridge.png" height="120">

#### CloudTrail
- Provides governance, compliance and audit for your AWS Account
- enabled by default
- Get an history of events / API calls made within your AWS Account:
  - Console
  - SDK
  - CLI
  - AWS Services
- Can put logs from CloudTrail into CloudWatch Logs or S3

#### X-Ray
- Visual analysis of our applications
- Uses cases:
  - Troubleshooting performance (bottlenecks)
  - Understand dependencies in a microservice architecture - Pinpoint service issues
  - Review request behavior
  - Find errors and exceptions
  - Are we meeting time SLA?
  - Where I am throttled?
  - Identify users that are impacted
- <img src="images/xray.png" height="250">

#### CodeGuru
- An ML-powered service for **automated code reviews and application performance recommendations**
- CodeGuru Reviewer: 
  - automated code reviews for static code analysis (development)
- CodeGuru Profiler: 
  - visibility/recommendations about application performance during runtime (production)
- <img src="images/codeguru.png" height="130">

**CodeGuru Reviewer:**
- Identify critical issues, security vulnerabilities, and hard-to-find bugs
- Example: 
  - common coding best practices, resource leaks, security detection, input validation

**CodeGuru Profiler:**
- Helps understand the runtime behavior of your application
- Example: 
  - identify if your application is consuming excessive CPU capacity on a logging routine
- Features:
  - Identify and remove code inefficiencies
  - Improve application performance (e.g.,reduceCPU utilization)
  - Decrease compute costs
  - Provides heap summary (identify which objects using
  up memory)
  - Anomaly Detection
- Support applications running on AWS or on- premise

#### Health Dashboard
**Service History:**
- Shows all regions, all services health
- Shows historical information for each day
- Has an RSS feed you can subscribe to

**Your Account:**
- alerts and remediation guidance when AWS is experiencing events that may impact you.
- gives you a personalized view into the performance and availability of the AWS services underlying your AWS resources

#### Cloud Monitoring - Summary
- CloudWatch:
  - Metrics: monitor the performance of AWS services and billing metrics
  - Alarms: automate notification, perform EC2 action, notify to SNS based on metric
  - Logs: collect log files from EC2 instances, servers,Lambda unctions...
- Events (or EventBridge): 
  - react to events in AWS, or trigger a rule on a schedule
- CloudTrail: 
  - audit API calls made within your AWS account
- CloudTrail Insights: 
  - automated analysis of your CloudTrail Events
- X-Ray: 
  - trace requests made through your distributed applications
- Amazon CodeGuru: 
  - automated code reviews and application performance recommendations
- AWS Health Dashboard: 
  - status of all AWS services across all regions
- AWS Account Health Dashboard: 
  - AWS events that impact your infrastructure

---

## VPC & Networking

#### VPC
- virtual private cloud

#### Site to Site VPN
- Connect an on-premises VPN to AWS
- The connection is automatically encrypted
- Goes over the **public internet**
- On-premises:
  - must use a **Customer Gateway (CGW)**
- AWS:
  - must use a **Virtual Private Gateway (VGW)**
- <img src="images/s2s.png" >

#### Direct Connect
- Establish a physical connection between on-premises and AWS
- The connection is private, secure and fast
- Goes over a **private network**
- Takes at least a month to establish

<img src="images/s2s-dc.png" height="190px">

#### Client VPN
- Connect from your computer using OpenVPN to your private network in AWS and on-premises
- Allow you to connect to your EC2 instances over a private IP (just as if you were in the private VPC network)
- Goes over **public Internet**
- <img src="images/client-vpn.png" height="110px">

#### Transit Gateway
- One single Gateway to provide this functionality
- <img src="images/transit-gateway.png" height="250px">

#### VPC & Networking - Summary
- VPC: 
  - Virtual Private Cloud
- Subnets: 
  - Tied to an AZ,network partition of theVPC
- Internet Gateway: 
  - at the VPC level, provide Internet Access
- NAT Gateway / Instances: 
  - give internet access to private subnets
- NACL: 
  - Stateless, subnet rules for inbound and outbound
- Security Groups: 
  - Stateful, operate at the EC2 instance level or ENI
- VPC Peering: 
  - Connect two VPC with non overlapping IP ranges, nontransitive
- Elastic IP: 
  - fixed public IPv4, ongoing cost if not in-use
- VPC Endpoints: 
  - Provide private access to AWS Services within VPC
- PrivateLink:
  - Privately connect to a service in a 3rd partyVPC
- VPC Flow Logs: 
  - network traffic logs
- Site to Site VPN: 
  - VPN over public internet between on-premises DC and AWS:
- Client VPN:
  - OpenVPN connection from your computer into your VPC
- Direct Connect: 
  - direct private connection to AWS
- Transit Gateway: 
  - Connect thousands ofVPC and on-premises networks together

---

