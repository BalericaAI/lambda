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


