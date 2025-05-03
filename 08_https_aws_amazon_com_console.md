# 🚀 EC2 Instance Launch & Access Guide

---

## 🌐 Step 1: Sign In to AWS Console

1. Go to: [AWS Console](https://aws.amazon.com/console/)
2. **Sign in** with your AWS account.
3. Select **Region**: `Mumbai (ap-south-1)`
   *(Always double-check your region to avoid launching in a different area.)*

---

## 🖥️ Step 2: Launch EC2 Instance (Ubuntu Server)

### 🔍 Find EC2 Service:

1. Use the **Search Bar** → type `ec2`
2. Click on **EC2** → it takes you to the EC2 **Dashboard**.

### 🚀 Launch EC2:

1. Click on **Instances** (left menu).
2. Click **Launch Instances** (orange button).

### 📝 Configure Basic Details:

* **Name**: `edbda public ec2`
* **Application & OS**: Choose **Ubuntu**
* **Amazon Machine Image (AMI)**: Select **Free tier eligible**
* **Architecture**: 64-bit (x86)

### 🔐 Key Pair (Login):

1. Click **Create new key pair**.
2. Provide:

   * **Key pair name**: `kalua`
   * **Key pair type**: RSA
   * **Private key file format**: `.pem`
3. Click **Create key pair**.
   *(This downloads the `kalua.pem` file — keep it safe!)*

### 🌐 Network Settings:

1. Click **Edit**.
2. **Auto-assign public IP**: Enable ✅

### 🔒 Security Group:

1. Security group name: *(use default or name it)*
2. Click **Add security group rule**:

   * **Type**: HTTP
   * **Source Type**: Anywhere (0.0.0.0/0) 🌐
     *(This allows web traffic to your instance.)*

### ✅ Launch:

Click **Launch Instance**.

---

## 👇 Step 3: Connect to Your EC2 Instance

### 🔙 Go Back:

* Click **EC2** (top-left) to return to the EC2 Dashboard.

### 🌐 Access via SSH:

1. Select your running **Instance**.
2. Click **Connect** (top menu).
3. Choose **SSH Client** tab.

### 🖥️ Run these commands in your terminal:

```bash
chmod 400 kalua.pem  # Secure the key
ssh -i kalua.pem ubuntu@<Public-IP>  # Example:
ssh -i kalua.pem ubuntu@3.111.47.244
```

*(Use your **Instance's Public IP Address** in place of `<Public-IP>`.)*

### 🚀 Run a Web Server:

```bash
sudo su  # Switch to root user
docker run -d --name "lol" -p 80:80 httpd
```

✅ Now, open your Instance's **Public IP** in a browser → you should see the **Apache HTTP Server page!**

---

## 🗑️ Step 4: Delete (Terminate) EC2 Instance

1. Select your Instance.
2. Click **Actions** (top-right corner).
3. Choose **Terminate Instance** (this deletes it).

### 🔄 To Check Status:

* Click the **Refresh icon** (top bar) until status shows **terminated**.

---

# 📦 S3 Bucket Creation & File Upload Guide

---

## 🪣 Step 1: Create an S3 Bucket

1. Search **S3** in the top search bar.
2. Click on **Create Bucket**.

### 📝 Configure:

* **Bucket Name**: `demooops`
  *(Bucket name must be unique globally.)*

* **Object Ownership**: Choose **ACLs disabled (recommended)**.

### 🔒 Public Access Settings:

1. **Uncheck** → Block all public access ❌

2. Check **I acknowledge** ✅

3. Click **Create Bucket**.

---

## ⬆️ Step 2: Upload Files to Bucket

1. Click on your **Bucket Name** (`demooops`).
2. Click **Upload** → then **Add files**.

   * Select a **.jpg file** (or any file you want to upload).
3. Click **Upload**.

✅ Once done, click **Close** (top-right) to go back to the Bucket page.

---

## 🗑️ Step 3: Delete S3 Bucket (Cleanup)

### ⚠️ Important:

* **Buckets must be empty before deletion!**

### Steps:

1. Go to your Bucket.
2. **Empty** it (select files → delete).
3. After it’s empty, select the Bucket → click **Delete**.

✅ Cleanup completed!

---

## ⚡ Quick Recap

* **EC2** = Virtual server 🖥️
* **Key Pair** = Used to securely connect via SSH 🔐
* **S3** = AWS storage bucket for files 📦
* **Terminate EC2** & **Delete S3 Bucket** to avoid charges 🗑️

---
