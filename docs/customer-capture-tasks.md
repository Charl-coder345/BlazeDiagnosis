# Customer Capture

This document breaks the Customer capture feature into clear, assignable tasks with acceptance criteria.

## Overview
Customer capture is the foundation for workshop workflows and vehicle tracking. It includes:
- creating and editing customer records
- listing and searching customers
- archiving customers with soft-delete semantics
- enforcing tenant scope and duplicate protection
- protecting customer visibility and private data

---

## Task 1: Backend — Customer CRUD + archive API
**Goal:** implement dependable customer persistence and scoped access.

**Work**
- `GET /api/customers` → list active customers for tenant
- `POST /api/customers` → create new customer
- `GET /api/customers/:id` → read single customer
- `PATCH /api/customers/:id` → update customer
- `DELETE /api/customers/:id` or archive route for soft archive

**Acceptance criteria**
- must require `tenantId`, `fullName`, and `mobileNumber` on create
- must reject duplicate phone number or email within the same tenant
- must only return non-archived customers in active lists
- must preserve archived customers for history and audit
- must return `Customer not found` for invalid IDs or archived customers when reading/updating
- must validate input fields and return clear errors

---

## Task 2: Backend — customer data model and tenant rules
**Goal:** enforce data integrity, tenant isolation, and relationship consistency.

**Work**
- ensure `CustomerEntity` includes audit timestamps, `isArchived`, and `archivedAt`
- enforce tenant consistency on create/update
- validate optional fields cleanly (
  - `email`
  - `address`
  - `companyName`
  - `taxNumber`
  - `preferredCommunicationChannel`
  - `marketingConsent`
  )
- ensure created customer records are safe to link to vehicles, jobs, quotes, and invoices

**Acceptance criteria**
- customer record always has `tenantId` and required identity fields
- duplicate phone or email rejects within same tenant
- archived customers remain available for history but are excluded from active lists
- optional customer fields do not break create or update flows

---

## Task 3: Frontend — Customer capture form and create/edit UI
**Goal:** provide a customer form for adding and updating customer profiles.

**Work**
- build customer form with fields:
  - full name
  - mobile number
  - alternate number
  - email
  - address
  - company name
  - tax number
  - preferred communication channel
  - marketing consent
- support create and edit modes
- display validation state for required fields
- preserve tenant context in payloads

**Acceptance criteria**
- user can add a new customer and immediately see it in the list
- user can edit an existing customer and save changes
- form prevents submission without required values
- form supports canceling edit and resetting to add mode
- user-facing errors appear when save fails

---

## Task 4: Frontend — Customer list, search, and archive management
**Goal:** make customer records easy to discover and manage.

**Work**
- display active customers in a list or cards
- support searching by name, phone, email, or company
- implement archive action for soft-delete
- support refresh/clear search

**Acceptance criteria**
- list shows only active customers
- search filters customers by the query fields
- archive removes the customer from active list immediately
- archived customers do not appear in normal search/list results
- display error when load or archive fails

---

## Task 5: Customer detail/relationship view
**Goal:** expose customer context for vehicles, jobs, and service workflows.

**Work**
- create a detail view or panel for a selected customer
- show customer metadata and status
- show related vehicles, jobs, or quotes if available
- show archive state and audit timestamps

**Acceptance criteria**
- detail view renders for selected customer
- archived customers remain viewable via direct link or history route
- related vehicle/job references appear if available
- detail view clearly labels archived state and timestamps

---

## Recommended assignment split
1. Backend CRUD + validation
2. Backend data model and tenant rules
3. Frontend customer form create/edit
4. Frontend customer list/search/archive UI
5. Frontend customer detail/relationship view
