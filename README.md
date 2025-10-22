# AWS CloudFront + S3 Static Website Hosting Project

This project demonstrates how I hosted my **personal resume HTML file** on **AWS S3** and distributed it globally using **AWS CloudFront CDN** for faster delivery and high availability.  
The demo file used is **`MadhuGResume.html`** hosted inside an **S3 bucket** named **`madhugresumedemo`** in the **us-east-1 (N.verginia)** region.


## Project Overview

The main goal of this project is to:
- Host a static website (my resume) on **Amazon S3**
- Configure the bucket for **static website hosting**.
- Create a **CloudFront distribution** to deliver content securely and faster.
- Access the hosted file securely through the **CloudFront domain**.


### Components:
- **Amazon S3** – To Store and host the static website files.
- **Amazon CloudFront** – Acts as CDN to distribute content globally.
- **User Browser** – Accesses the CloudFront URL to load the resume page.
- **(Optional) Route 53** – For custom domain routing.


## Steps to Recreate

### 1. Create S3 Bucket
1. Go to AWS Console → S3.
2. Created a new bucket: `madhugresumedemo`.
3. Selected **Region**: `us-east-1 (N.verginia)`.
4. Unchecked “Block all public access”.
5. Enabled **Static Website Hosting** under “Properties”.
6. Uploaded my file: `MadhuGResume.html`.


### 2. Set Bucket Policy
To allow public read access for my hosted website content:

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "PublicReadGetObject",
      "Effect": "Allow",
      "Principal": "*",
      "Action": "s3:GetObject",
      "Resource": "arn:aws:s3:::madhugresumedemo/*"
    }
  ]
}

