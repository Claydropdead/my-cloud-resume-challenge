---
title: "AWS Cloud Resume Challenge: Uploading My Resume Template to S3 Bucket"
seoTitle: "AWS Cloud Resume Challenge: S3 Bucket Upload"
seoDescription: "Learn how to upload a resume template to an Amazon S3 bucket as part of the AWS Cloud Resume Challenge"
datePublished: Sat Jan 11 2025 09:53:32 GMT+0000 (Coordinated Universal Time)
cuid: cm5s0dohf000309jgad1acagv
slug: aws-cloud-resume-challenge-uploading-my-resume-template-to-s3-bucket
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1736606047061/660bbb9a-9ef5-48e5-afdd-7e542a64ee9c.jpeg
tags: aws, aws-lambda, aws-cloudfront, aws-certified-solutions-architect-associate, aws-s3, aws-apigateway, aws-certified-cloud-practitioner, aws-dynamodb, aws-route53, aws-acm

---

### Introduction

In this blog post, I’ll Walk you through how I uploaded my resume template to an Amazon S3 bucket as part of the [AWS Cloud Resume Challenge](https://pinesprojects.cloud/conquering-the-aws-cloud-resume-challenge-my-journey-to-the-cloud). This challenge is a great way to learn core AWS services and build a serverless application that showcases your resume. Let's dive in!

## Step 1: Preparing the Resume Template

First, you need a resume template that will be used for uploading to the S3 bucket. You can create a simple HTML resume template or use an existing one.

You can use my [GitHub repository](https://github.com/Claydropdead/my-cloud-resume-challenge.git) or create your own template.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1736588760363/4a8c4575-e7a5-4dbf-93c8-3c62b982693f.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1736588814723/8187bdc4-27fd-48c1-bdb3-f891a4639456.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1736588858774/4e4581f4-5169-436f-9e5d-f770b574fae8.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1736588889983/a3731d84-4f4e-452a-afc8-1849e8536aa4.png align="center")

## Step 2: Setting Up the S3 Bucket

The next step is to create an S3 bucket to store your static website files (resume template). Here’s how I did it:

1. **Login to the AWS Management Console**: Navigate to the S3 service.
    
2. **Create a Bucket**:
    
    * Click on “Create Bucket.”
        
    * Specify a unique bucket name (e.g., `my-resume-bucket`).
        
    * Choose the appropriate AWS Region.
        
    * Ensure that ACLs are disabled, as we will use CloudFront to access the S3 bucket.
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1736587884317/146a8950-2883-44b7-a152-f21e9c31f022.png align="center")
        
3. **Configure Bucket Settings**:
    
    * Check the "Block Public Access" settings to confirm they are enabled.
        
    * Leave versioning and encryption settings as default for now.
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1736587913853/e6864f3b-6f20-48a8-9fee-4e55057c8877.png align="center")
        
4. **Upload Resume Template**:
    
    * Once the bucket is created, click on its name to open it.
        
    * Click “Upload” and add your resume template files (HTML, CSS, images, etc.).
        
    * Ensure the file names match the links in your resume.
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1736588027321/9c888089-776b-4255-a9c4-3c00c05e4ef0.png align="center")
        

# **Conclusion**

That's it! On the next blog, we will be using CloudFront to access the S3 bucket objects, and we will configure the S3 bucket policy to allow CloudFront to access those objects.

Uploading my resume template to an S3 bucket and configuring it for static website hosting was a rewarding experience. It’s a key step in the AWS Cloud Resume Challenge and demonstrates my ability to work with foundational AWS services.

Let me know if you’d like detailed instructions on any specific step!