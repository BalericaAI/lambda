Lab 8 – Document Intake & Classification with Bedrock + Aurora

Problem to solve
Build a serverless pipeline where users upload documents, an LLM classifies them (e.g., invoice, contract, resume), and results are stored and searchable.

Core services

    S3 (document uploads)
    EventBridge (S3 PutObject event → bus, or S3 trigger via Lambda + EventBridge)
    Lambda (classification worker using Amazon Bedrock or other LLM API)
    Aurora (documents table with metadata and classification)
    SNS (notify when certain class appears, e.g., “critical contract”)
    SQS (buffer queue between S3 events and classifier Lambda)

Criteria for success

    Dropping a file into S3 triggers an event into EventBridge and then into SQS.
    Classifier Lambda pulls from SQS, sends document text to Bedrock/LLM, and writes result in Aurora: {doc_id, s3_key, class, confidence, processed_at}.
    SNS alerts when a doc is classified as a special type (e.g., “legal_contract”).
    A small GET /documents?class=... endpoint (Lambda + API Gateway) queries Aurora and returns results.
    Full deployment via Terraform.
