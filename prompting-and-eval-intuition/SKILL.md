---
name: prompting-and-eval-intuition
description: Use when working with AI models - build intuition about AI personalities, strengths, blind spots, and quirks to sharpen both agency (prompt) and taste (eval)
---

# Prompting & Eval Intuition

## Overview

Yuchen Jin argues for building intuition about AI models' personalities, strengths, blind spots, and quirks, sharpening both "agency" (prompt) and "taste" (eval).

## When to Use

- Crafting prompts for AI
- Evaluating AI output
- Debugging AI failures
- Optimizing AI workflows
- Teaching others to use AI

## The Two Skills

```
Agency (Prompt): Getting AI to do what you want
Taste (Eval): Knowing if what AI did is good

Both required for AI mastery
```

## Agency: The Art of Prompting

### Level 1: Naive Prompting
```
"Make a login page"

Problem: Vague, AI guesses
Result: May not match needs
```

### Level 2: Detailed Prompting
```
"Create a login page with:
- Email and password fields
- Remember me checkbox
- Forgot password link
- Responsive design"

Better: More specific
Still: AI might miss patterns
```

### Level 3: Context-Aware Prompting ✅
```
"Create a login page following our auth pattern:
- Use AuthForm component (see src/components/AuthForm.tsx)
- Follow Material-UI styling (see src/theme/index.ts)
- Implement validation (see src/utils/validation.ts)
- Add error handling (see src/hooks/useErrorHandler.ts)"

Best: AI has full context and patterns
```

## Understanding AI Personalities

### Claude
**Strengths:**
- Thoughtful, careful
- Great at explaining reasoning
- Strong at following instructions
- Excellent with context

**Weaknesses:**
- Can be verbose
- Sometimes overthinks
- May ask for clarification more

**Prompting style:**
- Provide clear context
- Be explicit about constraints
- Ask for step-by-step reasoning

### GPT-4
**Strengths:**
- Fast, creative
- Good at code generation
- Handles ambiguity well
- Strong at completions

**Weaknesses:**
- Can hallucinate confidently
- May skip important checks
- Less likely to ask clarifying questions

**Prompting style:**
- Be very specific
- Add verification steps
- Request error handling

### Copilot
**Strengths:**
- Real-time suggestions
- Pattern recognition
- Fast completions
- IDE integration

**Weaknesses:**
- No conversation context
- Can't explain reasoning
- Autocomplete only

**Prompting style:**
- Use comments as prompts
- Show examples inline
- Name things clearly

## Common AI Blind Spots

### 1. Cannot Verify Code Executes
```
AI writes: db.query("SELECT * FROM users WHERE id = $1")
Reality: Syntax error, wrong driver method
Blind spot: Can't actually run the code
```

**Your job:** Verify, test, validate

### 2. Doesn't Know Your Codebase
```
AI suggests: Use UserService.getUser()
Reality: You have UserRepository.findById()
Blind spot: Inventing APIs that don't exist
```

**Your job:** Provide codebase context

### 3. Optimizes for Elegance Over Practicality
```
AI writes: Functional, immutable, perfect
Reality: Overkill for simple case
Blind spot: Not considering simplicity
```

**Your job:** Ask for simpler solutions

### 4. Doesn't Understand Business Context
```
AI suggests: Cache everything
Reality: Some data must be real-time
Blind spot: Missing business requirements
```

**Your job:** Specify constraints

## Taste: Evaluating AI Output

### Red Flags to Watch For

#### 1. Hallucinated APIs
```python
# AI suggests
from mylib import SuperCoolFunction

# Reality
# SuperCoolFunction doesn't exist
```

**Check:** Verify all imports and APIs

#### 2. Security Issues
```python
# AI suggests
query = f"SELECT * FROM users WHERE name = '{user_input}'"

# Reality
# SQL injection vulnerability
```

**Check:** Review for security patterns

#### 3. Performance Problems
```python
# AI suggests
for user in users:
    db.query(f"SELECT * FROM orders WHERE user_id = {user.id}")

# Reality
# N+1 query problem
```

**Check:** Look for inefficient patterns

#### 4. Over-Engineering
```python
# AI suggests
class AbstractFactoryProviderManager:
    def create_factory_provider(self): ...

# Reality
# Just need a simple function
```

**Check:** Is this simpler than needed?

## Building Intuition

### 1. Pattern Recognition

Track AI failures:
```markdown
## AI Failure Log

### Failed: Hallucinated API
- Prompt: "Use the caching library"
- Output: `from cache import SuperCache`
- Reality: No such import
- Lesson: Always verify imports

### Failed: Security Issue
- Prompt: "Add user search"
- Output: String concatenation SQL
- Reality: SQL injection risk
- Lesson: Check for security patterns
```

### 2. Prompt Experiments

Try variations:
```
Experiment: User registration

Prompt A: "Create user registration"
Result: Basic form, no validation

Prompt B: "Create user registration with email validation, password strength check, and duplicate email handling"
Result: Better, but generic validation

Prompt C: "Create user registration following our UserService pattern (see src/services/UserService.ts), using our validation library (see src/utils/validation.ts)"
Result: Perfect, follows patterns

Lesson: Context + specificity wins
```

### 3. Model Comparison

Same task, different models:
```
Task: Refactor complex function

Claude: Careful, asks questions, explains tradeoffs
GPT-4: Quick, makes assumptions, ships fast
Copilot: Real-time suggestions, no explanation

Lesson: Use right tool for the job
```

## The Prompting Framework

### Step 1: State Intent
```
"We need to add user authentication"
```

### Step 2: Provide Context
```
"Our auth uses JWT tokens stored in HTTP-only cookies.
See src/middleware/auth.ts for the pattern."
```

### Step 3: Specify Constraints
```
"Must handle token expiration gracefully.
Must work with our existing User model.
Must follow our error handling pattern."
```

### Step 4: Set Expectations
```
"Should include:
- Login endpoint
- Token refresh logic
- Logout functionality
- Error responses"
```

### Step 5: Request Verification
```
"Please explain:
1. How token refresh works
2. Where errors are handled
3. What tests are needed"
```

## The Evaluation Checklist

After AI generates code:

### Correctness
- [ ] Does it compile/run?
- [ ] Are all APIs real?
- [ ] Does logic make sense?
- [ ] Are edge cases handled?

### Quality
- [ ] Follows codebase patterns?
- [ ] Proper error handling?
- [ ] Security considerations?
- [ ] Performance concerns?

### Completeness
- [ ] Handles all requirements?
- [ ] Includes tests?
- [ ] Has documentation?
- [ ] Considers edge cases?

### Maintainability
- [ ] Clear naming?
- [ ] Reasonable complexity?
- [ ] Good abstractions?
- [ ] Easy to modify?

## Advanced Techniques

### Chain of Thought Prompting
```
"Let's solve this step by step:
1. First, identify the data structure needed
2. Then, outline the algorithm
3. Finally, implement with error handling"
```

### Few-Shot Learning
```
"Here are two examples of how we handle validation:

Example 1: Email validation (see src/utils/validators/email.ts)
Example 2: Password validation (see src/utils/validators/password.ts)

Now create username validation following the same pattern"
```

### Iterative Refinement
```
First pass: "Create basic auth system"
Review: Too simple
Second pass: "Add token refresh logic"
Review: Missing error handling
Third pass: "Add comprehensive error handling"
Result: Complete implementation
```

## Red Flags in Your Own Evaluation

You're not evaluating well if:
- Accepting code without reading it
- Not testing AI suggestions
- Assuming AI knows your codebase
- Trusting imports without checking
- Skipping security review
- Not considering performance

## The Learning Loop

```
Prompt → Evaluate → Learn → Improve Prompting → Repeat

Each iteration:
- Better prompts
- Better evaluation
- Sharper intuition
```

## Measuring Progress

Track these metrics:

```
Week 1:
- AI success rate: 40%
- Revisions needed: 3-4
- Time to good code: 30 min

Week 4:
- AI success rate: 70%
- Revisions needed: 1-2
- Time to good code: 10 min

Week 12:
- AI success rate: 90%
- Revisions needed: 0-1
- Time to good code: 5 min
```

## Remember

**"AI is a junior developer with infinite patience"**

- Give clear instructions (prompting)
- Review their work carefully (evaluation)
- Teach them your patterns (context)
- Build intuition through repetition (practice)

**The best AI engineers have the best intuition.**