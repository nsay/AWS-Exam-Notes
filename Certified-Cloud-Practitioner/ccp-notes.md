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
- ![EBS Volume](images/ebs-volume.png)

#### EBS Snapshots
- backup (snapshot) of your EBS volume at a point in time
- copy snapshots across AZ or Region
- ![EBS Snapshots](images/ebs-snapshots.png)

- EBS Snapshot Archive
  - Move a Snapshot to an ”archive tier” that is
75% cheaper
  - Takes within 24 to 72 hours for restoring the archive
  - ![EBS Snapshots Archive](images/ebs-snapshots3.png)

- Recycle Bin for EBS Snapshots
  - Setup rules to retain deleted snapshots so you can recover them after an accidental deletion
  - Specify retention (from 1 day to 1 year)
  - ![EBS Snapshots Archive](images/ebs-snapshots2.png)

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
- ![EFS](images/efs.png)

#### EBS vs EFS
- ![EBS vs EBS](images/ebs-efs.png)

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

FSx for Windows File Server
- Windows native shared file system
- Windows File Server

FSx for Lustre
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
- **EFS:** network file system, can be attached to 100s of instances in a region • EFS-IA: cost-optimized storage class for infrequent accessed files
- **FSx for Windows:** Network File System for Windows servers
- **FSx for Lustre:** High Performance Computing Linux file system