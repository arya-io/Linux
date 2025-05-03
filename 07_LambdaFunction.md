# 🌐 **AWS Lambda — Serverless Architecture**

*(Refer image on [Prezi](https://prezi.com/_vhtsx-u9qgq/serverless-architecture-aws-lambda/))*

---

## 🚀 **What is AWS Lambda?**

AWS Lambda is a *compute service* that lets you **run code without managing servers**. It is part of Amazon Web Services (AWS) and follows the **serverless** model — meaning:

* No need to provision or manage servers 🖥️
* Only focus on writing your actual code 👨‍💻
* Pay only for compute time consumed (no charge when code is not running)

✅ **Key features:**

* **Event-driven**: It gets triggered by AWS services (S3, DynamoDB, API Gateway, etc.)
* **Auto Scalable**: Automatically handles scaling
* **Integrated** with AWS ecosystem

---

## 📝 **Simple Lambda Function Code**

```python
def lambda_handler(event, context):
    print(event)
    return 'Hello from Lambda!'
```

* **event**: Contains information from the trigger (e.g., S3 upload event)
* **context**: Provides runtime info (like function name, memory limit)

---

# 🧩 **Example: S3 Bucket Triggering Lambda Function**

We will create a flow where **uploading a file to S3** will automatically **trigger Lambda**.

---

## 🛡️ **Step 1: Create IAM Role (Permissions Setup)**

1. Go to **IAM** ➡️ **Roles** ➡️ *Create Role*
2. **Trusted entity type**: AWS service
3. **Use case**: Lambda
4. **Permission Policies**:

   * ✅ `AmazonS3FullAccess`
   * ✅ `CloudWatchFullAccessV2`
   * ✅ `AWSLambdaBasicExecutionRole`
5. Name the role (e.g., `s3s3s3s3`) ➡️ Create Role

---

## 🐍 **Step 2: Create Lambda Function (Python Example)**

1. Go to **Lambda** ➡️ *Create function* ➡️ *Author from scratch*
2. Runtime: Python
3. Execution role: *Use existing role* ➡️ select `s3s3s3s3`

### 📄 **Lambda Code:**

```python
import json

def lambda_handler(event, context):
    print("Lambda Triggereddddddddddddddddddd")
    return {
        'statusCode': 200,
        'body': json.dumps('Hello from Lambda!')
    }
```

---

## 🔐 **Step 3: Create AWS Access Keys (for AWS CLI)**

* Go to **IAM** ➡️ *Users* ➡️ *Security Credentials* ➡️ *Create Access Key*
* Save **Access Key ID** and **Secret Access Key** (needed for AWS CLI)

---

## 🪣 **Step 4: Create S3 Bucket**

* Go to **S3 service** ➡️ *Create bucket*
* Name it e.g., `bucket_fun_lambda`

---

## 🔗 **Step 5: Connect S3 with Lambda (Add Trigger)**

1. In your **Lambda function** ➡️ *Add Trigger*
2. Choose **S3**
3. Select your bucket: `bucket_fun_lambda`
4. **Event Type**: *All object create events*
5. ✅ *Add* Trigger

---

## 📤 **Step 6: Upload File & Trigger Lambda**

Use AWS CLI to upload file:

```bash
aws s3 cp localfile.txt s3://bucket_fun_lambda
```

This action will **trigger the Lambda function**.

---

## 📊 **Step 7: Check Logs in CloudWatch**

1. Go to **CloudWatch** ➡️ *Log groups*
2. Open log group: `/aws/lambda/<your_lambda_function_name>`
3. ✅ View logs to verify Lambda execution!

---

# 🏁 **Recap Workflow**

1. **S3 Bucket** upload ➡️
2. **Lambda** gets triggered ➡️
3. **Logs** recorded in **CloudWatch**

---
