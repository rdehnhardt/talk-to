# Talk To — Cowork Plugin

Talk to specialized experts. Each role brings domain expertise while the project folder provides context. Works with any project.

## Quick Start

1. Install the plugin in Cowork (Customize > Upload custom plugin).
2. Point Cowork at your project folder.
3. Type `/talk-to:setup` to initialize the folder structure.
4. Type `/talk-to:pm` (or any role) to start working.

## Commands

| Command | Expert | Writes to | Reads from |
|---------|--------|-----------|------------|
| `/talk-to:setup` | — | Creates all folders | — |
| `/talk-to:analyst` | Business Analyst | `business-rules/` | `tasks/`, `decisions/` |
| `/talk-to:architect` | Software Architect | `decisions/` | `business-rules/`, `schemas/`, `infra/` |
| `/talk-to:dba` | Database Architect | `schemas/` | `business-rules/`, `decisions/` |
| `/talk-to:designer` | Product Designer | `design/` | `business-rules/`, `tasks/`, `decisions/` |
| `/talk-to:devops` | DevOps Engineer | `infra/` | `decisions/`, `schemas/` |
| `/talk-to:financial` | Financial Analyst | `financial/` | `business-rules/`, `marketing/`, `tasks/` |
| `/talk-to:marketing` | Growth Strategist | `marketing/` | `business-rules/`, `financial/`, `design/` |
| `/talk-to:pm` | Project Manager | `tasks/`, `ROADMAP.md`, `STATUS.md` | ALL folders |
| `/talk-to:technical` | Software Engineer | source code | `business-rules/`, `decisions/`, `schemas/`, `tasks/`, `design/` |

## Project Structure (created by `/talk-to:setup`)

```
your-project/
├── business-rules/       ← Analyst: domain rules, requirements, edge cases
│   └── INDEX.md
├── tasks/                ← PM: backlog, task files, milestones
│   └── INDEX.md
├── decisions/            ← Architect: ADRs, technical decisions
│   └── INDEX.md
├── schemas/              ← DBA: database schemas, data models
│   └── INDEX.md
├── design/               ← Designer: UI specs, design tokens, components
│   └── INDEX.md
├── infra/                ← DevOps: Docker, CI/CD, server configs
│   └── INDEX.md
├── marketing/            ← Marketing: campaigns, copy, positioning
│   └── INDEX.md
├── financial/            ← Financial: costs, pricing, projections
│   └── INDEX.md
├── ROADMAP.md            ← PM: macro view (phases + milestones)
└── STATUS.md             ← PM: current project snapshot
```

## How Cross-Reference Works

Every role can **read any folder** for context, but only **writes to their own folder**. This means:
- The Architect reads `business-rules/` before proposing solutions.
- The Technical reads `decisions/` + `schemas/` + `tasks/` before implementing.
- The PM reads ALL folders to maintain full project visibility.

Each folder has an `INDEX.md` that serves as a quick reference table. Roles update their INDEX when creating or modifying files.

## Customization

Each skill is a markdown file in `skills/<role>/SKILL.md`. Edit to match your preferences — add your tech stack, conventions, or specific workflows.

## Installation

Upload this folder as a custom plugin in Cowork, or via CLI:

```
claude plugin install ./talk-to
```
