# **AWS Training - Day 5 Notes**  

## **Security Groups in EC2**  
- **Security Groups (SG)** act as a **firewall** for EC2 instances, controlling inbound and outbound traffic.  
- SGs are **stateful**, meaning:  
  - If an inbound rule allows traffic, the corresponding outbound response is automatically allowed, even if there's no explicit outbound rule.  

### **Example of Stateful Behavior:**  
- Consider an EC2 instance running a database.  
- A client sends a `SELECT` query.  
- Even if there's **no outbound rule** defined, the client will still receive the response because **SG is stateful** (i.e., it remembers the connection and allows the return traffic).  

### **Outbound Rule Example:**  
- If we **only** set an outbound rule allowing traffic to `google.com`, we can still receive responses from Google **without an inbound rule** because the outbound connection was initiated from inside the instance, and security groups allow return traffic automatically.  

---

## **Network ACL (NACL)**  
- **NACLs** operate at the **subnet** level (which belongs to an **Availability Zone (AZ)**).  
- NACLs are **stateless**, meaning:  
  - If an inbound rule allows traffic, a separate outbound rule must also be defined for the return traffic.  

---

## **Stateful vs. Stateless in AWS**  

When working with **Security Groups (SGs)** and **Network ACLs (NACLs)** in AWS, understanding **stateful** and **stateless** behavior is crucial.  

### **1. Stateful (Security Groups)**  
A stateful system **remembers previous interactions** and allows return traffic automatically.  

#### **Example:**  
- You have an **EC2 instance** running a **database** inside a VPC.  
- A **client** sends a `SELECT` query to the database.  
- The security group allows **inbound traffic** on **port 3306 (MySQL)**.  
- Even if **no outbound rule** is defined, the database will still send the query response back to the client because **SGs are stateful** and automatically allow return traffic.  

#### **Key Point:**  
👉 If an incoming request is allowed, the response **does not need an explicit outbound rule**—it is automatically allowed.  

---

### **2. Stateless (Network ACLs)**  
A stateless system **does not remember previous interactions** and requires **explicit rules for both inbound and outbound traffic**.  

#### **Example:**  
- You have a **web server** inside a subnet with a **Network ACL**.  
- A **client** sends an HTTP request to the server on **port 80**.  
- If the NACL allows **inbound traffic** on **port 80** but does **not** explicitly allow **outbound traffic**, the response will be **blocked**.  

#### **Key Point:**  
👉 **Both inbound and outbound rules must be explicitly defined**, or else traffic in one direction may be blocked.  

---

## **Comparison Table**  

| Feature           | Security Group (SG) | Network ACL (NACL) |
|------------------|--------------------|--------------------|
| **Level**        | Instance level     | Subnet level |
| **Stateful?**    | ✅ Yes (Remembers connections) | ❌ No (Does not remember) |
| **Inbound Rules?** | Required | Required |
| **Outbound Rules?** | Not required for return traffic | Required for all traffic |
| **Example** | Client sends DB query, response allowed even without outbound rule | Client sends request, response is blocked if outbound rule is missing |

---

## **Key-Value Pair in EC2**  

1. Go to **EC2 -> Instances** -> Click **Launch an instance**.  
2. **Create Key Pair** -> Select **Key Pair Type (RSA)** -> Choose **Private Key File Format (.pem)**.  
3. The **.pem file** will be downloaded.  

![](/images/day5_1.png)  

4. **Network Settings** -> Select **Existing Security Group** (do not create a new security group for every instance).  
5. Click **Launch Instance**.  

### **Connecting to EC2 Locally:**  
1. Go to **EC2 -> Your Instance -> Connect to Instance**.  
2. Select **SSH Client** and copy the command provided.  
3. Run the command in your terminal.  

![](/images/day5_2.png)  

4. Ensure the **.pem file** is present in the same directory as the terminal window.  

![](/images/day5_3.png)  

---

## **EC2 as a Web Server**  
1. **Launch an instance** -> **Advanced settings**.  
2. Scroll down to **User Data** and add the following script:  

```bash
#!/bin/bash
# Use this for your user data (script from top to bottom)

# Update system packages
sudo yum update -y

# Install Apache HTTP Server (httpd)
sudo yum install -y httpd

# Start the httpd service
sudo systemctl start httpd

# Enable httpd to start on boot
sudo systemctl enable httpd
```

3. Run the following commands to verify and configure your web server:  

```bash
sudo systemctl status httpd
sudo chown -R ec2-user:ec2-user /var/www
echo "Hello World!" > /var/www/html/index.html
```

---

## **Creating an Image from an Instance (AMI)**  
1. **Select Instance** -> Go to **Actions** -> Click **Create Image**.  
2. **Launch New Instance** -> Go to **My AMIs** -> Specify **Number of Instances**.  

### **Important Components:**  
- **User Data** (startup script).  
- **AMI** (Amazon Machine Image for reusable instance setup).  

---

### **User Data in AWS (EC2 User Data)**
**User Data** in AWS is a feature that allows you to provide startup scripts that run when an EC2 instance **first boots up**. This is mainly used for **automating configurations, installations, and setups**.

---

### **🔹 How Does It Work?**
- When launching an EC2 instance, you can provide a **bash script** (for Linux) or a **PowerShell script** (for Windows).
- The script runs **only once** at the first boot (unless configured otherwise).
- Used for **software installation, system updates, and configuration**.

---

### **🔹 Example Use Cases**
✅ Installing packages (e.g., Python, Nginx, Docker)  
✅ Configuring environment variables  
✅ Setting up services (e.g., starting an app)  
✅ Running initialization scripts (e.g., downloading code from GitHub)  

---

### **🔹 Example: Linux User Data Script**
```bash
#!/bin/bash
yum update -y                # Update system packages
yum install -y httpd         # Install Apache
systemctl start httpd        # Start Apache server
systemctl enable httpd       # Enable Apache to start on boot
echo "Hello from EC2" > /var/www/html/index.html
```
📌 This script:
- Updates the system
- Installs Apache
- Starts Apache and enables it at boot
- Writes "Hello from EC2" to the web server’s homepage

---

### **🔹 Example: Windows User Data Script**
```powershell
<powershell>
Write-Output "Installing IIS..."
Install-WindowsFeature -name Web-Server -IncludeManagementTools
Write-Output "IIS Installed Successfully!"
</powershell>
```
📌 This installs **IIS (Internet Information Services)** on a Windows instance.

---

### **🔹 How to Add User Data?**
1. Go to **AWS EC2 Dashboard** → Launch Instance
2. Under **Advanced details**, find **User Data**
3. Paste your script
4. Launch the instance

---

### **🔹 How to Check If User Data Ran?**
For Linux:
```bash
sudo cat /var/log/cloud-init-output.log
```
For Windows:
- Check logs at `C:\ProgramData\Amazon\EC2-Windows\Launch\Log\`

---

💡 **Bonus Tip:** If you need the script to run on every reboot, modify the `rc.local` file (Linux) or use scheduled tasks (Windows).

---
### **What is AMI (Amazon Machine Image) in AWS?**  
An **Amazon Machine Image (AMI)** is a **pre-configured virtual machine template** used to launch EC2 instances. It includes:  
1. **Operating System (OS)** (Linux, Windows, etc.)  
2. **Pre-installed Software** (Apache, MySQL, Python, etc.)  
3. **Configuration Settings**  
4. **Application Data (optional)**  

### **🔹 Types of AMIs**
1. **AWS-Provided AMIs** → Official images from AWS (Amazon Linux, Ubuntu, Windows, etc.)  
2. **Marketplace AMIs** → Pre-built AMIs from third-party vendors (e.g., WordPress, Deep Learning AMIs)  
3. **Custom AMIs** → User-created AMIs with pre-installed software & configurations  
4. **Community AMIs** → Free AMIs shared by the community  

---

### **🔹 Why Use AMI?**
✅ **Faster Instance Deployment** – Launch EC2 with pre-configured settings  
✅ **Scalability** – Use the same AMI to create multiple instances  
✅ **Customization** – Create an AMI with your required software stack  
✅ **Backup & Recovery** – Take AMI snapshots for disaster recovery  

---

### **🔹 How to Create a Custom AMI?**
1. Launch an EC2 instance & configure it  
2. Install necessary software & configure settings  
3. Go to **EC2 Dashboard → Instances → Actions → Create Image**  
4. AWS creates an **AMI snapshot** that you can use to launch new instances  

---

### **🔹 Example Use Case**
You're setting up an **AI/ML server** on EC2 with TensorFlow, PyTorch, and other dependencies. Instead of installing everything manually each time, you:  
1. Install everything once  
2. Create an **AMI**  
3. Launch multiple EC2 instances from that AMI, saving time 🚀  

---

### **🔹 AMI vs Snapshot**
| Feature | AMI | Snapshot |
|---------|-----|----------|
| Includes OS? | ✅ Yes | ❌ No |
| Includes Data? | ✅ Yes (if selected) | ✅ Yes |
| Use Case | Launch instances | Backup EBS volumes |

---


# AWS Activity: Security Group & EC2 in Different Regions

## Steps:
1. **Create a Security Group (SG) in Region 1**  
2. **Create an EC2 instance in Region 2**  
3. **Attempt to attach the SG from Region 1 to the EC2 in Region 2**  

## Output:
🚫 **The Security Group (SG) will not be available in Region 2.**  

## **Why is the Security Group (SG) Not Available in Region 2?**  
Security Groups (SGs) are **region-specific**, meaning they only exist in the AWS region where they were created. When you try to attach an SG from **Region 1** to an EC2 instance in **Region 2**, it won’t be available because AWS does not automatically replicate SGs across regions.

---

## **Why Does a Security Group Ask for a VPC?**  
A Security Group (SG) is **associated with a Virtual Private Cloud (VPC)** because:  
1. **SGs are a VPC-level feature** → They control inbound & outbound traffic within a VPC.  
2. **Different VPCs have separate networking rules** → An SG must belong to a specific VPC to enforce security rules.  
3. **AWS Networking Isolation** → Each region has its own VPCs, so an SG from one region **cannot** be used in another region.  

