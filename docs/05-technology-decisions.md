# Technology Decisions

## Capability before vendor

Choose technology for the capability and feedback loop it enables, not because it appears in another project.

Before choosing a framework, database, cloud, CI provider, observability vendor, or deployment platform, identify:

1. the outcome and first credible evidence;
2. the operational risk and reversibility;
3. the smallest capability set required now;
4. the cost of changing later;
5. whether an existing personal implementation meaningfully reduces delivery risk.

## Default decision order

Prefer, in order:

1. **Existing proven fit** — reuse a stack or service already understood when it materially shortens delivery or operational uncertainty.
2. **Simplest adequate option** — prefer fewer moving parts when they satisfy the current outcome.
3. **Explicit boundary** — hide replaceable vendors/framework details behind a useful contract when future replacement is plausible or costly.
4. **Evidence before standardization** — repeated successful use may justify a personal default; one project does not.

## When reuse is valuable

Reusing an existing technology is especially valuable when it gives:

- known deployment and rollback behavior;
- existing integration or test harnesses;
- known operational failure modes;
- existing observability/security configuration;
- lower AI/agent context and setup cost;
- reusable scripts, templates, or skills.

Reuse is not valuable when it imports unnecessary infrastructure, ceremony, or cognitive load into a smaller problem.

## Stack defaults are contextual

There is no universal personal mandate for:

- one frontend framework;
- one backend language;
- one database;
- one cloud provider;
- one CI vendor;
- one observability platform;
- containers or Kubernetes for every project.

A technology may become a **preferred starting point for a problem class** after repeated evidence, but the decision should remain explainable in terms of outcome, risk, speed, and operating cost.

## Architecture investment

Add architectural boundaries where they protect a real seam:

- business rules from frameworks/storage;
- external APIs/providers;
- persistent data semantics;
- authentication/authorization;
- asynchronous workflows;
- AI/model providers;
- high-cost or high-change integrations.

Do not create interfaces, layers, services, or abstractions solely to satisfy an architecture pattern. A small project may begin directly and introduce a boundary once replacement, testing, or change pressure becomes real.

## Technology change

Treat migration as a product/engineering investment. Before replacing an existing component, state:

- what outcome improves;
- what evidence proves the current solution is insufficient;
- migration and rollback path;
- compatibility period if any;
- operational and data risk;
- how success will be measured after cutover.

Avoid rewrites whose primary evidence is preference rather than an observed constraint.
