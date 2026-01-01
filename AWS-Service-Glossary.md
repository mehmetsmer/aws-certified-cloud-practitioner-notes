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

| Feature / Service | Technical Definition & Use Case | Console Location |
| :--- | :--- | :--- |
| **Instances** | Virtual servers in the AWS Cloud. Provides scalable computing capacity. | EC2 Dashboard > Left Menu > **Instances** |
| **AMI (Amazon Machine Image)** | A template that contains the software configuration (OS, application server, and applications) required to launch an instance. | Selected during "Launch Instance" wizard. |
| **Instance Types** | Combinations of CPU, memory, storage, and networking capacity (e.g., t2.micro, m5.large) to fit different use cases. | Selected during "Launch Instance" wizard. |
| **Security Groups** | A virtual firewall for your EC2 instances to control incoming and outgoing traffic. Acts at the instance level. | EC2 Dashboard > Left Menu > **Security Groups** |
| **Key Pairs** | A set of security credentials (private key and public key) used to prove your identity when connecting to an instance. | EC2 Dashboard > Left Menu > **Key Pairs** |
| **User Data** | Scripts or configuration parameters run on the instance during the initial boot process (bootstrapping). | Launch Instance Wizard > **Advanced Details** section. |
| **Elastic IP** | A static IPv4 address designed for dynamic cloud computing. It remains associated with your account until you release it. | EC2 Dashboard > Left Menu > **Elastic IPs** |

---

## 💰 3. Billing & Cost Management
**Console Path:** Search Bar > "Billing"

| Feature / Service | Technical Definition & Use Case | Console Location |
| :--- | :--- | :--- |
| **AWS Budgets** | A service that allows you to set custom budgets to track your cost and usage, and alerts you when you exceed your thresholds. | Billing Dashboard > Left Menu > **Budgets** |
| **Bills** | Provides details of your AWS charges and usage data for each service. | Billing Dashboard > Left Menu > **Bills** |

---

## 🔌 4. Connectivity Protocols

| Protocol | Port | Description |
| :--- | :--- | :--- |
| **SSH (Secure Shell)** | **22** | Cryptographic network protocol for operating network services securely over an unsecured network. Standard for Linux access. |
| **SFTP (SSH File Transfer)** | **22** | Secure File Transfer Protocol. Uses SSH to transfer files securely. |
| **HTTP** | **80** | Hypertext Transfer Protocol. Standard protocol for unencrypted web traffic. |
| **HTTPS** | **443** | Hypertext Transfer Protocol Secure. Encrypted web traffic using SSL/TLS. |
| **RDP (Remote Desktop)** | **3389** | Proprietary protocol developed by Microsoft to connect to another computer with a graphical interface. Standard for Windows access. |
