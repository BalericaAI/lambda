Lab 2 – Centralized Notification Hub for Application Events

Problem to solve
Create a central “notification hub” that listens to app events and dynamically routes messages to email/SMS/Slack based on Aurora-stored user preferences.

Core services

    EventBridge (central bus for UserSignup, PasswordReset, OrderShipped, etc.)
    Lambda (router + per-channel handlers)
    Aurora Serverless (user table + notification_preferences)
    SNS (email/SMS topic, multiple subscriptions)
    SQS (buffer queue for slow notification channels)
    Optionally: Amazon SES / external webhook

Criteria for success

    In Aurora, each user has preferences like: {email: true, sms: false, slack: true}.
    Sending a synthetic event (e.g., UserSignup) onto EventBridge results in:
        Lambda “router” reading preferences from Aurora
        SNS and/or SQS targets being invoked per user preferences
    At least three event types are supported with different routing behavior.
    Demonstrate that adding a new channel requires no changes to existing event producers, just new consumers.
    All infra created via Terraform.
