# K-Forge Website · Agent Context

> Operational context and rules for AI agents working in this repository.

---

## K-Forge Ecosystem

K-Forge is a software development club at Fundación Universitaria Konrad Lorenz (FUKL), Bogotá, founded by Brian Vargas (@13rianVargas). The club builds real-world software products for the university and community.

| Project | Repo | Description |
|---------|------|-------------|
| **K-Forge Website** | `K-Forge/` | Public landing page — you are here |
| KApp | `KApp/` | University management platform (Spring Boot microservices) |
| TiendaQ | `TiendaQ/` | University e-commerce system (Spring Boot + Angular) |
| Roastory | `Roastory/` | Library-cafe management system (Node.js + MongoDB) |

---

## Project Overview

**K-Forge Website** is the official public landing page for the K-Forge club. It presents the club identity, members, projects, and links. Deployed on Vercel.

**Live:** https://kforge.vercel.app

---

## Tech Stack

| Layer | Technology |
|-------|-----------|
| Framework | Angular 21 (standalone components, no NgModules) |
| State | Angular Signals (`signal`, `computed`) |
| Styling | Tailwind CSS 3 with project design tokens |
| i18n | Custom service — `es` and `en` (`src/app/services/i18n.service.ts`) |
| External data | GitHub API (public repository info) |
| Package manager | pnpm (install) + Bun (scripts) |
| Deploy | Vercel |

---

## Project Structure

```text
K-Forge/
├── src/
│   ├── app/
│   │   ├── components/     # Standalone visual sections
│   │   ├── services/       # i18n, GitHub API, reusable logic
│   │   └── app.ts          # Main component composition
│   └── styles.css          # Global styles + design tokens
├── public/                 # Static assets
├── angular.json
├── tailwind.config.js
├── vercel.json
└── package.json
```

---

## Dev Commands

```bash
# One-time tooling setup
corepack enable && corepack prepare pnpm@latest --activate
curl -fsSL https://bun.sh/install | bash

# Dev server
pnpm install && bun start     # → http://localhost:4200

# Production build
bun run build
```

---

## Conventions

### Code

- All components are standalone (no NgModules).
- Use signals (`signal`, `computed`, `effect`) for local reactive state. No services for UI state.
- Modern control flow: `@if`, `@for`, `@switch` — never `*ngIf`/`*ngFor`.
- Tailwind design tokens: `midnight`, `surface`, `violet-primary`, `violet-secondary`, etc. Never hardcoded colors.
- New section: create standalone component under `src/app/components/<section>/`, register in `app.ts`, add i18n keys.

### i18n

- Every visible string must exist in both `es` and `en` in `src/app/services/i18n.service.ts`.
- No hardcoded text in templates — always reference i18n keys.

### Git

- **Commits:** Conventional Commits, English, lowercase, no scope, no final period.
  ```
  feat: add projects section
  fix: resolve mobile nav overflow
  chore: update angular to 21.3
  ```
- **Branches:** Git Flow — `main`, `develop`, `feature/*`, `bugfix/*`, `hotfix/*`, `release/*`.

### Versioning

SemVer `MAJOR.MINOR.PATCH`. Release cycle: alpha → beta → stable.

---

## Current State

- Production: deployed and live at https://kforge.vercel.app
- Sections: hero, about, members, projects (GitHub API), contact.
- i18n: `es` and `en` fully implemented.
- No backend — data is static + GitHub API.

---

## AI Agent Instructions

- This is a public-facing repository. Only authorized K-Forge members maintain it.
- Respect the Vercel deployment configuration (`vercel.json`). Do not change it without explicit request.
- Do not create CONTRIBUTING.md, CONTRIBUTORS.md, or modify LICENSE unless explicitly asked.
- Never hardcode credentials, API keys, or sensitive data.
- Keep i18n parity: every new user-facing string must exist in both `es` and `en`.
- Test changes locally with `bun start` before proposing.
- No emojis in technical markdown documents.
- No automatic commits. Present changes for review first.


---

## Temporary Files

- `tmp/` is gitignored. Store one-off scripts and throwaway files there.
- Delete after use. Never commit anything from `tmp/`.