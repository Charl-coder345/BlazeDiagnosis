# Blaze Diagnostics App

Blaze Diagnostics is a workshop management and customer communication system for mechanical workshops.

The system is intended to improve communication between workshops and clients by tracking vehicle jobs, quote approvals, parts ordering, parts delivery, mechanic progress, invoicing, and collection readiness.

## Tech Stack explained
Understanding what each tech stack do helps you to work with the code more confident and enables informed decision making.

- Next.js: a React-based full-stack framework designed for building fast and production ready web applications, key features of Next.js includes File-based Routing and API Routes.
  
- TypeScript : a strongly typed programming language that builds on JavaScript to support a tighter intergration with a coding editor, and catching errors early in the development process.
  
- React: a JavaScript library developed by Facebook for building dynamic and efficient user interfaces.
  It is widely used for creating single-page applications (SPAs) and follows a component-based architecture
  
## Current Technical Stack

- Frontend: Next.js, React, TypeScript, Tailwind CSS
- Backend: Node.js, TypeScript, modular service/controller/repository structure
- Database: PostgreSQL
- Current ORM in the uploaded app: Prisma
- Earlier planning referenced: Drizzle ORM
- Version control: GitHub

Important: The current uploaded application uses Prisma. Do not assign Drizzle implementation work until the ORM direction has been confirmed. See `docs/technical/ORM_DECISION_NOTE.md`.

## Student Groups Using This Repository

This repository has been adjusted for the current CTU Bloemfontein internship groups:

- Software Engineering 1
- Software Engineering 2
- Software Development 1
- Software Development 2
- Cloud Administration
- Cyber Security

Architectural Draughting students should use the separate `synergy-inc-architectural-draughting` repository.

## Where Students Should Start

1. `STUDENT_START_HERE.md`
2. `docs/internship/REMOTE_INTERNSHIP_PLAN.md`
3. `docs/internship/FIRST_WEEK_TRAINING_SCHEDULE.md`
4. `docs/training/GITHUB_WORKFLOW.md`
5. `docs/training/GROUP_LEARNING_PATHS.md`
6. The learning path for your specific group in `docs/training/`
7. `docs/backlog/STUDENT_STARTER_TASKS_BY_GROUP.md`
8. `docs/backlog/BLAZE_DIAGNOSTICS_ISSUES_BY_GROUP.md`

## Repository Bootstrap

### Workspace Layout

- `backend/` - API and domain modules
- `frontend/` - Next.js application
- `docs/` - product, API, schema, training, backlog, and internship documents
- `.github/` - GitHub issue and pull request templates

### Quick Start

1. Copy `.env.example` to `.env`.
2. Copy `backend/.env.example` to `backend/.env` if required.
3. Copy `frontend/.env.example` to `frontend/.env.local`.
4. Start local services with `docker-compose up -d`.
5. Install dependencies in the required workspace.
6. Run the relevant database generate/migrate/seed commands once confirmed by the mentor.
7. Start the backend.
8. Start the frontend.

## Student GitHub Workflow

Students must not commit directly to `main`.

Expected workflow:

1. Read the issue.
2. Create a branch.
3. Make a small focused change.
4. Test or review your work.
5. Commit with a clear message.
6. Push the branch.
7. Open a pull request.
8. Respond to review feedback.

## Security Rule

Never commit passwords, API keys, database URLs, tokens, `.env` files, personal credentials, or private customer information.

## Student MVP Planning Update

This repository now includes student-ready MVP planning material grouped for:

- Software Engineering 1
- Software Engineering 2
- Software Development 1
- Software Development 2
- Cloud Administration
- Cyber Security

Start with:

- `STUDENT_START_HERE.md`
- `docs/training/FIRST_WEEK_BLAZE_DIAGNOSTICS_TECH_STACK.md`
- `docs/backlog/MVP_BACKLOG_BY_GROUP.md`
- `docs/backlog/MVP_USER_STORIES.md`

Cloud Administration students should also read:

- `docs/cloud/CLOUD_ADMINISTRATION_MVP_TASKS.md`

Cyber Security students should also read:

- `docs/security/CYBER_SECURITY_MVP_TASKS.md`

## Student Learning Resources

Blaze Diagnostics learning resources are available at:

`docs/training/student-learning-resources.md`

The full internship-wide resource list is maintained in the `internship-training-and-docs` repository under:

`13-resource-index/self-paced-resource-urls.md`
