# Context and Rule Inheritance

## Goal

Humans and agents should be able to enter a project and determine quickly:

- what outcome is being pursued;
- which source is canonical for each type of information;
- which shared defaults apply;
- which project-specific rules intentionally differ;
- what evidence is required before claiming completion.

## Context order

Read from broad to specific:

1. **Personal Engineering Guidelines** — shared defaults and principles.
2. **Project-local `AGENTS.md` / README** — project-specific operating contract and entry points.
3. **Current Issue / roadmap / specification / ADR / runbook** — task and decision context.
4. **Current code / tests / CI configuration** — executable implementation and verification truth.
5. **Runtime state / deployment / telemetry** — actual operational truth when runtime claims matter.

A more specific source may intentionally override a shared default.

## Local override rule

A project-local rule should explain a material deviation when the reason is not obvious, especially when it changes:

- security or credential handling;
- privacy boundaries;
- production/deployment authority;
- testing or verification depth;
- migration/rollback expectations;
- recurring cost or external side effects.

Specific context may reduce ceremony, but it should not silently weaken a safety or evidence boundary whose underlying risk still exists.

## Canonical ownership

Avoid keeping the same mutable rule in multiple places. Prefer links and routing.

Typical ownership:

- shared engineering principle → this repository;
- reusable execution workflow → Skill / Runbook;
- executable bootstrap/release mechanism → template repository or scripts;
- project-specific implementation rule → project-local `AGENTS.md` / docs;
- product intent → designated product/spec source;
- engineering task state → Issue / roadmap / task tracker;
- implementation and verification → PR / code / tests / CI;
- operational truth → runtime / monitoring / deployment evidence.

If two sources conflict, resolve the authority conflict rather than copying both versions forward.

## Keep the always-loaded context small

`AGENTS.md` should primarily contain invariants, authority boundaries, routing, and completion rules that are needed frequently.

Move detailed, situational material into focused docs/skills/runbooks and route to them when needed. This reduces human and model context cost without making important rules undiscoverable.

## Durable handoff

For multi-session or multi-agent work, preserve enough structured state that a fresh agent can continue without the prior transcript. At minimum, durable state should make clear:

- target/outcome;
- current status;
- acceptance criteria;
- evidence already obtained;
- unresolved risks/decisions;
- next useful action;
- authority or permission constraints.

The downstream agent should re-read current repository/CI/runtime state rather than trusting the handoff as proof.

## Prevent rule drift

When the same guidance starts appearing repeatedly in project-local prompts or reviews:

1. determine whether it is truly cross-project;
2. if yes, promote the principle here or the executable workflow into a shared Skill/Runbook;
3. replace duplicated local prose with a link plus only the project-specific delta;
4. keep deterministic enforcement in code/tests/CI when possible.

Do not centralize a rule merely because it can be centralized. Promote only when shared ownership reduces confusion or repeated work.
