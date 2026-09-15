# AI-Assisted Development

## Goal

Use AI to reduce execution cost and increase learning speed while keeping responsibility, permissions, evidence, and durable state explicit.

## Context routing

Before implementing, read only the context needed for the current task, in this order:

1. shared personal engineering guidelines;
2. target repo `AGENTS.md` / README;
3. active Issue / roadmap / spec / ADR / runbook;
4. relevant code and tests;
5. CI/runtime state when the task depends on it.

Do not load every document by default. Route first, then deepen context as uncertainty requires.

## Work contract

Substantial AI-assisted work should have an executable problem statement with:

- Why / desired outcome;
- observable acceptance criteria;
- scope and non-goals;
- important constraints;
- risk / permission boundary;
- required evidence;
- expected next state.

The solution may evolve during implementation. Preserve problem/outcome stability unless new evidence changes it.

## Execution loop

Use a compact loop:

`Outcome -> Context -> Plan -> Implement -> Review -> Verify -> Record`

Planning should be just detailed enough to expose risky assumptions and boundaries. Avoid producing a long plan when a small reversible implementation can answer the question faster.

## TDD and AI

When behavior is clear enough to specify, prefer:

`behavior/contract -> failing test -> implementation -> refactor -> evidence`

Do not generate tests merely to mirror implementation. Tests should protect behavior, contracts, or known failure modes.

## Multi-session / multi-agent work

Important state must survive the current transcript. Store task ownership, decisions, checkpoints, review results, and next actions in durable systems such as GitHub Issues/PRs, repository files, or explicit runtime state.

Prefer independent work boundaries. Avoid multiple agents simultaneously editing the same files unless reconciliation cost is justified.

Before a new worker resumes:

- read durable state;
- reconcile current branch/PR/CI/runtime status;
- continue existing work when safe rather than recreating it.

## Deterministic vs AI work

Use deterministic code/tests/scripts for deterministic decisions whenever practical. AI is especially useful for:

- exploration and synthesis;
- ambiguous debugging;
- design tradeoffs;
- implementation assistance;
- review and explanation;
- prioritization where judgment is required.

A repeated prompt that performs stable mechanical work is a candidate for automation.

## Security and authorization

Credential availability is not authorization.

AI workers must not infer permission to:

- spend money;
- deploy or mutate production;
- access unrelated private data;
- perform destructive actions;
- use company credentials for personal work.

Scale human approval requirements with impact and reversibility.

## Definition of Done

AI-generated code follows the same standard as human-generated code. Do not claim completion merely because:

- code was generated;
- tests were written;
- CI is green;
- a tool returned success.

Verify the actual claim at the appropriate layer and leave durable evidence.
