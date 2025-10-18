
## 🧰 **Services Used**
- **Amazon S3** – Object storage to host the resume.
- **Amazon CloudFront** – Content Delivery Network (CDN) for faster global access.
- **Amazon Route 53 (Optional)** – Domain management.
- **AWS IAM** – For access control and permissions.

---

## ⚙️ **Steps to Reproduce**

### 1️⃣ Create an S3 Bucket
1. Log in to [AWS Console](https://aws.amazon.com/console/).
2. Open **S3 Service → Create bucket**.
3. Use a **unique name** (e.g., `madhugresumedemo`).
4. Select a region (e.g., `us-east-1`).
5. Keep default settings or enable **versioning**.

### 2️⃣ Upload the Resume File
- Uploaded my file `MadhuG_Resume.html` into the bucket.

### 3️⃣ Enable Static Website Hosting
1. Go to **Properties → Static website hosting**.
2. Enable it and set **MadhuG_Resume.html** as the default root object.
3. Note down the **S3 website endpoint** (e.g., `madhugresmedemo.s3-website-us-east-1.amazonaws.com`).

### 4️⃣ Set Public Permissions
Use the following **bucket policy** to allow read access:

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "PublicReadGetObject",
      "Effect": "Allow",
      "Principal": "*",
      "Action": "s3:GetObject",
      "Resource": "arn:aws:s3:::madhugresumedeme/*"
    }
  ]
}
