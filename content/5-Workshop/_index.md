---
title: "Workshop"
date: 2024-01-01
weight: 5
chapter: false
pre: " <b> 5. </b> "
---

# Secure Hybrid Access to S3 using VPC Endpoints

#### Overview

This workshop focuses on one of the most practical security problems in cloud infrastructure: how to access Amazon S3 privately and safely from different environments without sending traffic across the public Internet.

In many real-world systems, especially those handling internal files, logs, backups, or sensitive application data, keeping S3 access private is an important architectural requirement. Instead of allowing workloads to go out through public endpoints, AWS provides VPC endpoint mechanisms that help route traffic internally and reduce exposure.

In this lab, the goal is not only to create endpoints, but also to understand why different endpoint types exist, where each one should be used, and how endpoint policies can add another layer of access control. The workshop gradually moves from conceptual understanding to actual implementation and testing.

You will work with two different approaches for accessing Amazon S3:

- **Gateway VPC Endpoint**: Used when resources inside a VPC need private access to Amazon S3 or DynamoDB through route table entries. This option is simple, efficient, and well suited for cloud workloads running directly in the VPC.
- **Interface VPC Endpoint**: Used when private connectivity must be extended through private IP addresses and DNS resolution, especially in scenarios involving on-premises integration, hybrid connectivity, or PrivateLink-style communication.

By the end of the workshop, you will not only know how to configure these endpoints, but also how to compare their behavior, test the traffic path, and apply endpoint policies to tighten access rules. This makes the workshop especially valuable for anyone learning cloud networking, hybrid architecture, and secure AWS service access.

#### What you will gain

- Understand the purpose of VPC endpoints in AWS network security architecture.
- Learn the difference between Gateway endpoints and Interface endpoints in practical scenarios.
- Practice private S3 access from both VPC-based workloads and simulated on-premises environments.
- Explore how DNS, route tables, and endpoint policies affect access flow.
- Build a stronger foundation for designing secure hybrid cloud architectures in future projects.

#### Content

1. [Workshop overview](5.1-Workshop-overview)
2. [Prerequiste](5.2-Prerequiste/)
3. [Access S3 from VPC](5.3-S3-vpc/)
4. [Access S3 from On-premises](5.4-S3-onprem/)
5. [VPC Endpoint Policies (Bonus)](5.5-Policy/)
6. [Clean up](5.6-Cleanup/)
