# Milestone Anti-Patterns — Common Mistakes & Fixes

This catalog documents the most common mistakes in milestone planning and
how to fix each one.

## Anti-Pattern 1: SDLC Phases as Milestones

**What it looks like**:
```text
M1: Development Completed
M2: Testing Completed
M3: UAT Completed
M4: Deployment Completed
```

**Why it's wrong**: These are activities (process steps), not achievements
(outcomes). "Development completed" conveys zero information about whether
anything works. Each phase can be "100% complete" while the project is
failing.

**How to fix it**: Replace each phase with the outcome it was meant to achieve.

| Instead of... | Ask... | Replace with... |
|---------------|--------|-----------------|
| Development Completed | What capability is now available? | "Core engine processes a request end-to-end" |
| Testing Completed | What quality bar is now met? | "System passes SLA benchmark under peak load" |
| UAT Completed | What did users confirm? | "Pilot users achieve 90% task completion rate" |
| Deployment Completed | What is now live? | "100% of production traffic migrated" |

## Anti-Pattern 2: Feature Lists as Milestones

**What it looks like**:
```text
M1: User login
M2: Dashboard
M3: Search
M4: Notifications
M5: Settings
```

**Why it's wrong**: Feature lists are granular and don't tell a story about
risk, value, or progress. They also tend to multiply — a project with 20
features would produce an unmanageable 20 milestones.

**How to fix it**: Group features into capability or value achievements.

```text
M1: Core platform with authentication and basic navigation
M2: Primary user workflows operational (search → view → act)
M3: Complete user experience with supporting features
```

## Anti-Pattern 3: No Exit Criteria

**What it looks like**:
```text
M2: Core capability operational
Checklist:
- [ ] Set up database
- [ ] Implement API
- [ ] Build frontend
```

**Why it's wrong**: Without exit criteria, there's no way to know if the
milestone is truly achieved. "Set up database" is checked off — but does
it handle the required throughput? Is it secure? Nobody knows.

**How to fix it**: Add binary exit criteria to every milestone.

```text
Exit Criteria:
1. API responds to all 12 documented endpoints with <200ms p95 latency
2. Database handles 1000 concurrent connections without degradation
3. Frontend passes accessibility audit (WCAG 2.1 AA)
```

## Anti-Pattern 4: Activity Language in Milestone Names

**What it looks like**:
```text
M1: Write design document
M2: Set up CI/CD pipeline
M3: Conduct code review
M4: Run performance tests
```

**Why it's wrong**: Milestone names that start with verbs describe activities,
not outcomes. An activity is something you do; an outcome is something you
achieve.

**How to fix it**: Rewrite using noun phrases that describe a state.

| Activity Language | Outcome Language |
|-------------------|-----------------|
| Write design document | Design document approved |
| Set up CI/CD pipeline | CI/CD pipeline operational |
| Conduct code review | Codebase passes review gates |
| Run performance tests | Performance benchmarks met |

## Anti-Pattern 5: Risk Buried Late

**What it looks like**:
```text
M1: Frontend scaffolding
M2: Backend API
M3: Database setup
M4: Third-party integration
M5: Launch
```

**Why it's wrong**: If the third-party integration is the highest risk (the
external API might not support the needed throughput), it should be validated
first — not in M4 after most of the budget is spent.

**How to fix it**: Move the riskiest milestone to M1.

```text
M1: Third-party API validated (throughput, reliability, cost)
M2: Database schema and core API operational
M3: Frontend integrated with backend
M4: Full user flow validated
M5: Launch
```

## Anti-Pattern 6: Too Many or Too Few Milestones

**Symptoms**:
- **Too many** (>10): Milestones are really just tasks. The plan loses
  its function as a high-level progress map.
- **Too few** (<3): Milestones are too coarse. Months pass between gates,
  and the team loses visibility.

**How to fix it**: Target 3–7 milestones. If you have more than 7, group
them. If you have fewer than 3, decompose the largest one.

## Anti-Pattern 7: Milestones with No Evidence

**What it looks like**: A milestone plan with checklist items but no
evidence requirements. The only proof of completion is the PIC saying
"it's done."

**Why it's wrong**: Without evidence, milestone completion is subjective.
Different stakeholders will disagree about whether the milestone is
truly achieved.

**How to fix it**: For every milestone, specify at least one evidence
artifact: a document, a dashboard, a test report, a sign-off, or a
working demo URL.

## Anti-Pattern 8: All Milestones Are the Same Type

**What it looks like**: Every milestone is a Capability Gate. There's no
Decision Gate, no Validation Gate, no Production Gate.

**Why it's wrong**: A project needs different types of milestones to address
different types of risk and value. An all-capability plan may deliver
working software that nobody wants, or that can't be operated in production.

**How to fix it**: Use the 6-Gate system to audit coverage. Ask:
- Is there a Decision Gate for high-impact choices?
- Is there a Validation Gate for user/stakeholder feedback?
- Is there a Production Gate for operational readiness?

## Quick Self-Audit

Before finalizing any milestone plan, run these checks:

- [ ] Zero SDLC phases as top-level milestones
- [ ] Zero verb-first milestone names
- [ ] 3–7 total milestones
- [ ] Highest risk in M1 or M2
- [ ] Every milestone has exit criteria
- [ ] Every milestone has evidence requirements
- [ ] At least one Validation Gate before Production Gate
- [ ] A Production Gate exists (for projects that go live)
