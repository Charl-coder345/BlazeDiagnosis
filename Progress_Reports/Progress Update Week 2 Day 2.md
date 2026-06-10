**Date:** 2026 / 06 / 09
**User:** PJ
**Tag:** #WIL 
**Status:** #incomplete 
**Link:** [[WIL HUB]] | [[WIL Notes]]

---
**What happened today:**

We have two groups so far in SD2: Jarvix & Ultron
- [x] Review the MVP backlog.
	- The MVP_BACKLOG_BY_GROUP.md file includes the scope and roles the system requires us to implement. The MVP should include the following, that we know the Software Development 2 group must do for their part:
		- Authentication and role-based access - Jarvix 
		- Customer management - Ultron
		- Vehicle management - Ultron
		- Job cards - Jarvix
		- Job status updates - Jarvix
		- Quote approval workflow - Jarvix
		- Parts tracking - Ultron
		- Customer tracking page - Ultron
		- Basic invoice generation - Ultron || Jarvix
		- Activity log - Not entirely sure if we do this
	- The system needs to implement the following roles as well:
		- Workshop Admin
		- Service Advisor
		- Mechanic
		- Customer
		- System Admin, if required later
	- What is expected of the SD2 group to do according to the backlog is the following:
		1. Focus: Next.js pages/routes, forms, API interactions, CRUD screens, and workflow implementation.
		2. Starter Tasks: 
			- Review project routes.
			- Review forms and data submission patterns.
			- Study customer, vehicle, job-card, and quote workflows.
			- Review current backend endpoints.
		3. Possible MVP Tasks:
			- Build customer create/edit screen.
			- Build vehicle create/edit screen.
			- Build job-card create screen.
			- Build job-card details screen.
			- Build quote approval UI.
			- Build parts tracking UI.
			- Connect forms to API routes where available.
- [x] Review existing app architecture.
	- So according to the api-contracts.md, there are in some instances comments that guides on what a certain section of the API must be able to do. There are cases where it seems to already have a snippet of the GET, POST and PATCH requests and it seems like everything is going to be requested through a JSON file.
	- The app will cover a lot of information, we need to make sure that the correct IDs are used and that no information is overwritten.
- [x] Identify database-related code.
	1. The database must have the following key roles implemented:
		- Every tenant-owned table must include tenant_id.
		- Customer, vehicle, job, quote, invoice, and payment workflows must be auditable.
		- Quote versions must be preserved, not overwritten.
		- Job status transitions should be validated through a service layer.
		- Supplier and marketplace tables should remain behind Phase 2 feature flags
	2. The database should include these core tables:
		- tenants
		- branches
		- users
		- customers
		- vehicles
		- jobs
		- inspections
		- quotes
		- quote_lines
		- part_requests
		- invoices
		- payments
		- notifications
		- job_status_history
	3. Phase 2 will implement these extension tables
		- suppliers
		- supplier_branches
		- products
		- inventory_items
		- supplier_prices
		- purchase_orders
		- purchase_order_lines
		- promotions
- [x] Identify current ORM usage and database models.
	- After careful review, I have read through the ORM_DECISION_NOTE.md file and seen that there was a consideration made to switch and migrate to Drizzle ORM, but there are 2 options we have. One is to continue using the Prisma ORM and the other is to migrate the existing ORM to Drizzle rather, but we need to make the decision and not do it ourselves as stated by the document explicitly. Upon further review, we have established that Drizzle is used.
- [x] Review customer, vehicle, job card, quote, and status workflow requirements.
	- Customer
		- It seems like this is more catered to the personal details for the customer who wants to have a profile for the application, a unique ID is assigned upon account creation.
	- Vehicle
		- This includes a record of all the details for a specific vehicle, uniquely identified by the tenenatID and customerID accordingly, the record stores a very detailed summary of every vehicle stored in the database.
	- Job Card
		- This includes the full details why a vehicle is in the mechanic shop, listing the vehicleID, tenantID, customerID and another ID which will be used to make a record of each instance a vehicle was brought to the shop. Customers are allowed to make a complaint and the mechanics can give a full diagnosis and summary of what they have done on the customers vehicle.
	- Quote
		- The quotes are essentially receipts of the labor that was done and the amount needed to pay from the customer after service completion. Also containing a unique ID to keep track of each payment made, tax is also included with payment prompts.
	- Status workflow
		- From what I understand, the status workflow is the active logs that will store records for each necessary instance the application wants to validate and update correctly to the database, such as the quote approvals, invoice creation when logged, user timestamps and when changes are made to the application.
- [x] Select a backend, database, or feature planning issue.
	- We are going to implement the database using PostgreSQL.
---
**Expected Output:** *By the end of Day 2, each student should have*
- [x] Identified one feature area to work on
	- We have split the workload into two groups and considering the use of Prisma, we might actually just continue working with the current design rather than migrate to a newer ORM and potentially breaking an already unstable code structure.
- [x] Added notes to the relevant issue
	- The issue that we have is that our SD2 group is split into 2 groups, where 4 people are not present in either one. Considering the workload of the project we need to tackle, we need to address this matter as soon as possible. 
- [x] Confirmed what needs to be implemented or clarified
	- We have decided that the Invoice section will be done by both groups, considering it has two instances, a receipt for the customer and one for the business.
- [x] Posted a progress update