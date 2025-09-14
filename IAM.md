What is IAM in AWS? 
IAM stands for Identity and Access Management.
It is a secure way to control who can access your AWS resources and what actions they can perform.

🔐 What Does IAM Do?
Think of IAM as a security guard in a company:

Users are employees.

Policies are rules that say what each employee can and cannot do.

Roles are temporary job assignments.

Groups are teams with similar access levels.

📦 Real-Life Example (Simple):
Imagine you're building a small app hosted on AWS. You have:

An S3 bucket to store files (e.g., images, PDFs).

An EC2 instance running your app.

A friend helping you upload files.

Without IAM:
Everyone would have full access to everything = ❌ Not secure!

With IAM:
You can create specific users and roles with limited access.

✅ Example Setup:
Entity	Purpose	IAM Configuration
You (admin)	Full control of AWS account	Create an IAM user with AdminAccess policy.
Friend (developer)	Only uploads files to S3	Create IAM user with AmazonS3PutObject policy for that bucket only.
App on EC2	Needs to read images from S3	Assign an IAM role to EC2 with AmazonS3ReadOnlyAccess policy.

🔧 Visual Representation:
plaintext
Copy
Edit
IAM
├── Users
│   ├── You (Admin) → Full access
│   └── Friend (Uploader) → Only S3 upload
│
├── Roles
│   └── EC2 Role → Read-only access to S3
│
└── Policies
    ├── AdministratorAccess
    ├── AmazonS3ReadOnlyAccess
    └── Custom: Allow only "PutObject" in S3 bucket
