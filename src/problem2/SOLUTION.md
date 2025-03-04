**Overview diagram**
![image](https://github.com/user-attachments/assets/1564d76e-2d13-46d4-8447-f74cd19b6143)


**Services Breakdown**
**Compute & Networking**

- Amazon EKS – Runs Kubernetes workloads (Altenative: Kubernetes cluster running on EC2 instance)
- AWS ALB / Global Accelerator – Load balancing and traffic routing to Kubernetes services (Altenative: HAproxy running on EC2 instance)
- Route 53 – Manages domain and DNS (Altenative:Using native DNS of internet provider or using Cloudflare service)
- AWS WAF - Filters incoming traffic to prevent attacks, DDOS protection (Altenative: Cloudflare for WAF)
- API Gateway -  For authentication and rate-limits requests (Using Kong, or WSO2 AM running on EC2 instance)

**Database, Storage & Persistence**
- Amazon S3 – Stores static assets (images, reports, config files). (Altenative: using EBS attached to EC2 instance for storing files)
- Amazon RDS – For transactional DB (Using MySQL/PostresSQL running on EC2 instance).
- Amazon Dynamo DB - For non-relational DB.
- Amazon ElastiCache (Redis) – Improves app performance with caching (Using Redis running on EC2 instance).

**Messaging & Streaming**
- Amazon SQS – For asynchronous trade processing. (Altenative: Running Kafka on EC2 instance)
- Amazon SNS - Sends notifications about trade status or alerts (e.g., failed orders).(Altenative: Running Rabbit MQ on EC2 instance)

**Logging & Monitoring**
ELK Stack (Elasticsearch, Logstash, Kibana) running on EC2 instances
- Logstash – Collects logs from Kubernetes pods.
- Elasticsearch – Indexes logs for fast searching.
- Kibana – Provides dashboards for log analysis.

**AWS CloudWatch**
Monitors AWS infrastructure (EC2, ALB, RDS, EKS, etc.).
Sends alerts for failures (e.g., high CPU usage, memory spikes).

**Prometheus & Grafana**
Prometheus – Scrapes Kubernetes and application metrics.
Grafana – Visualizes Prometheus metrics.

**Security**

- IAM - For RBAC
- AWS Cloudtrail - For auditing

