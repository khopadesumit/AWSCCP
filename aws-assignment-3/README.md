# 🎂 Birthday Reminder App (AWS Cloud Practitioner Assignment)

## 📌 Overview

The **Birthday Reminder App** is a serverless web application built using AWS services.
It allows users to **add and view birthdays** through a simple UI hosted on S3.

---

## 🏗️ Architecture

This application follows a serverless architecture:

```
Frontend (S3 Static Website)
        ↓
API Gateway (REST API)
        ↓
AWS Lambda (Business Logic)
        ↓
DynamoDB (Database)
```

---

## 🧰 AWS Services Used

* **Amazon S3** – Static website hosting
* **Amazon API Gateway** – REST API endpoints
* **AWS Lambda** – Backend logic
* **Amazon DynamoDB** – Data storage
* **AWS CloudFormation** – Infrastructure provisioning
* **Amazon CloudWatch** – Logs & monitoring

---

## 📁 Project Structure

```
aws-assignment/
│── part2-s3-assignment/
│   ├── birthday.html
│   ├── README.md
│   └── images/
│
│── cloudformation-template.yaml
│── README.md
```

---

## 🚀 Deployment Steps

### 🔹 Step 1: Deploy CloudFormation Stack

1. Go to AWS Console → CloudFormation
2. Click **Create Stack**
3. Upload file:

   ```
   cloudformation-template.yaml
   ```
4. Provide stack name:

   ```
   birthday-reminder-stack
   ```
5. Select environment:

   ```
   dev
   ```
6. Click **Create Stack**

✅ This will create:

* DynamoDB Table
* Lambda Functions
* API Gateway
* IAM Role

---

### 🔹 Step 2: Get API Endpoint

After deployment:

* Go to **Outputs** tab
* Copy:

  ```
  APIEndpoint
  ```

Example:

```
https://abc123.execute-api.us-east-1.amazonaws.com/dev
```

---

### 🔹 Step 3: Deploy Frontend on S3

1. Go to S3 → Create bucket:

   ```
   aws-ccp-assignment
   ```
2. Disable **Block Public Access**
3. Upload:

   * birthday.html
   * images folder (if any)

---

### 🔹 Step 4: Enable Static Website Hosting

* Go to bucket → Properties
* Enable:

  ```
  Static Website Hosting
  ```
* Set:

  ```
  Index document: birthday.html
  ```

---

### 🔹 Step 5: Add Bucket Policy

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "PublicRead",
      "Effect": "Allow",
      "Principal": "*",
      "Action": "s3:GetObject",
      "Resource": "arn:aws:s3:::aws-ccp-assignment/*"
    }
  ]
}
```

---

### 🔹 Step 6: Access Website

Open:

```
http://aws-ccp-assignment.s3-website-us-east-1.amazonaws.com/
```

---

### 🔹 Step 7: Configure API in UI

* Paste API endpoint in UI input field
* Click **Save**
* Start adding birthdays 🎉

---

## 📡 API Endpoints

| Method | Endpoint   | Description      |
| ------ | ---------- | ---------------- |
| GET    | /birthdays | Fetch birthdays  |
| POST   | /birthdays | Add new birthday |

---

## 🗄️ DynamoDB Design

| Attribute  | Type   | Description                  |
| ---------- | ------ | ---------------------------- |
| birthMonth | Number | Partition Key                |
| sortKey    | String | Sort Key (birthDay#personId) |
| name       | String | Person name                  |
| birthDate  | String | Full date                    |
| email      | String | Email                        |
| phone      | String | Phone                        |

---

## 🔐 IAM Role

Lambda uses:

* Managed Policy: `AWSLambdaBasicExecutionRole`
* Inline Policy: DynamoDB access

---

## ⚠️ Important Notes

* Ensure **CORS is enabled** in API Gateway
* Ensure S3 bucket is **public**
* Avoid using `Scan` in production (use Query)

---

## ✅ Features

* Add birthday
* View birthdays
* Monthly filtering
* Serverless architecture
* Fully scalable

---

## 🧠 Learning Outcomes

* Hands-on with serverless architecture
* Infrastructure as Code using CloudFormation
* Integration of multiple AWS services
* API development using API Gateway + Lambda

---

## 📌 Conclusion

This project demonstrates how to build a **fully serverless application** using AWS services with minimal infrastructure management.

---

## 🙌 Author

**Sumit**
AWS Cloud Practitioner Learner
