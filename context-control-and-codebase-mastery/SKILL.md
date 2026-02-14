---
name: context-control-and-codebase-mastery
description: Use when providing context to AI - master both writing good code AND knowing your codebase deeply to provide the right context; great patterns in your codebase let AI execute incredibly well
---

# Context Control & Codebase Mastery

## Overview

The biggest leverage is context control — knowing how to write good code AND knowing your codebase deeply to provide the right context to LLMs. Great patterns in your codebase let AI execute incredibly well.

## When to Use

- Starting any AI-assisted task
- Code reviews
- Refactoring existing code
- Onboarding to new codebases
- Teaching AI your patterns

## The Leverage Formula

```
AI Effectiveness = Code Quality × Context Quality × Pattern Consistency

10x improvement possible by optimizing all three
```

## Two Mastery Dimensions

### 1. Code Quality (Write Great Patterns)
```
Good code → AI understands → AI extends well
Bad code → AI confused → AI creates more bad code
```

### 2. Codebase Knowledge (Provide Right Context)
```
Know patterns → Target context → AI follows patterns
Don't know → Random context → AI invents patterns
```

## Context Control Mastery

### Level 1: Context Dumping ❌
```python
# "Here's everything"
/read src/
/read lib/
/read utils/

# AI gets lost in noise
```

### Level 2: Targeted Context ⚠️
```python
# Better but still guessing
/read src/auth.py
/read src/user.py

# Might miss key patterns
```

### Level 3: Pattern-Aware Context ✅
```python
# Know the codebase, provide exactly what's needed
/read src/middleware/auth.py  # Auth pattern
/read src/models/base.py      # Model pattern
/read src/utils/validation.py # Validation pattern

# AI now understands the patterns and follows them
```

## Codebase Knowledge Levels

### Novice
- Knows file locations
- Can find specific functions
- Searches for examples

### Intermediate
- Knows common patterns
- Understands architecture
- Can trace dependencies

### Expert ✅ (Target)
- Knows design decisions
- Understands pattern origins
- Can predict ripple effects
- Provides perfect context to AI

## Building Codebase Mastery

### 1. Read the Best Code
```bash
# Find exemplar files
git log --format=format: --name-only \
  | sort | uniq -c | sort -rn | head -20

# Files changed most = core patterns
# Read and understand these deeply
```

### 2. Trace Pattern Evolution
```bash
# How did this pattern emerge?
git log -p src/models/base.py

# Understand WHY, not just WHAT
```

### 3. Map the Architecture
```markdown
# Mental model
Auth: Middleware-based, JWT tokens
Data: Repository pattern, TypeORM
API: REST + GraphQL hybrid
Testing: Jest + integration tests
```

### 4. Know the Gotchas
```markdown
# Tribal knowledge
- Don't use sync operations in async handlers
- Always use transactions for multi-table ops
- Auth tokens expire in 1 hour
- Database connection pooling is critical
```

## Context Patterns

### Pattern 1: Exemplar-Driven
```
Task: Add new API endpoint

Context to provide:
1. Best existing endpoint as example
2. Auth middleware pattern
3. Validation pattern
4. Error handling pattern

AI follows established patterns perfectly
```

### Pattern 2: Layered Context
```
Task: Refactor user service

Layer 1 (Architecture):
/read docs/ARCHITECTURE.md

Layer 2 (Patterns):
/read src/services/base_service.py

Layer 3 (Specific):
/read src/services/user_service.py

AI understands the full context pyramid
```

### Pattern 3: Constraint-First
```
Task: Add caching

Context:
1. Existing cache pattern (Redis)
2. Cache key conventions
3. Invalidation strategy
4. Performance requirements

AI implements within constraints
```

## Writing Code for AI

### Principle: Explicit > Implicit

❌ Bad (AI struggles):
```python
# Magic constants, unclear flow
def process(x):
    return x * 2.5 if x > 10 else x / 3.7
```

✅ Good (AI extends easily):
```python
# Clear intent, explicit naming
SCALE_FACTOR_LARGE = 2.5
SCALE_FACTOR_SMALL = 3.7
THRESHOLD = 10

def scale_value(value: float) -> float:
    """Scale value based on magnitude using business rules."""
    if value > THRESHOLD:
        return value * SCALE_FACTOR_LARGE
    else:
        return value / SCALE_FACTOR_SMALL
```

### Principle: Patterns > Cleverness

❌ Bad (AI can't replicate):
```python
# Clever one-liner
users = [u for u in users if (lambda x: x.age > 18 and x.verified)(u)]
```

✅ Good (AI follows pattern):
```python
# Clear pattern
def is_eligible_user(user: User) -> bool:
    """User eligibility criteria."""
    return user.age > 18 and user.verified

eligible_users = filter(is_eligible_user, users)
```

### Principle: Consistent > Creative

❌ Bad (inconsistent):
```python
# Different naming styles
def getUserData()  # camelCase
def fetch_orders() # snake_case
def GetInvoices()  # PascalCase
```

✅ Good (consistent):
```python
# One style, AI learns it
def get_user_data()
def get_orders()
def get_invoices()
```

## The Context Providing Workflow

### Step 1: Understand the Task
```
Task: "Add export to CSV feature"

Questions:
- Which model?
- Similar exports exist?
- What format requirements?
- Where in the codebase?
```

### Step 2: Identify Patterns
```
Pattern search:
- How do we do exports now? (PDF, JSON)
- How do we handle large datasets? (Streaming)
- How do we format data? (Serializers)
```

### Step 3: Provide Targeted Context
```python
# Exact files AI needs to follow patterns
/read src/exports/pdf_exporter.py      # Export pattern
/read src/serializers/user.py          # Data formatting
/read src/utils/streaming.py           # Large dataset handling

# Now AI has perfect context
```

### Step 4: Validate Pattern Adherence
```
Review AI output:
✓ Follows export pattern
✓ Uses serializer pattern
✓ Handles streaming
✓ Matches code style
```

## Red Flags

### Context Control Issues
- Providing files AI doesn't need
- Missing key pattern examples
- Giving docs instead of code
- Random file selection

### Codebase Knowledge Gaps
- Can't explain why patterns exist
- Don't know best examples
- Unfamiliar with core abstractions
- Can't predict AI's struggles

## Measuring Mastery

You've achieved mastery when:
- AI rarely needs additional context
- AI's first attempt is usually correct
- AI follows patterns without being told
- You can predict what AI will struggle with
- Code reviews are mostly "LGTM"

## Investment Strategy

### Week 1-2: Learn the Codebase
- Read best examples of each pattern
- Understand architecture decisions
- Map out the mental model

### Week 3-4: Practice Context Control
- Experiment with minimal context
- Notice what AI struggles with
- Build pattern recognition

### Month 2+: Master the Combination
- Provide perfect context effortlessly
- Write code that AI amplifies
- Teach patterns to AI efficiently

## Real-World Impact

**Before mastery:**
- 30 min finding right context
- AI makes 3-4 attempts
- Code review catches pattern violations

**After mastery:**
- 2 min providing perfect context
- AI gets it right first try
- Code review is just approval

**10x improvement in AI-assisted velocity**

## Remember

```
Great codebase + Deep knowledge + Perfect context = AI superpowers

Missing any one = Struggling with AI
```

The leverage is in mastery, not just using AI.
