# Day 2 Task 1 - First Security checklist

# Blaze Diagnosis Cyber Security Review Checklist
```
Reviewer: Kobus Mienie

Date:  09/06/2026
```

## Repository Safety

- [X] `.env` files are ignored.
- [X] `.env.example` files do not contain real secrets.
- [X] No passwords are committed.
- [X] No API keys are committed.
- [X] No database credentials are committed.
- [X] No private customer data is committed.

## Authentication

- [X] Passwords are not stored in plain text.
- [X] Sessions or tokens expire.
- [X] Logout invalidates the session where applicable.
- [X] Forgot/reset password flow does not expose sensitive data.

## Authorization

- [X] Protected routes require authentication.
- [X] Role-based permissions are defined.
- [X] Users cannot access other tenants' data.
- [X] Customers cannot view other customers' jobs.
- [X] Internal-only fields are not exposed on customer-facing pages.

## API Security

- [X] API routes validate input.
- [X] API routes check permissions.
- [X] Error messages do not leak technical details.
- [X] IDs and tokens are not easily guessable.
- [X] Public approval links are protected with secure tokens.

## Database and Data Protection

- [X] Tenant-owned records include tenant scoping.
- [X] Queries are scoped by tenant or customer where required.
- [X] Sensitive information is not returned unnecessarily.
- [X] Audit logs exist for important actions.

## Customer Tracking and Quote Approval

- [X] Customer tracking access is secure.
- [X] Quote approval links cannot be guessed.
- [X] Approval/rejection actions are logged.
- [X] Expiry rules are considered for public links.
- [X] Customer-facing pages do not show supplier costs unless intended.
