---
title: "Blog 3"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 3.3. </b> "
---

# Session Policies in Amazon EKS Pod Identity

Amazon EKS Pod Identity has recently added the session policies feature, allowing you to narrow IAM permissions flexibly and precisely for each pod without needing to create many separate IAM roles. This is an important step forward that helps apply the principle of least privilege more effectively in large-scale Kubernetes environments.

### Key points to know

- A session policy is an inline IAM policy specified when creating or updating a Pod Identity association.
- Effective permissions are the intersection between the IAM role permissions and the session policy, so the session policy can only narrow permissions, not expand them.
- It helps avoid over-permissioning when reusing a single IAM role for multiple workloads with different needs.
- It supports both same-account and cross-account setups through IAM role chaining.
- It significantly reduces the number of IAM roles that need to be managed, helping avoid hitting IAM quota limits in large clusters.
- It can be configured through the AWS Management Console, AWS CLI, or AWS SDK when creating an association between a Kubernetes ServiceAccount and an IAM role.

This feature is especially useful when you have many applications running on the same IAM role but need different permission restrictions. For example, one pod may only need read access to a specific S3 bucket while another pod only needs permission to call certain APIs.

### Why this matters

For large Kubernetes environments, Pod Identity session policies help apply least privilege in a more practical and scalable way. Instead of creating many separate IAM roles for similar workloads, teams can reuse a role and restrict each workload more precisely through a session policy.

### Practical value

- Simplifies IAM role management in large EKS clusters.
- Reduces security risks caused by overly broad permissions.
- Supports more precise access control for workload-specific requirements.
- Makes large-scale Kubernetes security governance easier to maintain over time.

### Suggested additions

- Add the architecture image used in your original post.
- Add the original article link.
- Add the implementation or usage guide link if you want this page to mirror the published FCAJ article more closely.
