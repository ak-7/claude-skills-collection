---
name: ai-augmented-workflow-mastery
description: Use when working with AI coding tools - master the new programmable layer of agents, subagents, prompts, contexts, memory, modes, permissions, tools, plugins, and MCP integrations
---

# AI-Augmented Workflow Mastery

## Overview

Karpathy describes a new programmable layer of abstraction involving agents, subagents, prompts, contexts, memory, modes, permissions, tools, plugins, MCP, and IDE integrations — mastering this stack is now essential.

## When to Use

- Setting up AI-assisted workflows
- Optimizing Claude Code/Cursor usage
- Designing agent interactions
- Managing context and memory
- Building custom tools/plugins

## The New Stack

```
Traditional Stack:      New AI Stack:
- Code                  - Agents
- Functions             - Subagents
- Modules               - Prompts
- APIs                  - Contexts
                        - Memory (skills/CLAUDE.md)
                        - Modes
                        - Permissions
                        - Tools
                        - Plugins
                        - MCP servers
                        - IDE integrations
```

## Mastery Levels

### Level 1: Basic User
- Uses AI as autocomplete
- Copies suggestions directly
- Doesn't understand tool boundaries

### Level 2: Tool User
- Knows slash commands
- Uses skills occasionally
- Basic context awareness

### Level 3: Context Master ✅ (Target)
- Manages context strategically
- Creates custom skills
- Understands tool limitations
- Optimizes for AI strengths

### Level 4: System Builder
- Builds plugins and MCP servers
- Designs multi-agent workflows
- Creates shareable patterns

## Key Concepts to Master

### 1. Context Control
```
# BAD: Wasteful context
/read entire_codebase/

# GOOD: Targeted context
/read src/auth/login.py
```

### 2. Agent Decomposition
```
# BAD: One agent does everything
"Fix all bugs in the codebase"

# GOOD: Subagents with clear tasks
Task 1: Find auth bugs (Explore agent)
Task 2: Fix critical bug (focused agent)
Task 3: Run tests (verification)
```

### 3. Memory Management
```
# Persistent (skills, CLAUDE.md)
- Patterns to always follow
- Project-specific rules
- Consents and preferences

# Session (conversation)
- Current task context
- Temporary decisions
```

### 4. Tool Selection
```
When to use what:
- Bash: Terminal operations
- Read: File content
- Edit: Precise changes
- Task: Complex multi-step work
- Skill: Reusable patterns
```

## The Programmable Layer

Think of AI as a new abstraction layer you can program:

```python
# Old way: Write code
def process_data(data):
    # explicit logic
    pass

# New way: Program the AI
@skill("data-processing-pattern")
def process_data_with_ai(data, agent):
    # AI follows learned pattern
    # You control high-level flow
    pass
```

## Optimization Patterns

### Context Efficiency
- ✅ Provide minimal necessary context
- ✅ Use skills for repetitive guidance
- ✅ Leverage CLAUDE.md for project rules
- ❌ Don't dump entire codebases

### Agent Orchestration
- ✅ Break complex tasks into subagents
- ✅ Use specialized agents (Explore, Plan)
- ✅ Parallel execution when possible
- ❌ Don't use one agent for everything

### Memory Strategy
- ✅ Skills for permanent patterns
- ✅ CLAUDE.md for project specifics
- ✅ Conversation for ephemeral context
- ❌ Don't repeat same guidance

## Red Flags

- Not using skills for repeated patterns
- Dumping full files instead of targeted reads
- Single agent for multi-step workflows
- Not leveraging MCP servers
- Ignoring IDE integrations

## Real-World Impact

**Before mastery:**
- 30 min tasks with poor context
- Repeating same guidance
- Fighting tool limitations

**After mastery:**
- 5 min tasks with optimized context
- Skills handle repetition
- Tools amplify your intent

**10x comes from mastering the AI stack, not just using it.**

## Learning Path

1. **Week 1:** Master basic tools (Read, Edit, Bash)
2. **Week 2:** Create custom skills
3. **Week 3:** Use Task tool with subagents
4. **Week 4:** Optimize context patterns
5. **Month 2:** Build custom MCP servers
6. **Month 3:** Design multi-agent systems

## Remember

This is a new skill stack as important as learning Git, Docker, or Kubernetes was. Invest in mastering it.
