# Personal Engineering Guidelines

A practical, evolving engineering baseline for Kos's personal software projects.

> These guidelines are distilled from repeated patterns observed across active personal projects and engineering work I materially contributed to. They are a reference, not a constraint: prioritize the personal or product outcome, learning velocity, and delivery; use engineering to make experiments safer, more repeatable, and easier for humans and agents to continue; keep improving the system as evidence accumulates.

## Core principle

**Optimize for outcome and learning velocity. Engineering exists to reduce risk, rework, and coordination cost—not to add ceremony.**

Prefer the shortest trustworthy feedback loop. Increase rigor when a change is hard to reverse, has a large blast radius, touches credentials/private data/money, or creates durable state and external side effects.

## How to use this repository

This repository contains shared principles and defaults. It does not override more specific project context.

Read context in this order:

1. This repository's principles.
2. The target repository's `AGENTS.md` and `README.md`.
3. Current Issue / roadmap / specification / ADR / runbook.
4. Current code, tests, CI, and runtime evidence.

The more specific source wins when it intentionally differs from this baseline. Project-local context may reduce ceremony, but it should not silently weaken a safety or evidence boundary whose underlying risk still exists.

## Canonical responsibility split

- **Personal Engineering Guidelines** — shared principles and cross-project defaults.
- **Skills / Runbooks** — repeatable executable workflows.
- **`side-project-template`** — executable repository/release bootstrap, not prose policy.
- **Project-local `AGENTS.md`** — project-specific constraints and current execution rules.
- **GitHub Issues / PRs / CI** — durable engineering work and evidence.
- **Notion** — product intent, long-form design, personal knowledge, and other canonical state where explicitly designated.
- **Chat history** — useful working context, but never the only durable source of truth.

## Baseline

See:

- [`docs/01-principles.md`](docs/01-principles.md) — engineering principles.
- [`docs/02-delivery-and-evidence.md`](docs/02-delivery-and-evidence.md) — delivery, testing, evidence, and operational safety.
- [`docs/03-ai-assisted-development.md`](docs/03-ai-assisted-development.md) — AI-native development baseline.
- [`docs/04-project-maturity-and-capabilities.md`](docs/04-project-maturity-and-capabilities.md) — risk-scaled capabilities from Prototype / PoC through long-lived production.
- [`docs/05-technology-decisions.md`](docs/05-technology-decisions.md) — capability-first technology selection and migration decisions.
- [`docs/06-observability-and-alerting.md`](docs/06-observability-and-alerting.md) — observability, deterministic alerting, noise control, and monitor-the-monitoring.
- [`docs/07-context-and-rule-inheritance.md`](docs/07-context-and-rule-inheritance.md) — canonical routing, local overrides, durable handoff, and rule-drift control.
- [`docs/08-guideline-evolution.md`](docs/08-guideline-evolution.md) — promotion, demotion, retirement, and evidence-driven evolution of the baseline.
- [`examples/anonymized-practice-patterns.md`](examples/anonymized-practice-patterns.md) — sanitized real-world examples showing how the principles were applied.
- [`templates/PROJECT_BOOTSTRAP_CHECKLIST.md`](templates/PROJECT_BOOTSTRAP_CHECKLIST.md) — minimum project bootstrap checklist.
- [`templates/PROJECT_PROFILE.md`](templates/PROJECT_PROFILE.md) — lightweight maturity/risk/capability profile for routing a project.
- [`templates/EVIDENCE_CHECKLIST.md`](templates/EVIDENCE_CHECKLIST.md) — claim-to-evidence checklist before declaring material work complete.

## Evidence

The raw cross-repository survey, private repository mappings, professional-project attribution, and sensitive implementation evidence live in a separate private repository. Public guidelines contain only principles, sanitized examples, and reusable methods.

Professional examples are included only when I materially contributed to the engineering work; otherwise they remain private observed evidence rather than personal accomplishment claims.

## Status

**v0.1 — evidence-based bootstrap.** This baseline should evolve when repeated project evidence shows a better default.
