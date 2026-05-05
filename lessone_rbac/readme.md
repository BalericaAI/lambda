RBAC — Role-Based Access Control

What is RBAC?

Role-Based Access Control (RBAC) is a security model where:

Access is assigned to roles, not directly to users.

Simple Model---> User → Role → Permissions → Resource

| User     | Role    | Access            |
| -------- | ------- | ----------------- |
| student1 | student | `/python`         |
| admin1   | admin   | `/python + /node` |


Purpose of RBAC in This Lab

So far:

WAF → filters traffic
Cognito → verifies identity

Now: RBAC → controls what authenticated users can do
Translation: “Not everyone who gets in should have full access.”

Updated System Flow: Client → WAF → API Gateway (Auth) → Lambda (RBAC decision)

Important:

Authentication happens at API Gateway
Authorization (RBAC) often happens in Lambda

RBAC in Cognito

With Amazon Cognito, RBAC is implemented using:

Groups

Examples:

    students
    admins
    Lizzo lovers
    Chewbacca
    Malgus Clan

Token Claims

When a user logs in, their JWT contains:

    "cognito:groups": ["students"]


Why RBAC Matters????

1. Scalability

Instead of: ---> assigning permissions per user ❌
You:---> assign roles once✅
Or you could assign multiple times to Lizzo.  You want that???

2. Consistency

All users in a role behave the same way

3. Security

You follow:

    Least Privilege Principle

Users only get what they need

Connecting RBAC to Microsoft / Active Directory

RBAC in Microsoft World

In:

Active Directory
Microsoft Entra ID

RBAC is implemented through:

✔ Security Groups

Examples:

        Domain Users
        Admins
        HR
        Finance

| Concept      | Cognito          | Microsoft           |
| ------------ | ---------------- | ------------------- |
| User         | User Pool User   | AD User             |
| Group        | Cognito Group    | Security Group      |
| Role         | Group membership | Group membership    |
| Token Claims | JWT              | SAML / OAuth claims |

Say this: “Cognito groups = AD security groups. Same idea, different platform.”

Mental Model (Important)

Cognito (This Lab)
    Lightweight
    API-focused
    Cloud-native

AD / Entra SEIR 
    Enterprise identity
    Corporate networks
    SSO across apps

“Today you learn RBAC in Cognito. Later you will see the same model in AD and Entra—just bigger and more complex.”

RBAC Decision Point in System

Where does RBAC happen?

Two options:

        1. API Gateway (Advanced)
        
        Harder
        Less flexible
        
        2. Lambda (Recommended for Lab)
        
        Why Lambda?
        Easy to understand
        Easy to debug
        Real-world pattern for many systems

Example RBAC Logic

In Lambda:

        groups = event["requestContext"]["authorizer"]["claims"].get("cognito:groups", [])
        
        if "admin" in groups:
            # full access
        elif "student" in groups:
            # limited access
        else:
            # deny

“Your code decides access based on identity claims.”

NOTE:

Authentication ≠ authorization
Just because you log in doesn’t mean you can do everything
Systems enforce behavior based on identity
“RBAC is how companies survive audits.”

