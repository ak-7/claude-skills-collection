# PARA Interview Prep Skill — Meta E6/E7 Staff MLE

## What This Is

The operating manual for your PARA interview workspace. It defines how Projects, Areas, Resources, and Completed Prep work together to take you from "strong technical depth, weak execution discipline" to clearing the E6 bar — and developing E7 taste over time.

This file lives at the workspace root alongside CLAUDE.md. CLAUDE.md describes what's in the workspace. This file describes **how to use it**.

---

## How PARA Maps to Interview Prep

```
PARA Layer     │ Interview Function          │ When You Use It
───────────────┼─────────────────────────────┼──────────────────────────────
Projects/      │ Active practice streams     │ Daily — this is where you DO work
Areas/         │ Progress tracking & gaps    │ Weekly — review trajectory
Resources/     │ Reference lookup            │ During practice — when you need details
Completed Prep/│ Archived finished rounds    │ Never (unless reviewing old patterns)
```

### Projects/ — Where You Practice

Each project is an active prep stream with its own rhythm:

| Project | What | Cadence | Done When |
|---|---|---|---|
| `ml-system-design` | 6-section template mastery, architecture drills | Daily (Week 1-4 plan) | All 11 questions scored 2+ on structure |
| `coding-prep` | ML from scratch, algorithms, AI coding | Daily, 1-2 problems | P0+P1 coding fixes all completed |
| `ml-fundamentals` | Loss functions, optimization, regularization, probabilistic models, information theory, generalization theory | Daily, woven into system design practice | Can derive any loss function and explain WHY it fits the business objective |
| `behavioral-prep` | STAR stories, project deep dives, pitch | 2x/week | 3 projects + 8 stories fluent without notes |
| `practice-workbooks` | Structured 30-min timed runs (P1-P10) | Daily — the core loop | 10 workbooks scored, all critical categories at 2+ |
| `practice-mocks` | Live mock sessions | 1-2x/week | Consistent 20+/30 with external evaluator |
| `past-interview-feedback` | Learnings from real interviews | Once, then reference | Recurring themes extracted and addressed |

**Rule:** When a project is "done," move it to `Completed Prep/`. Don't delete — you may revisit patterns.

### Areas/ — Where You Track State

`Areas/interview-context/` holds your ongoing trajectory:
- `strengths/` — What you consistently score well on
- `gaps/` — Priority gaps (P0/P1/P2) with status

Update this weekly. The question is always: **"Are my critical categories trending up?"**

### Resources/ — Where You Look Things Up

You don't study Resources. You **reference** them during practice when you need depth:
- `cheatsheets/` — Quick formulas, model comparisons, vocabulary
- `system-design-notes/` — Deep .docx notes per question (P6-P10 mapped)
- `reference-materials/` — Broader prep docs, spoken training scripts

**Rule:** If you're spending more time in Resources than Projects, you're procrastinating. Practice first, reference second.

### Completed Prep/ — Where Finished Work Goes

When you've scored 2+ on all critical categories for a workbook, move it here. This keeps Projects/ focused on what still needs work.

---

## The E6 Bar — "Structured Excellence"

An E6 walks into a system design interview and the interviewer thinks: "This person has built production ML systems. They know exactly how to structure the problem, justify their decisions, and anticipate failure modes."

### E6 Calibration (4 Focus Areas, 12 Dimensions)

**1. Problem Navigation**
- Structures entire problem space before sub-problems; bounds and prioritizes
- Anticipates common AND obscure challenges; selects right abstractions
- Independently leads exploration; proactively reduces ambiguity

**E6 signal:** You synthesize clarifying questions into a 1-sentence problem statement with a quantified success metric — without being asked.

**2. Solution Design**
- Addresses multiple critical aspects; easy-to-understand architecture
- Comprehensive data strategy with clear justification

**E6 signal:** You draw the architecture (serving + training paths) in the first 5 minutes — before anyone asks.

**3. Technical Excellence**
- Mastery across the stack; explains the "whys"; compares frameworks
- Expert-level working knowledge of multiple problem areas
- Proactively discusses nuanced tradeoff implications
- Expert-level evaluation discussion; high confidence in validity

**E6 signal:** For every decision, you present 3 alternatives (simple/medium/complex) and justify your choice with latency math and business constraints.

**4. Technical Communication**
- Complex topics easily digestible; clear, concise, compelling
- Expert-level fluency; integrates critical, complex vocabulary
- Incorporates feedback; responds to indirect prompts

**E6 signal:** You never say "slow" — you say "impacts TTFT." You never say "it's better" — you say "reduces P99 latency from 120ms to 35ms because..."

---

## The E7 Bar — "Taste and Vision"

An E7 walks into the same interview and the interviewer thinks: "This person doesn't just build systems — they see the system that should exist."

### What Changes from E6 to E7

| Dimension | E6 (Exceptional) | E7 (Beyond) |
|---|---|---|
| Problem Navigation | Structures and bounds the problem | Reframes the problem — identifies what the interviewer should have asked |
| Architecture | Production-grade serving + training | Cross-system thinking — how this interacts with 3 other systems; data flywheel |
| Model Justification | 3 alternatives with justification | Evolution path: "Start with X, but architect for Y because data distribution shifts in 6 months" |
| Tradeoffs | Proactively discusses implications | 2nd/3rd order effects: "Optimize engagement → quality degrades → churn in 90 days" |
| Metrics | Expert A/B test design | Metric ecosystems; when A/B tests lie; long-term holdout design |
| Depth | Deep in multiple areas | Connects depth across areas: "Quantization choice affects feature store design because..." |
| Communication | Clear, concise, compelling | Teaches the interviewer something new |
| Edge Cases | Cold start, drift, adversarial | Designs for failures that haven't happened yet |

### E7 Taste Markers

These emerge from practice and reflection. Check them off as they become natural:

- [ ] You see problems as **systems of systems**, not isolated components
- [ ] You naturally ask "what breaks at 10x scale?" before prompted
- [ ] You explain WHY a loss function shape matches the business objective
- [ ] You design the **data flywheel** — how the system improves itself
- [ ] You identify the **1 thing that matters most** and spend 60% of time there
- [ ] You anticipate the interviewer's next question and answer it preemptively
- [ ] You think in **evolution paths**: V1 → V2 → V3 with migration triggers
- [ ] You connect technical decisions to **org constraints** (team size, oncall, hiring)
- [ ] You evaluate metrics skeptically — "NDCG looks good but masks popularity bias"
- [ ] You reference **real production incidents** as design rationale

---

## Daily Practice Workflow

### The Loop (30-45 min)

```
1. PICK    → Practice workbook or mock from Projects/practice-workbooks/
2. TIMER   → 30 minutes strict
3. EXECUTE → 6-section template (5-5-10-5-3-2)
4. SCORE   → E6 rubric, 10 dimensions, /30
5. REFLECT → "What would E7 have done differently?" (1 sentence)
6. LOG     → Score + reflection in Progress Tracker below
7. UPDATE  → If gap found, add to Areas/interview-context/gaps/
```

### When to Use Each Project

| If you need to... | Go to |
|---|---|
| Do a timed practice run | `Projects/practice-workbooks/` |
| Study loss functions, optimization theory, or derivations | `Projects/ml-fundamentals/` |
| Work on coding problems | `Projects/coding-prep/` |
| Polish a STAR story or rehearse pitch | `Projects/behavioral-prep/` |
| Do a live mock | `Projects/practice-mocks/` |
| Look up a formula or architecture pattern | `Resources/cheatsheets/` |
| Look up detailed notes for a specific question | `Resources/system-design-notes/` |
| Check what gaps remain | `Areas/interview-context/gaps/` |
| Review what you did well in past real interviews | `Projects/past-interview-feedback/` |

---

## Scoring System

### E6 Self-Scoring (10 Dimensions, /30)

| # | Category | Type | 0 | 1 | 2 (E6 bar) | 3 (E7 signal) |
|---|---|---|---|---|---|---|
| 1 | Structure & Flow | Critical | No template | Jumped around | 6 sections in order, well-timed | Automatic, smooth transitions |
| 2 | Problem Scoping | Critical | Restated question | Generic questions | 1-sentence synthesis + metric | Reframed problem + metric ecosystem |
| 3 | Architecture First | Critical | No diagram | Drew after models | Serving + training + feature store | + Cross-system + data flywheel |
| 4 | Model Justification | Critical | Named 1 model | Weak justification | 3 alternatives, clear justification | + Evolution path + distribution reasoning |
| 5 | Latency Calculation | Critical | No numbers | Guessed total | P50 breakdown with math | + P99, bottleneck, optimization |
| 6 | Loss Function Math | Important | Named loss only | Formula, no intuition | Formula + intuition + business link | + Alternatives + calibration strategy |
| 7 | Metrics with Targets | Important | Generic metrics | No numbers | Offline + A/B + MDE + guard rails | + When metrics lie + holdouts |
| 8 | Feature Engineering | Important | No features | Listed without reason | Justified + freshness | + Interactions + store design |
| 9 | Deep Dive | Nice-to-have | Surface level | Depth when prompted | Self-directed depth on 1 component | Taught interviewer something |
| 10 | Edge Cases & V2 | Nice-to-have | None | 1 edge case | Cold start + drift + adversarial | + Future failure modes + V2 triggers |

### Thresholds

- **E6 Bar:** 20+/30 total, categories 1-5 all at 2+
- **Strong E6:** 24+/30 total, categories 1-5 all at 2+, at least 2 at 3
- **E7 Signal:** 27+/30 total, 5+ categories at 3, none below 2

---

## Progress Tracker

### Practice Log

| # | Date | Problem | Score /30 | Crit 2+? | Weakest | E7 Reflection |
|---|---|---|---|---|---|---|
| 1 | | | | | | |
| 2 | | | | | | |
| 3 | | | | | | |
| 4 | | | | | | |
| 5 | | | | | | |
| 6 | | | | | | |
| 7 | | | | | | |
| 8 | | | | | | |
| 9 | | | | | | |
| 10 | | | | | | |

### Milestones

- [ ] **Week 1:** 5 runs completed, structure is automatic
- [ ] **Week 2:** All critical categories consistently at 2+
- [ ] **Week 3:** Total score consistently 20+/30 (E6 bar)
- [ ] **Week 4:** At least 2 runs at 24+/30 (Strong E6)
- [ ] **Stretch:** 1 run at 27+/30 (E7 signal)

### E7 Taste Development

After each practice, 1 sentence: "What would E7 have done differently?"

When the same insight recurs 3+ times, check it off in E7 Taste Markers above. That's taste becoming instinct.

---

## Gap Tracker

| Priority | Gap | Status | Action | Target Date |
|---|---|---|---|---|
| P0 | Q9 Multimodal (C+) | Open | Practice P7 + gaps analysis | Week 2 |
| P0 | Q18 Visual Search (C) | Open | Practice + gaps analysis | Week 2 |
| P1 | Core SWE / Distributed Systems | Open | Study + practice | Week 3 |
| P1 | AI Safety deep-dive | Open | Practice P9 | Week 3 |
| P2 | MLOps / Production Monitoring | Partial | Reference review | Week 4 |

Move closed gaps here with what fixed them — this is how you learn what works.

---

## ml-fundamentals Project Scope

This project covers the theoretical foundations that make your system design answers go from "I know quantile regression" to "Let me explain WHY asymmetric loss is the right choice for this business constraint."

### Core Topics

**Optimization & Training**
- SGD, Adam, learning rate schedules — when each matters
- Gradient flow: vanishing/exploding, skip connections, normalization
- Convergence guarantees: convex vs non-convex, saddle points

**Loss Functions & Objectives**
- Cross-entropy, focal loss, contrastive loss, triplet loss — derive each from first principles
- Multi-task loss balancing: uncertainty weighting, gradient normalization
- When loss function choice changes model behavior (not just accuracy)

**Regularization & Generalization**
- L1/L2, dropout, data augmentation, early stopping — why each works differently
- Bias-variance tradeoff in deep learning: double descent, interpolation threshold
- Generalization bounds: PAC learning, Rademacher complexity (intuition, not proofs)

**Probabilistic Models**
- MLE vs MAP vs Bayesian inference — when each is appropriate
- Calibration: why models are overconfident, temperature scaling, Platt scaling
- Uncertainty quantification: epistemic vs aleatoric

**Information Theory**
- KL divergence — why it's asymmetric, when to use which direction
- Mutual information — feature selection, representation learning
- Entropy in decision trees vs neural attention

**Evaluation & Metrics**
- Precision-Recall vs ROC — when each misleads
- Calibration curves, Brier score, expected calibration error
- Offline-online metric gaps: why good offline metrics don't always predict online wins

### How ml-fundamentals Integrates with Practice

Don't study this in isolation. During every practice workbook:
- Section 3 (Model): derive the loss function, don't just name it
- Section 5 (Metrics): explain why the offline metric is a valid proxy
- Section 4 (Serving): connect model choice to inference cost

The goal is that fundamentals become the LANGUAGE you think in, not a separate topic.

---

## Pre-Interview Checklist

### System Design
- [ ] All practice workbooks (P1-P10) scored 20+/30
- [ ] All 5 critical rubric categories consistently at 2+
- [ ] Chunked Prefills and PagedAttention explained fluently
- [ ] Multi-stage multimodal training explained fluently
- [ ] 90-second Physics-First opening practiced
- [ ] KV-cache napkin math under 60 seconds

### ML Fundamentals
- [ ] Can derive cross-entropy, focal, quantile, contrastive loss from first principles
- [ ] Can explain calibration: why, how, when it matters
- [ ] Can connect any loss function to business objective in 2 sentences
- [ ] Adam vs SGD: when and why, not just "Adam is default"
- [ ] Offline-online metric gap: 3 examples of when good offline ≠ good online

### Coding
- [ ] Softmax + attention from scratch (sqrt(d_k) scaling)
- [ ] Beam search with heap management
- [ ] Flash Attention tiling intuition
- [ ] All P0 + P1 coding fixes completed

### Behavioral
- [ ] 3 projects ready (Video AI, Conversation AI, PEV3) — 6+ months, launched, scaled
- [ ] Each story is self-directed ("I identified, I got buy-in, my idea won")
- [ ] 8 STAR stories fluent without notes
- [ ] Project Deep Dive (Immersive Video) rehearsed

### Communication
- [ ] Vocabulary upgrades memorized
- [ ] Napkin Math: VRAM rule, A100 capacity, QPS calculations
- [ ] 5-5-10-5-3-2 timing internalized

### Meta-Specific
- [ ] Company pitch rehearsed
- [ ] "Why Meta" answer ready
- [ ] Team match preferences identified

---

## How This File Evolves

Update after:
1. **Every practice session** — Log score in Progress Tracker
2. **Every real mock** — Update Gap Tracker
3. **Every E7 insight** — Add to Taste Development log
4. **When a gap closes** — Move from Gap Tracker to closed with what fixed it
5. **When taste develops** — Check off E7 Taste Markers

The goal is not to check every box. The goal is to reach the point where structure is automatic and taste is internalized.
