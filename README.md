
# 🌐 AWS CloudFront + S3 Static Website Hosting Project

This project demonstrates how to **host a static website on AWS S3** and **deliver it globally using AWS CloudFront CDN** for better performance and availability.  
The demo uses a sample file named **`MadhuGResume.html`** hosted in an **S3 bucket** called **`madhugresumedemo`** in the **us-east-1 (N.verginia)** region.


## 🚀 Project Overview

The goal of this project is to:
- Upload and host a static HTML file (`MadhuGResume.html`) on S3.
- Configure the bucket for **static website hosting**.
- Create a **CloudFront distribution** to deliver content securely and faster.
- Access the website through the CloudFront domain name.


## 🏗️ Architecture

![Architecture Diagram](A_digital_diagram_in_the_image_illustrates_the_arc.png)

### Components:
- **Amazon S3** – Stores the static website files.
- **Amazon CloudFront** – Acts as CDN to distribute content globally.
- **User Browser** – Accesses the CloudFront URL to load the resume page.
- **(Optional) Route 53** – For custom domain routing.


## 🧱 Steps to Recreate

### 1️⃣ Create S3 Bucket
1. Go to AWS Console → S3.
2. Create a new bucket: `madhugresumedemo`.
3. Choose **Region**: `us-east-1 (N.verginia)`.
4. Uncheck “Block all public access”.
5. Enable **Static Website Hosting** under “Properties”.
6. Upload your file: `MadhuGResume.html`.


### 2️⃣ Set Bucket Policy
Allow public read access for website content:

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
````

---

### 3️⃣ Test S3 Website

* Open **Static Website URL** from S3 properties.
* Example:
  `http://madhugresumedemo.s3-website-us-east-1.amazonaws.com`

---

### 4️⃣ Create CloudFront Distribution

1. Go to **CloudFront Console → Create Distribution**.
2. Choose **Origin Domain**: your S3 static website endpoint.
3. Set:

   * Viewer Protocol Policy: **Redirect HTTP to HTTPS**
   * Allowed HTTP Methods: **GET, HEAD**
4. Click **Create Distribution**.
5. Wait until status shows **Deployed**.


### 5️⃣ Test CloudFront Distribution

* Open the **CloudFront domain name**, e.g.
  `https://dxxxxx.cloudfront.net/MadhuGResume.html`

* Your website should now load from the CDN edge location!

---

## 🧩 Common Issues

| Error               | Reason                       | Fix                                                              |
| ------------------- | ---------------------------- | ---------------------------------------------------------------- |
| 504 Gateway Timeout | CloudFront couldn’t reach S3 | Ensure S3 endpoint is **static website endpoint** not bucket URL |
| AccessDenied        | Missing bucket policy        | Add public read permission in bucket policy                      |
| File Not Found      | Wrong path or filename       | Check `MadhuGResume.html` case sensitivity                       |

---

## 📹 Live Demo Script (for Recording)

1. Introduce yourself and project purpose.
2. Show the S3 bucket (`madhugresumedemo`) in **ap-south-1**.
3. Open `MadhuGResume.html` file in browser using S3 static URL.
4. Create and configure CloudFront distribution.
5. Demonstrate accessing via CloudFront domain.
6. End with explaining 504 issue and fix (correct S3 endpoint).

---

## 📁 Project Files

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

