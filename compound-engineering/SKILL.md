---
name: compound-engineering
description: >
  Compound Engineering methodology where each unit of work makes subsequent work easier.
  Applies the Plan → Work → Review → Compound loop, 8 beliefs to unlearn, 5-stage adoption
  ladder, agent-native architecture, and the 50/50 rule. Auto-invokes on engineering workflow
  discussions, planning, code review strategy, and AI-augmented development.
---

# Compound Engineering

Source: https://every.to/guides/compound-engineering

## Core Philosophy

Each unit of engineering work should make subsequent units easier — not harder. Traditional development accumulates complexity; compound engineering flips this so features, fixes, and patterns become tools for future work.

---

## The Main Loop

**Plan → Work → Review → Compound → Repeat**

Time allocation: **80% on planning and review, 20% on execution and compounding.**

### Step 1: Plan
- Understand the requirement (what, why, constraints)
- Research the codebase (similar functionality, existing patterns)
- Research externally (framework docs, best practices)
- Design the solution (approach, affected files)
- Validate the plan (coherence, completeness)

### Step 2: Work
- Set up isolation (git worktrees or branches)
- Execute the plan step by step
- Run validations (tests, linting, type checking)
- Track progress
- Handle issues and adapt

### Step 3: Review
- Have multiple agents review output
- Prioritize findings (P1/P2/P3)
- Resolve findings
- Validate fixes
- Capture patterns for future prevention

### Step 4: Compound (Most Critical)
- Capture what worked and what didn't
- Make solutions findable with YAML frontmatter
- Update the system (CLAUDE.md, create new agents)
- Verify the learning would catch this automatically next time

---

## Eight Beliefs to Unlearn

### 1. "The code must be written by hand"
The requirement is writing good code. Who types doesn't matter.

### 2. "Every line must be manually reviewed"
Automated systems can catch issues as effectively. If you don't trust results, fix the system rather than compensating with manual work.

### 3. "Solutions must originate from the engineer"
When AI researches and recommends, the engineer adds taste — knowing what fits this codebase, team, and context.

### 4. "Code is the primary artifact"
A system that produces code consistently beats any individual implementation. Process > perfection.

### 5. "Writing code is the core job function"
Ship value through planning, reviewing, and teaching systems. Code is one input. Effective compound engineers write less code and ship more.

### 6. "First attempts should be good"
First attempts: ~95% garbage. Second attempts: ~50%. This is the process, not failure. Goal: iterate fast enough that attempt three lands in less time than attempt one.

### 7. "Code is self-expression"
Code belongs to the team, product, and users — not ego. Detachment enables better feedback and fearless refactoring.

### 8. "More typing equals more learning"
Understanding matters more than muscle memory. Reviewing 10 AI implementations teaches more patterns than hand-typing two.

---

## The 50/50 Rule

Allocate **50% of engineering time to features, 50% to improving systems.** Traditional teams do 90/10, treating system work as overhead. An hour creating a review agent saves 10 hours of review over a year.

---

## Five Stages of Adoption

### Stage 0: Manual Development
Writing code line-by-line. Research via docs and Stack Overflow.

### Stage 1: Chat-Based Assistance
AI as smart reference tool. Copy-pasting snippets. Reviewing every line.

### Stage 2: Agentic Tools With Line-by-Line Review
Agentic tools with file access and direct changes. Still gatekeeping everything. **Most developers plateau here.**

### Stage 3: Plan-First, PR-Only Review
Collaborate on detailed plan. Step away while AI implements. Review at PR level, not line level. **Compound engineering begins here.**

### Stage 4: Idea to PR (Single Machine)
Provide idea, agent handles everything. Involvement: ideation, PR review, merge.

### Stage 5: Parallel Cloud Execution
Run 3+ features with 3+ agents independently. Review PRs as they finish. Agents propose fixes proactively.

---

## How to Level Up

### 0 → 1: Start Collaborating
- Pick one tool, ask questions first before writing
- Delegate boilerplate (tests, configs, repetitive functions)
- **Compounding move:** Keep running notes of working prompts

### 1 → 2: Let the Agent In
- Switch to agentic mode with file system access
- Start with targeted, narrow changes
- **Compounding move:** Create CLAUDE.md documenting preferences; add notes when agent makes mistakes

### 2 → 3: Trust the Plan (Key Transition)
- Invest in planning (spell out requirements, approach, edge cases)
- Let agent research codebase and patterns
- Review at PR level
- **Compounding move:** Document what plans missed for next iteration

### 3 → 4: Describe, Don't Plan
- Give outcomes, not instructions ("Add email notifications for new comments")
- Let agent determine implementation, approve approach before execution
- **Compounding move:** Build library of outcome-focused instructions

### 4 → 5: Parallelize Everything
- Move execution to cloud, run parallel work streams
- Build a queue of ideas, bugs, improvements
- **Compounding move:** Document which tasks parallelize well

---

## Three Critical Questions

Before approving any AI output:

1. **"What was the hardest decision you made here?"** — Reveals tricky parts and judgment calls.
2. **"What alternatives did you reject, and why?"** — Shows options considered, catches bad choices.
3. **"What are you least confident about?"** — Gets AI to admit weaknesses.

---

## Agent-Native Architecture

Agent-native means agents have same capabilities as developers. Withholding capabilities becomes manual work.

### Progressive Levels

| Level | Capabilities | Unlocks |
|---|---|---|
| 1: Basic Dev | File access, tests, git commits | Basic compound engineering |
| 2: Full Local | Browser, local logs, PR creation | Stages 3-4 |
| 3: Prod Visibility | Read-only prod logs, error tracking, monitoring | Proactive debugging |
| 4: Full Integration | Ticket system, deployment, external services | Stage 5 |

### Agent-Native Mindset
- "How will the agent interact with this?" (building features)
- "What would the agent need to see?" (debugging)
- "Will the agent understand this?" (documenting)

---

## Review Categories & Agents

| Category | Focus |
|---|---|
| Security | OWASP top 10, injection, auth/authz |
| Performance | N+1 queries, missing indexes, caching, algorithms |
| Architecture | System design, boundaries, dependency directions |
| Patterns | Design patterns, anti-patterns, code smells |
| Data | Migrations, transactions, referential integrity |
| Quality | YAGNI, complexity, readability |
| Deployment | Pre-deploy checklists, rollback plans |

### Output Format
```
P1 - CRITICAL (must fix):
[ ] SQL injection in search (security)
[ ] Missing transaction around user creation (data)

P2 - IMPORTANT (should fix):
[ ] N+1 query in comments loading (performance)
[ ] Controller doing business logic (architecture)

P3 - MINOR (nice to fix):
[ ] Unused variable (quality)
```

---

## Project Structure

```
your-project/
├── CLAUDE.md              # Agent instructions, preferences, patterns
├── docs/
│   ├── brainstorms/       # Fuzzy requirement exploration
│   ├── solutions/         # Solved problems (searchable, with YAML frontmatter)
│   └── plans/             # Detailed implementation plans
└── todos/                 # Prioritized work items
    ├── 001-ready-p1-fix-auth.md
    └── 002-pending-p2-add-tests.md
```

---

## Beliefs to Adopt

### Extract Taste Into Systems
Document naming, error handling, testing taste in CLAUDE.md, agents, skills, and slash commands. Point agents at style guides and decision records.

### Trust the Process, Build Safety Nets
Set up guardrails (tests, automatic review, monitoring). If output feels untrustworthy, add systems making it trustworthy — don't switch to manual review.

### Parallelization as Your Friend
You're no longer the bottleneck. Compute capacity is. Run multiple agents simultaneously. When stuck, start another task.

### Plans Are the New Code
Plans are the most important artifact. Fixing ideas on paper is cheaper than fixing code.

---

## Team Collaboration

### PR Ownership
Person initiating work owns PR regardless of who wrote code. Responsible for plan quality, review, fixes, and post-merge impact.

### Human Review Focus (When AI Already Reviewed)
- Does this match agreement?
- Does approach make sense?
- Are there business logic issues?
- **Don't check:** syntax, security, performance, style (AI agents did)

### Scaling Patterns
- **Clear ownership + async updates:** Each feature has one owner
- **Feature flags + small PRs:** Ship small, merge frequently, resolve conflicts immediately
- **Compound docs = tribal knowledge:** Run `/compound` after implementing — solution is documented, anyone can find it

---

## Design Workflow

### The Baby App Approach
1. Create throwaway prototype repo
2. "Vibe code" the design
3. Iterate until satisfaction
4. Capture design system (colors, spacing, typography)
5. Transfer to main app

### The Vibe Coding Paradox
Vibe code to **discover** what you want, then spec to **build** it properly. Prototype → user feedback → delete → proper plan.

**Perfect for:** Personal projects, prototypes, experiments, internal tools, UX exploration
**Not great for:** Production systems, security-sensitive apps, performance-critical systems

---

## Core Principles (Summary)

1. **Every unit of work makes subsequent work easier.** Code, docs, and tooling compound.
2. **Taste belongs in systems, not review.** Bake judgment into config, schemas, automated checks.
3. **Teach the system, don't do the work.** Context compounds exponentially; code-typing solves only immediate tasks.
4. **Build safety nets, not review processes.** Verification infrastructure builds trust.
5. **Make environments agent-native.** Structure projects for autonomous AI navigation.
6. **Apply compound thinking everywhere.** Every artifact enables next iteration to move faster.
7. **Embrace discomfort of letting go.** Imperfect scalable results beat perfect non-scalable ones.
8. **Ship more value. Type less code.** Measure output by problems solved, not keystrokes logged.
