Lab 1B – Terraform Deployment Walkthrough
Objective

In this lab, you will deploy the same AWS infrastructure that you previously created using the AWS Console. The purpose is to demonstrate how Infrastructure as Code (IaC) can provision an entire serverless application consistently and repeatedly.

By the end of this lab, you will have deployed:

Amazon API Gateway (REST API)
AWS Lambda
AWS WAF
CloudWatch Log Groups
DynamoDB
IAM Roles and Policies
Amazon EventBridge
Amazon Bedrock configuration
Prerequisites

Before beginning, verify:

Terraform is installed.
AWS CLI is configured (aws configure).
You have an AWS account with permissions to create Lambda, API Gateway, WAF, CloudWatch, DynamoDB, IAM, EventBridge, and Bedrock resources.
Bedrock model access has been enabled for Anthropic Claude 3 Haiku in your AWS Region. Bedrock model access is enabled separately from Terraform.

Step 1 — Change to the Terraform Directory

cd lessonh_WAF/terraform

Expected files:

    provider.tf
    variables.tf
    apigateway.tf
    waf.tf
    cloudwatch.tf
    dynamodb.tf
    iam.tf
    bedrock.tf
    eventbridge.tf
    lambda_waf.tf
    outputs.tf
    terraform.tfvars

Step 2 — Initialize Terraform

    terraform init


