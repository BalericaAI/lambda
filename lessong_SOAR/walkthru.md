Are you ready?

“We already detect unused tokens. Now we will orchestrate an automated response workflow.”

Now we build:

    Unused Token Detected
    → EventBridge Event
    → Lambda Enrichment
    → SNS Alert
    → Slack Notification
    → Optional Account Disable

AI Incident Summary Generator

Workflow

    Unused Token Detected
    → EventBridge
    → Lambda gathers details
    → Bedrock prompt generated
    → AI creates security summary
    → Send summary to Slack/SNS

Example Input

    {
      "username": "student1",
      "issued_at": "2026-05-19T20:00:00Z",
      "used": false,
      "group": "students",
      "source_ip": "1.2.3.4"
    }

Bedrock Prompt

    You are a SOC analyst assistant.
    
    Analyze this event:
    
    - User authenticated successfully
    - JWT token issued
    - Token never used within 15 minutes
    
    Provide:
    1. Severity
    2. Possible explanations
    3. Recommended analyst actions
    4. Short executive summary

Example Output

    Severity: Low-Medium
    
    Possible Causes:
    - User confusion
    - Automation failure
    - Credential testing activity
    
    Recommended Actions:
    - Verify repeated occurrence
    - Correlate source IP activity
    - Check for abnormal authentication patterns
    
    Executive Summary:
    A Cognito-authenticated user generated a token but did not interact with protected APIs within the expected timeframe.

What is your goal here?

You Demonstrate:

    AI enrichment
    prompt engineering
    event summarization
    SOC augmentation

WITHOUT:

    dangerous automation
    hallucination risks controlling systems

Hey... isn't this why you are in the class in the first place? Besides wanting selfies with Chewbacca?

