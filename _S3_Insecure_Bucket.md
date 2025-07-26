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
<img width="1524" height="896" alt="Screen Shot 2025-07-26 at 10 45 42 PM" src="https://github.com/user-attachments/assets/1f721c5c-8cf3-41f0-9e10-8115da0ac739" />
<img width="1526" height="898" alt="Screen Shot 2025-07-26 at 10 45 23 PM" src="https://github.com/user-attachments/assets/c64e0370-0a22-46c7-9565-e8038d52b5dd" />
<img width="1522" height="895" alt="Screen Shot 2025-07-26 at 10 45 09 PM" src="https://github.com/user-attachments/assets/f1f7734a-bbe3-449a-a7de-af10a1238643" />
<img width="1524" height="895" alt="Screen Shot 2025-07-26 at 10 44 45 PM" src="https://github.com/user-attachments/assets/6519c5b5-ebda-4cc4-b1b4-ae3406fe5ef7" />


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


