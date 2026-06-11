# template-base

The central, language-agnostic upstream parent template for the `itsjennyfiggy-platform` ecosystem. All platform repositories inherit their `.agents/` rules, workflows, and skills from this repo via the `template-sync-orchestrator`.

---

## Purpose

This repository holds the developer tooling configurations, agent safety rules, CI/CD workflow conventions, project planning templates, and testing standards that apply uniformly across every repository in the platform. Child templates (e.g. `template-homelab`, `template-github-action`) and service repos consume these by subscribing to the sync pipeline.

---

## Repository structure

```
├── .agents/
│   ├── rules/
│   │   ├── dependency_management.md      # Anti-hallucination + version-grounding rules for packages/actions
│   │   ├── environment_bootstrapping.md  # Port safety, process cleanup, DB migration ordering
│   │   ├── subagent_orchestration.md     # When and how to spawn parallel agents
│   │   └── testing_standards.md         # TDD mandate, 85% coverage gate, AAA pattern
│   ├── skills/
│   │   └── dependency-auditor/           # Skill + license-check script for auditing packages
│   └── workflows/
│       └── bootstrap.md                  # Local environment bootstrapping workflow
├── docs/
│   ├── adr/
│   │   ├── README.md                     # ADR index (canonical, complete list)
│   │   ├── 0001-release-automation-strategy.md
│   │   └── 0002-github-app-identity-strategy.md
│   └── templates/
│       └── PROJECT_PLANNING.md           # Project scoping template
├── .editorconfig                         # Indentation and line-ending standards
├── CLAUDE.md                             # Agent rules index (token: [REPO_NAME] for sync substitution)
├── LICENSE                               # CC0 1.0 Universal
├── README.md                             # This file (describes template-base itself)
└── README.template.md                    # Blank README skeleton for child repos (copy this, not README.md)
```

---

## For child repositories: use README.template.md

When scaffolding a new repository from any child template, copy `README.template.md` as the starting point for that repo's `README.md`. It contains the standard section structure for platform services (`Features & Scope`, `Tech Stack & Architecture`, `Getting Started`, `Agent Guidelines`).

Do not copy `README.md` — it describes `template-base` itself and is not a generic app README.

---

## Architecture Decision Records

Significant, cross-cutting platform decisions are recorded in [`docs/adr/`](docs/adr/README.md). Current ADRs:

| ADR | Title | Status |
|---|---|---|
| [0001](docs/adr/0001-release-automation-strategy.md) | Release Automation Strategy | Accepted |
| [0002](docs/adr/0002-github-app-identity-strategy.md) | GitHub App Identity Strategy | Accepted |

---

## Licensing

CC0 1.0 Universal (Public Domain). See [LICENSE](LICENSE).
