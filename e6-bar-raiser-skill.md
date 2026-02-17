---
name: e6-bar-raiser
description: >
  Meta E6/E7 calibration bar raiser for ML System Design mocks.
  Grades mock answers against the E6 rubric, identifies gaps, logs scores,
  and appends corrections with what the candidate should have written.
  Auto-invokes when user shares a mock answer for grading.
---

# E6 Bar Raiser Skill

## When to Invoke

Activate when the user:
- Shares a mock interview answer for grading
- Asks to be graded against E6/E7 calibration
- Wants feedback on a system design practice run
- Says "grade this", "score this", "review my mock"

## Grading Workflow

### Step 1: Read the Mock Answer

Read the user's answer from the Google Doc or pasted text. Identify which practice problem it is (P1-P10 or custom).

### Step 2: Grade Against E6 Rubric (10 Dimensions)

Score each dimension 0-3:

| # | Category | Type | What 2 (E6 bar) Looks Like |
|---|---|---|---|
| 1 | Structure & Flow | Critical | 6 sections in order (5-5-10-5-3-2), no jumping |
| 2 | Problem Scoping | Critical | 1-sentence synthesis with quantified baseline → target |
| 3 | Architecture First | Critical | Serving + training paths with named components, failure modes |
| 4 | Model Justification | Critical | 3 alternatives (simple/medium/complex), justified choice |
| 5 | Latency Calculation | Critical | P50/P99 breakdown per component with actual numbers |
| 6 | Loss Function Math | Important | Formula + intuition + business connection |
| 7 | Metrics with Targets | Important | Offline metric + A/B test (MDE, duration, guard rails) |
| 8 | Feature Engineering | Important | Features justified with WHY + freshness/update frequency |
| 9 | Deep Dive | Nice-to-have | Self-directed depth on 1 component |
| 10 | Edge Cases & V2 | Nice-to-have | Cold start + drift + adversarial + V1→V2→V3 roadmap |

**E6 Bar:** 20+/30 total, categories 1-5 ALL at 2+
**Strong E6:** 24+/30, at least 2 categories at 3
**E7 Signal:** 27+/30, 5+ categories at 3

### Step 3: Write Detailed Feedback

For each of the 4 focus areas (Problem Navigation, Solution Design, Technical Excellence, Technical Communication):

1. **What they did well** — specific evidence
2. **What E6 requires that's missing** — with concrete examples of what E6 sounds like
3. **Dimension ratings** — Insufficient / Solid / Exceptional per sub-dimension

### Step 4: Produce Score Summary

Format as individual lines (not a table — tables render poorly in Google Docs):

```
1. Structure — Score: X → Y — [Key fix]
2. Scoping — Score: X → Y — [Key fix]
...
```

Color code:
- **Red bold** for dimensions where score < 2 (below E6 bar)
- **Green bold** for the corrected total

### Step 5: Identify Top 3 Gaps

Prioritize as P0/P1/P2 with:
- What the gap is
- What E6 looks like (concrete example)
- Action to fix it

### Step 6: Append Corrections to the Doc

Append an "E6 BAR RAISER CORRECTIONS" section to the user's mock doc with:
- Each section header
- "Your version:" — brief summary of what they wrote
- "[CORRECTION]" — what E6 sounds like, with exact words/math/architecture
- Format all [CORRECTION] tags in red bold

### Step 7: Log Score

Append a row to the E6 Score Tracker spreadsheet:
- Spreadsheet ID: `1F_XOrCbo4d5kR14caLXvhUODY46LVtsdYLfRHLSK9wk`
- Columns: #, Date, Problem, scores 1-10, Total, Crit 2+?, Level, E7 Reflection, Top Gap

### Step 8: Log New Gaps

Append rows to the E6 Gap Tracker spreadsheet:
- Spreadsheet ID: `1B4v9l2swSUneREEqmNSAwtCR_JMLmzZ3Qd4o4v689k0`
- Only add NEW gaps not already tracked
- Columns: #, Date Found, Gap, Category, Priority, What E6 Looks Like, Action, Status, Date Closed

### Step 9: E7 Reflection

Ask: "What would E7 have done differently?" and include 1-sentence answer in the score log.

## Key Grading Principles

### Be Specific, Not Generic
- BAD: "Your architecture needs more detail"
- GOOD: "You wrote 'ingestion → feature store → LUT'. E6 says: 'Order → API Gateway → Redis (3ms) → LightGBM (2ms) → Calibration (1ms) → Response. P50: 6ms.'"

### Grade the Packaging, Not Just the Knowledge
- The candidate often KNOWS the right answer but doesn't PRESENT it in the structured way E6 expects
- Identify where knowledge exists but packaging is missing

### Always Show What E6 Sounds Like
- For every gap, write the exact words/math/diagram the candidate should have said
- This builds taste over time

### Credit Where Due
- If the candidate has the right intuition, acknowledge it even if execution is imperfect
- Bump scores when candidate pushes back with valid evidence (like the Problem Scoping example)

### Loss Function Reference (Common in ML System Design)

| Problem | Loss | tau/param | Intuition |
|---|---|---|---|
| Delivery estimation | Quantile (tau=0.95) | 0.95 | Late costs 19x more than early |
| Fraud detection | Focal / Weighted CE | gamma=2, alpha=0.75 | Rare class, hard examples matter more |
| Search ranking | Pairwise (BPR) or Listwise (LambdaRank) | margin | Relative order matters, not absolute score |
| Recommendation | Multi-objective (engagement + quality) | weighted sum | Balance short-term engagement vs long-term quality |
| Dynamic pricing | Revenue = price × P(conversion at price) | — | Optimize expected revenue, not just prediction accuracy |

### Latency Reference (Typical Production Systems)

| Component | P50 | P99 |
|---|---|---|
| Redis feature lookup | 1-3ms | 5-10ms |
| LightGBM inference | 1-3ms | 5-8ms |
| Deep model inference (GPU) | 5-15ms | 20-50ms |
| ANN lookup (FAISS/ScaNN) | 1-5ms | 10-20ms |
| API gateway routing | 1-2ms | 3-5ms |
| Calibration layer | 1ms | 2ms |

## Post-Interview Grading Sheet

For more detailed grading (mimicking what a real Meta interviewer fills out), use the template:
- Doc ID: `1ltHjyxI4VtPqNBdolctzHRCHedi6Q7l9Y7EUmOlyqG0`
- Copy it for each mock session
