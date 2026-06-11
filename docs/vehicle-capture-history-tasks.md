# Vehicle Capture and History

This document breaks down the Vehicle capture and history feature into clear, assignable tasks with acceptance criteria.

## Overview
The Vehicle capture and history feature includes:
- creating and editing vehicle records
- listing and searching vehicles
- archiving vehicles with soft-delete semantics
- showing vehicle detail and history context for audit and job tracking
- enforcing customer/tenant ownership and duplicate protection

---

## Task 1: Backend — Vehicle CRUD + archive API
**Goal:** implement reliable vehicle persistence and tenant-safe access.

**Work**
- `GET /api/vehicles` → list active vehicles for tenant
- `POST /api/vehicles` → create new vehicle
- `GET /api/vehicles/:id` → read single vehicle
- `PATCH /api/vehicles/:id` → update vehicle
- archive route for soft archive (`POST /api/vehicles/:id/archive` or equivalent)

**Acceptance criteria**
- must require `tenantId` and `customerId` on create
- must reject duplicate `registrationNumber` or `vin` within same tenant
- must only return non-archived vehicles in active lists
- must preserve archived vehicles for history/audit
- must return `Vehicle not found` for invalid IDs or archived vehicles when reading/updating
- must validate required fields and return clear errors

---

## Task 2: Backend — Vehicle history / detail model and rules
**Goal:** support vehicle audit context and link vehicle records to jobs/quotes.

**Work**
- ensure `VehicleEntity` includes audit timestamps and `isArchived` / `archivedAt`
- ensure vehicle can resolve to owning customer and tenant
- enforce that a vehicle cannot exist without a valid customer
- enforce tenant consistency between vehicle and customer

**Acceptance criteria**
- vehicle record always has `customerId` and `tenantId`
- archived customers do not break vehicle history
- archived vehicles remain linked to their customer
- search and list filter by tenant and permitted customer scope only

---

## Task 3: Frontend — Vehicle capture UI
**Goal:** build create/edit vehicle screen that matches the data model.

**Work**
- `VehiclesPanel` form for create/edit
- fields: customer selector, registration number, VIN, make, model, variant, year, engine, fuel type, transmission, odometer, color
- support save/create, edit, reset/cancel
- validate required fields: customer, registration number, make, model
- preserve tenant ID from current tenant context

**Acceptance criteria**
- user can add a vehicle and see it immediately in the list
- user can edit an existing vehicle and save changes
- user can cancel editing and return to add mode
- form prevents submission when required values are missing
- vehicle creation normalizes reg/VIN values when present

---

## Task 4: Frontend — Vehicle list/search/archive
**Goal:** make vehicles discoverable and manageable.

**Work**
- list active vehicles with key details
- search by registration, VIN, make, model, variant, fuel, transmission
- archive button for soft-delete / hide from active list
- clear search and reload support

**Acceptance criteria**
- list shows only active vehicles
- search returns filtered results based on query
- archive removes vehicle from active list immediately
- archived vehicles are not shown in the normal list
- errors are displayed when archive or load fails

---

## Task 5: Vehicle detail/history view
**Goal:** expose vehicle history and relationships in a detail view.

**Work**
- create vehicle detail page or panel
- show vehicle metadata, owner customer name, timestamps, archive status
- show linked jobs / quotes / inspections summary if available
- allow navigation from the vehicle list to detail view

**Acceptance criteria**
- detail view renders for a selected vehicle
- archived vehicles remain viewable via direct link or history route
- related job/quote references appear if available
- detail view clearly labels archived state and timestamps

---

## Recommended assignment split
1. Backend CRUD + validation
2. Backend history/linkage + data rules
3. Frontend create/edit form
4. Frontend list/search/archive UI
5. Frontend vehicle detail/history view
