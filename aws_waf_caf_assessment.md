# AWS Well-Architected & Cloud Adoption Framework Assessment Report

---

# Task 1 – Review of Existing Architecture

## Existing Components

- Single EC2 instance hosting frontend
- Single EC2 instance hosting database (MySQL)
- Single Availability Zone deployment
- Public subnet deployment
- Open security group rules (0.0.0.0/0)
- No automated backup
- No monitoring or logging
- Manual scaling

## Identified Risks

- Single point of failure
- No high availability
- Security exposure
- No disaster recovery strategy
- Operational inefficiency
- No cost monitoring

---

# Task 2 – AWS Well-Architected Framework Evaluation

| Pillar                 | Observation                              | Improvement Recommendation                | Supporting AWS Service        |
| ---------------------- | ---------------------------------------- | ----------------------------------------- | ----------------------------- |
| Operational Excellence | Manual deployment and monitoring         | Implement CI/CD and monitoring automation | CodePipeline, CloudWatch      |
| Security               | Open security groups and public database | Apply least privilege and private subnets | IAM, Security Groups, AWS WAF |
| Reliability            | Single-AZ deployment                     | Multi-AZ architecture with failover       | Auto Scaling, RDS Multi-AZ    |
| Performance Efficiency | Static instance sizing                   | Auto Scaling and caching layer            | EC2 Auto Scaling, ElastiCache |
| Cost Optimization      | No cost tracking                         | Implement monitoring and right-sizing     | Cost Explorer, Savings Plans  |

---

# Task 3 – AWS Cloud Adoption Framework (CAF)

## 1. Business Perspective

The organization aims to modernize infrastructure and improve scalability. However, migration objectives must be aligned with measurable KPIs such as uptime, performance improvement, and cost reduction. Executive sponsorship and ROI modeling are critical to ensure strategic alignment.

## 2. People Perspective

Cloud adoption requires training staff in AWS architecture, DevOps practices, and security. Establishing a Cloud Center of Excellence (CCoE) will help standardize practices and support long-term adoption.

## 3. Governance Perspective

Governance controls such as AWS Organizations, tagging strategies, Service Control Policies (SCPs), and budget monitoring must be implemented to prevent cloud sprawl and cost overruns.

## 4. Platform Perspective

Adopt managed services such as Amazon RDS, Auto Scaling, and Infrastructure as Code (IaC). This reduces operational overhead and improves scalability and reliability.

## 5. Security Perspective

Security must be built-in through IAM least privilege, encryption at rest and in transit, private subnet isolation, AWS WAF, and CloudTrail logging.

## 6. Operations Perspective

Operational excellence requires monitoring, alerting, backup automation, and incident response playbooks using CloudWatch, AWS Backup, and Systems Manager.

---

# Task 4 – Improved Architecture Design

## Architecture Overview

The improved architecture includes:

- Amazon VPC with public and private subnets across multiple Availability Zones
- Internet Gateway and NAT Gateways
- Application Load Balancer in public subnets
- EC2 Auto Scaling Group in private subnets
- Amazon ElastiCache (Redis) for session management
- Amazon RDS MySQL (Multi-AZ) with read replicas
- AWS WAF for web protection
- IAM roles for secure access
- CloudWatch and CloudTrail for monitoring and logging
- Automated backups enabled

This design ensures high availability, scalability, fault tolerance, operational efficiency, and security compliance.

---

# Reflection (150 Words)

This lab reinforced that cloud migration is not simply about moving servers to AWS but about redesigning systems to leverage cloud-native best practices. The AWS Well-Architected Framework provides a structured method to evaluate architecture across reliability, security, performance, cost, and operational excellence. Meanwhile, the Cloud Adoption Framework emphasizes organizational readiness, governance, and people enablement. The most important lesson learned is that successful cloud transformation requires both technical and organizational alignment. Managed services such as RDS, Auto Scaling, and ElastiCache significantly enhance resilience and reduce operational complexity. Security and governance must be implemented from the beginning to avoid risks later. Overall, this exercise strengthened architectural thinking and the ability to communicate structured cloud design decisions effectively.
