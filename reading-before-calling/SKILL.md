---
name: reading-before-calling
description: Use when calling functions with tuple unpacking, kwargs, or return value access - prevents parameter mismatches, wrong unpacking order, and stale documentation errors
---

# Reading Before Calling

## Overview

Always read function implementation before calling. Assumptions about signatures, return order, and parameters cause bugs that take 10+ minutes to debug vs 10 seconds to prevent.

## When to Use

- Unpacking tuple return values
- Using kwargs/named parameters
- Accessing dict/object keys from return values
- Calling unfamiliar functions
- Working under time pressure (ESPECIALLY then)

**When NOT to use:**
- Built-in Python functions (list.append, dict.get)
- Standard library with stable APIs
- Functions you wrote in the current session

## The Iron Law

```
READ THE IMPLEMENTATION. DON'T GUESS.
```

**No exceptions:**
- Not when "docstring is clear"
- Not when "pattern looks familiar"
- Not when "I'll fail fast and fix"
- Not when "meeting is waiting"

## Quick Reference

**Before ANY function call, verify:**

| Check | How | Example |
|-------|-----|---------|
| Return order | Read `return` statement | `return p50, p90, p99, avg, qps` |
| Parameter names | Read function signature | `def func(iterations=100)` not `num_iterations` |
| Return structure | Read return statement | `return {"stats": ..., "meta": ...}` |
| Parameter order | Check positional vs kwargs | First 2 positional, rest kwargs |

**Time cost:** 10 seconds reading vs 10 minutes debugging.

## Common Mistakes

### ❌ BAD: Trust docstring
```python
def calculate_stats(...):
    """Returns: (avg, p50, p99, qps, p90)"""  # ← STALE!
    return p50, p90, p99, avg, qps           # ← ACTUAL

# You write:
avg, p50, p99, qps, p90 = calculate_stats(...)  # TypeError!
```

### ✅ GOOD: Read return statement
```python
# Read implementation: return p50, p90, p99, avg, qps
p50, p90, p99, avg, qps = calculate_stats(...)
```

### ❌ BAD: Assume parameter name
```python
# Saw pattern before, assume name
run_benchmark(model, num_iterations=500)  # TypeError!
```

### ✅ GOOD: Read signature
```python
# Read: def run_benchmark(model, iterations=100, **kwargs)
run_benchmark(model, iterations=500)
```

### ❌ BAD: Fail-fast with fallbacks
```python
# "I'll just try common keys"
result = benchmark_stats(data, config)
p90 = result.get('p90') or result.get('latency_p90') or result.get('p90_latency')
# Still wastes time when none match
```

### ✅ GOOD: Read what it actually returns
```python
# Read implementation: return {"metrics": {"p90_ms": ...}}
result = benchmark_stats(data, config)
p90 = result["metrics"]["p90_ms"]
```

## Rationalization Table

| Excuse | Reality |
|--------|---------|
| "Docstring is clear" | Docstrings go stale. Code is truth. |
| "Pattern matches previous code" | Different repos = different implementations. |
| "I'll fail fast with .get()" | Still wastes time debugging. Prevention is faster. |
| "Error will tell me if wrong" | Why wait for errors? Read first. |
| "Reading takes too long (meeting waiting)" | 10 sec reading > 10 min debugging + explaining to team. |
| "I've seen this pattern 5 times" | 6th time is different. Always verify. |
| "Function name is obvious" | Names lie. `calculate_stats` could return any order. |
| "I'll just try it" | Trying = debugging. Reading = preventing. |

## Red Flags - STOP and Read Implementation

You're about to skip reading if you think:
- "Docstring says..."
- "This looks like..."
- "I'll just try..."
- "Error will tell me..."
- "No time to read..."
- "I've seen this before..."
- "Function name suggests..."

**All of these mean: Stop. Read the implementation.**

## Real-World Impact

**The `calculate_stats()` bug:**
- Docstring: `(avg, p50, p99, qps, p90)`
- Actual: `(p50, p90, p99, avg, qps)`
- Time to prevent: **10 seconds** (read return statement)
- Time to debug: **15 minutes** (trace TypeError, find mismatch, fix, test)
- Time saved: **14 min 50 sec**

**Time pressure is NOT an excuse:**
- Meeting waiting? 10 sec reading still faster than explaining bugs
- Production down? Wrong fix wastes more time than reading
- Quick hotfix? Wrong hotfix = rolling back + doing it again

**10 seconds reading > 10 minutes debugging. Always.**
