---
title: "Proposal"
date: 2024-01-01
weight: 2
chapter: false
pre: " <b> 2. </b> "
---

# Smart Healthcare Appointment System Deployment Proposal on AWS

### 1. Executive Summary

Smart Healthcare Appointment System is a platform designed to help patients book medical appointments, manage health records, and connect with healthcare facilities quickly and transparently. The core objective goes beyond a simple booking website; it builds a structured, highly secure digital health system capable of long-term scaling to handle high traffic during peak hours.

During my internship, I primarily focused on backend development and infrastructure, while also supporting the team in connecting the user interface with asynchronous processing systems and AWS services. Therefore, this proposal reflects both a product perspective and technical mindset, bridging an academic project into a production-ready cloud healthcare platform.

A key aspect of the system is avoiding a traditional monolithic architecture. Instead, the design cleanly separates layers into frontend, business logic, asynchronous message queues, and databases. This approach ensures high availability, patient data security, and stable operations.

### 2. Problem Statement

In current medical environments, appointment scheduling and record management are often fragmented or manually operated, leading to several challenges:

- Patients spend long hours waiting at reception or experience system congestion during peak registration hours.
- Appointment data and personal health information face risks of exposure if not strictly partitioned and protected.
- Systems are prone to bottlenecks during sudden surges in traffic, disrupting healthcare services.
- Difficulty in synchronizing appointment statuses between patients, doctors, and various hospital departments.

#### Current Issues

If built as a simple monolithic model where all request traffic routes directly to a single server, the system would quickly crash under high concurrent user loads. Furthermore, a lack of asynchronous processing mechanisms or secure network zoning reduces scalability and healthcare data safety.

Another issue is that many systems only solve basic data storage without optimizing for load capacity, real-time error monitoring, and industry-standard healthcare security compliance.

#### Proposed Solution

The Smart Healthcare Appointment System is proposed with the following structure:

- Frontend provides search, booking, health record management, and doctor information experiences.
- Backend Node.js/Express handles business logic, authentication, authorization, and appointment coordination.
- PostgreSQL stores appointment metadata, patient/doctor details, and medical statuses.
- Amazon S3 stores medical records, test results, and healthcare images to offload the backend and fit object storage models.
- Scaling services like CloudFront, SQS, CloudWatch, and SNS are introduced to boost performance, handle peak queues, monitor, and optimize costs.

The core of the solution is a multi-tier architecture combined with asynchronous queues for peak appointment flows, while the backend focuses on metadata and healthcare business logic. This architecture suits a digital health platform experiencing continuous growth in data volume and concurrent users.

### 3. Solution Architecture

The architecture below illustrates the deployment direction of the Smart Healthcare Appointment System on AWS, featuring a content delivery layer, secure VPC network layer, application layer, data layer, and operations monitoring layer:

![Smart Healthcare Appointment System Architecture](/images/2-Proposal/so-do.jpg)

#### Key Component Descriptions

- **Amazon Route 53, Amazon CloudFront, AWS WAF, and AWS Certificate Manager**: Act as the Global Edge Security & CDN layer, delivering static content, managing domains, automating SSL certificates, and mitigating web threats.
- **Internet Gateway and Application Load Balancer**: Receive user requests, route traffic into Public Subnets, and distribute loads to the backend system.
- **Amazon EC2 (in Private Subnet)**: Runs the backend to process booking business logic, authentication, and healthcare data coordination.
- **Amazon RDS PostgreSQL (Multi-AZ) and Amazon ElastiCache for Redis**: Store appointment metadata, patient info, accounts, medical statuses, and cache data to accelerate query performance.
- **Amazon S3 (Upload)**: Stores medical records, test results, and health imagery using Presigned URLs allowing direct client uploads.
- **Event-Driven Execution Bus (SQS FIFO Queue, AWS Lambda, SNS & SES)**: Asynchronously handles peak booking tasks, sends appointment notifications, and automates confirmation emails.
- **Amazon CloudWatch**: Supports logging, monitoring, and automated alerting (CloudWatch Alarm) during system incidents or CPU overload.

#### Significance of the Architecture for Smart Healthcare Appointment System

This architecture demonstrates that the Smart Healthcare Appointment System is not just a basic web application, but a robust system featuring a security edge layer, content delivery, clearly separated VPC network tiers (Public/Private Subnets), large-scale async processing, and rigorous operations monitoring. This provides a solid foundation ensuring medical data safety, high load capacity, and real-world scalability.

### 4. Technical Implementation

During the internship, the team focused on feasible tasks aligned with the existing codebase:

- Developed frontend interfaces for Home, Search, Appointment Booking, Patient Profile, and Admin Dashboard.
- Designed simulated login workflows and role-based access for patients, doctors, and administrators.
- Standardized appointment metadata structure for search, management, and coordination.
- Prepared the upload workflow for medical records and health images using a presigned URL model.
- Supported Express backend integration with PostgreSQL and S3 at a level appropriate for the demo.

This also means not every component in the architecture diagram is 100% fully deployed yet. Services like SQS, CloudWatch, and SNS currently serve as logical scaling directions rather than fully finalized components. Presenting this clearly ensures the report remains honest regarding the actual scope.

### 5. Roadmap and Milestones

#### Phase 1: Core Product Completion

- Stabilize search, booking, record preview, and user navigation experiences.
- Standardize metadata and appointment approval workflows.
- Complete the admin dashboard and basic analytics.

#### Phase 2: Real Cloud Integration

- Establish stable connections between frontend, Express backend, and PostgreSQL.
- Complete direct uploads to S3 using presigned URLs for medical records.
- Standardize configuration environments and conduct end-to-end testing.

#### Phase 3: System Expansion

- Add background processing for heavy or asynchronous tasks.
- Integrate monitoring, alerting, and logging for a production-ready environment.
- Optimize costs using lifecycle policies and data tiering for long-term storage.

### 6. Budget Estimation

The image below outlines the monthly cost estimation for the Smart Healthcare Appointment System aggregated from the AWS Pricing Calculator and exported on June 20, 2026:

| Category | Estimated Monthly Cost (USD) | Notes |
| --- | ---: | --- |
| RDS PostgreSQL Multi-AZ | 85.50 | Largest cost driver due to high availability priority |
| EC2 Server (t4g.micro x2) | 19.51 | Two application servers across two AZs |
| Application Load Balancer | 18.98 | Traffic distribution and unified entry point |
| NAT Instance (t4g.nano) | 4.64 | Supports outbound traffic for private subnets |
| ElastiCache for Redis | 7.50 | Data caching and query performance optimization |
| Others (CloudWatch, SQS, SNS) | 5.07 | Costs for monitoring, logging, and async processing |
| **Total** | **141.20** | Reference cost for the directional architecture |

The estimated cost above fits a production-oriented or complete demo architecture rather than a minimal learning environment setup. For the internship or experimentation phase, the team can reduce costs via:

- Using a single-AZ configuration for dev/test environments before requiring high availability.
- Shutting down or downsizing EC2 instances when continuous execution is not required.
- Leveraging S3 lifecycle rules to transition infrequently accessed data to Glacier.
- Enabling detailed CloudWatch logs only for components requiring active tracking.
- Utilizing IAM Roles and S3 Gateway Endpoints to reduce misconfiguration risks instead of hard-coding access keys.

### 7. Risk Assessment

| Risk | Impact | Mitigation Strategy |
| --- | --- | --- |
| Misalignment between frontend, backend, and presigned URL flow | Upload failures, out-of-sync health record data | Standardize API contracts, test incrementally, and perform end-to-end testing before demo |
| Inconsistent or poorly-reviewed appointment/patient metadata | Inefficient search, cluttered appointment management | Define mandatory metadata, add review statuses, and establish admin/doctor review workflows |
| Insecure AWS access permission configurations | Medical data leaks or unauthorized privilege escalation | Apply IAM Roles, Principle of Least Privilege, and avoid hard-coding keys in source code |
| Cost inflation from maintaining a large architecture for dev | Budget waste when systems lack real user loads | Separate dev/demo environments, scale down resources, and monitor costs periodically |
| Lack of operational visibility during system failures | Difficulty detecting and handling appointment outages promptly | Set up metrics, logs, CloudWatch Alarms, and SNS notifications for critical endpoints |
| Internship scope insufficient to complete the entire architecture | Reports prone to being perceived as overclaims | Clearly distinguish completed work from future directions illustrated via roadmap |

### 8. Expected Results

Smart Healthcare Appointment System delivers value across three dimensions:

- **For End Users**: Patients and doctors get a centralized platform to book appointments and manage medical records more quickly, intuitively, and reliably.
- **For the Development Team**: The project tightly integrates frontend, backend, metadata design, and cloud architecture thinking into a single complete product.
- **For Learning Direction**: The project serves as a bridge between UI/UX, real-world healthcare business logic, and secure AWS system deployment.

From a personal perspective, this proposal reflects my transition from thinking about UI aesthetics to ensuring design experiences go hand-in-hand with data flow, security, cost, and operational management. That is the greatest learning value Smart Healthcare Appointment System has brought me during this internship.
