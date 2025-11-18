# TaskFlow — Challenge (Node + TypeScript + Express + Drizzle + Bun)

Descripción
- API REST sencilla para gestionar proyectos y tareas. Pensada como challenge para portfolio usando Bun, TypeScript, Express y Drizzle ORM.

Requisitos
- Bun (https://bun.sh)
- PostgreSQL (o SQLite para modo demo)
- Node.js solo si quieres usar npm/yarn (opcional)

Instalación rápida (Postgres)
1. Clona el repo
   bun install
2. Crea archivo .env (ejemplo .env.example)
   DATABASE_URL=postgres://user:pass@localhost:5432/taskflow
   JWT_SECRET=un-secret-largo
3. Corre migrations y seeds
   bun run migrate
   bun run seed
4. Levanta en modo dev
   bun run dev
5. Accede a http://localhost:3000

Scripts (package.json)
- dev: correr servidor en modo desarrollo
- build: compilar/transpilar (si aplica)
- migrate: correr migraciones Drizzle
- seed: cargar datos de ejemplo
- test: ejecutar tests

Endpoints principales (resumen)
- POST /auth/register
- POST /auth/login
- GET /projects
- POST /projects
- GET /projects/:id
- PUT /projects/:id
- DELETE /projects/:id
- GET /projects/:projectId/tasks
- POST /projects/:projectId/tasks
- GET /tasks/:id
- PUT /tasks/:id
- DELETE /tasks/:id

Estructura sugerida
- src/
  - server.ts
  - app.ts
  - routes/
  - controllers/
  - services/
  - db/
  - models/
  - tests/
- prisma/ or migrations/ (dependiendo de Drizzle)
- .github/ (templates para issues/PRs)
- README.md
- SPEC.md

Consejos para portfolio
- Incluye capturas de pantalla de Postman o Swagger
- Añade un GIF corto mostrando endpoints funcionando
- Documenta decisiones técnicas (por qué Drizzle, por qué Bun)
- Muestra commits atómicos y PRs (si es posible)
