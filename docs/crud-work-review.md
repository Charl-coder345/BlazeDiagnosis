# CRUD Work Review

This document reviews the proposed CRUD work for the Blaze Diagnostics MVP and summarizes the current task definitions.

## Current proposed CRUD work

### Customer capture
- Backend CRUD + archive API
- Customer data model and tenant rules
- Frontend customer create/edit form
- Customer list/search/archive UI
- Customer detail/relationship view

### Vehicle capture and history
- Backend vehicle CRUD + archive API
- Vehicle history/detail model and tenant link rules
- Frontend vehicle create/edit form
- Vehicle list/search/archive UI
- Vehicle detail/history view

### Parts lifecycle tracking
- Backend part request model and persistence
- Parts lifecycle API endpoints
- Parts lifecycle status rules
- Frontend parts request creation UI
- Frontend parts list and lifecycle management UI

## Review summary

### Strengths
- Tasks are broken into backend and frontend responsibilities.
- Acceptance criteria are explicit and tied to expected user-visible behavior.
- Soft-delete/archive behavior is included, which is important for audit and history.
- Tenant and scope rules are covered for customer and vehicle features.
- Task definitions are modular and assignable.

### Areas to improve
- Add explicit test coverage tasks for backend routes, validation, and UI flows.
- Add requirements for authorization and role checks in API acceptance criteria.
- Add API contract or schema verification as a separate deliverable.
- Strengthen detail-view expectations by naming which related records should appear (vehicles, jobs, quotes, parts).
- For parts lifecycle, make status transition rules more actionable with allowed transitions and blocked transitions.

### Risks and gaps
- If authorization is not enforced, CRUD endpoints could expose cross-tenant or cross-customer data.
- Without dedicated test tasks, edge cases such as duplicate handling, invalid input, and archive state may be missed.
- Parts workflow may require deeper job integration than a standalone CRUD task.
- UI error states and empty-list handling are present but should be more clearly documented as part of acceptance criteria.

## Recommendations
- Create follow-up tasks for:
  - API contract review and documentation
  - integration tests across customer → vehicle → job relationships
  - authorization/permission checks for CRUD routes
  - API error handling and user-facing error messages
- Keep the CRUD task docs in sync with the feature inventory and sprint plan.
- Reference this review from the feature inventory or backlog docs when assigning work.

## Notes
- Existing task definitions are documented in:
  - `docs/customer-capture-tasks.md`
  - `docs/vehicle-capture-history-tasks.md`
  - `docs/parts-lifecycle-tracking-tasks.md`
