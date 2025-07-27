# Goal-Tracker
Full‑stack habit/goal tracker with real‑time analytics, streaks, completion metrics, and secure OAuth/email auth. Monorepo with shared components, type‑safe APIs, and e2e coverage (Playwright) enforced via strict linting

Build consistency, one day at a time – an open-source daily goal & habit tracker built with Next.js App Router and Supabase.

![Daily Goal Tracker UI](docs/screenshots/home.png)
![Dashboard UI](docs/screenshots/dashboard.png)
![Settings UI](docs/screenshots/settings.png)

## ✨ Key Features

- **Daily Goal Management** – add, edit, or remove goals and mark them complete as you work through the day.
- **Progress Metrics** – today’s progress, overall completion rate, and current streak at-a-glance.
- **Tomorrow Planner** – queue up tomorrow’s goals so you start every day with a clear plan.
- **Analytics Dashboard**  
  • Weekly completion chart  
  • Monthly overview (set vs. completed goals)  
  • Category breakdown across work, health, personal, and more.
- **Authentication & Profiles** – email / password and OAuth providers powered by Supabase Auth.
- **Responsive & Accessible UI** – built with Tailwind CSS and a reusable React component kit.

## 🏗️ Monorepo Architecture

This repository is managed with **Turborepo** and **pnpm workspaces**.  
Each package is isolated yet shareable across the code-base:

| Package             | Description                                                        |
| ------------------- | ------------------------------------------------------------------ |
| `apps/web`          | Next.js 15 front-end (App Router, React Server Components).        |
| `packages/api`      | tRPC + Express server exposing goal endpoints.                     |
| `packages/auth`     | Supabase auth helpers, React context, hooks, and route guards.     |
| `packages/ui`       | Design-system and Storybook documentation.                         |
| `packages/schema`   | Shared Zod schemas & types used across FE/BE.                      |
| `packages/supabase` | Supabase client (browser + server) pre-configured for the project. |

> For a deeper dive, see `docs/architecture.md`.

## 🧰 Tech Stack & Tooling

- **Frameworks**: Next.js 15 • React 19 • Express 4
- **Language**: TypeScript 5.8
- **Styling**: Tailwind CSS 4 • CSS Modules
- **Auth & DB**: Supabase (v2 SDK) • Supabase Auth UI
- **API Layer**: tRPC • Zod validation
- **State / Data**: React Query (coming soon)
- **Testing**: Vitest + Testing Library • Playwright e2e
- **Quality**: ESLint • Prettier • Husky + lint-staged git hooks
- **Tooling**: Turborepo build cache • pnpm workspaces • Storybook 8 • tsup bundler

## 🚀 Getting Started

```bash
# 1. Install dependencies (root of the repo)
pnpm install

# 2. Copy env example and fill in your Supabase keys
cp apps/web/.env.example apps/web/.env.local
cp packages/api/.env.example packages/api/.env

# 3. Run everything in parallel (web, api, ui storybook, etc.)
pnpm dev

# 4. Open the app
http://localhost:3000
```

Each workspace also exposes its own `dev`, `build`, `lint`, and `test` scripts – look inside the individual `package.json` files for details.

## 🖼️ Screenshots

| Home                               | Dashboard                                    | Settings                                   |
| ---------------------------------- | -------------------------------------------- | ------------------------------------------ |
| ![Home](docs/screenshots/home.png) | ![Dashboard](docs/screenshots/dashboard.png) | ![Settings](docs/screenshots/settings.png) |

> The `docs/screenshots/*` images are optimised PNGs located inside the repo to keep the README self-contained. Feel free to replace them with your own captures.

## 🗺️ Project Structure (simplified)

```text
prep-pilot/
├─ apps/
│  └─ web/                # Next.js front-end
├─ packages/
│  ├─ api/                # tRPC & Express server
│  ├─ auth/               # Supabase auth helpers & hooks
│  ├─ ui/                 # Component library + Storybook
│  ├─ schema/             # Zod models & shared types
│  └─ supabase/           # Configured Supabase clients
├─ docs/                  # Architecture & design docs
└─ test/                  # e2e tests
```

## 🧪 Tests

- **Unit/Component** – `vitest` runs in every package (`pnpm test`).
- **E2E** – Playwright smoke tests live in `test/e2e` and run against the built app.

## 📦 Production Build

```bash
# Build all workspaces and produce Docker-optimised output
yarn build   # or pnpm build
```

A multi-stage Dockerfile is provided that leverages Turborepo’s caching and only ships the necessary artefacts.

## 🙌 Contributing

PRs are welcome!

1. Fork the repo
2. Create a branch `git checkout -b feature/your-feature`
3. Commit your changes `pnpm commit`
4. Push and open a PR

Please ensure all unit & e2e tests pass and adhere to the existing code style.

## 📝 License

MIT © 2025 Prep Pilot
=======
