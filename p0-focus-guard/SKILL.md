---
name: p0-focus-guard
description: >
  Priority focus guard that surfaces P0 tasks from the PARA workspace at session start.
  Prevents context-switching to lower-priority work. Reads from E6 Gap Tracker and
  Score Tracker spreadsheets. Auto-invokes at session start, when creating tmux sessions,
  or when the user starts working on something not in their P0 list.
---

# P0 Focus Guard

## When to Invoke

Activate AUTOMATICALLY when:
- A new session or tmux session starts
- User says "what should I work on", "what's next", "priorities"
- User starts working on something — check if it's P0 before proceeding
- User asks to switch tasks

## Priority Framework

### P0 — Do NOW (blocks E6 bar)
Tasks where score < 2 on critical rubric categories (1-5). These are interview-failing gaps.
**Rule: No P1/P2 work until all P0s are closed or actively in progress.**

### P1 — Do THIS WEEK (strong E6 signal)
Tasks where score < 2 on important categories (6-8) or where packaging needs work.
**Rule: Only after daily P0 practice is done.**

### P2 — Do WHEN READY (E7 signal)
Nice-to-have depth, edge cases, V2 roadmaps.
**Rule: Only in final week or when P0+P1 are green.**

## Data Sources

### E6 Gap Tracker (live priorities)
- Spreadsheet: `1B4v9l2swSUneREEqmNSAwtCR_JMLmzZ3Qd4o4v689k0`
- Read columns: Gap, Category, Priority, Status
- Filter: Status = "Open", sort by Priority

### E6 Score Tracker (progress signal)
- Spreadsheet: `1F_XOrCbo4d5kR14caLXvhUODY46LVtsdYLfRHLSK9wk`
- Read: latest row to see which critical categories are still below 2

### 4-Week Plan (current week goals)
- Doc: `1-FHtg9tVueH7huudM3H3GZ84f8L65z7Z4f_UugNONt0`
- Check what this week's focus area is

## Session Start Protocol

When a new session begins, execute this sequence:

### 1. Read Current P0s
```
Read E6 Gap Tracker → filter Priority = P0, Status = Open
Read E6 Score Tracker → get latest row → find categories scoring < 2
```

### 2. Display Focus Card
Format output as:

```
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
  P0 FOCUS — [Today's Date]
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

  YOUR P0 GAPS (must fix to clear E6):

  1. [Gap name] — [Category] — [Action]
  2. [Gap name] — [Category] — [Action]
  3. [Gap name] — [Category] — [Action]

  LATEST SCORE: [X]/30 — [Level]
  CRITICAL CATEGORIES BELOW BAR: [list]

  THIS WEEK'S FOCUS: [from 4-week plan]

  SUGGESTED SESSION:
  → [specific practice recommendation]

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
```

### 3. Suggest Tmux Session Name
Based on P0 priority, suggest:
```
tmux new -s e6-[category]-[date]
```

## Focus Guard Rules

### When User Starts Non-P0 Work
If the user begins a task that doesn't map to a P0 gap:

1. **Acknowledge** — Don't block, but surface the conflict
2. **Show trade-off** — "This is P1/P2. Your P0 gaps [X, Y, Z] are still open."
3. **Offer redirect** — "Want to spend 30 min on [P0 task] first, then come back to this?"
4. **Respect their choice** — If they proceed, don't nag again in this session

### Exceptions (Don't Block)
- User explicitly says "I know this isn't P0"
- Task is urgent/external (real interview prep, recruiter response)
- Task takes < 5 minutes
- It's a break/context-switch for mental health

## Priority Mapping to PARA Workspace

| Priority | PARA Location | What Lives Here |
|---|---|---|
| P0 | Projects/practice-workbooks/ | Timed practice on gap areas |
| P0 | Projects/ml-fundamentals/ | Loss function derivations |
| P0 | Projects/ml-system-design/ | Architecture drills |
| P1 | Projects/practice-workbooks/ | A/B test design, feature justification |
| P1 | Projects/coding-prep/ | Beam search, attention from scratch |
| P1 | Projects/behavioral-prep/ | STAR stories |
| P2 | Projects/practice-mocks/ | Full mock sessions |
| P2 | Resources/ | Reference lookup only |

## Closing a P0

A P0 is closed when:
1. The gap category scores **2+** in **two consecutive** practice sessions
2. Update Gap Tracker: Status → "Closed", Date Closed → today
3. If all P0s are closed, promote the highest P1 to P0

## Weekly Priority Review

Every Sunday or Monday:
1. Read all open gaps from Gap Tracker
2. Read last 3 scores from Score Tracker
3. Re-prioritize based on trend:
   - Category trending up (1→2) → keep P1
   - Category stuck at 0-1 after 3 attempts → escalate to P0
   - Category consistently at 2+ → close and move to P2/done
4. Update Gap Tracker with new priorities

## Integration with E6 Bar Raiser

After every mock grading (via e6-bar-raiser skill):
1. Check if new gaps were found
2. Auto-assign priority based on category type:
   - Critical category (1-5) scoring < 2 → P0
   - Important category (6-8) scoring < 2 → P1
   - Nice-to-have category (9-10) scoring < 2 → P2
3. Update Gap Tracker
4. Re-display Focus Card with updated P0 list
