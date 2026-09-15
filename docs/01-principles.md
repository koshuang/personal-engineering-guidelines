# Engineering Principles

## 1. Outcome before implementation

Define the desired user/personal outcome, observable acceptance criteria, material constraints, and the decision the work should enable before optimizing implementation detail.

## 2. Optimize for the fastest trustworthy feedback loop

Prefer experiments and vertical slices that answer the important question quickly. Faster code production is not useful if verification, deployment, or real usage feedback arrives late.

## 3. Scale rigor with risk and reversibility

Low-risk, cheap, reversible work should move quickly. Add stronger review, tests, migration planning, rollout controls, backups, and manual approval as blast radius and irreversibility increase.

## 4. Contract first when boundaries matter

For APIs, data formats, agent inputs/outputs, persistence semantics, and external integrations, define the observable contract before coupling implementation to a vendor or framework.

## 5. Make important behavior executable

When a rule can be checked deterministically, encode it in tests, scripts, schemas, CI, or runtime guards instead of relying on memory or prompts.

## 6. Prefer small, coherent, reversible changes

Small batches reduce debugging cost, merge conflict, agent coordination cost, and rollback risk. Avoid splitting work so finely that each slice loses independent meaning.

## 7. Keep canonical state explicit

Durable product intent, engineering scope, implementation evidence, runtime state, and personal knowledge may live in different systems. Name the canonical owner instead of maintaining editable copies everywhere.

## 8. Evidence before DONE

A task is complete only when the claimed behavior has proportionate evidence. Green CI is necessary when CI applies, but is not proof of runtime or integration behavior by itself.

## 9. Intentional debt is allowed

A shortcut is acceptable when it materially improves learning or delivery and its risk is understood. Hidden accidental complexity is not justified by calling the project a prototype.

## 10. Continuously improve the baseline

These guidelines are defaults derived from repeated evidence, not doctrine. Promote a practice when it repeatedly improves outcomes or prevents recurring failure; demote it when evidence shows unnecessary cost.
