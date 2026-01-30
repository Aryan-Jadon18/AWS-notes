# IAM Permissions Guide

This document outlines commonly used IAM permissions for AWS services.  
It includes examples in both XML and JSON formats, along with best practices for scoping permissions.

---

## EC2 Permissions
- `ec2:DescribeInstances` – List and view EC2 instances  
- `ec2:StartInstances` – Start stopped instances  
- `ec2:StopInstances` – Stop running instances  
- `ec2:TerminateInstances` – Delete instances  
- `ec2:DescribeSecurityGroups` – View security groups  

---

## S3 Permissions
- `s3:ListBucket` – List objects in a bucket  
- `s3:GetObject` – Read/download objects  
- `s3:PutObject` – Upload objects  
- `s3:DeleteObject` – Remove objects  
- `s3:GetBucketLocation` – Check bucket region  

---

## IAM Permissions
- `iam:CreateUser` – Create new IAM users  
- `iam:AttachUserPolicy` – Attach policies to users  
- `iam:CreateRole` – Create new roles  
- `iam:PassRole` – Allow services to assume roles  
- `iam:ListRoles` – View existing roles  

---

## CloudFormation Permissions
- `cloudformation:CreateStack` – Create new stacks  
- `cloudformation:UpdateStack` – Update existing stacks  
- `cloudformation:DeleteStack` – Remove stacks  
- `cloudformation:DescribeStacks` – View stack details  

---

## CloudWatch Permissions
- `cloudwatch:PutMetricData` – Publish custom metrics  
- `cloudwatch:GetMetricStatistics` – Retrieve metric data  
- `cloudwatch:DescribeAlarms` – View alarms  
- `cloudwatch:PutDashboard` – Create dashboards  

---

## Policy Examples

### XML Example (less common, JSON preferred)
```xml
<Policy>
  <Statement>
    <Effect>Allow</Effect>
    <Action>ec2:DescribeInstances</Action>
    <Action>s3:GetObject</Action>
    <Action>s3:PutObject</Action>
    <Resource>*</Resource>
  </Statement>
</Policy>

JSON:
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Action": [
        "ec2:DescribeInstances",
        "ec2:StartInstances",
        "ec2:StopInstances",
        "s3:ListBucket",
        "s3:GetObject",
        "s3:PutObject",
        "cloudformation:CreateStack",
        "cloudformation:UpdateStack",
        "cloudformation:DescribeStacks",
        "cloudwatch:PutMetricData",
        "cloudwatch:GetMetricStatistics",
        "cloudwatch:DescribeAlarms",
        "iam:ListRoles",
        "iam:PassRole"
      ],
      "Resource": "*"
    }
  ]
}

this is a general-purpose developer policy.
-For S3, restrict to "arn:aws:s3:::my-bucket/*".
-For EC2, restrict to specific instance IDs
-For IAM, be careful - iam:PassRole is powerful and should be limited to trusted roles.
```
