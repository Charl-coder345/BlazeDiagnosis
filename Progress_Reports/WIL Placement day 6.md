**Date:** 2026-06-08
**Tag:** #WIL
**Status:** #ongoing
**Link:** [[WIL HUB]] | [[WIL Notes]]

---
**Sources**

| Topic | Video | Doc |
| ----- | ----- | --- |
|       |       |     |

---
**Task to complete**

**Task 1:** *Review the current Project structure*
- [x] Open the Blaze Diagnostics repository
- [x] Review the folders and files
- [x] Identify where the fronted code is located
It is located in the frontend folder
- [x] Identify Where the back-end or database related cod is located.
It is located in the backend folder
- [x] Write short notes explaining what you found.
I found that all of the files are structured neatly and are easily readable.
This helps ensure me that I wont have to struggle with spaghetti code, which brings me immense joy.

**Task 2:** *Confirm local Setup*
- [x] Clone the reposition
- [x] Install dependencies
- [x] Try to run the project locally
- [x] Document any errors
You wil get an error when trying to run the app in the root directory instead of the frontend directory use `cd frontend` to navigate to it.
- [ ] Do not silently struggle with setup problem

**Task 3:** *Review the MVP Backlog*
- [x] Read the MVP user stories
- [ ] Identify which feature area you understand best
- [ ] Choose one small issue to start with
- [ ] Comment on the issue before working on it

**Task 4:** *Create or Improve Documentation*
- [x] Improve setup instructions 
- [x] Add missing notes for new students
- [x] Documents common setup errors
- [x] Add explanations for the tech stack

**Task 5:** *Fronted Starter Task*
- [x] Review an exiting page or components
I ran the application and tried to use it to see how it feels. While the application is easy
enough to use, it took me a while to find the buttons to create a user, because they look like plain text due to styling.
- [x] Identify a small improvement
The submit button styling can be changed to make them more visible.
All of the text on the application is the same size, Making the headers bigger or bold might help with easier navigation
- [ ] Use tailwind CSS carefully
- [ ] Submit the work for review

---
**Time Spent:** 


** Day 2 Update: Identify current ORM usage and database models.

** 1. Executive Summary
Conducted a thorough technical investigation of the Blaze Diagnostics codebase to map out the application's structural design, verify the local development environment configuration across ports `3000` and `4000`, and identify the current data persistence lifecycle layers. 

** 2. Key Discoveries & Architectural Overview
While the system's long-term design is explicitly structured around a relational database model, the active codebase implements an isolated, decoupled architectural pattern for rapid local development.

** Database Strategy (Planned vs. Active):**
  * **Planned Blueprint:** Identified a comprehensive, enterprise-grade multi-tenant schema configured in `schema.prisma` targeting a **PostgreSQL** database backend. The layout accounts for robust state machines via enums (e.g., `JobStatus`, `QuoteStatus`) to govern the workshop operational workflow.
  * **Active Implementation:** Discovered that the backend currently circumvents active database migrations by using a centralized, in-memory mock store (`in-memory-db`). Data mutations rely on native JavaScript array utilities to simulate persistence.

* ** The 3-Tier Backend Pipeline:**
  Traced a complete data execution flow using the `Vehicle` domain as a reference architecture:
  1. **Controller Layer (`vehicles.controller.ts`):** Serves as the API interface. It accepts payloads, executes structural validation checks, and formats uniform JSON network responses (`ok()`).
  2. **Service Layer (`vehicles.service.ts`):** Enforces core business logic constraints. It manages structural entity mutations, applies operational metadata (audit timestamps via `createAuditTimestamps()`), and runs data-integrity guards (blocking duplicate registration numbers or VINs).
  3. **Repository Layer (`vehicles.repository.ts`):** Manages the direct state transitions of the data data-store. It handles complex search query filtering and applies multi-tenant isolation filters (`tenantId`) to ensure data privacy between different workshops.


