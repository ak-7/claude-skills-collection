---
name: systems-thinking-over-code-output
description: Use when making technical architecture decisions - prioritize leverage and downstream impact over code volume; 10x comes from better decisions, not faster typing
---

# Systems Thinking > Code Output

## Overview

10x engineers don't write code 10 times faster — they make technical architecture decisions that result in dramatically better downstream impact. As Andrew Ng emphasizes, it's about leverage, not volume.

## When to Use

- Designing new systems or features
- Evaluating architecture alternatives
- Code reviews focusing on structure
- Refactoring decisions
- Choosing between implementation approaches

## Core Principle

```
IMPACT = LEVERAGE × EXECUTION

10x impact comes from 10x better architecture, not 10x more code
```

## Questions to Ask Before Coding

| Question | Why It Matters |
|----------|----------------|
| What's the 10x better architecture? | Right structure multiplies all future work |
| What decision makes everything else easier? | Leverage point identification |
| What will I/team build on top of this? | Downstream impact assessment |
| How does this constrain future choices? | Architecture debt analysis |
| What abstraction unlocks the most value? | Leverage maximization |

## Red Flags - Stop and Think

- "Let me just start coding"
- "I'll refactor it later"
- "This is the obvious solution"
- "Everyone does it this way"
- Copying patterns without understanding tradeoffs

**All of these mean: Step back. Think about leverage.**

## Leverage Thinking Patterns

### ❌ LOW Leverage
```
Problem: Need to add 5 similar features
Approach: Copy-paste code 5 times
Result: 5x work, technical debt
```

### ✅ HIGH Leverage
```
Problem: Need to add 5 similar features
Approach: Design extensible architecture once
Result: 5 features from 1x work + config
```

## Real-World Examples

**Low leverage:**
- Writing custom code for each integration
- Building feature-specific solutions
- Optimizing before understanding bottlenecks

**High leverage:**
- Creating plugin architectures
- Building composable primitives
- Identifying true constraints first

## The 10x Multiplier

One good architecture decision can:
- Save months of refactoring
- Enable features you haven't thought of yet
- Make the codebase 10x easier to work with
- Multiply the productivity of everyone who touches it

**Time investment:** 1 day thinking > 1 week coding wrong solution

## Evaluation Checklist

Before committing to an approach:

- [ ] Identified the leverage point
- [ ] Considered 3+ alternative architectures
- [ ] Thought about downstream impact
- [ ] Evaluated against future requirements
- [ ] Understood the constraints deeply
- [ ] Chose simplicity over cleverness (unless complexity is the leverage)

## Remember

**You're not paid to write code. You're paid to solve problems with maximum leverage.**

The code is just the artifact of good thinking.
