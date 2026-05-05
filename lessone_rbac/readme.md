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




