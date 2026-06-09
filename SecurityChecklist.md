# Task 1 - Security checklist

# Blaze Diagnosis Cyber Security Checklist
```
Reviewer: 

Date:
```

```
Nr                       Security Check                                                          Yes/No                      Comments/Findings
```

## Login Risks

1.  Are strong password requirements enforced (length, complexity, uniqueness)?
2. Is Multi-Factor Authentication (MFA) available or required?
3. Are login attempts limited to prevent brute-force attacks?
4. Are user sessions automatically timed out after inactivity?
5. Are account lockout mechanisms implemented after multiple failed login attempts?
6. Are secure protocols (HTTPS/TLS) used for login pages?


## Role-Based Access Control (RBAC)

7. Are users assigned roles based on job responsibilities?
8. Are permissions restricted according to the principle of least privilege?
9. Can users access only the data and functions required for their role?
10. Are administrator privileges limited to authorized personnel?
11. Are role permissions reviewed regularly?


## Customer Data Exposure

12. Is sensitive customer data encrypted at rest?
13. Is sensitive customer data encrypted during transmission?
14. Are customer records protected from unauthorized access?
15. Is personal information masked when displayed where appropriate?
16. Are data exports restricted and monitored?
17. Are customer data retention and deletion policies implemented?

## API Access Control

18. Are APIs protected with authentication mechanisms?
19. Are API authorization checks performed for every request?
20. Are API keys securely stored and managed?
21. Is rate limiting implemented to prevent abuse?
22. Are API requests and responses logged for auditing?
23. Are unused or deprecated API endpoints disabled?

## Password Handling

24. Are passwords hashed before storage?
25. Are strong hashing algorithms used (e.g., bcrypt, Argon2, PBKDF2)?
26. Are passwords never stored in plain text?
27. Are password reset processes secure and time-limited?
28. Are password change requests logged and monitored?

## Environment Variables

29. Are secrets stored in environment variables rather than source code?
30. Are production and development environments separated?
31. Is access to environment configuration restricted?
32. Are environment variables excluded from version control systems?
33. Are secrets rotated periodically?

## GitHub Secret Exposure

34. Are API keys, passwords, and tokens excluded from repositories?
35. Are .env files listed in .gitignore?
36. Is secret-scanning enabled for repositories?
37. Are pull requests reviewed for accidental secret exposure?
38. Have exposed secrets been revoked and replaced immediately?

## Error Message Safety

39. Do error messages avoid revealing system details?
40. Are database errors hidden from end users?
41. Are stack traces disabled in production environments?
42. Are detailed error logs stored securely for administrators only?
43. Do user-facing error messages provide minimal information?
44. Are application logs monitored for suspicious activity?

## Overall Assessment
```
90–100%	Excellent security posture
75–89%	Good security posture with minor improvements needed
50–74%	Moderate risk – several areas require attention
Below 50%	High risk – immediate remediation recommended
```
Summary of Findings:


Recommended Actions:

```
Total Checks Passed: ______ / 44
Security Compliance Percentage: ______ %
```