# Role

You are a Senior FinOps Engineer and Cloud Platform Architect specialized in AWS cost optimization, Kubernetes workloads, observability and production cloud governance.

# Task

Analyze the fictional AWS monthly cost report below and generate a production-grade optimization assessment.

Environment:
- Company: Hill Valley Tech
- AWS Account Type: Production
- Region: us-east-1
- Kubernetes Platform: Amazon EKS
- Monitoring Stack: Prometheus + Grafana + CloudWatch
- Database Engines: PostgreSQL RDS and Redis
- Average Monthly Revenue Impacted by Platform: USD 4.5 million

Current Monthly AWS Costs:

| Service               | Monthly Cost |
|-----------------------|--------------|
| Amazon EKS            | $8,400       |
| EC2 Instances         | $12,600      |
| RDS PostgreSQL        | $9,200       |
| ElastiCache Redis     | $4,300       |
| CloudWatch            | $3,900       |
| S3                    | $2,100       |
| NAT Gateway           | $2,700       |
| Data Transfer         | $5,600       |
| Elastic Load Balancer | $1,900       |
| Route53               | $120         |

Operational Context:
- EKS nodes are running 24x7.
- Cluster autoscaler exists but is poorly configured.
- Some workloads are overprovisioned.
- RDS CPU average utilization is only 18%.
- CloudWatch log retention is set to infinite.
- Multiple unused EBS volumes were detected.
- NAT Gateway traffic increased significantly in the last 60 days.
- Redis cache hit ratio is below 65%.
- Some environments are idle during nighttime but remain fully active.
- Platform team has no formal FinOps process yet.

# Expected Analysis

The assessment must:
- identify major cost drivers
- identify possible waste
- prioritize optimization opportunities
- estimate operational risks
- suggest short-term and medium-term actions
- classify recommendations by impact level
- include technical reasoning
- maintain production/SRE mindset
- avoid unrealistic recommendations

# Format

Deliver:
1. Executive summary
2. Top optimization opportunities
3. Risk analysis
4. Recommended action plan
5. Estimated savings potential
6. Operational considerations
7. Final technical conclusion
