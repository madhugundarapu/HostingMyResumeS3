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

### 3. Test S3 Website Hosting

* Opened **Static Website URL** from S3 properties.

  `http://madhugresumedemo.s3-website-us-east-1.amazonaws.com`
I saw my resume page displayed successfully.
---

### 4. Create CloudFront Distribution

1. Go to **CloudFront Console → Create Distribution**.
2. Chooses **Origin Domain**: my S3 static website endpoint.
3. Set:

   * Viewer Protocol Policy: **Redirect HTTP to HTTPS**
   * Allowed HTTP Methods: **GET, HEAD**
4. Click **Create Distribution**.
5. Wait until the status shows **Deployed**.


### 5. Test CloudFront Distribution

Once deployed * Open the **CloudFront domain name**,
  `https://dxxxxx.cloudfront.net/MadhuGResume.html`

* My resume file will now load globally through the CloudFront CDN - faster and more secure!


## Common Issues

| Error               | Reason                       | Fix                                                              |
| ------------------- | ---------------------------- | ---------------------------------------------------------------- |
| 504 Gateway Timeout | CloudFront couldn’t reach S3 | Ensure S3 endpoint is **static website endpoint** not bucket URL |
| AccessDenied        | Missing bucket policy        | Add public read permission in bucket policy                      |
| File Not Found      | Wrong path or filename       | Check `MadhuGResume.html` case sensitivity                       |

---

## Project Files

| File                                                     | Description              |
| -------------------------------------------------------- | ------------------------ |
| `MadhuGResume.html`                                      | Static HTML Resume Page  |
| `A_digital_diagram_in_the_image_illustrates_the_arc.png` | Architecture Diagram     |
| `README.md`                                              | Documentation for GitHub |

---

## 🧠 Learning Outcomes

* Hosting static websites using AWS S3.
* Setting up CloudFront CDN.
* Understanding static vs dynamic content hosting.
* Diagnosing CloudFront-S3 connectivity errors.


**Author:** Madhu Gundarapu
**Region:** `us-east-1 (N.verginia)`
**Project:** AWS S3 + CloudFront Resume Hosting
