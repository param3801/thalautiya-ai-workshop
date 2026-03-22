# Day 1 — Foundation: Lambda + Amazon Bedrock

##  Goal
Build an AWS Lambda function that calls Amazon Bedrock and returns an AI response.

##  What You Will Build
By the end of Day 1, you will have a Lambda function that:
- Accepts a user message as input
- Sends it to Claude AI via Amazon Bedrock
- Returns the AI's response

---

## 🛠️ Step-by-Step Setup

### Step 1 — Enable Bedrock Model Access
1. Go to **AWS Console** → Search **"Bedrock"**
2. Left sidebar → **"Model access"**
3. Click **"Manage model access"**
4. Enable:
   -  Anthropic Claude 3 Haiku
   -  Anthropic Claude Sonnet 4
   -  Amazon Titan Text
5. Click **"Save changes"** — wait 2-3 minutes

---

### Step 2 — Create IAM Role
1. AWS Console → **IAM** → **Roles** → **"Create role"**
2. Trusted entity: `AWS service` → `Lambda`
3. Add these permissions:
   - `AmazonBedrockFullAccess`
   - `AWSLambdaFullAccess`
4. Role name: `ai-lambda-role`
5. Click **"Create role"**

---

### Step 3 — Create Lambda Function
1. AWS Console → **Lambda** → **"Create function"**
2. Settings:
   - Function name: `ai-assistant`
   - Runtime: `Python 3.12`
   - Architecture: `x86_64`
   - Execution role: `ai-lambda-role`
3. Click **"Create function"**

---

### Step 4 — Add the Code
1. Lambda → **Code** tab
2. Delete existing code
3. Paste the code from `lambda_function.py`
4. Click **"Deploy"**

---

### Step 5 — Increase Timeout
1. Lambda → **Configuration** → **General configuration** → **Edit**
2. Timeout: set to `30 seconds`
3. Click **"Save"**

---

### Step 6 — Test
1. Lambda → **Test** tab
2. Create new test event with this JSON:
```json
{
  "message": "Hello! What is AWS?"
}
```
3. Click **"Test"** — you should see an AI response! 

---

##  Files
- `lambda_function.py` — Lambda function code

---

##  Key Concepts Learned
- What is Amazon Bedrock
- How AWS Lambda works
- How to call an AI model from Lambda
- IAM roles and permissions
