Cognito ClickOps Lab — User Authentication (No Federation)
We will do Federation in SEIR-II

Objective---> “We are not building a login page. We are building an identity system that issues tokens.”

Students will:

    Create a User Pool
    Enable login with:
        username
        email
        phone number
    Enforce MFA
    Create and authenticate a user
    Use the JWT to call your REST API

Updated Flow: Client → WAF → API Gateway (Cognito Authorizer) → Lambda


Task 1 — Create Cognito User Pool
  Navigation
  
    AWS Console → Cognito
    Click User Pools
    Click Create user pool


Step-by-Step Configuration

