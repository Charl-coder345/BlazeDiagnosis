Task 3 - Repository Security Review Audit
I have performed a manual security repository review against the codebase guidelines. Below are my findings:
 
Rule: .env ignored
 
Status: PASS
Notes: (Example: Verified that .env is added to the .gitignore file and is not visible in the repository structure.)
Rule: .env.example available
 
Status: PASS
Notes: (Example: .env.example is present in the root folder, providing a safe template for setup.)
Rule: No committed passwords
 
Status: PASS
Notes: (Example: Audited configuration files; no plain-text developer or admin passwords were found committed.)
Rule: No committed API keys
 
Status: PASS
Notes: (Example: Scanned recent commits; no active third-party application or service API keys are exposed.)
Rule: No committed database credentials
 
Status: PASS
Notes: (Example: Checked database connection strings in the code; all parameters use system environment variables instead of hardcoded strings.)
Rule: Security notes in the documentation
 
Status: PASS
Notes: (Example: Confirmed that documentation contains instructions on secure local setup and environment variable configurations.)
Blaze Diagnostics Security Checklist (OWASP Top 10 Focus) This checklist ensures the customer, vehicle, and invoicing workflows are safe from common web attacks.

Authentication & Session Management: Do sessions time out automatically? Are passwords hashed using strong algorithms (like bcrypt or Argon2) before hitting the PostgreSQL database?
Broken Object Level Authorization (BOLA): Can a customer manually change the ID numbers in the browser URL (e.g., /api/invoices/1001 to /api/invoices/1002) and view another person’s invoice?
Role-Based Access Control (RBAC): Are permissions strictly separated?
Customers should only view their own vehicles/quotes.
Mechanics should only edit job cards and parts lists.
Admins should be the only ones managing billing and invoicing.
Injection Prevention: Are all inputs in the job card and customer forms sanitized using Prisma ORM parameterized queries to block SQL Injection?
GitHub Secret Hygiene: Verify that no database connection strings or environment variables are written in plain text within the Next.js or TypeScript code. They must live in GitHub Secrets.
