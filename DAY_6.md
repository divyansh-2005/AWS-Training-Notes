# **AWS Training - Day 6**  
## **Agenda**  
- Elastic Load Balancer (ELB)  
- Auto Scaling Group (ASG)  
- Virtual Private Cloud (VPC)  

---

## **1. Elastic Load Balancer (ELB)**  
- Distributes incoming traffic across multiple servers to ensure efficient load balancing.  
- Supports servers across different Availability Zones (AZs) for high availability.  
- **Health Check:**  
  - Continuously monitors server health.  
  - If a server becomes unresponsive, ELB automatically redirects traffic to healthy servers.  

---

## **2. Auto Scaling Group (ASG)**  
- Ensures a specified number of servers are always running.  
- Example Configuration:  
  - **Min:** 1, **Max:** 10, **Desired:** 3 → ASG maintains at least 3 instances running.  
- **Scaling Policies:**  
  - Can scale up/down automatically based on demand.  
  - Can be scheduled to adjust the number of instances at specific times.  

---

## **3. Virtual Private Cloud (VPC)**  
- A logically isolated section of AWS that allows you to launch AWS resources in a customizable virtual network.  
- Provides **complete control** over network settings, including IP addressing, subnets, route tables, and gateways.  
- **Key Components:**  
  - **Subnets:** Divide the VPC into smaller sections (Public & Private).  
  - **Route Tables:** Direct network traffic between subnets and the internet.  
  - **Internet Gateway (IGW):** Enables public access to instances.  
  - **NAT Gateway:** Allows private instances to access the internet securely.  
  - **Security Groups & NACLs:** Control inbound and outbound traffic for security.  

---