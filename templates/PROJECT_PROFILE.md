# Project Profile

Use this only when it materially improves routing. Typical triggers are project bootstrap, a maturity/risk change, a new deployment/runtime boundary, or repeated confusion about which capabilities/evidence the project actually requires.

Do **not** add or keep this file merely for consistency. If the existing README / `AGENTS.md` / roadmap / runbooks already make the maturity, risk, canonical sources, and required evidence unambiguous, this profile may be unnecessary.

Keep it short; it is a routing aid, not ceremony and not a second copy of repository policy.

## Adoption gate

Create or update this profile when at least one of these is true:

- project maturity has changed (for example PoC → MVP, MVP → Pilot, Pilot → Production);
- blast radius, persistent data, credentials, money, external side effects, recurring cost, or operational ownership materially changed;
- agents or humans repeatedly choose the wrong verification, delivery, or safety level;
- canonical-source precedence is unclear across shared and repo-local rules;
- the project needs an explicit local strengthening/narrowing of the shared baseline.

Prefer no profile when none of those conditions exists.

## Outcome

- Problem / desired outcome:
- First credible evidence:
- Current delivery mode: Prototype / PoC / MVP / Pilot / Production
- Primary users / operator:
- Important non-goals:

## Risk profile

- Reversibility: low / medium / high
- Blast radius: low / medium / high
- Persistent data: none / limited / material
- External side effects: none / limited / material
- Credentials / private data / money involved: no / yes
- Recurring infrastructure / API cost: low / medium / high

## Capability profile

Mark only what is justified now.

- [ ] Project-local `AGENTS.md`
- [ ] Deterministic local tests
- [ ] CI quality gate
- [ ] Real database / API / browser integration evidence
- [ ] Build/package verification
- [ ] Immutable artifact or image
- [ ] Deployment traceability to source revision
- [ ] Runtime health/readiness check
- [ ] Rollback/recovery path
- [ ] Error/usage observability
- [ ] Actionable alerting
- [ ] Scheduled/autonomous-work recovery
- [ ] Privacy/security scrubbing

## Canonical sources

- Product/spec:
- Engineering task state:
- Repository rules:
- Runtime state:
- Long-form knowledge:

## Current deliberate exceptions

Record only meaningful deviations from the shared baseline.

| Exception | Why | Risk accepted | Revisit trigger |
| --- | --- | --- | --- |
| | | | |

## Next maturity trigger

What real-world condition would justify adding the next layer of engineering capability?

## Removal trigger

Remove or fold this profile back into existing repo documentation if it becomes stale, duplicates stronger canonical sources, is rarely consulted, or no longer changes engineering decisions.
