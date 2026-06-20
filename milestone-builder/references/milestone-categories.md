# Milestone Categories — The 6-Gate System

Every milestone falls into one of six categories (gates). This taxonomy
helps ensure the milestone plan is complete and balanced.

## Gate 1: Decision Gate

**Purpose**: Ratify a critical, high-impact, hard-to-reverse decision.

**When to Use**:
- Architecture choice (monolith vs. microservices)
- Build vs. buy decision
- Vendor or platform selection
- Technology stack commitment
- Org structure or team ownership decision

**Decision Criteria**: The decision is irreversible or extremely costly to
reverse. Delaying it blocks multiple downstream workstreams.

**Typical Milestone Name Patterns**:
- "Architecture Decision Record (ADR) Approved"
- "Vendor Selection Finalized"
- "Build vs. Buy Decision Ratified"

**Example**:
```
M1: Architecture Approved
- ADR-001 through ADR-005 reviewed and signed
- Performance model validated against target SLAs
- Cost model approved by finance
```

## Gate 2: Risk Gate

**Purpose**: Eliminate the highest-uncertainty risk in the project.

**When to Use**:
- Unproven technology or algorithm
- External dependency with unknown reliability
- Regulatory or legal uncertainty
- Scale or performance risk
- Security or compliance risk

**Decision Criteria**: If this risk materializes, the project fails. It
must be addressed before investing further.

**Typical Milestone Name Patterns**:
- "Core Technology PoC Validated"
- "Third-Party API Reliability Proven"
- "Regulatory Pre-Approval Received"
- "Performance Benchmark Met"

**Example**:
```
M1: Payment Institution Onboarding Approved
- Merchant application submitted and acknowledged
- Compliance review completed with no blocking issues
- Test account credentials issued
```

## Gate 3: Capability Gate

**Purpose**: Prove a core system capability works end-to-end.

**When to Use**:
- New capability that is central to project success
- Capability that spans multiple components
- Capability that was flagged as a technical risk

**Decision Criteria**: Without this capability, the project cannot deliver
its value proposition.

**Typical Milestone Name Patterns**:
- "Single-Agent Capability Closed-Loop"
- "Real-Time Data Pipeline Operational"
- "Recommendation Engine Serving Live Traffic"

**Example**:
```
M2: Single Agent Capability Closed-Loop
- Agent successfully executes a complete task from user prompt to result
- Tool calling works across all 5 registered tools
- Response latency < 3 seconds for standard queries
```

## Gate 4: Integration Gate

**Purpose**: Prove that independent systems or teams can work together.

**When to Use**:
- Multi-system projects (frontend + backend + external API)
- Multi-team projects (product + engineering + operations)
- Projects with external dependencies

**Decision Criteria**: The project's value depends on multiple systems
or teams coordinating successfully.

**Typical Milestone Name Patterns**:
- "End-to-End Business Flow Operational"
- "All External APIs Integrated and Monitored"
- "Cross-Team Integration Test Passed"

**Example**:
```
M3: Multi-Agent Collaborative Closed-Loop
- Agent-to-agent handoff completes within SLA
- Shared context propagates correctly across agents
- Conflict resolution works for overlapping tool calls
```

## Gate 5: Validation Gate

**Purpose**: Prove the solution delivers value to real users or stakeholders.

**When to Use**:
- User-facing features
- Business-critical systems
- Any project where success depends on human behavior

**Decision Criteria**: Technical correctness is not enough — real users
must confirm the solution works for them.

**Typical Milestone Name Patterns**:
- "Pilot User Validation Passed"
- "Internal Dogfooding Complete"
- "Stakeholder Demo Approved"
- "User Acceptance Criteria Met"

**Example**:
```
M4: Pilot Business Scenario Validated
- 3 real business use cases executed successfully
- Pilot users report >80% satisfaction
- Task completion rate >90% for defined scenarios
```

## Gate 6: Production Gate

**Purpose**: Prove the system is ready for production operation.

**When to Use**:
- All projects before go-live
- This is always the final milestone

**Decision Criteria**: The system must operate reliably, securely, and
observably in a production environment.

**Typical Milestone Name Patterns**:
- "Production Go-Live"
- "GA Launch"
- "Production Cutover Complete"

**Example**:
```
M5: Production Go-Live
- Monitoring and alerting configured and tested
- Runbooks written and reviewed
- Capacity planning approved for projected load
- Rollback plan tested
- 100% of production traffic migrated
```

## Gate Composition in a Typical Plan

| M# | Gate Type | Focus |
|----|-----------|-------|
| M1 | Risk Gate or Decision Gate | Eliminate the biggest unknown |
| M2 | Capability Gate | Prove the core works |
| M3 | Integration Gate or Capability Gate | Prove things work together |
| M4 | Validation Gate | Prove users find it valuable |
| M5 | Production Gate | Prove it's ready to operate |

Not every plan needs all six gates. A simpler project might only need 3–4.
The key is that each milestone is a genuine outcome, not a process step.
