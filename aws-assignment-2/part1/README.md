# 📘 AWS Assignment 2: EC2 Instance, SSH & Linux Commands

## 👤 Author
**Sumit Khopade**

---

## 🎯 Objective
To launch an EC2 instance, connect using SSH, and execute basic Linux commands.

---

## 🛠️ Services Used
- EC2 (Elastic Compute Cloud)
- IAM (for access)
- SSH (Secure Shell)

---

## 🔹 Part 1: Launch EC2 Instance

### Configuration:
- **Instance Name:** MyFirstEC2  
- **AMI:** Amazon Linux (Free Tier)  
- **Instance Type:** t2.micro  
- **Key Pair:** Created new `.pem` file (Assignment.pem)  
- **Security Group:**  
  - Allowed SSH (Port 22)  
  - Source: My IP only  

---

## 🔹 Part 2: Connect to Instance

### Command Used (PowerShell):

```bash
ssh -i .\Assignment.pem ec2-user@3.89.252.98

[ec2-user@ip-172-31-23-194 ~]$

What happens if you lose your .pem file?
You cannot connect to the EC2 instance via SSH
AWS does not allow re-downloading the key<img width="1920" height="1840" alt="MyFirstEC2" src="https://github.com/user-attachments/assets/d1179cf2-f03a-4717-a415-4485615bb058" />

You need advanced recovery steps (attach volume, update keys, etc.)

## 🔹 Part 3: Linux Commands Executed
pwd
ls
mkdir test-folder
cd test-folder
touch file1.txt
ls


<img width="1920" height="1840" alt="MyFirstEC2" src="https://github.com/user-attachments/assets/da568bfa-5fa1-4c34-8d91-6613e4200bdf" />


<img width="833" height="529" alt="ssh-output png" src="https://github.com/user-attachments/assets/06a613ac-9170-4a70-914d-dff91b83ed2e" />
