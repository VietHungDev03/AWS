---
title: "Event 2"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 4.2. </b> "
---


# Summary Report: "GenAI-powered App-DB Modernization workshop"

### Event Objectives

- Share best practices in modern application design.
- Introduce Domain-Driven Design (DDD) and event-driven architecture.
- Provide guidance on selecting the right compute services.
- Present AI tools to support the development lifecycle.

### Speakers

- **Jignesh Shah** - Director, Open Source Databases
- **Erica Liu** - Sr. GTM Specialist, AppMod
- **Fabrianne Effendi** - Assc. Specialist SA, Serverless Amazon Web Services

### Key Highlights

#### Identifying the drawbacks of legacy application architecture

- Long product release cycles can lead to lost revenue and missed opportunities.
- Inefficient operations reduce productivity and increase costs.
- Non-compliance with security regulations can result in breaches and reputational damage.

#### Transitioning to modern application architecture - Microservices

Migrating to a modular system means each function becomes an independent service communicating through events, built on three core pillars:

- **Queue Management**: Handle asynchronous tasks.
- **Caching Strategy**: Optimize performance.
- **Message Handling**: Flexible inter-service communication.

#### Domain-Driven Design (DDD)

- Four-step method: identify domain events, arrange the timeline, identify actors, and define bounded contexts.
- Bookstore case study showing how DDD works in practice.
- Context mapping patterns for integrating bounded contexts.

#### Event-Driven Architecture

- Three integration patterns: Publish/Subscribe, Point-to-point, and Streaming.
- Main benefits: loose coupling, scalability, and resilience.
- Comparison between synchronous and asynchronous communication approaches.

#### Compute Evolution

- Shared Responsibility Model across EC2, ECS, Fargate, and Lambda.
- Serverless benefits such as no server management, auto-scaling, and pay-for-value.
- Criteria for selecting between functions and containers.

#### Amazon Q Developer

- Support for SDLC automation from planning to maintenance.
- Code transformation scenarios such as Java upgrade and .NET modernization.
- AWS Transform agents for VMware, Mainframe, and .NET migration.

### Key Takeaways

#### Design Mindset

- **Business-first approach**: Start from the business domain, not only the technology.
- **Ubiquitous language**: Build a shared vocabulary between business and technical teams.
- **Bounded contexts**: Manage complexity in large systems by identifying clear boundaries.

#### Technical Architecture

- **Event storming technique**: A practical method for modeling business processes.
- Prefer **event-driven communication** where it improves flexibility and resilience.
- Understand when to use sync, async, pub/sub, and streaming patterns.
- Know how to choose between VM, containers, and serverless depending on the workload.

#### Modernization Strategy

- Use a phased roadmap instead of rushing modernization efforts.
- Apply the **7Rs framework** depending on the nature of each application.
- Measure ROI through both cost reduction and business agility gains.

### Applying to Work

- Apply DDD thinking to current projects through event storming with business teams.
- Refactor service boundaries based on bounded contexts.
- Replace selected synchronous calls with asynchronous messaging patterns.
- Pilot AWS Lambda for suitable serverless use cases.
- Explore Amazon Q Developer in the development workflow to improve productivity.

### Event Experience

Attending the **GenAI-powered App-DB Modernization** workshop was extremely valuable, giving me a comprehensive view of application and database modernization using modern methods and tools.

#### Learning from highly skilled speakers

- Experts from AWS and major technology organizations shared best practices in modern application design.
- Real-world case studies helped me better understand how DDD and Event-Driven Architecture can be applied in large projects.

#### Hands-on technical exposure

- Event storming content helped me visualize how business processes can be modeled into domain events.
- I learned more about splitting microservices and defining bounded contexts to manage large-system complexity.
- I better understood trade-offs between synchronous and asynchronous communication patterns.

#### Leveraging modern tools

- I explored Amazon Q Developer as an AI assistant supporting the SDLC from planning to maintenance.
- I learned how automation and serverless services such as AWS Lambda can improve development productivity.

#### Networking and discussions

- The workshop created opportunities to exchange ideas with experts, peers, and business teams.
- Practical examples reinforced the value of a business-first approach instead of focusing only on technology choices.

#### Lessons learned

- DDD and event-driven patterns help reduce coupling while improving scalability and resilience.
- Modernization must follow a phased roadmap with clear ROI awareness.
- AI tools such as Amazon Q Developer can create strong productivity gains when integrated properly.

#### Event photo

![GenAI-powered App-DB Modernization workshop](/images/4-EventParticipated/event2.jpg)

> Overall, the event not only provided technical knowledge but also helped me reshape my thinking about application design, modernization strategy, and collaboration across teams.
