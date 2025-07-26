# 🛡️Simulating an Insecure S3 Bucket (CloudSec Demo)
**Objective:** Understand how a misconfigured S3 bucket leads to data exposure, and set the stage to fix it.

---

## ✅ Description

 I created an S3 bucket, uploaded a dummy sensitive file, and intentionally misconfigured it to be publicly accessible. The goal is to understand how simple mistakes in cloud setups can expose sensitive data — and how to identify and fix them.

---

## 🔧 Tools Used

- AWS S3
- AWS Console
- Text Editor (`sensitive.txt`)

## 🪣 Bucket Setup

- **Bucket Name:** `ikenna-cloudsec-demo`
- **Region:** `us-east-1` (or your region)
- **Public Access Settings:**
  - Block all public access: ❌ Disabled

### 📄 Public Bucket Policy Applied

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "PublicReadGetObject",
      "Effect": "Allow",
      "Principal": "*",
      "Action": "s3:GetObject",
      "Resource": "arn:aws:s3:::ikenna-cloudsec-demo/*"
    }
  ]
}
```

---

## 🔐 Exposed File

- **File Name:** `sensitive.txt`
- **Content:**
  ```
  This is confidential data. Do not share.
  ```
- **Object URL:** [https://ikenna-cloud.s3.eu-north-1.amazonaws.com/Sensitive.txt)]
- **Publicly Accessible:** ✅ Yes (tested in Incognito mode)

---

## 📸 Screenshots
<img width="1680" height="1050" alt="Screen Shot 2025-07-26 at 6 33 16 PM" src="https://github.com/user-attachments/assets/23a00f32-1ea4-4e97-b6cf-936effd5de18" />
<img width="1680" height="1050" alt="Screen Shot 2025-07-26 at 6 31 54 PM" src="https://github.com/user-attachments/assets/b4074240-3ba8-4d71-9eb0-37fe377f1160" />
<img width="1680" height="1050" alt="Screen Shot 2025-07-26 at 6 30 29 PM" src="https://github.com/user-attachments/assets/7fc8ae64-6f76-4a8b-9856-bb384cc12c31" />
<img width="1680" height="1050" alt="Screen Shot 2025-07-26 at 6 28 39 PM" src="https://github.com/user-attachments/assets/b2c330d9-ec32-4cc5-a641-9eecaae362a5" />

1. Bucket public access settings
2. Bucket policy showing public access
3. `sensitive.txt` opened via incognito mode
4. Upload interface or file view (optional)

---

## 🧠 Lessons Learned

- S3 buckets can be dangerously exposed with a few clicks.
- Public bucket policies override ACL blocks.
- Anyone with the link could access sensitive data if misconfigured.

---


