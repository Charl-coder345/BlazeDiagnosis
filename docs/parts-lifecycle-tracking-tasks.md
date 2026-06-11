# Parts Lifecycle Tracking

This document breaks the Parts lifecycle tracking feature into clear, assignable tasks with acceptance criteria.

## Overview
Parts lifecycle tracking covers the lifecycle of parts used on job cards, from request through ordering, delivery, installation, and cancellation. It includes:
- adding parts requirements to a job
- tracking part quantity, cost, supplier reference, and ETA
- updating part status through lifecycle stages
- listing job parts and their status
- protecting tenant scope and auditability

---

## Task 1: Backend — Part request model and persistence
**Goal:** define the part lifecycle entity and persistence behavior.

**Work**
- implement `PartRequestEntity` persistence in `backend/src/modules/parts`
- define DTOs for creating and updating part requests
- add repository methods for create, search, findById, and update
- support tenant-scoped storage and job association

**Acceptance criteria**
- part request entity includes `jobId`, `description`, `quantity`, lifecycle `status`, and optional fields:
  - `costPrice`
  - `sellPrice`
  - `supplierReference`
  - `etaDate`
- create/update DTOs validate required fields
- persistence layer can create and update part requests and query by job
- tenant or job scope must prevent cross-tenant access

---

## Task 2: Backend — Parts lifecycle API end points
**Goal:** expose part lifecycle operations through HTTP routes.

**Work**
- implement `POST /api/jobs/:id/parts` to add a part request to a job
- implement `PATCH /api/parts/:id/status` to change the part's lifecycle status
- implement `GET /api/jobs/:id/parts` to list parts for a job
- wire controllers, services, validators, and routes for the parts module

**Acceptance criteria**
- adding a part to a job requires valid `jobId`, `description`, and `quantity`
- part status updates are allowed only with valid lifecycle values
- listing parts returns all parts linked to a job in the correct tenant scope
- invalid job or part IDs return clear errors like `Job not found` or `Part request not found`

---

## Task 3: Backend — Lifecycle rules and status transitions
**Goal:** enforce part status flow and lifecycle integrity.

**Work**
- define allowed lifecycle statuses and transitions:
  - `REQUIRED`
  - `PENDING_APPROVAL`
  - `READY_TO_ORDER`
  - `ORDERED`
  - `SHIPPED`
  - `RECEIVED`
  - `INSTALLED`
  - `RETURNED`
  - `CANCELLED`
- ensure status updates preserve audit timestamps
- optionally add history or event notes for status changes

**Acceptance criteria**
- incorrect status values are rejected
- lifecycle progression is clear and does not allow invalid regressions if enforced
- `REQUIRED` -> `READY_TO_ORDER` -> `ORDERED` -> `SHIPPED` -> `RECEIVED` -> `INSTALLED` is supported
- cancellation is allowed from appropriate states

---

## Task 4: Frontend — Parts request creation UI
**Goal:** let users add parts to a job from the UI.

**Work**
- add a parts form or panel for job pages
- include fields: description, quantity, cost price, sell price, supplier reference, ETA, and status
- send new part requests to `POST /api/jobs/:id/parts`
- validate required fields in the UI

**Acceptance criteria**
- user can add a part request for a selected job
- part requests appear in the job’s parts list after creation
- required field validation works in the browser
- errors display when create fails

---

## Task 5: Frontend — Parts list and lifecycle management
**Goal:** make part requests discoverable and easy to update.

**Work**
- display a list of parts for each job with quantity, status, supplier reference, ETA, and pricing
- allow status updates through a dropdown or buttons
- refresh the list after a status change
- support filtering or grouping by part lifecycle status if useful

**Acceptance criteria**
- parts list displays all job-linked parts and status fields
- status changes persist and the UI refreshes accordingly
- job parts list clearly shows ordered, shipped, received, installed, and cancelled states
- any load or update errors are shown clearly

---

## Recommended assignment split
1. Backend model and persistence
2. Backend API and routes
3. Backend lifecycle rules/status transitions
4. Frontend part request creation UI
5. Frontend parts list/lifecycle management UI
