---
title: "Conquering the AWS Cloud Resume Challenge: My Journey to the Cloud"
seoTitle: "AWS Cloud Resume Challenge Success Journey"
seoDescription: "Learn to build a cloud-hosted resume with AWS services, including Route 53, Lambda, and DynamoDB, in the AWS Cloud Resume Challenge"
datePublished: Fri Jan 10 2025 22:24:59 GMT+0000 (Coordinated Universal Time)
cuid: cm5rbs75f000208kwdyw5g33m
slug: conquering-the-aws-cloud-resume-challenge-my-journey-to-the-cloud
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1736547694324/e665cdfe-1e82-411d-ae4e-a2a9a54dc4d8.jpeg
tags: aws, cloudfront, aws-lambda, api-gateway, acm, aws-certified-solutions-architect-associate, route53, cloud-resume-challenge, aws-cloud-practitioner, aws-dynamodb, s3-static-website-hosting, aws-cloud-resume-challenge

---

# **Introduction**

The **AWS Cloud Resume Challenge** is a popular project designed to showcase and enhance your cloud computing skills by building a cloud-hosted, interactive resume. It involves using a wide range of AWS services to design, deploy, and manage a professional resume that demonstrates your technical expertise. By completing this challenge, you gain practical experience with hosting, securing, automating, and monitoring cloud-based solutions.

In this post, I’ll share how I leveraged various AWS services to build my cloud resume. This project highlights my ability to design and deploy scalable, secure, and automated solutions in AWS.

# **AWS Services Used**

* **AWS Route 53**: Domain registration and DNS management.
    
* **AWS CloudFront**: Content delivery and HTTPS support.
    
* **AWS Certificate Manager (ACM)**: SSL/TLS certificate for HTTPS.
    
* **AWS S3**: Static website hosting.
    
* **AWS API Gateway**: REST API for serverless backend.
    
* **AWS Lambda**: Serverless function for business logic.
    
* **AWS SNS (Simple Notification Service)**: Notifications for deployment updates.
    
* **AWS DynamoDB**: NoSQL database for storing visitor counts.
    
* **AWS CloudFormation**: Infrastructure-as-Code (IaC) to automate resource provisioning.
    

# **My Design Architecture**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1736304172997/dce65051-f322-4bc3-8958-48dd33d338f6.png align="center")

For the design of my AWS cloud resume, I utilized [Lucidchart](https://lucid.app/lucidchart/c310596e-4dc8-4fbf-9bef-bcd64769c15c/edit?viewport_loc=-864%2C-1697%2C3852%2C1959%2C0_0&invitationId=inv_60e8f79d-a2ed-48c2-918e-1bc9cb5feaa5) to gain a clear overview of the workflow for my project. This tool allowed me to visually map out the structure, processes, and key components involved in my cloud architecture.

### **Workflow**

#### **1\. User Accesses the Website**

* **Step 1.1**:  
    The user enters your domain in a web browser.
    
* **Step 1.2**:  
    Route 53 resolves the domain to the CloudFront distribution.
    

#### **2\. CloudFront Serves the Static Website Content**

* **Step 2.1**:  
    CloudFront checks if the requested content is cached.
    
* **Step 2.2**:  
    If cached, CloudFront serves the content directly to the user.
    
* **Step 2.3**:  
    If not cached, CloudFront fetches the content from the S3 bucket, caches it, and then serves it to the user.
    

#### **3\. User Triggers an Action (e.g., Visitor Counter or Form Submission)**

* **Step 3.1**:  
    The user interacts with the website, triggering an API call (e.g., clicking to update the visitor counter).
    
* **Step 3.2**:  
    The request is sent to API Gateway, which serves as the entry point for the backend.
    

#### **4\. API Gateway Routes the Request to Lambda**

* **Step 4.1**:  
    API Gateway receives the request and forwards it to the appropriate Lambda function.
    
* **Step 4.2**:  
    Lambda executes the necessary business logic (e.g., retrieving and incrementing the visitor count).
    

#### **5\. Lambda Interacts with DynamoDB**

* **Step 5.1**:  
    Lambda queries DynamoDB to retrieve the current visitor count.
    
* **Step 5.2**:  
    Lambda increments the count and updates DynamoDB with the new value.
    

#### **6\. (Optional) Email Notifications via SES**

* **Step 6.1**:  
    If configured, Lambda triggers Amazon SES to send an email notification (e.g., for deployment updates or form submissions).
    

#### **7\. Response to User**

* **Step 7.1**:  
    Lambda sends the updated visitor count (or another response) back to API Gateway.
    
* **Step 7.2**:  
    API Gateway sends the response to the user’s browser, updating the website dynamically.
    

# **AWS Cloud Resume Challenge Tutorial**

* **Create a Static Website (HTML/CSS)**:
    
    * I created the template for your resume using HTML and CSS, which is the first step.
        
* **Set Up Static Website on AWS S3**:
    
    * Then I uploaded the static website (HTML and CSS) to an S3 bucket.
        
    * I also blocked public access to your S3 bucket, which is a good security practice when using CloudFront.
        
* **Set Up CloudFront Distribution**:
    
    * I used **CloudFront** to distribute my static website. By doing this, CloudFront caches and serves your website content globally, improving performance.
        
* **Custom Domain Setup**:
    
    * I used **Route 53** for domain name management. I created a **Hosted Zone** in **Route 53** and added a **DNS record** to point to my CloudFront distribution
        
    * I purchased a domain name from **Hostinger** and linked it to your Route 53 configuration.
        
* **SSL Certificate via ACM**:
    
    * I requested an SSL certificate from **AWS Certificate Manager (ACM)** to enable **HTTPS** for secure communication between users and your website.
        
    * I associated this SSL certificate with your CloudFront distribution to serve your website over HTTPS.
        
* **DNS Configuration**:
    
    * I configured Route 53 DNS settings to point to your CloudFront distribution, ensuring that visitors to your custom domain (e.g., [`www.your-domain.com`](http://www.your-domain.com)) are routed to CloudFront.
        

### **Adding Dynamic Features for Visitor Counter (API Gateway, Lambda, DynamoDB)**:

**Visitor Counter Setup**

* **API Gateway**: I created an **API** using **Amazon API Gateway** to handle requests related to the visitor counter (e.g., every time a user visits your website, the counter is incremented).
    
* **AWS Lambda**: I set up an **AWS Lambda function** that gets triggered by **API Gateway** every time a user visits the website. The Lambda function will increment the visitor count in **DynamoDB**.
    
* **Amazon DynamoDB**: I used **DynamoDB** to store the visitor count. Each time the Lambda function is triggered, it updates the visitor count in DynamoDB.
    
* **Display Visitor Count**: I also modify my website to display the current visitor count dynamically by making an API request to the API Gateway endpoint, which returns the current count stored in DynamoDB.
    

**Email Notification with SES**

* You configured **Amazon SES** to send an email notification each time the visitor counter is updated (e.g., after every set number of visits, or when a milestone number of visitors is reached).
    
* The **Lambda function** that updates the visitor counter can also send an email via SES, informing you (or any recipient) about the updated visitor count or other milestones.
    
* **SES Email Template**: You can create an email template in **Amazon SES** or dynamically generate the content inside the Lambda function based on the visitor count.
    

### **How CloudFormation Fits in**:

1. **CloudFormation Template**: I created a CloudFormation template to define all the resources required for the setup:
    
    * **S3 bucket** for the static website.
        
    * **CloudFront distribution** for content delivery.
        
    * **API Gateway** for the visitor counter API.
        
    * **Lambda function** to handle business logic and database updates.
        
    * **DynamoDB** to store the visitor count.
        
    * **SES** for email notifications.
        
2. **Stack Deployment**: Using CloudFormation, I deployed the entire stack at once, automating the setup of all AWS services, eliminating the need for manual configuration.
    

# **Final Thoughts:**

Completing the AWS Cloud Resume Challenge has been an incredibly rewarding experience! By leveraging powerful AWS services like **S3**, **CloudFront**, **API Gateway**, **Lambda**, **DynamoDB**, and **SES**, I was able to create a dynamic and secure static website. Using **CloudFormation** to automate the entire process added an extra layer of efficiency and scalability to my solution.

In my upcoming blog post, I’ll dive into every detail of the setup, including the code, configurations, and challenges I faced along the way. Whether you’re just starting out with AWS or looking to enhance your skills, this tutorial will guide you through the process step-by-step.

Stay tuned and get ready to build your own cloud-powered resume website!