# Rossik_Tools
This repo will contain everything regarding the Rossik_Tools applications

# Internal App Platform

Monorepo for internal web applications.

This repository provides a standardized foundation for building internal tools:
- Backend-first architecture
- Shared authentication and data access
- Consistent deployment and development workflow

The goal is to avoid one-off apps and instead build reusable, maintainable internal software.

---

## Repository structure

├── apps/
│ ├── api/ # NestJS backend (TypeScript)
│ └── web/ # Angular frontend (CSS)
├── packages/ # Shared libraries (future)
├── docker-compose.yml
├── package.json
└── tsconfig.base.json


---

## Tech stack

### Backend
- TypeScript
- NestJS
- (Database integration added later)
- Docker-ready
- run using npm run dev:api - localhost:3000

### Frontend
- Angular
- CSS (no SSR/SSG by default)
- run using npm run dev:web - localhost:4200

### Tooling
- Node.js
- npm workspaces
- Docker / Docker Compose
- GitHub (PR-based workflow)

---

## Branching & workflow

- `main`  
  Stable / production-ready code  
  ❌ Direct pushes disabled

- `development`  
  Integration branch  
  ❌ Direct pushes disabled

- `feat/*`  
  Feature branches created from `development`

### Workflow
1. Create feature branch from `development`
2. Commit and push feature branch
3. Open PR: `feat/*` → `development`
4. Review and merge
5. Open PR: `development` → `main` when ready
6. Delete feature branch after merge

# new feature:
git checkout development
git pull
git checkout -b feat/feature-name

# edit files...
git add .
git commit -m "test: verify PR flow"

# when feature is done
git push -u origin feat/test-flow

# open Github - create pull request
base = development
compare = feature branch

# after development is commited
create another pull request into main
review
merge
delete feature branch

---

## Local development
npm install
npm run dev:api
npm run dev:web

### Prerequisites
- Node.js (LTS recommended)
- npm
- Docker Desktop (optional, for containers)

### Install dependencies
```bash
npm install
