# 🛡️ Day 1: Simulating an Insecure S3 Bucket (CloudSec Demo)

**Date:** [Replace with your date]  
**Challenge:** 100 Days of Cloud Security  
**Objective:** Understand how a misconfigured S3 bucket leads to data exposure, and set the stage to fix it.

---

## ✅ Description

This is Day 1 of my 100 Days of Cloud Security challenge. I created an S3 bucket, uploaded a dummy sensitive file, and intentionally misconfigured it to be publicly accessible. The goal is to understand how simple mistakes in cloud setups can expose sensitive data — and how to identify and fix them.

---

## 🔧 Tools Used

- AWS S3
- AWS Console
- Text Editor (`sensitive.txt`)

---

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
- **Object URL:** [Paste your Object URL here]
- **Publicly Accessible:** ✅ Yes (tested in Incognito mode)

---

## 📸 Screenshots

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

## 🔜 What’s Next (Day 2 Preview)

- Create an IAM user with scoped access
- Lock down the S3 bucket
- Enforce the principle of least privilege
