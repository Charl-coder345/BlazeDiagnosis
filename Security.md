Blaze Diagnostics Security Checklist (OWASP Top 10 Focus) This checklist ensures the customer, vehicle, and invoicing workflows are safe from common web attacks.

Authentication & Session Management: Do sessions time out automatically? Are passwords hashed using strong algorithms (like bcrypt or Argon2) before hitting the PostgreSQL database?
Broken Object Level Authorization (BOLA): Can a customer manually change the ID numbers in the browser URL (e.g., /api/invoices/1001 to /api/invoices/1002) and view another person’s invoice?
Role-Based Access Control (RBAC): Are permissions strictly separated?
Customers should only view their own vehicles/quotes.
Mechanics should only edit job cards and parts lists.
Admins should be the only ones managing billing and invoicing.
Injection Prevention: Are all inputs in the job card and customer forms sanitized using Prisma ORM parameterized queries to block SQL Injection?
GitHub Secret Hygiene: Verify that no database connection strings or environment variables are written in plain text within the Next.js or TypeScript code. They must live in GitHub Secrets.
