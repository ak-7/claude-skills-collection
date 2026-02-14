---
name: architecture-90-10-rule
description: Use when starting new features or major work - spend 90% of time on planning and architecture because good structure dramatically improves LLM effectiveness and future development speed
---

# Architecture & Planning (90/10 Rule)

## Overview

It's worth spending 90% of time on planning and designing good architecture because of how much better the LLM will work with the codebase in the future. The plan is everything; execution follows.

## When to Use

- Starting new features
- Major refactors
- New projects
- System design decisions
- Before writing ANY significant code

## The 90/10 Split

```
Traditional:           AI-Augmented:
10% Planning          90% Planning & Architecture
90% Coding            10% Execution (AI-assisted)
```

**Why this works:** Good architecture makes AI 10x more effective. Bad architecture makes AI create technical debt faster.

## The Iron Law

```
NEVER START CODING BEFORE ARCHITECTURE IS CLEAR
```

**Exceptions:** None. Even "quick prototypes" need architectural thinking.

## 90% Planning Checklist

### Phase 1: Problem Understanding (20%)
- [ ] What problem are we actually solving?
- [ ] What are the constraints?
- [ ] What are the success criteria?
- [ ] What's the scope (and what's explicitly out)?

### Phase 2: Architecture Design (40%)
- [ ] What's the high-level structure?
- [ ] What are the key abstractions?
- [ ] How do components interact?
- [ ] What are the extension points?
- [ ] What patterns from existing codebase apply?

### Phase 3: AI Optimization (20%)
- [ ] How will AI understand this structure?
- [ ] What context will AI need?
- [ ] Are abstractions clear and consistent?
- [ ] Will this be maintainable with AI assistance?

### Phase 4: Execution Plan (10%)
- [ ] Break into implementable chunks
- [ ] Identify dependencies
- [ ] Plan testing strategy
- [ ] Document key decisions

## Why This Multiplies AI Effectiveness

### ❌ BAD Architecture + AI
```
Problem: Add user authentication

Bad approach:
- Start coding login page
- AI suggests scattered auth logic
- Security mixed with UI
- Hard to test
- Future features break things

Result: 10x technical debt, created faster
```

### ✅ GOOD Architecture + AI
```
Problem: Add user authentication

Good approach:
1. Design auth middleware pattern
2. Separate concerns (auth, session, UI)
3. Define clear interfaces
4. Plan for OAuth, 2FA future additions

Then AI executes:
- Clean separation of concerns
- Follows established patterns
- Easy to extend
- Testable components

Result: 10x better code, faster
```

## Planning Artifacts

Create these BEFORE coding:

### 1. Architecture Document
```markdown
# Feature: User Authentication

## Overview
Middleware-based auth with pluggable providers

## Components
- AuthMiddleware: Request interception
- AuthProvider: Interface for auth backends
- SessionManager: Token/session handling

## Data Flow
[Request] → AuthMiddleware → AuthProvider → SessionManager → [Protected Route]

## Extension Points
- New auth providers (OAuth, SAML)
- Custom session storage
- Auth event hooks
```

### 2. Interface Definitions
```python
# Define interfaces before implementation
class AuthProvider(Protocol):
    def authenticate(self, credentials: dict) -> User: ...
    def validate_token(self, token: str) -> bool: ...
```

### 3. Test Strategy
```markdown
## Testing Approach
- Unit: Each provider independently
- Integration: Middleware + provider flow
- E2E: Full auth flow with real requests
```

## Time Investment Math

**Scenario:** Add major feature (estimate 20 hours total)

**Traditional (10/90):**
- 2 hours planning
- 18 hours coding + debugging + refactoring
- Result: Suboptimal architecture, tech debt

**90/10 Rule:**
- 18 hours planning & architecture
- 2 hours AI-assisted execution
- Result: Clean architecture, extensible, maintainable

**Long-term payoff:**
- Future features: 10x easier
- AI effectiveness: 10x better
- Technical debt: 10x less

## Red Flags - Stop Coding

You're violating the 90/10 rule if:
- "Let me just try something"
- "I'll refactor once it works"
- "The structure will emerge"
- Starting to code before plan is written
- Jumping to implementation details

**All of these mean: Stop. Go back to planning.**

## Planning Tools

### 1. EnterPlanMode
Use `/plan` for complex features - forces structured thinking

### 2. Architecture Diagrams
```
[Client] → [API Gateway] → [Auth Service] → [User Service]
                                ↓
                          [Session Store]
```

### 3. Decision Records
```markdown
## Decision: Use JWT for session tokens

### Context
Need stateless auth for microservices

### Options
1. Server-side sessions
2. JWT tokens
3. OAuth tokens

### Decision: JWT

### Rationale
- Stateless (scales horizontally)
- Standard format
- Can be validated without DB lookup
```

## Real-World Examples

**Example 1: API Client Library**

❌ Bad (start coding):
```python
# Just start building
def call_api(endpoint):
    response = requests.get(endpoint)
    return response.json()
```

✅ Good (plan first):
```
Architecture:
- BaseClient: Connection management
- RequestBuilder: Compose requests
- ResponseParser: Handle responses
- RetryStrategy: Configurable retries
- AuthHandler: Token injection

Then AI implements each cleanly
```

**Example 2: Data Pipeline**

❌ Bad (immediate coding):
```python
# Quick script
data = read_csv('input.csv')
cleaned = data.dropna()
transformed = cleaned.apply(lambda x: x * 2)
write_csv(transformed, 'output.csv')
```

✅ Good (architecture first):
```
Design:
1. Pipeline stages: Extract → Transform → Load
2. Each stage is pluggable
3. Error handling strategy
4. Observability points
5. Testing approach

Then AI implements pipeline framework
```

## The Paradox

**Spending more time planning = Finishing faster**

Because:
- AI executes good architecture rapidly
- No backtracking or refactoring
- Future work builds on solid foundation
- Technical debt stays low

## Measuring Success

You're doing it right when:
- Coding phase is almost boring (AI just executes)
- No major surprises during implementation
- Future features are easy to add
- Team can understand and extend your code
- AI suggestions align with architecture

## Remember

**The plan is everything. The plan is nothing.**

- The plan is everything: Forces deep thinking
- The plan is nothing: Adapt when you learn

But always start with 90% planning. The execution will take care of itself.
