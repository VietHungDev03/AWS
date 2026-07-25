---
title: "Blog 1"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 3.1. </b> "
---

# Amazon VPC - The Foundation of Every Architecture on AWS

The first blog post I chose to translate revolves around a core problem in AWS system design: how to build a secure, highly protected, and easily scalable network architecture using Amazon VPC.

The article from AWS introduces the importance of designing a network architecture before deploying applications, segmenting network zones, and understanding access control mechanisms.

### 1. Amazon VPC Solution Overview

Amazon VPC (Virtual Private Cloud) allows you to create a virtual private network on AWS to securely deploy and manage resources. Key components include:

- **Amazon VPC**: Provides IP address ranges (CIDR Blocks) and full control over network configuration.
- **Public Subnet & Private Subnet**: Segregates public and internal network zones to optimize security.
- **Route Table & Internet Gateway**: Handles traffic routing and Internet connectivity.
- **NAT Gateway**: Supports outbound internet connectivity for resources residing in the Private Subnet.

Additionally, Security Groups and Network ACLs control access across multiple layers. Designing the network infrastructure from the start ensures the system remains stable and easy to scale when traffic surges.

### 2. How Subnet Segmentation and Access Control Work

Instead of placing all resources in one place, the architecture divides the system into separate network zones to reduce the attack surface:

- **Public Subnet**: Houses resources requiring internet connectivity, such as Application Load Balancers or Bastion Hosts.
- **Private Subnet**: Houses critical components like Amazon EC2 instances handling business logic or Amazon RDS databases, without direct internet access.
- **Security Group**: Operates at the resource level (Instance Level) and is stateful, automatically allowing return traffic.
- **Network ACL**: Operates at the subnet level, can be configured with allow/deny rules, and is stateless, requiring both inbound and outbound rules to be explicitly defined.

This approach implements a Defense in Depth model to maximize system protection.

### 3. Request Flow and Network Design

From the article's content, I summarize the infrastructure's operational workflow as follows:

- Users send requests from the Internet through the Internet Gateway.
- Traffic enters the Application Load Balancer located in the Public Subnet.
- The Load Balancer forwards requests down to Amazon EC2 instances located in the Private Subnet to process business logic.
- EC2 instances connect to the internal Amazon RDS database.
- Services in the Private Subnet utilize a NAT Gateway when secure outbound internet access is required.

This model enables the system to serve user demands while keeping sensitive internal data secure.

### 4. What I Learned from the Blog Post

This article helped me realize that building cloud applications is not just about provisioning servers, but network foundations play a decisive role in stability and security. As an infrastructure engineer in the Smart Healthcare Appointment System project, VPC design concepts are extremely useful for configurations such as:

- Allocating separate subnets for web services and medical databases.
- Configuring strict Security Groups to protect patient information.
- Setting up secure Route Tables and Gateways.

Understanding this model helps me design systems that comply with strict security standards in the healthcare industry.

### 5. Connection to Smart Healthcare Appointment System

- Smart Healthcare Appointment System needs to adopt the Public/Private Subnet segmentation model to protect appointment data and user information.
- Configuring Security Groups and Network ACLs helps minimize unauthorized access to the backend system.
- A robust VPC network foundation provides the prerequisite to easily scale as user volume grows.

### 6. Conclusion

Network design with Amazon VPC is the most critical foundational step before deploying any system on AWS. Mastering how VPCs, subnets, and security layers operate helps optimize performance, availability, and safety for real-world applications.

FCAJ group post link: <https://www.facebook.com/groups/awsstudygroupfcj/permalink/2220573215374305/>
