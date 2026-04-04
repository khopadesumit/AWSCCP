# ☁️ Static Website Hosting on Amazon S3

This project demonstrates how to host a static website using Amazon S3.

---

## 📌 Overview

Using Amazon S3 from Amazon Web Services (AWS), we can host static websites (HTML, CSS, JS) with high availability and scalability.

---

## 🚀 Steps to Launch Website

### ✅ Step 1: Create S3 Bucket

1. Go to AWS Console → S3

2. Click **Create bucket**

3. Enter:

   * **Bucket name:** `sumit-bucket-assignment2` *(must be globally unique)*
   * **Region:** Mumbai (ap-south-1)

4. Under **Block Public Access**:

   * ❌ Uncheck **Block all public access**
   * ✅ Tick acknowledgment checkbox

5. Click **Create bucket**

---

### ✅ Step 2: Upload Website Files

1. Open the bucket
2. Click **Upload**
3. Add files:

   * `index.html`
   * (Optional: CSS, JS, images)
4. Click **Upload**

---

### ✅ Step 3: Make Files Public (Bucket Policy)

Go to **Permissions → Bucket Policy** and add:

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "PublicRead",
      "Effect": "Allow",
      "Principal": "*",
      "Action": ["s3:GetObject"],
      "Resource": ["arn:aws:s3:::sumit-bucket-assignment2/*"]
    }
  ]
}
```

👉 Replace `sumit-bucket-assignment2` with your bucket name.

---

### ✅ Step 4: Enable Static Website Hosting

1. Go to **Properties**
2. Scroll to **Static website hosting**
3. Click **Edit**
4. Enable hosting
5. Set:

   * **Index document:** `index.html`
6. Click **Save changes**

---

### ✅ Step 5: Access Website

Example endpoint:

```
http://sumit-bucket-assignment2.s3-website-ap-south-1.amazonaws.com
```

Open in your browser to view your live website 🎉

---

## ⚠️ Important Notes

* This setup makes your website **publicly accessible**
* Do not upload sensitive data
* Ensure all assets (CSS, JS, images) are uploaded correctly

---

## 🌍 Future Improvements

* Use CloudFront for CDN
* Add custom domain using Route 53
* Enable HTTPS (SSL)

---

## 📂 Project Structure

```
project-folder/
│── index.html
│── images/
```

---

## 🙌 Conclusion

Amazon S3 provides a simple and cost-effective way to host static websites with minimal setup.

---
