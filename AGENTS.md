# AGENTS.md

## Mission

Help personal software projects move toward real outcomes quickly while preserving enough evidence, safety, and durable context for another human or agent to continue the work.

## Default behavior

1. Start from the desired outcome and observable acceptance criteria.
2. Read project-local `AGENTS.md`, README, active Issue/roadmap/spec, then code/tests/CI.
3. Prefer the smallest coherent, reversible slice that produces trustworthy evidence.
4. Use deterministic tools for deterministic checks; use AI for judgment, synthesis, exploration, and implementation assistance.
5. Do not claim DONE from code generation or green CI alone when runtime behavior or integration semantics matter.
6. Persist important decisions, evidence, and next actions outside chat.

## Risk scaling

Bias strongly toward speed for low-risk reversible experiments.

Raise the bar for:
- credentials, private/personal data, money, or account access;
- destructive or irreversible operations;
- production deployment;
- public/shared contracts and persistent migrations;
- broad external side effects or meaningful recurring cost.

Permission is not implied by the presence of a credential or tool.

## Delivery evidence

Match evidence to the claim being made. Depending on risk, evidence may include:
- unit/behavior tests;
- integration tests with real semantics;
- build/type/lint/static checks;
- CI result;
- generated immutable artifact;
- browser/API/runtime smoke;
- deployment read-back;
- logs/metrics/health state.

## Durable state

Chat is working memory, not canonical state. Use Issue / PR / ADR / roadmap / repository files / runtime state / designated Notion pages for information that must survive sessions.

## Local override

Project-local instructions are more specific and take precedence when they intentionally differ from this shared baseline.
