iam permissions:
EC2:
-ec2:DescribeInstances = list ad view Ec2 instances
-ec2:StartInstances = start stopped instances
-ec2:StopInstances = stop running instances
-ec2:TerminateInstances = delete instances
-ec2:escribeSecurityGroups - view security groups

S3:
-s3:ListBucket - list objects in a bucket
-s3:GetObject - read/download objects
-s3:PutObject - upload objects
-s3:DeleteObject - remove objects
-s3:GetBuketLocation - check bucket region

IAM:
-iam:CreateUser - create new iam users
-iam:AttachUserPolicy - attach policies to users
-iam:CreateRole - create new roles
-iam:PassRole - allow services to assume roles
-iam:ListRoles - view exisiting roles

CloudFormation:
-cloudformation:CreateStack - create new stacks
-cloudformation:UpdateStack - update existing stacks
-cloudformation:DeleteStack - remove stacks
-cloudformation:DescribeStacks - view stack details

CloudWatch:
-cloudwatch:PutMetricData - publish custom metrics
-cloudwatch:GetMetricStatistics - retrieve metric data
-cloudwatch:DescribeAlarms - view alarms
-cloudwatch:PutDashboard - create dashboards

XML example: less used(json is more often used in AWS)
<Policy>
	<Statement>
		<Effect>Allow</Effect>
		<Action>ec2:DescribeInstances</Action>
		<Action>s3:GetObject</Action>
		<Action>s3.PutObject</Action>
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
