# Repository Guidelines

## Project Structure & Module Organization
Open Canvas is a Yarn workspaces monorepo.
- `apps/web`: Next.js frontend and UI assets.
- `apps/agents`: LangGraph server and agent runtime.
- `packages/shared`: Shared types, utilities, and model config.
- `packages/evals`: Evaluation helpers and integration tests.
- `static/`: Screenshots and static assets.
- `langgraph.json`: LangGraph CLI configuration for local agents.

## Build, Test, and Development Commands
- `yarn install`: Install workspace dependencies at the repo root.
- `yarn build`: Build all workspaces via Turborepo.
- `yarn lint` / `yarn lint:fix`: Run ESLint across workspaces (fix when needed).
- `yarn format` / `yarn format:check`: Run Prettier across workspaces.
- `cd apps/agents && yarn dev`: Start LangGraph server on port 54367.
- `cd apps/web && yarn dev`: Start the Next.js app on `http://localhost:3000`.
- `cd apps/web && yarn eval`: Run Vitest-based evals with `ls.vitest.config.ts`.

## Coding Style & Naming Conventions
- TypeScript-first; follow local Prettier configs (2-space indentation, semicolons).
- ESLint is enforced per workspace (`apps/web`, `apps/agents`, `packages/shared`).
- Prefer descriptive names; keep React components in `PascalCase` and hooks in `useThing` form.

## Testing Guidelines
- Vitest is used for evaluation tests in `apps/web`.
- Integration tests live in `packages/evals` (e.g., `*.test.ts`).
- Name test files with `.test.ts` or `.int.test.ts` and keep fixtures close to the test when possible.

## Commit & Pull Request Guidelines
- Recent commits use conventional-style prefixes (e.g., `fix:`). Follow this pattern when practical.
- PRs should include a short summary, test commands run, and screenshots for UI changes.
- Link relevant issues and note any config changes or new env vars.

## Configuration & Secrets
- Copy `.env.example` to `.env` at the repo root and in `apps/web/`.
- Never commit API keys or Supabase credentials; document required variables in the PR.
