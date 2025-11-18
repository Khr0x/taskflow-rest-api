# TaskFlow — Challenge (Node + TypeScript + Express + Drizzle + Bun)

Description
- Simple REST API to manage projects and tasks. Built as a portfolio challenge using Bun, TypeScript, Express and Drizzle ORM. Includes basic JWT authentication, migrations and seeds for example data.

Technologies
- Bun (runtime/package manager/task runner)
- TypeScript
- Express
- Drizzle ORM
- PostgreSQL (recommended) / SQLite (demo mode)
- JWT for authentication

Requirements
- Bun: https://bun.sh
- PostgreSQL (or SQLite for demo)
- Node.js only if you prefer npm/yarn (optional)

Status
- Challenge / demo: functional as an example and a base to extend for a portfolio.

Quick installation (Postgres)
1. Clone the repository
```bash
git clone <repo-url>
cd <repo-directory>
```
2. Install dependencies with Bun
```bash
bun install
```
3. Create a `.env` file from `.env.example` and set the variables:
```env
# .env
DATABASE_URL=postgres://user:pass@localhost:5432/taskflow
JWT_SECRET=a-long-secure-secret
PORT=3000
```
4. Run migrations and seeds
```bash
bun run migrate
bun run seed
```
5. Start the app in development
```bash
bun run dev
```
6. Visit the API:
http://localhost:3000

Demo mode with SQLite
- To try without PostgreSQL, use a `.env` like:
```env
DATABASE_URL=file:./dev.db
JWT_SECRET=a-long-secure-secret
PORT=3000
```
- Run the same migrate/seed and dev commands (depending on project configuration).

Environment variables (main)
- DATABASE_URL: database connection URL (Postgres or SQLite).
  - Postgres example: `postgres://user:pass@localhost:5432/taskflow`
  - SQLite example: `file:./dev.db`
- JWT_SECRET: long secret used to sign JWT tokens.
- PORT: server port (default 3000).

NPM / Bun scripts (package.json)
- dev: run server in development mode
- build: compile/transpile (if applicable)
- migrate: run Drizzle migrations
- seed: load example data
- test: run tests

Common commands
```bash
bun run dev        # development
bun run build      # build (if applicable)
bun run migrate    # apply migrations
bun run seed       # seed DB with example data
bun run test       # run tests
```

Main endpoints (summary)
- POST /auth/register — register user (body: { name, email, password })
- POST /auth/login — login (body: { email, password }) => returns JWT
- GET /projects — list projects (auth required)
- POST /projects — create project (auth required)
- GET /projects/:id — view project by id (auth required)
- PUT /projects/:id — update project (auth required)
- DELETE /projects/:id — delete project (auth required)
- GET /projects/:projectId/tasks — list tasks in a project (auth required)
- POST /projects/:projectId/tasks — create task in project (auth required)
- GET /tasks/:id — view task by id (auth required)
- PUT /tasks/:id — update task (auth required)
- DELETE /tasks/:id — delete task (auth required)

Basic usage examples (curl)
- Register:
```bash
curl -X POST http://localhost:3000/auth/register \
  -H "Content-Type: application/json" \
  -d '{"name":"User","email":"user@example.com","password":"secret"}'
```
- Login:
```bash
curl -X POST http://localhost:3000/auth/login \
  -H "Content-Type: application/json" \
  -d '{"email":"user@example.com","password":"secret"}'
# Response includes token: { "token": "..." }
```
- Create project (use returned token in Authorization header):
```bash
curl -X POST http://localhost:3000/projects \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer <TOKEN>" \
  -d '{"title":"Demo Project","description":"Description"}'
```

Migrations & Seeds
- Migrations are handled with Drizzle (or the tool documented in SPEC.md).
- `bun run migrate` should apply migrations.
- `bun run seed` should populate example users, projects and tasks.

Contributing
- Read SPEC.md before proposing changes.
- Open issues for bugs or improvements and submit PRs with clear descriptions.
- Follow the project's code style if linters/formatters are configured.

License
- MIT (or your chosen license). Add a LICENSE file if applicable.

Contact
- Add your contact info or link to your GitHub profile.

Notes
- Adjust commands, script names and migration details to match the concrete implementation in this repository.
