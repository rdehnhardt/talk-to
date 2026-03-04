# Project Structure Convention

This skill defines the standard folder structure that all roles follow. It applies automatically to every project.

## Required Folders

When any `/talk-to:*` command is invoked for the first time in a project folder, check if the following structure exists. If any folder is missing, create it with an empty `INDEX.md` inside.

```
<project-root>/
├── business-rules/       ← Analyst owns. Business rules, requirements, domain logic.
│   └── INDEX.md
├── tasks/                ← PM owns. Backlog, tasks, milestones.
│   └── INDEX.md
├── decisions/            ← Architect owns. ADRs, technical decisions, trade-offs.
│   └── INDEX.md
├── schemas/              ← DBA owns. Database schemas, migrations, data models.
│   └── INDEX.md
├── design/               ← Designer owns. UI specs, design tokens, component specs.
│   └── INDEX.md
├── infra/                ← DevOps owns. Docker configs, CI/CD, server setup, runbooks.
│   └── INDEX.md
├── marketing/            ← Marketing owns. Campaigns, copy, positioning, competitors.
│   └── INDEX.md
└── financial/            ← Financial owns. Costs, pricing, projections, models.
    └── INDEX.md
```

## INDEX.md Convention

Each `INDEX.md` serves as a quick reference for everything in that folder. Format:

```markdown
# [Folder Name]

| File | Summary | Status | Date |
|------|---------|--------|------|
| filename.md | Brief description | active/draft/archived | YYYY-MM-DD |
```

When a role creates or updates a file in their folder, they MUST also update the corresponding `INDEX.md`.

## File Naming Convention

Files inside folders use kebab-case with a descriptive name:
- `business-rules/invoice-expiration.md`
- `tasks/implement-wallet-sync.md`
- `decisions/dec-001-non-custodial.md`
- `schemas/merchant-wallets.md`

## Cross-Reference Rules

Every role can READ any folder for context. Each role WRITES only to their own folder. The mapping is:

| Role | Writes to | Reads before acting |
|------|-----------|-------------------|
| Analyst | `business-rules/` | `tasks/`, `decisions/` |
| Architect | `decisions/` | `business-rules/`, `schemas/`, `infra/` |
| DBA | `schemas/` | `business-rules/`, `decisions/` |
| Designer | `design/` | `business-rules/`, `tasks/`, `decisions/` |
| DevOps | `infra/` | `decisions/`, `schemas/` |
| Financial | `financial/` | `business-rules/`, `marketing/`, `tasks/` |
| Marketing | `marketing/` | `business-rules/`, `financial/`, `design/` |
| PM | `tasks/` | ALL folders (needs full visibility) |
| Technical | source code | `business-rules/`, `decisions/`, `schemas/`, `tasks/`, `design/` |

## Root-Level Files

These optional files live at the project root and are maintained by the PM:
- `ROADMAP.md` — High-level phases and milestones (macro view).
- `STATUS.md` — Current project snapshot (what's done, in progress, blocked).

Any role can reference these files for context.
