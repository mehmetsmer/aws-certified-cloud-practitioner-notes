# AWS Service & Concept Glossary

This document serves as a technical reference guide for key AWS services and features explored during my learning journey. It focuses on service definitions, use cases, and navigation paths within the AWS Management Console.

## 🔐 1. Identity and Access Management (IAM)
**Console Path:** Search Bar > "IAM"

| Feature / Service | Technical Definition & Use Case | Console Location |
| :--- | :--- | :--- |
| **IAM Users** | Entities that represent the person or service interacting with AWS. Used for individual access instead of the Root Account. | IAM Dashboard > Left Menu > **Users** |
| **User Groups** | A collection of IAM users. Used to apply permissions to multiple users simultaneously for easier management. | IAM Dashboard > Left Menu > **User Groups** |
| **IAM Policies** | JSON documents that define permissions. They determine what actions are allowed or denied on AWS resources. | IAM Dashboard > Left Menu > **Policies** |
| **IAM Roles** | An identity with specific permissions that does not have long-term credentials (password or access keys). Used for temporary access delegation. | IAM Dashboard > Left Menu > **Roles** |
| **MFA (Multi-Factor Auth)** | A security best practice that adds an extra layer of protection on top of your username and password. | Top Right Corner (Account Name) > **Security Credentials** |
| **Access Keys** | Long-term credentials (Access Key ID and Secret Access Key) used for programmatic access via AWS CLI or SDK. | Top Right Corner (Account Name) > **Security Credentials** |
| **Credential Report** | A report that lists all users in the account and the status of their various credentials (passwords, access keys, MFA). | IAM Dashboard > Left Menu > **Credential Report** |

---

## 🖥️ 2. Amazon EC2 (Elastic Compute Cloud)
**Console Path:** Search Bar > "EC2"

This section consolidates topics from EC2 Fundamentals, Solution Architect Level Features, and Block Storage.

| Feature / Service | Technical Definition & Use Case | Console Location |
| :--- | :--- | :--- |
| **EC2 User Data** | Bootstrapping scripts run only once when the instance is first launched. Used to install software/updates automatically. | Launch Instance Wizard > **Advanced Details** |
| **Instance Types** | Defines the hardware of the host computer (CPU, RAM, Network). Examples: t2.micro, c5.large, r5.xlarge. | Selected during "Launch Instance" wizard. |
| **Security Groups** | Stateful firewall acting at the instance level. Controls inbound/outbound traffic (allow rules only). | EC2 Dashboard > Left Menu > **Security Groups** |
| **Key Pairs (SSH)** | Credential file (.pem or .ppk) required to connect to an instance via SSH. | EC2 Dashboard > Left Menu > **Key Pairs** |
| **EC2 Instance Connect** | Browser-based SSH connection tool. Works without managing local key files. | EC2 Dashboard > Select Instance > **Connect** |
| **IAM Roles for EC2** | Assigns permissions to an EC2 instance so it can access other AWS services (like S3) without hardcoding credentials. | Launch Instance Wizard > **Advanced Details** |
| **Spot Instances** | Spare EC2 capacity offered at steep discounts (up to 90%). Can be reclaimed by AWS with 2 mins notice. | EC2 Dashboard > Left Menu > **Spot Requests** |
| **Elastic IP** | A static Public IPv4 address. You own it until you release it. Helps mask instance failures by remapping IP. | EC2 Dashboard > Left Menu > **Elastic IPs** |
| **Placement Groups** | Controls how instances are placed on physical hardware. Strategies: **Cluster** (Performance), **Spread** (Safety), **Partition** (Distributed). | EC2 Dashboard > Left Menu > **Placement Groups** |
| **ENI (Elastic Network Interface)** | A virtual network card attached to an instance. Primary ENIs are default; secondary ENIs facilitate failover/management. | EC2 Dashboard > Left Menu > **Network Interfaces** |
| **EC2 Hibernate** | Saves RAM state to the EBS root volume upon shutdown. Enables faster boot-up with applications pre-loaded. | Launch Instance Wizard > **Advanced Details** |
| **AMI (Amazon Machine Image)** | A packaged image containing the OS and data to launch an instance. Can be AWS-provided or Custom. | EC2 Dashboard > Left Menu > **AMIs** |
| **EBS (Elastic Block Store)** | Persistent block-level storage volumes for use with EC2 instances. Acts like a network drive. Locked to a specific AZ. | EC2 Dashboard > Left Menu > **Volumes** |
| **EBS Snapshots** | Point-in-time backup of an EBS volume stored in S3. Incremental backups (only changes are saved). | EC2 Dashboard > Left Menu > **Snapshots** |
| **Instance Store** | High-performance hardware disk physically attached to the host. **Ephemeral:** Data is lost if instance stops. | Selected via Instance Type (e.g., i3, d2 families) |

---

## ⚖️ 3. ELB & ASG (High Availability & Scalability)
**Console Path:** Search Bar > "EC2" (Located in Left Menu)

| Feature / Service | Technical Definition & Use Case | Console Location |
| :--- | :--- | :--- |
| **ELB (Elastic Load Balancer)** | Automatically distributes incoming application traffic across multiple targets (EC2 instances) in multiple AZs. | EC2 Dashboard > Left Menu > **Load Balancers** |
| **ALB (Application Load Balancer)** | Layer 7 (HTTP/HTTPS) load balancer. Supports path-based routing, host-based routing, and containerized apps. | Selected during "Create Load Balancer". |
| **NLB (Network Load Balancer)** | Layer 4 (TCP/UDP) load balancer. High performance (millions of requests/sec) and Static IP support. | Selected during "Create Load Balancer". |
| **Target Groups** | Logical groups of resources (EC2, Lambda, IP) that the Load Balancer routes traffic to. Health checks are defined here. | EC2 Dashboard > Left Menu > **Target Groups** |
| **ASG (Auto Scaling Group)** | Automatically adjusts the number of EC2 instances to match load. Ensures min/max instance counts (Self-Healing). | EC2 Dashboard > Left Menu > **Auto Scaling Groups** |
| **Scaling Policies** | Rules that tell ASG when to scale out (add) or scale in (remove). Types: Target Tracking, Step Scaling, Simple Scaling. | ASG Dashboard > **Automatic Scaling** Tab |

---

## 🗄️ 4. Amazon S3 & EFS (Shared & Object Storage)
**Console Path:** Search Bar > "S3" or "EFS"

| Feature / Service | Technical Definition & Use Case | Console Location |
| :--- | :--- | :--- |
| **Amazon S3 (Simple Storage Service)** | Object storage built to store and retrieve any amount of data. Infinite scaling, regional (not tied to AZ). | Services > **S3** |
| **S3 Buckets** | Containers for objects (files). Bucket names must be **globally unique** across all AWS accounts. | S3 > **Create Bucket** |
| **S3 Versioning** | Keeps multiple variants of an object in the same bucket. Protects against accidental deletion or overwrites. | S3 > Bucket > **Properties** |
| **S3 Storage Classes** | Tiers to optimize cost (e.g., Standard, Intelligent-Tiering, Glacier for archive). | S3 > Object > **Properties** |
| **Amazon EFS** | Managed NFS file system. Can be mounted by hundreds of EC2 instances across **different AZs**. Linux only. | Services > **EFS** |
| **EFS Mount Targets** | Network interfaces created in VPC subnets that allow EC2 instances to connect to the EFS file system. | EFS > File System > **Network** |
| **Security Group Chaining** | Best practice for EFS: The EFS Security Group allows traffic *only* from the EC2 Security Group ID (not IPs). | EC2 > **Security Groups** |

---

## 🛢️ 5. Databases & Analytics
**Console Path:** Search Bar > "RDS" or "DynamoDB"

| Feature / Service | Technical Definition & Use Case | Console Location |
| :--- | :--- | :--- |
| **Amazon RDS** | Managed Relational Database Service. Supports SQL engines (MySQL, Postgres, SQL Server, Oracle, MariaDB). Uses EBS for storage. | Services > **RDS** |
| **Amazon Aurora** | AWS-proprietary relational database. Compatible with MySQL/Postgres but 5x faster and auto-scaling storage. | Services > **RDS** |
| **Amazon DynamoDB** | Fully managed **NoSQL** database (Key-Value). Serverless, single-digit millisecond latency, scales to any size. | Services > **DynamoDB** |
| **Amazon ElastiCache** | Managed in-memory caching service (Redis or Memcached). Used to speed up heavy database queries. | Services > **ElastiCache** |

---

## 💰 6. Billing & Cost Management
**Console Path:** Search Bar > "Billing"

| Feature / Service | Technical Definition & Use Case | Console Location |
| :--- | :--- | :--- |
| **AWS Budgets** | A service that allows you to set custom budgets to track your cost and usage, and alerts you when you exceed your thresholds. | Billing Dashboard > Left Menu > **Budgets** |
| **Bills** | Provides details of your AWS charges and usage data for each service. | Billing Dashboard > Left Menu > **Bills** |

---

## 🔌 7. Connectivity Protocols

| Protocol | Port | Description |
| :--- | :--- | :--- |
| **SSH (Secure Shell)** | **22** | Cryptographic network protocol for operating network services securely over an unsecured network. Standard for Linux access. |
| **SFTP (SSH File Transfer)** | **22** | Secure File Transfer Protocol. Uses SSH to transfer files securely. |
| **HTTP** | **80** | Hypertext Transfer Protocol. Standard protocol for unencrypted web traffic. |
| **HTTPS** | **443** | Hypertext Transfer Protocol Secure. Encrypted web traffic using SSL/TLS. |
| **RDP (Remote Desktop)** | **3389** | Proprietary protocol developed by Microsoft to connect to another computer with a graphical interface. Standard for Windows access. |
