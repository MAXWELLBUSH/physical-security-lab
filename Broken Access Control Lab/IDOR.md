📄 README 2 — IDOR (Insecure Direct Object Reference) Vulnerability Report
Title: IDOR Exploitation in User Profile Management System
1. Introduction

In this lab, I investigated and exploited an Insecure Direct Object Reference (IDOR) vulnerability in a user profile management system. I was logged in as a regular user with limited privileges, but the application failed to properly enforce authorization checks when accessing user profiles.

By manipulating user IDs in the URL, I was able to access other users’ profiles, including the administrator account, and retrieve sensitive information.

2. Understanding the Application Behavior

After logging into the system, I accessed my own profile using the following endpoint:

/idor1/profile/3


The application displayed my profile information, including:

User ID

Username

Email

Role

From this, I concluded that the application used the user ID in the URL to determine which profile to display.

However, I observed that the application did not verify whether the requested profile belonged to the authenticated user.

3. Exploitation of the Vulnerability

To test for IDOR, I modified the user ID in the URL.

I accessed:

/idor1/profile/2


The application displayed another user’s profile, even though I was not authorized to view it. This confirmed the presence of an IDOR vulnerability.

I then accessed:

/idor1/profile/1


This revealed the administrator’s profile, which contained sensitive information such as:

Admin role and privileges

Password hash

Additional administrative data

I further tested multiple user IDs to enumerate users in the system, demonstrating that any user profile could be accessed by simply changing the ID.

4. Why This Vulnerability is Catastrophic

The impact of IDOR vulnerabilities is extremely serious:

a) Unauthorized Access to User Data

Attackers can access personal information such as emails, usernames, and private data of other users, violating privacy.

b) Administrative Account Compromise

Access to admin profiles can expose password hashes and privileged information, enabling attackers to take over administrative accounts.

c) Data Breach

Large-scale exploitation of IDOR can lead to massive data leaks affecting thousands or millions of users.

d) Privilege Escalation

Attackers can gain higher privileges by accessing resources intended only for administrators.

e) Legal and Compliance Risks

Exposure of sensitive user data can lead to violations of data protection laws such as GDPR or HIPAA, resulting in legal penalties and reputational damage.

In real-world applications, IDOR vulnerabilities have been responsible for major security breaches and data leaks.

5. Root Cause of the Vulnerability

The IDOR vulnerability existed because:

The application relied on predictable, sequential user IDs.

Authorization checks were missing or insufficient.

The system trusted client-side input without validation.

There was no verification that the requested resource belonged to the authenticated user.

6. Prevention and Mitigation Techniques

To prevent IDOR vulnerabilities, developers should implement the following measures:

a) Strong Authorization Checks

Verify that the authenticated user is authorized to access the requested resource.

b) Use Indirect Object References

Replace sequential IDs with random, non-predictable identifiers such as UUIDs or tokens.

c) User Context Validation

Ensure that users can only access resources associated with their own accounts.

d) Consistent Access Control Policies

Apply the same authorization logic across all endpoints and APIs.

e) Secure API Design

Avoid exposing sensitive data through APIs without proper authentication and authorization.

7. Conclusion

In this lab, I demonstrated how an IDOR vulnerability can allow a regular user to access other users’ profiles and sensitive administrative information by simply modifying URL parameters. This highlighted the dangers of relying on predictable object references and failing to enforce proper authorization checks.

The lab emphasized the importance of implementing robust access control mechanisms and secure design principles to protect user data and prevent unauthorized access.