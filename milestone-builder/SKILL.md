---
name: milestone-builder
description: |
  Transform project requirements and task breakdowns into outcome-driven milestones,
  actionable checklists, exit criteria, and evidence requirements. This skill should
  be used when users need to create a milestone plan, decompose a project into
  achievement gates, build milestone checklists, define project exit criteria, or
  produce a structured execution roadmap. Triggers on requests like "help me build
  milestones for this project", "create a milestone plan from this PRD", "decompose
  this spec into milestones", "I need a project roadmap with checklists", "define
  exit criteria for these milestones", or when a PIC/Tech Lead/TPM/EM shares project
  documents and asks for structured planning output. Applies to software projects,
  AI/ML projects, platform projects, microservice projects, and enterprise technical
  projects.
---

# Milestone Builder

Transform project inputs into a complete **Milestone Plan** with checklists, exit
criteria, and evidence requirements. The skill enforces outcome-driven planning
and risk-first ordering — it never produces SDLC-phase milestones (development
→ testing → deployment) as top-level gates.

## Core Philosophy

Three layers, strictly separated:

| Layer | Definition | Example |
|-------|------------|---------|
| **Milestone** | A key achievement that proves project progress (Outcome) | "Payment institution onboarding approved" |
| **Checklist** | Concrete actions required to reach the milestone (Activities) | "Submit merchant application documents" |
| **Evidence** | Verifiable proof that the milestone is truly complete (Proof) | "Approval email from payment institution" |

Hard rule: **Milestones are achievements, not activities.** Never promote an
SDLC phase (Development Completed, Testing Completed, UAT Completed) to a
Milestone — those are Checklist items.

For the full methodology behind this philosophy, consult
[references/milestone-methodology.md](references/milestone-methodology.md).

## When to Use

Invoke this skill when the user:

- Shares a PRD, spec, or task breakdown and asks for milestones
- Says "help me plan this project" or "decompose this into milestones"
- Is a PIC/Tech Lead/TPM/EM preparing for a project kickoff or review
- Needs a milestone plan with checklists, exit criteria, and evidence
- Wants to validate an existing milestone plan against best practices
- Asks to "review my milestones" or "are my milestones outcome-driven?"

## Input Schema

The skill accepts one or more of the following as input:

1. **Project requirements document** (PRD, spec, proposal) — the target goal
2. **Task breakdown / WBS** — existing activity-level decomposition (optional)
3. **Constraints** — deadline, budget, team size, dependencies (optional)
4. **Risk register** — known risks and concerns (optional)

If only a task breakdown is provided without requirements, ask for the goal
document before proceeding. The skill cannot build outcome milestones from
activity lists alone — it needs to know what success looks like.

## Reasoning Framework

Execute these steps in order before producing any output. Do not skip steps.
Show a brief summary of each step's findings before proceeding to output.

### Step 1 — Define Project Success

Ask and answer: *What does success look like?*

Reduce to a single sentence that an executive would understand:
> "Users can resolve support issues through an AI chatbot without human
> intervention for Tier-1 queries."

If the input lacks a clear success definition, pause and ask the user.

### Step 2 — Identify Risks

List every risk that could prevent success. Categorize:

- **Technical risk** — unproven technology, scale, performance
- **Integration risk** — external dependencies, API contracts
- **Business risk** — regulatory, legal, stakeholder alignment
- **Operational risk** — team capacity, skill gaps, timeline

### Step 3 — Rank Risks

Order risks by: likelihood × impact. The highest-ranked risk determines
Milestone 1 (Risk First Principle).

### Step 4 — Identify Required Capabilities

Derive from the success definition: what capabilities must exist?
These are NOT features — they are *abilities the system must have*.

> Example: "The system must be able to classify customer intent from
> natural language queries in < 500ms."

### Step 5 — Identify Integration Requirements

What external systems, teams, or APIs must the project integrate with?
Each integration is a source of risk and may warrant its own milestone.

### Step 6 — Identify Business Validation Requirements

What must be proven to real users or stakeholders before the project
can be considered successful? Examples: user acceptance testing, pilot
program, stakeholder demo, compliance sign-off.

### Step 7 — Identify Production Readiness Requirements

What must be true for the system to operate in production? Examples:
monitoring, alerting, runbooks, capacity planning, SLA guarantees.

### Step 8 — Generate Milestones (3–7 total)

Group the capabilities, integrations, validations, and production
requirements into 3–7 outcome milestones. Apply the [6-Gate category
system](references/milestone-categories.md) to classify each milestone.

Apply Risk First ordering: the milestone that eliminates the highest
risk becomes M1.

### Step 9 — Generate Checklists

For each milestone, produce 3–7 concrete, verifiable checklist items.
Each item must be an activity that can be unambiguously checked off.

### Step 10 — Generate Exit Criteria

For each milestone, define 1–3 conditions that MUST be true for the
milestone to be considered complete. Exit criteria differ from checklist
items — they are binary gates, not tasks.

### Step 11 — Generate Evidence Requirements

For each milestone, specify the proof artifacts that demonstrate
completion. Evidence must be durable, shareable, and independently
verifiable.

### Step 12 — Perform Quality Review

Run the [Quality Review Framework](#quality-review-framework) against
the output. Flag and fix any issues before presenting the final result.

## Milestone Categories (6-Gate System)

Classify every milestone into one of these six categories. For detailed
criteria, scenarios, and case studies, refer to
[references/milestone-categories.md](references/milestone-categories.md).

| Gate | Purpose | When to Use |
|------|---------|-------------|
| **Decision Gate** | Approve a critical choice (architecture, vendor, tech stack) | High-impact irreversible decisions |
| **Risk Gate** | Eliminate the highest uncertainty | Unproven technology, external dependency, regulatory risk |
| **Capability Gate** | Prove a core capability works end-to-end | New capability that must be demonstrated |
| **Integration Gate** | Prove systems work together | Multi-system, multi-team projects |
| **Validation Gate** | Prove value to real users/stakeholders | User-facing features, business-critical systems |
| **Production Gate** | Prove readiness for production operation | All projects before go-live |

## Milestone Construction Rules

Each milestone must satisfy ALL of these rules:

1. **The "So What?" Test**: If presented to an executive, they should say
   "Good, a major risk is eliminated" — not "So what?"
2. **Binary Verdict**: It must be answerable with "Done" or "Not Done."
   No partial credit.
3. **Risk-Linked**: State explicitly which risk(s) this milestone eliminates.
4. **Value-Linked**: State explicitly what value is validated by this milestone.
5. **Independent**: Completing this milestone should deliver value even if
   later milestones are never reached.

### Anti-Patterns — Never Do This

For a comprehensive catalog, see [references/anti-patterns.md](references/anti-patterns.md).

| Anti-Pattern | Why Wrong | Fix |
|--------------|-----------|-----|
| "Development Completed" | Activity, no proof of working | "Core engine passes 100-test smoke suite" |
| "Testing Completed" | Activity, no risk addressed | "Performance benchmark meets SLA targets" |
| "UAT Completed" | Activity, no outcome stated | "Pilot users achieve 90% task success rate" |
| Milestones without exit criteria | Unverifiable | Add binary exit criteria to every milestone |
| Feature lists as milestones | Too granular, no risk story | Group features into capability achievements |

## Checklist Construction Rules

For each milestone, generate 3–7 checklist items that are:

- **Actionable**: Start with a verb ("Deploy," "Configure," "Draft," "Run")
- **Verifiable**: A third party could confirm completion without asking you
- **Scoped**: Completable within the milestone window, not spanning milestones
- **Concrete**: No vague items like "Handle edge cases" — specify which cases

## Exit Criteria Framework

Exit criteria are binary conditions. They are NOT tasks — they are the
measurable proof that a milestone is achieved.

Format each exit criterion as a yes/no question:
> "Can the system classify 100 intents with >90% accuracy?"

Exit criteria differ from checklist items:
- Checklist: "Train intent classification model on 10k examples"
- Exit criterion: "Model achieves >90% accuracy on held-out test set"

Each milestone must have 1–3 exit criteria.

## Evidence Framework

For each milestone, specify 1–3 evidence artifacts:

- **Durable** — a document, dashboard, or record (not a verbal confirmation)
- **Shareable** — can be linked or attached in a status report
- **Verifiable** — a third party can independently assess it

| Evidence Type | Examples |
|---------------|----------|
| Document | Design doc, API contract, runbook, test report |
| Artifact | Working demo URL, dashboard screenshot, build log |
| Approval | Sign-off email, Jira ticket status, meeting minutes |
| Data | Benchmark results, error rate chart, user feedback summary |

## Quality Review Framework

Before presenting the final output, verify ALL of the following:

- [ ] Every milestone passes the "So What?" test
- [ ] Milestone count is between 3 and 7
- [ ] The highest risk is addressed in M1 or M2
- [ ] No SDLC phase appears as a top-level milestone
- [ ] Each milestone has 1–3 exit criteria (binary)
- [ ] Each milestone has 1–3 evidence requirements
- [ ] Each milestone has a checklist of 3–7 concrete items
- [ ] Checkpoints form a logical value progression (M1 → M5 approaches success)
- [ ] A new team member could understand project status from this plan

## Output Template

Produce output in the following structure:

```markdown
# Milestone Plan: [Project Name]

## 1. Project Success Definition
[Single sentence — what does winning look like?]

## 2. Risk Assessment

### Top Risks (Ranked)
| # | Risk | Category | Likelihood | Impact | Addressed By |
|---|------|----------|------------|--------|--------------|
| 1 | ...   | ...      | High/Med/Low | High/Med/Low | M1 |
| 2 | ...   | ...      | ...          | ...          | M2 |

## 3. Milestone Overview

| M# | Name | Category | Eliminates Risk | Validates |
|----|------|----------|-----------------|-----------|
| M1 | ...  | Risk Gate | Risk #1          | ...       |

## 4. Detailed Milestones

### M1: [Milestone Name]
- **Category**: [Gate type]
- **Risk Eliminated**: [Which risk from the risk table]
- **Value Validated**: [What is proven by this milestone]

**Exit Criteria** (binary):
1. [Yes/no condition]
2. [Yes/no condition]

**Checklist**:
- [ ] [Actionable, verifiable task]
- [ ] [Actionable, verifiable task]

**Evidence Required**:
1. [Type] — [Specific artifact]
2. [Type] — [Specific artifact]

### M2: ...
[Repeat for all milestones]

## 5. Execution Path

[Mermaid or text diagram showing milestone sequence and dependencies]
```

## Post-Output Interaction

After presenting the milestone plan, ask:
> "Would you like me to adjust any milestone, add detail to a checklist,
> or reorder based on additional constraints?"

## References

- [references/milestone-methodology.md](references/milestone-methodology.md) —
  Full methodology: why outcome-driven milestones matter, the 5 purposes,
  industry patterns (Google, Microsoft), and the Risk First Principle
- [references/milestone-categories.md](references/milestone-categories.md) —
  Detailed 6-Gate system with criteria, scenarios, and case studies
- [references/anti-patterns.md](references/anti-patterns.md) —
  Comprehensive catalog of milestone anti-patterns with diagnosis and fixes

## Examples

- [examples/example-ai-agent-platform.md](examples/example-ai-agent-platform.md) —
  Complete input/output: building an AI Agent platform
- [examples/example-payment-gateway.md](examples/example-payment-gateway.md) —
  Complete input/output: integrating a new payment channel
