---
title: "Blog 2"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 3.2. </b> "
---

# AWS Architecture Blog | What I Learned About Event-Driven Architecture with Amazon SQS and AWS Lambda

Hello everyone,

While exploring AWS, I realized that not every request from users needs to be processed immediately. If all requests are handled directly by the backend, the system is very prone to overloading when traffic spikes.

What I learned is that AWS provides an effective solution by combining Amazon SQS, AWS Lambda, and Amazon CloudWatch to build an Event-Driven architecture, making the system flexible, stable, and scalable.

The second blog post I chose to translate revolves around a very practical problem in distributed architecture design: how to handle asynchronous requests, relieve backend load, and ensure the system does not crash during traffic surges. Instead of processing every request immediately, an Event-Driven architecture combined with message queues helps services operate flexibly, stably, and automates the processing workflow.

The article from AWS introduces how to combine Amazon API Gateway, Amazon SQS, AWS Lambda, and Amazon CloudWatch to build this model. This is an important approach to optimize performance, reduce operational costs, and enhance availability for cloud applications.

### 1. Solution Overview

The architecture described in the article uses:

- **Amazon API Gateway** to receive requests from clients and route data into the message queue.
- **Amazon SQS** as a message queue to store messages in order while waiting for processing.
- **AWS Lambda** to process data automatically using a serverless model.
- **Amazon DynamoDB** as the backend database to store results.
- **Amazon CloudWatch** for system monitoring.
- **Amazon SNS** to send alerts when incidents occur.

A notable point is that the system completely decouples the request-receiving component from the business logic component, preventing bottlenecks when a large number of requests arrive simultaneously.

### 2. How Event-Driven Architecture Works

Instead of synchronous direct processing, event-driven architecture allows components to communicate via messages:

- Users send requests through API Gateway.
- API Gateway pushes requests into the Amazon SQS queue instead of calling the backend directly.
- SQS stores messages securely and distributes them one by one to Lambda.
- AWS Lambda triggers automatically to process each message without server management.
- Processing results are saved to the database or logged on CloudWatch.

This approach directly reduces backend load, prevents overloading, and ensures no data loss during traffic spikes.

### 3. Main Processing Flow

From the content of the article, I summarize the operational flow as follows:

- Client sends a request to Amazon API Gateway.
- API Gateway forwards the request to the Amazon SQS queue.
- Amazon SQS stores messages in order and triggers AWS Lambda.
- AWS Lambda processes the data and saves it to the backend database.
- Amazon CloudWatch collects logs, metrics, and sends alerts via Amazon SNS if errors or anomalies are detected.

In this model, service decoupling increases isolation, meaning if one component fails, the rest of the system can still operate normally.

### 4. What I Learned from the Blog Post

This article drew my attention more to designing background tasks and asynchronous processing in large-scale systems. Working with infrastructure and the backend, I found Event-Driven architecture with SQS and Lambda very useful for problems such as:

- Handling heavy background jobs like sending emails or generating reports.
- Receiving a high volume of medical appointment registration requests without crashing the server.
- Synchronizing data securely between microservices.

Even when the system has not yet adopted the entire complex model, understanding event-driven thinking helps me design data processing pipelines that handle loads better.

### 5. Connection to Smart Healthcare Appointment System

- Smart Healthcare Appointment System can adopt the SQS queue to handle peak appointment booking traffic, avoiding system congestion.
- Using AWS Lambda for background processing tasks optimizes costs since you only pay for actual code execution time.
- Integrating CloudWatch helps closely monitor performance and detect issues early during the operation of the healthcare system.

### 6. Conclusion

Event-Driven architecture with Amazon SQS and AWS Lambda is becoming a core solution for building high-load distributed systems. Applying this model helps minimize latency, increases scalability, and ensures absolute stability for modern applications.

FCAJ group post link: <https://www.facebook.com/groups/awsstudygroupfcj/permalink/2219595365472090/>
