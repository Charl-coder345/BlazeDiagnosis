# Project Analysis

## Setup Instructions

1. Open VS Code.
2. Clone the repository into an empty folder using: `git clone <URL>`
3. Navigate to the frontend directory: `cd frontend`
4. Run `npm install` to install all frontend dependencies.
5. Navigate to the backend directory: `cd backend`
6. Run `npm install` to install all backend dependencies.
7. Once completed, your environment is ready.
8. Run `npm run build` in frontend to build and then run `npm start` to start the application.

## Common Errors

1. Root installation error: Running `npm install` in the root folder instead of inside the `frontend` or `backend` directories will cause missing dependency or package.json errors.
2. Package manager conflicts: Using alternative package managers like `pnpm` or `yarn` instead of `npm` may cause dependency or lockfile conflicts. This is being addressed in upcoming commits from Ben.

## Tech Stack Summary

* Next.js: A full-stack meta-framework built on top of React. It combines Server-Side Rendering (SSR) and Client-Side Rendering (CSR) to optimize performance, initial load times, and SEO.
* Tailwind CSS: A utility-first CSS framework. It utilizes inline styling classes directly within the component code, speeding up development and eliminating the need to maintain multiple separate CSS files.
* TypeScript: A statically typed superset of JavaScript. Similar to Java and C#, it enforces strict type checking to catch errors during development rather than at runtime, saving debugging time later.
* Drizzle ORM: An Object-Relational Mapping tool used to interact cleanly with our PostgreSQL database. It was selected as a faster, more lightweight alternative to our original choice, Prisma.
* GitHub: Used for version control, allowing the team to track precise code changes line-by-line.

