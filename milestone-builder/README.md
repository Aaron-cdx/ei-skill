# Milestone Builder

A Claude Code skill that transforms project requirements and task breakdowns into
**outcome-driven milestones** with actionable checklists, exit criteria, and
evidence requirements.

Built on the principle: **Milestones are achievements, not activities.**

## Philosophy

Most project plans mistake the software development lifecycle (SDLC) for milestones:

```text
❌ Development → Testing → UAT → Deployment
```

This skill produces outcome-driven milestones instead:

```text
✅ Risk eliminated → Capability proven → Integration verified → User validated → Production ready
```

Each milestone = **Key Achievement + Risk Eliminated + Value Validated**

For the full methodology, see [references/milestone-methodology.md](references/milestone-methodology.md).

## What This Skill Produces

For any project input (PRD, spec, task breakdown), the skill outputs:

| Output | Description |
|--------|-------------|
| **Success Definition** | One sentence — what does winning look like? |
| **Risk Assessment** | Top risks ranked by likelihood × impact |
| **Milestones (3–7)** | Outcome gates, each classified by gate type |
| **Exit Criteria** | Binary yes/no conditions per milestone |
| **Checklists** | 3–7 actionable, verifiable tasks per milestone |
| **Evidence Requirements** | Durable proof artifacts per milestone |
| **Execution Path** | Milestone sequence with dependencies |

## Installation

**Prerequisites**: [Claude Code](https://docs.anthropic.com/en/docs/claude-code) + Git

### One-Click Install

```bash
# Install to current project (recommended)
git clone --depth 1 https://github.com/Aaron-cdx/ei-skill.git /tmp/ei-skill && mkdir -p .claude/skills && cp -r /tmp/ei-skill/milestone-builder .claude/skills/ && rm -rf /tmp/ei-skill
```

```bash
# Install globally (available across all projects)
git clone --depth 1 https://github.com/Aaron-cdx/ei-skill.git /tmp/ei-skill && mkdir -p ~/.claude/skills && cp -r /tmp/ei-skill/milestone-builder ~/.claude/skills/ && rm -rf /tmp/ei-skill
```

### PowerShell (Windows)

```powershell
git clone --depth 1 https://github.com/Aaron-cdx/ei-skill.git $env:TEMP/ei-skill; mkdir -p .claude/skills; cp -r $env:TEMP/ei-skill/milestone-builder .claude/skills/; rm -r -fo $env:TEMP/ei-skill
```

### Verify

In Claude Code, run `/milestone-builder` — if the skill is recognized, you're ready.

## Usage

### Basic Usage

Provide project documents and ask for a milestone plan:

```
/build a milestone plan for this PRD
```

Or with a specific file:

```
/ milestone-builder -- read spec.md and build milestones
```

### Trigger Phrases

The skill activates automatically when you use phrases like:

- "Help me build milestones for this project"
- "Create a milestone plan from this PRD"
- "Decompose this spec into milestones"
- "I need a project roadmap with checklists"
- "Define exit criteria for these milestones"
- "Review my milestones — are they outcome-driven?"

### Input Format

Provide one or more of:
1. **Project requirements** (PRD, spec, proposal) — required
2. **Task breakdown / WBS** — optional, will be restructured
3. **Constraints** — deadline, budget, team size
4. **Risk register** — known concerns

Example prompt:
```
Here's my project spec:

[ paste or reference your spec ]

Please build a milestone plan with checklists and exit criteria.
```

### What Happens Internally

The skill runs a 12-step reasoning process before producing output:

1. Define project success
2. Identify risks
3. Rank risks (Risk First Principle)
4. Identify required capabilities
5. Identify integration requirements
6. Identify business validation requirements
7. Identify production readiness requirements
8. Generate milestones (classified into 6 gate types)
9. Generate checklists
10. Generate exit criteria
11. Generate evidence requirements
12. Quality review (self-audit)

Then it presents the complete Milestone Plan and asks if you want adjustments.

## Example

**Input**: A PRD for building an AI Agent platform with a 6-month timeline and
8-person team.

**Output**: 5 milestones with risk assessment, exit criteria, checklists, and
evidence requirements.

See the full example at [examples/example-ai-agent-platform.md](examples/example-ai-agent-platform.md).

## Skill Structure

```
milestone-builder/
├── SKILL.md                              # Main skill instructions
├── README.md                             # This file
├── references/                           # Detailed methodology docs
│   ├── milestone-methodology.md          # Philosophy & industry patterns
│   ├── milestone-categories.md           # 6-Gate system detail
│   └── anti-patterns.md                  # Common mistakes catalog
└── examples/                             # Complete input/output examples
    ├── example-ai-agent-platform.md
    └── example-payment-gateway.md
```

## Who This Is For

- **PIC (Person In Charge)** — First-time project leads learning to plan
- **Tech Lead / Engineering Manager** — Structuring team projects for executive visibility
- **TPM (Technical Program Manager)** — Standardizing milestone format across programs
- **Product Manager** — Aligning product milestones with engineering reality

## Key Concepts

### The 6-Gate System

| Gate | Purpose |
|------|---------|
| Decision Gate | Ratify irreversible choices |
| Risk Gate | Eliminate highest uncertainty |
| Capability Gate | Prove core capability works |
| Integration Gate | Prove systems work together |
| Validation Gate | Prove value to real users |
| Production Gate | Prove readiness for operation |

### The Three Layers

| Layer | Question Answered |
|-------|-------------------|
| Milestone | What achievement was reached? |
| Checklist | What actions were taken? |
| Evidence | How do we know it's really done? |

### Quality Standards

Every output is self-audited against 9 quality gates before presentation,
including the "So What?" test: if you presented this milestone to an
executive, would they say "Good, a major risk is eliminated" or "So what?"

## Contributing

To suggest improvements or report issues:
1. Open an issue on GitHub
2. Submit a PR with changes to SKILL.md or reference files
3. For new examples, add to the `examples/` directory

## License

MIT
