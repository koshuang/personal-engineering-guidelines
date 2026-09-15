# Project Maturity and Capability Model

This is a risk-scaled reference, not a mandatory maturity process. Add engineering capability when it improves learning speed, reliability, recovery, or continuity.

## Prototype

Goal: answer whether an idea, interaction, or technical shape is worth pursuing.

Usually enough:

- clear question / hypothesis;
- smallest runnable implementation;
- manual verification may be acceptable;
- disposable data and architecture may be acceptable;
- no production automation unless required by the experiment.

Do not spend heavily on CI, architecture layers, migration systems, or observability unless they are part of the question being tested.

## PoC

Goal: prove a specific technical or integration assumption.

Add what is needed to make the proof credible:

- explicit contract or success criterion;
- test at the actual risk boundary (real API, DB, browser, model, queue, etc.);
- enough logging/evidence to explain success or failure;
- bounded credentials, cost, and side effects;
- repeatable setup when reproduction matters.

A PoC may still be disposable.

## MVP

Goal: test product value with real users using the smallest usable solution.

Usually add:

- core behavior tests;
- CI for cheap repeatable checks;
- basic error visibility;
- secrets/private-data discipline;
- a known deploy/release path;
- runtime or browser/API smoke evidence for material user flows;
- basic backup/recovery thinking when durable user data exists.

Optimize for learning velocity, not architectural completeness.

## Pilot / Beta

Goal: validate product and operations under bounded real-world usage.

Usually add:

- deterministic CI gates for application changes;
- real integration tests where persistence/contracts are material;
- release/source traceability;
- health/readiness checks;
- rollback or fast mitigation path;
- feature flags / progressive rollout when frontend/backend or multiple versions may coexist;
- error monitoring and key product/operational signals;
- alerts for failures that should not wait for manual discovery;
- explicit ownership of migrations, retries, queues, and scheduled work.

## Production / Long-lived

Goal: make delivery and operation repeatable enough that the project can evolve without depending on one session, machine, or person remembering hidden context.

Strong defaults:

### Delivery

- build once in CI when practical;
- deploy an immutable artifact/image tied to a source revision;
- avoid compiling/building application code on the production host unless the topology makes that the safer choice;
- serialize unsafe concurrent deployments;
- verify runtime health after deployment;
- retain a rollback/mitigation path.

### Quality

- fast deterministic tests for business behavior;
- real DB/API/browser/runtime evidence where mocks cannot prove the risk;
- static/type/architecture checks where they prevent recurring defects;
- migration/schema verification for persistent systems;
- security/dependency checks proportionate to exposure.

### Operations

- separate liveness from dependency/readiness health when that distinction matters;
- structured error/operational visibility;
- actionable alerting with noise control;
- monitor scheduled jobs, queues, backups, cost/quota, and other silent-failure paths when material;
- monitor the monitoring for important notification paths;
- preserve enough evidence to reconstruct what was deployed and what happened.

### AI / agent continuity

- repository-local agent contract / routing;
- durable task and next-action state outside chat;
- structured handoffs for multi-agent or multi-session work when useful;
- explicit permission and destructive-action boundaries;
- deterministic checks in code/CI rather than prompts whenever possible.

## Cost-aware CI

CI should maximize useful confidence per unit cost/time.

Good optimization examples:

- run cheaper gates before expensive builds/browser tests;
- use lightweight lanes for docs/metadata-only changes when the complete change can be classified safely;
- avoid duplicate jobs that prove the same thing;
- cache dependencies/build intermediates only when safe and useful;
- cancel obsolete runs when a newer revision replaces them;
- schedule expensive security or synthetic checks at an appropriate cadence instead of every commit when immediate feedback is unnecessary.

Do not weaken required evidence merely to reduce CI usage. Change the shape/frequency of verification instead.

## Observability and alerting

Use the signal source closest to the failure mode:

- application exceptions / regressions → application error monitoring;
- infrastructure saturation / managed-service health → cloud or infrastructure monitoring;
- business/system invariants, cost, quota, stale state → deterministic scheduled scans;
- user-critical flows → synthetic/API/browser checks.

Prefer:

`deterministic detection -> optional AI interpretation -> notification/action`

AI is useful for summarizing, grouping, explaining, or prioritizing signals. It should not be the only detector when a condition can be checked deterministically.

## Progressive rollout and compatibility

Use feature flags, additive contracts, dual-read/write transitions, or other compatibility techniques when they shorten the feedback loop or make deployment safer.

Do not preserve compatibility forever by default. Remove transitional paths once the rollout is complete and evidence says the old path is no longer needed.

## Rule of thumb

If a capability costs more than the risk or learning delay it removes, skip or simplify it.

If failure would be expensive, silent, hard to reverse, or difficult to diagnose later, invest before increasing exposure.
