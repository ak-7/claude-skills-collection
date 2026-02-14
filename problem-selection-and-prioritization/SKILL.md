---
name: problem-selection-and-prioritization
description: Use when deciding what to build - taste in choosing what to build is the ultimate multiplier; know what is valuable, get it done, and ship to market
---

# Problem Selection & Prioritization

## Overview

It has to do with knowing what is valuable and what is not, and actually getting it done and to market. Taste in choosing what to build is the ultimate multiplier.

## When to Use

- Planning sprints
- Evaluating feature requests
- Prioritizing backlog
- Deciding what to build next
- Saying no to ideas

## The Ultimate Multiplier

```
IMPACT = SKILL × PROBLEM_SELECTION × EXECUTION

Perfect execution on wrong problem = 0 impact
Average execution on right problem = 10x impact
```

## The Taste Framework

### What Makes a Problem Valuable?

| Dimension | Good Problem | Bad Problem |
|-----------|-------------|-------------|
| **User Impact** | Removes major pain point | Nice-to-have polish |
| **Market Timing** | Right now is critical | Could wait 6 months |
| **Leverage** | Unlocks future features | One-off solution |
| **Moat** | Builds competitive advantage | Easy to copy |
| **Learning** | Teaches important lessons | Repeats known work |

## The Selection Process

### Phase 1: Generate Options
```
Brainstorm potential problems to solve:
- User pain points
- Technical debt items
- New feature ideas
- Performance improvements
- Developer experience
```

### Phase 2: Apply Filters

#### Filter 1: Impact Score (0-10)
```
Questions:
- How many users affected?
- How severe is the problem?
- What's the willingness to pay?
- Does it enable new use cases?
```

#### Filter 2: Effort Score (0-10)
```
Questions:
- How complex is the solution?
- What's the technical risk?
- Do we have the skills?
- What are dependencies?
```

#### Filter 3: Strategic Value (0-10)
```
Questions:
- Does it build a moat?
- Does it improve core value prop?
- Does it enable future work?
- Does it teach us something?
```

### Phase 3: Prioritize

```
Priority Score = (Impact + Strategic) / Effort

High Priority: Score > 3
Medium Priority: Score 1.5-3
Low Priority: Score < 1.5
```

## The Taste Test

Before committing to build something, ask:

1. **Will users notice within 5 minutes?**
   - If no: Probably not valuable enough

2. **Would I pay for this feature?**
   - If no: Why are we building it?

3. **Does this compound?**
   - If no: Might be a distraction

4. **Is this the right problem?**
   - Often the stated problem isn't the real problem

5. **Are we the right team?**
   - Unique advantage vs commodity work

## Saying No (The Most Important Skill)

### When to Say No

| Situation | Why No |
|-----------|---------|
| "Everyone else has this feature" | Copying ≠ innovating |
| "It's technically interesting" | Interesting ≠ valuable |
| "We already started" | Sunk cost fallacy |
| "It won't take long" | Opportunity cost matters |
| "The founder/CEO wants it" | Still need to evaluate honestly |

### How to Say No

```
Instead of: "No, that's a bad idea"

Say: "Great idea. Let's evaluate it against our current priorities:
- Project A: 10x impact for customers
- Project B: 5x impact for customers
- This idea: 2x impact for customers

Should we deprioritize A or B to do this?"
```

## Market Timing

### Too Early
```
Problem: Building before market is ready
Example: Google Glass, Segway
Result: Wasted effort, missed opportunity
```

### Right Time ✅
```
Problem: Market ready, gap exists
Example: Slack (team chat), Notion (docs)
Result: Product-market fit, growth
```

### Too Late
```
Problem: Market saturated, incumbents strong
Example: New social networks, search engines
Result: Hard to differentiate
```

## The Execution Reality

**Picking the right problem is 50% of success**

The other 50%:
- 20% Execution quality
- 20% Getting it to market
- 10% Timing and luck

```
Great problem + poor execution = Better than
Poor problem + great execution
```

## Real-World Examples

### Example 1: The Feature That Didn't Matter

❌ Bad selection:
```
Request: "Add 50 export formats"
Reality: Users only use PDF and CSV
Effort: 3 months
Impact: Almost none

Better: Fix PDF export bugs (2 weeks, high impact)
```

### Example 2: The Feature That Changed Everything

✅ Good selection:
```
Problem: Users manually copy-pasting data
Insight: API integration would save hours/week
Effort: 1 month
Impact: Retention +40%, expansion revenue +25%

This was the right problem to solve
```

### Example 3: Technical Debt vs Features

Trade-off analysis:
```
Option A: Rewrite authentication system
- Impact: Slight improvement
- Effort: 2 months
- Strategic: Some learning

Option B: Build team collaboration features
- Impact: High (top user request)
- Effort: 2 months
- Strategic: Competitive advantage

Choice: B, then refactor auth incrementally
```

## The Compounding Test

Great problem selections compound:

```
Bad: One-off features
- Each feature is isolated
- Maintenance burden grows
- Codebase becomes messy

Good: Platform features
- Each feature enables 10 more
- Ecosystem grows
- Value compounds
```

### Examples:

**Non-compounding:**
- Custom export to 20 formats
- Niche integrations
- Cosmetic UI changes

**Compounding:**
- Plugin API
- Webhook system
- Public API
- Extensibility framework

## Developing Taste

### 1. Study Great Products
```
Analyze: Why did Notion beat Evernote?
- Better problem selection
- Platform thinking
- Timing (remote work boom)
```

### 2. Learn from Failures
```
Post-mortem: What did we build that nobody used?
- Features that seemed cool but...
- Didn't solve real problems
- Were too early or too late
```

### 3. Talk to Users (Constantly)
```
Weekly user interviews:
- What's frustrating you?
- What workaround do you use?
- What would you pay more for?
```

### 4. Measure Ruthlessly
```
After launch:
- Adoption rate
- Usage frequency
- Willingness to pay
- NPS impact

Learn from the data
```

## Red Flags in Problem Selection

- No clear user pain point
- "Build it and they will come" thinking
- Following competitors blindly
- "We think users want this"
- No way to measure success
- Solving problems we have, not users have

## The Decision Matrix

When stuck between options:

```
Option A: [Feature X]
- User Impact: 8/10
- Strategic Value: 6/10
- Effort: 7/10
- Priority Score: (8+6)/7 = 2.0

Option B: [Feature Y]
- User Impact: 9/10
- Strategic Value: 9/10
- Effort: 5/10
- Priority Score: (9+9)/5 = 3.6

Choice: B has better leverage
```

## Remember

**"Strategy is about choosing what NOT to do" - Michael Porter**

- The best engineers know what not to build
- Taste is developed through experience
- Talk to users, measure outcomes, iterate

**Your career trajectory depends more on problem selection than coding skill.**

Choose wisely.
