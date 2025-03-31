# **AWS Training - Day 9**
# Deploying and managing Infrastruture at Scale

## CloudFormation
 It is a service it allows to outline AWS infrastructure for any resource

## Beanstalk

## AWS Cloud Development Kit (CDK)
 Allows use to use aws on jupyter notebook, vs code, pycharme, .. IDE
 ex: s3_client = boto3(s3);

## Typical architecture: Web App 3-tier
- Global Accelrater

It looks like you are trying to create a *Web Service Environment* using *AWS Elastic Beanstalk. Here's a simplified step-by-step guide to creating an environment in **AWS Elastic Beanstalk* based on your description:

### Steps to Create an Elastic Beanstalk Environment (Using Python Example):

1. *Go to the AWS Management Console:*
   - Open the *AWS Management Console* and navigate to *Elastic Beanstalk* under the *Services* section.

2. *Create a New Application:*
   - Click on *Create a new application* (or use an existing one if you prefer).
   - *Name your application* (e.g., MyPythonApp).

3. *Choose Platform:*
   - Choose the platform as *Python* (for your Python-based web application).
   - Select the *Python version* you want to use.

4. *Sample Application:*
   - Select *Sample Application* to use a default sample application provided by AWS, which is a quick way to get started.

5. *Create a New Role:*
   - For the environment, create a *new IAM role*.
   - Enter a *Service Role Name* (e.g., MyElasticBeanstalkRole).

6. *Define VPC Settings:*
   - Choose *VPC* (Virtual Private Cloud) settings.
   - Select *All Availability Zones* (AZs) for better availability.
   - *Without DB* (skip database setup as per your choice).

7. *Root Volume Type:*
   - Set the *Root Volume Type* to *General Purpose (SSD)*.
   - This is the default disk type for storing your application and OS files.

8. *Instance Settings:*
   - Set the *Instance Type* to *t2.micro* (which is part of the AWS Free Tier).
   - Choose *On-Demand* for pricing options (this means you pay for instance usage as it happens, instead of Reserved Instances).

9. *Security Group:*
   - Choose *Default Security Group* to keep it simple, or you can create a custom security group for your needs.

10. *Review and Launch:*
    - Once all settings are defined, click on *Create Environment*. This will initiate the creation of your Elastic Beanstalk environment using the configurations you provided.

11. *CloudFormation (Optional Step):*
    - In the background, Elastic Beanstalk uses *AWS CloudFormation* to automatically create the necessary resources like EC2 instances, VPC, security groups, etc.

### Summary of Your Steps:
- Create a new application.
- Choose the Python platform.
- Use a sample app.
- Create a new IAM role.
- Set up VPC with all AZs, no DB.
- Use *t2.micro* instance, general-purpose SSD, default security group.
- *CloudFormation* will be used in the background for resource management.

This process will deploy your Python web application on *Elastic Beanstalk* with the default settings you've chosen.

---
# AWS Code Deploy
 it is both cloud and on device service

# CodeCommit

# CodeBuild

# CodePipeline

# CodeArtifact

# System Manager (SSM)
- Fleet manager
- patch 



