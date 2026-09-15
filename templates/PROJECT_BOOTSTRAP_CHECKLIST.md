# Project Bootstrap Checklist

Use this as a lightweight checklist, not a gate. Skip items that do not improve the current project's outcome or risk profile.

## Outcome

- [ ] State the problem / desired outcome.
- [ ] Define the first credible evidence or acceptance criteria.
- [ ] Decide whether this is a Prototype, PoC, MVP, Pilot, or Production-oriented project.
- [ ] Record important non-goals and constraints.

## Repository context

- [ ] Add a concise README with purpose, run/test instructions, and canonical external links.
- [ ] Add project-local `AGENTS.md` when AI/agent work is expected.
- [ ] Identify the canonical product/spec source if it lives outside GitHub.
- [ ] Keep secrets and private data out of repository history.

## Engineering baseline

- [ ] Choose the smallest stack that fits the problem.
- [ ] Define contracts first where API/data/agent/integration boundaries matter.
- [ ] Add deterministic tests for the first important behavior or failure mode.
- [ ] Add CI once repeatable checks provide enough value to justify it.
- [ ] Use real integration semantics where mocks would hide the primary risk.

## Delivery

- [ ] Define how a verified revision becomes a runnable artifact or deployment.
- [ ] Prefer build-once / immutable artifacts for deployed software when practical.
- [ ] Decide whether deployment should be manual or automated based on risk and frequency.
- [ ] Add runtime/browser/API smoke evidence when build/CI cannot prove the user-visible claim.
- [ ] Make rollback/recovery explicit before high-impact or persistent changes.

## Automation / agent work

- [ ] Persist task/next-action state outside chat for multi-session work.
- [ ] Bound permissions, cost, retries, and side effects.
- [ ] Make scheduled work idempotent/deduplicated where appropriate.
- [ ] Define an objective completion/closure condition.
- [ ] Add observability before increasing autonomy.

## Done

- [ ] Verify acceptance criteria at the correct layer.
- [ ] Save evidence and material decisions durably.
- [ ] Record follow-up work only when it is genuinely useful; do not manufacture backlog.
