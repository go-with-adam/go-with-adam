# Adam Boryniec

Software engineer working across backend, frontend, data, and AI. Most of my recent work is a multi-tenant SaaS for regulated industries — built end-to-end, currently in production with paying users.

The code is private. This page is the public-facing summary.

## What I've been building

A multi-tenant SaaS platform (**talari.ai**) serving regulated professions, currently clinical practices with vertical site templates rolling out for adjacent verticals. I've owned the engineering top-to-bottom: data model, auth, billing, AI pipelines, infrastructure, and the GDPR/compliance surface.

It's been the deepest engineering experience of my career — real users, real compliance constraints, real production incidents — and I'm looking for my next role on a team where I can keep working at this depth without the operational overhead of running the business.

## Selected technical work

- **GDPR Articles 15, 17, and 33 implemented end-to-end.** Data export with manifest + SHA-256 integrity payload; right-to-erasure with 30-day grace and email-token cancellation (designed so soft-deleted users can't log in to cancel); breach-notification timer with 24h/48h/71h escalating reminders and description-field encryption at rest. Hardened admin endpoints, immutable audit logs.

- **RAG pipeline with provenance, designed for regulated use cases.** Citation-map architecture: every claim in a generated report carries `[N]` markers linked to source chunks, with a sidecar JSON capturing the full retrieval context. Eval harness with study-ready sample cases gates model swaps. The shape was deliberate — pure templates were useless, raw LLM was unsafe; grounded RAG with auditable provenance is the only version I'd put in front of a regulator.

- **Typed `UserContext` for multi-tenant impersonation.** A customer-visible bug ("editor sees owner-only collections under impersonation") turned out not to be a bug but a category. After three local hotfixes failed, I rebuilt the affected surface around a typed context object that distinguishes impersonator from target at the type level — the compiler now refuses the ambiguous case. Followed up with surface-area tests, not change-diff tests.

- **Operational discipline at small scale.** Staging and production on separate hosts; two-track migrations (Sequelize for Node, raw SQL for Python); pre-deploy canary checks; atomic role transitions on Postgres (`REASSIGN OWNED` bundled with `GRANT`-back in the same transaction). Postmortems written for every prod incident, including the small ones.

## Stack

**Backend:** Node.js · Express · Sequelize · PostgreSQL · Redis · Python · FastAPI · Pydantic · SQLAlchemy
**Frontend:** Next.js (App Router) · React 19 · TypeScript · Tailwind · MUI
**Data / AI:** Qdrant · Ollama · custom RAG pipeline · LiveKit (real-time voice)
**Infra:** Docker · PM2 · systemd · nginx · GitHub Actions

## How I work

I write the minimum code that solves the problem and verify in a real environment before claiming done. I treat security and compliance as load-bearing, not paperwork. I'd rather rewrite 200 lines into 50 than ship the larger version.

For productivity I use agentic AI tooling heavily — specialized review agents (security, QA, database, frontend) run in parallel on every PR, and persistent project memory survives across sessions. It's how I keep review quality high while moving at the pace a small team would.

## What I'm looking for

Senior or staff IC roles where the engineering problem is the hard part — distributed systems, AI/ML infrastructure, security and compliance, or developer platforms. Comfortable as a deep specialist or a generalist across the stack; happiest on teams that take production reliability and code quality seriously.

## Activity

Most repositories are private. Contribution graph is enabled so activity is visible.

## Contact

- Email: adam.boryniec@gmail.com
- LinkedIn: https://www.linkedin.com/in/adam-boryniec/
