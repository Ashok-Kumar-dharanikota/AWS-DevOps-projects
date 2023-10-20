# Static Website Hosting with AWS S3 + CloudFront

![Banner](https://cdn.hashnode.com/res/hashnode/image/upload/v1696775549603/b2779620-8849-4fdd-ac12-bc8820758afb.png?w=1600&h=840&fit=crop&crop=entropy&auto=compress,format&format=webp)

## Table of Contents

- [Overview](#overview)
- [Prerequisites](#prerequisites)
- [Setting Up S3 for Static Hosting](#setting-up-s3-for-static-hosting)
- [Setting Up CloudFront for Content Delivery](#setting-up-cloudfront-for-content-delivery)
- [Deploying the Website](#deploying-the-website)
- [References](#references)

## Overview

Hosting a static website means serving only HTML, CSS, and JS without the need for server-side processing. AWS offers a highly scalable and reliable infrastructure for hosting static websites. With S3 and CloudFront, we can store our website files and serve them to users with high availability and low latency. 

## Prerequisites

- AWS account
- AWS CLI
- Domain name (optional)
- Website files

## Setting Up S3 for Static Hosting

### 1. Create an S3 Bucket:

Log in to AWS Console: Navigate to S3 and create a new bucket with a name of your choice.

Bucket Configuration:

Set the bucket to public (note the security concerns when doing so).
Enable Static website hosting under the properties tab.
Provide index.html for both Index and Error documents (or as per your structure).
Upload Website Files: Using AWS Console or AWS CLI, upload your static website files to the bucket.

## Setting Up CloudFront for Content Delivery

Navigate to the CloudFront service in the AWS Console.
Click on Create Distribution.
Choose Web Distribution.
For the Origin Domain Name, select the S3 bucket you created earlier.
If using a custom domain, configure Alternate Domain Names (CNAMEs).
Set the Default Root Object to index.html.
Complete the distribution creation and wait for it to be deployed.

## Deploying the Website

Your website is now accessible via the CloudFront Distribution URL or through your custom domain if configured.

## Benefits of This Setup

Highly Available: AWS ensures that your content is reliably accessible with 99.99% uptime.
Low Latency: With CloudFront, your content is delivered from the nearest edge location.
Scalable: Automatically scales to cater to the number of visitors.
Secure: With AWS, you can configure SSL/TLS for secure content delivery.


## References

### Check out my Blog to learn more

https://ashok405.hashnode.dev/static-website-hosting-on-aws-s3-cloudfront

1. **Amazon S3 - Hosting a Static Website**: [AWS Official Documentation](https://docs.aws.amazon.com/AmazonS3/latest/userguide/WebsiteHosting.html)
2. **Amazon CloudFront - Developer Guide**: [AWS CloudFront User Guide](https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/Introduction.html)
3. **AWS CLI Command Reference**: [AWS CLI Documentation](https://docs.aws.amazon.com/cli/latest/index.html)
4. **Amazon Route 53 - Configuring DNS for your Web Distribution**: [AWS Route 53 Guide](https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/routing-to-cloudfront-distribution.html)
5. **Best Practices for Hosting Static Websites**: [AWS Whitepapers](https://aws.amazon.com/whitepapers/)

