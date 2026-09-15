# Anonymized Practice Patterns

These examples are distilled from real engineering work across personal and professional projects. They are intentionally anonymized and simplified so the reusable engineering decision remains visible without exposing private product, company, customer, infrastructure, or incident details.

They are **examples, not mandates**. The goal is to show how the principles in this repository have been applied under real constraints.

## 1. High-volume query: bound the failure before finishing the optimization

A high-traffic SaaS backend had a cached aggregate query whose cost increased sharply as daily data volume grew. Under a heavy import window, concurrent cache misses could amplify database load.

The improvement path was staged:

1. add a bounded database statement timeout and structured duration/outcome logging so failure becomes visible and contained;
2. use production-like query plans and representative data to identify the actual expensive predicate/query shape;
3. preserve semantic parity while restructuring the query;
4. measure cold and warm behavior separately;
5. when the remaining cost proved to be random row lookups, add a covering index only after rehearsing the schema change under representative load and lock conditions.

**Lesson:** observability and bounded failure are useful intermediate outcomes. Do not wait for the perfect optimization before making an expensive path measurable and safe.

## 2. Mature backend: fast behavior lane + thin fidelity lane

A mature backend had substantial business behavior covered mostly by database-bound tests. That made structural refactoring slow and expensive.

The migration strategy was:

- introduce ports around persistence/external seams;
- pin business behavior with hand-written in-memory fakes and shared contract tests;
- move most use-case flow verification into a fast deterministic lane;
- keep thin real-database or real-adapter contract tests where SQL/persistence/gateway fidelity actually matters;
- avoid creating a fake for pure collaborators when a faithful fake would merely duplicate the production algorithm.

**Lesson:** most business behavior should be cheap to verify, but fast tests are not a substitute for real integration semantics at the boundaries where fidelity matters.

## 3. Long-lived coding agent: small kernel, routed context, durable state

A long-running AI-assisted refactoring workflow initially loaded too much static context and relied too heavily on session continuity.

It evolved toward:

- a small always-loaded invariant kernel;
- a router to load task-specific rules only when needed;
- durable task/run state outside chat;
- explicit ownership/lease and checkpoint semantics;
- structured implementation/review/verifier handoffs;
- re-polling repository, CI, and review state before declaring completion;
- deterministic run-log fields and reconciliation rules;
- prompt/rule changes evaluated with isolated contexts rather than trusting intuition alone.

**Lesson:** agent effectiveness is often a context/state-engineering problem, not just a model-quality problem. Keep durable truth outside the transcript and require objective evidence at handoff boundaries.

## 4. Existing production infrastructure: import first, mutate later

An existing production edge configuration needed to move under Infrastructure as Code.

Instead of combining adoption and redesign, the first step was deliberately import-only:

- inventory live resources;
- model only configuration intentionally owned by the team;
- import existing state;
- prove the post-import plan is no-change;
- keep credentials out of the repository;
- defer policy redesign and drift automation to later changes.

**Lesson:** bringing an existing system under management is a different operation from changing that system. Separating them materially reduces blast radius and makes review clearer.

## 5. Operational alert: deterministic detection, optional AI interpretation

A background-work system needed to surface growing backlog before it became a customer-visible incident.

The alert path used:

- scheduled deterministic threshold checks;
- per-signal detail rather than a single opaque failure flag;
- cooldown/deduplication while a breach remains active;
- immediate re-arm after recovery;
- a common team notification destination;
- explicit handling for a missing notification integration;
- heartbeat/test-delivery checks for important alert paths.

AI can summarize, group, explain, or prioritize these signals, but it is not the sole detector when the condition can be computed deterministically.

**Lesson:** an alert is an execution mechanism, not merely a dashboard metric. It needs ownership, noise control, actionable context, and proof that the notification path itself works.

## 6. Cross-component feature: fail-closed progressive rollout

A feature spanned independently deployed frontend and backend components, so a perfectly atomic release was unrealistic.

The rollout used additive contracts and coordinated feature flags that defaulted off. Compatibility rules allowed old and new versions to coexist during the transition, and activation happened only after both sides were ready.

**Lesson:** compatibility and feature flags are acceleration tools when they reduce coordination risk. They are not ceremony to apply to every change.

## 7. CI cost: choose the cheapest trustworthy lane

A project had meaningful CI cost constraints but still needed stable required checks.

Instead of removing validation, the workflow classified the complete change scope and routed it:

- documentation-only work used a lightweight lane;
- application/runtime/dependency changes ran the full gates;
- expensive build/browser/database work happened after cheaper deterministic checks;
- repeated policy checks were folded into existing jobs rather than creating extra runner lanes;
- production credentials were not required merely to verify a build.

**Lesson:** CI optimization should reduce unnecessary work, not reduce confidence in the claim being made.

## 8. Workflow tools: preserve responsibility, not ceremony

A delivery process used different surfaces for product intent, engineering scope, implementation, and review evidence. Over time it became clear that requiring every artifact for every change created unnecessary overhead.

The refined rule became:

- preserve product intent;
- preserve enough engineering scope/acceptance criteria for the risk;
- preserve implementation and verification evidence for material changes;
- link canonical sources instead of copying mutable requirements everywhere;
- skip or combine artifacts when a shorter path provides the same trustworthy outcome.

**Lesson:** business value and trustworthy feedback are higher-order goals than process completeness.
