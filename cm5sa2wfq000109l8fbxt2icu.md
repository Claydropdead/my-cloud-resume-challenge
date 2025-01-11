---
title: "AWS Cloud Resume Challenge: Setting Up CloudFront Distribution"
seoTitle: "Setting Up CloudFront for AWS Resume Challenge"
seoDescription: "Set up an AWS CloudFront distribution to enhance your resume website's performance, security, and scalability with Amazon Web Services"
datePublished: Sat Jan 11 2025 14:25:06 GMT+0000 (Coordinated Universal Time)
cuid: cm5sa2wfq000109l8fbxt2icu
slug: aws-cloud-resume-challenge-setting-up-cloudfront-distribution
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1736605911542/6502a2a3-f109-4514-abe8-62a9e34d1168.png
tags: aws, aws-lambda, aws-cloudfront, acm, aws-certified-solutions-architect-associate, aws-s3, aws-apigateway, aws-certified-cloud-practitioner, aws-dynamodb, aws-route53, aws-ses-send-email

---

## Introduction

In this blog post, I’ll guide you through setting up a CloudFront distribution to serve your resume from an S3 bucket. This is part of the [AWS Cloud Resume Challenge](https://cloudresumechallenge.dev), and it’s an essential step to improve the performance, security, and scalability of your static website. Let’s get started!

## Step 1: Understanding CloudFront

Amazon CloudFront is a content delivery network (CDN) service that securely delivers data, videos, applications, and APIs to customers globally with low latency and high transfer speeds. In our case, CloudFront will cache the content of our S3 bucket in edge locations worldwide, enhancing the speed and reliability of our resume website.

## Step 2: Setting Up a CloudFront Distribution

Follow these steps to set up a CloudFront distribution for your S3 bucket:

1. **Login to AWS Management Console**:
    
    * Navigate to the CloudFront service.
        
2. **Create a New Distribution**:
    
    * Click on "Create Distribution."
        

**Configure the Origin Settings:**

* Set the "Origin Domain Name" to the name of your S3 bucket. The **origin domain** refers to the source from which CloudFront retrieves the original content to cache and serve to end users. It is a key component of a CloudFront distribution and defines where CloudFront should go to fetch content when a user requests it.
    
* Leave "Origin Path" empty.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1736604718891/5baf337f-7773-4f1a-9065-058cd891b8ea.png align="center")
    
* Create an **Origin Access Identity** (OAI) to allow CloudFront to securely access your S3 bucket. An **Origin Access Identity (OAI)** in **Amazon CloudFront** is a special user identity that you can associate with your CloudFront distribution to securely control access to an **Amazon S3 bucket**. It ensures that your S3 content can only be accessed through CloudFront and not directly from the S3 bucket, enhancing security.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1736604753094/e3a62abd-dcd0-4d2a-873e-7bad1e49aec0.png align="center")
    

**Default Cache Behavior Settings:**

* Viewer Protocol Policy: HTTPS only.
    
* Allowed HTTP Methods: GET, HEAD.
    

**Web Application Firewall (WAF):**

* Do not enable security protections. Select this option if your application does not need security protections from AWS WAF.
    

**Default root object - index.html**

**Create Distribution**:

* Leave other settings default.
    
* Click "Create Distribution" and wait for the status to change to "Deployed."
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1736604818383/654bff7b-e359-4f43-aaa9-4e7f3e745669.png align="center")

After creating your CloudFront distribution, you need to update the bucket policy in your S3 bucket. Simply click "Copy Policy," then navigate to the **Permissions** tab of your S3 bucket then edit bucket policy and paste the policy there.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1736604847225/0b2ad936-6466-4d23-9e4e-013f81345d02.png align="center")

## Step 3: Testing the Distribution

Once your distribution is deployed, test it by:

1. Accessing your CloudFront distribution domain. Click on your CloudFront Distribution then find this (e.g., `d1234abcd.cloudfront.net`) Copy it then paste it on your browser.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1736604870663/15aa828c-ccfc-4c9b-a5a3-bb91ca538de8.png align="center")
    
2. Verifying that your resume website loads correctly.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1736604889132/bfe0c438-2773-48f1-8d0b-44bf2ab9958c.png align="center")

Congratulations on successfully deploying your CloudFront distribution! With this setup, your resume website is now faster, more secure, and ready to handle traffic efficiently.

Setting up a CloudFront distribution enhances the performance and security of your static resume website. In the next blog, I’ll cover integrating a custom domain using Route 53 and ACM. Since we are using the CloudFront domain name and we don’t want to rely on that, we’ll ensure your resume website has a professional and personalized domain.

Stay tuned and let me know if you have questions or need further assistance! Thank you.