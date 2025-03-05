**AWS Cloud Training Workshop - Day 2**

## **Today's Agenda (From Class Whiteboard)**
- **Access Key and Security Key**
- **Creating Budget**
- **IAM Concepts:**
  - User
  - Group
  - Policy
  - Role
- **AWS CLI:**
  - Installation
  - Running `aws s3 ls`
- **S3 Service**
- **EC2/S3 Role Assignments**


## **IAM User**
1. IAM (Identity and Access Management) is a **global service**.
2. It is completely **free** to create any number of users.

### **Why do we create an IAM user?**
- IAM users allow controlled access to AWS services.
- Policies define the **permissions** granted to users.

## **User Groups**
1. Instead of assigning policies to individual users, we can attach policies to **groups** for better management.

## **AWS CLI**
### **Creating an Access Key for AWS CLI**
1. Go to **IAM -> Users**
2. Select **Security Credentials**
3. Click **Create Access Keys**
4. Download the access key for CLI access.

### **Installing AWS CLI and Configuring**
1. Download and install AWS CLI.
2. Open a terminal and configure using:
   ```sh
   aws configure
   ```

## **Amazon S3**
### **Creating an S3 Bucket**
1. Go to **AWS Console -> S3**
2. Click **Create Bucket** and follow the setup steps.

### **Using AWS CLI for S3**
- **List all S3 buckets:**
  ```sh
  aws s3 ls
  ```
- **Create a new S3 bucket:**
  ```sh
  aws s3 mb s3://divyansh-demo-1
  ```

## **Billing and Cost Management**
- AWS **Billing and Cost Management** helps track and control expenses related to cloud usage.

## **IAM Components**
- **User**
- **Group**
- **Policy**
- **Role**

## **Roles in IAM**
- If a service needs to interact with another service, it requires a **role**.
- Example: An **EC2 instance** needs a role to communicate with **S3**.

### **Creating a Role**
1. Go to **IAM -> Roles**
2. Select the required service (e.g., EC2)
3. Assign necessary permissions

### **Difference Between IAM User and Role**
| Feature | IAM User | IAM Role |
|---------|---------|----------|
| Assigned to | Individuals | AWS Services |
| Authentication | Requires username/password or access key | No credentials needed by user |
| Use Case | Human access to AWS resources | Service-to-service interaction |

## **Policies in IAM**
### **Custom IAM Policy Example**
- Allow an IAM user to **read** and **list** all S3 buckets and EC2 instances, but **deny** deletion of any bucket or instance.

#### **Creating a Custom Policy**
```json
{
  "Effect": "Deny",
  "Action": "*",
  "Resource": "*",
  "Condition": {
    "StringNotEquals": {
      "aws:RequestedRegion": "us-east-1"
    }
  }
}
```

### **Attaching the Policy to a User**
1. Go to **IAM -> Policies**
2. Create a new policy with the above JSON.
3. Attach the policy to the required IAM user.
4. Login as that IAM user and verify policy restrictions.

**Note:** The policy restricts bucket creation only in the `us-east-1` region but allows creation in other regions.

---



