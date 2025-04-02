# **AWS Training - Day 14**

## Trusted Advisor
    - AWS Trusted Advisor provides recommendations across multiple categories, including cost optimization and security. These recommendations help you follow AWS best practices to optimize your services and resources.
    
## AWS Trusted Advisor - Key Areas  

1. **Cost Optimization**  
   - Suggests actions to reduce costs.  
   - Recommends deleting unused/idle resources.  
   - Advises on using reserved capacity.  

2. **Performance**  
   - Improves service performance.  
   - Suggests provisioned throughput options.  
   - Monitors overutilized EC2 instances.  

3. **Security**  
   - Enhances application security.  
   - Recommends AWS security features.  
   - Reviews permissions.  

4. **Fault Tolerance**  
   - Ensures application availability.  
   - Suggests auto-scaling, backups, health checks.  
   - Recommends redundant Availability Zones.  

5. **Service Limits**  
   - Monitors service quota usage.  
   - Alerts on approaching limits.  
   - Recommends deleting resources or requesting quota increases.  


## AWS Support Plans  

| **Support Plan**           | **Features**                                                                 |
|----------------------------|-----------------------------------------------------------------------------|
| **Basic Support**          | - Free for all AWS customers. <br> - Access to AWS documentation, whitepapers, and support forums. |
| **Developer Support**      | - Email support during business hours. <br> - General guidance within 24 hours. <br> - System impairment response within 12 hours. |
| **Business Support**       | - 24/7 phone, chat, and email support. <br> - Response times: Production system down – 1 hour. <br> - AWS Trusted Advisor full access. |
| **Enterprise On-Ramp**     | - 24/7 access to AWS experts. <br> - Response times: Critical workload down – 30 minutes. <br> - Technical account management. |
| **Enterprise Support**     | - Includes all lower-tier support plans. <br> - Response times: Business-critical system down – 15 minutes. <br> - Dedicated Technical Account Manager (TAM). <br> - Infrastructure event management. <br> - Personalized architectural guidance. |

### **AWS RDS Pricing**  

Amazon Relational Database Service (RDS) pricing depends on several factors:  

1. **Instance Pricing**  
   - Charged per hour or per second, depending on the instance type.  
   - Includes Standard (On-Demand), Reserved, and Spot Instances.  

2. **Storage Costs**  
   - Based on storage type:  
     - **General Purpose (SSD)** – Cost-effective, standard performance.  
     - **Provisioned IOPS (SSD)** – High performance for intensive workloads.  
     - **Magnetic Storage** – Legacy option, rarely used.  

3. **Database Engine**  
   - Pricing varies for different engines:  
     - **MySQL, PostgreSQL, MariaDB** – Open-source, lower cost.  
     - **SQL Server, Oracle** – Proprietary, higher cost due to licensing.  
     - **Amazon Aurora** – AWS-optimized, billed per second.  

4. **Backup & Snapshot Storage**  
   - Free storage up to the size of the RDS instance.  
   - Additional storage charged per GB.  

5. **Data Transfer**  
   - **Inbound Data Transfer** – Usually free.  
   - **Outbound Data Transfer** – Charged per GB beyond free tier limits.  

6. **Read Replicas & Multi-AZ Deployments**  
   - Read replicas billed separately.  
   - Multi-AZ deployments incur additional costs for redundancy.  

For exact pricing, visit the **[AWS RDS Pricing Page](https://aws.amazon.com/rds/pricing/)**.

---
# Other Compute Section

## What is Docker