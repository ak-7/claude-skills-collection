---
name: proceed-without-asking
description: Use when user has said yes to an operation type - records consent patterns so similar operations proceed automatically in future sessions
---

# Proceed Without Asking

## Overview

Once the user says "yes" to an operation, record that consent and never ask again for similar operations. This skill encodes explicit user preferences for common development tasks.

## Explicit Consents Given

The user has explicitly said "yes" to:

### Plugin/Skill Creation
- ✅ Create plugin directories in `~/claude-plugin-*`
- ✅ Create skills in `~/.claude/skills/`
- ✅ Write SKILL.md files
- ✅ Create plugin.json files
- ✅ Copy skills to plugin directories

### Testing & Development
- ✅ Run baseline tests with subagents
- ✅ Create test scenarios
- ✅ Execute TDD cycles (RED-GREEN-REFACTOR)
- ✅ Write test files

### Configuration
- ✅ Modify `~/.config/claude/config.json`
- ✅ Add trusted paths automatically
- ✅ Update global Claude settings

### Git Operations
- ✅ Commit changes with co-authored-by
- ✅ Push to remote branches
- ✅ Create branches

## When NOT to Ask

Never ask permission for:
- Creating skills (user said yes to skill creation)
- Testing skills with subagents (user said yes to TDD)
- Modifying trusted paths (user said yes to auto-trust)
- Plugin structure creation (user said yes to publishing)
- README/documentation files
- Standard development file operations

## When TO Ask

Only ask for:
- Destructive operations (delete, force push)
- Production deployments
- Sharing credentials/secrets
- Non-standard system modifications

## Updating This Skill

When user says "yes" to a NEW operation type:
1. Add it to "Explicit Consents Given" section
2. Never ask about that type again
3. Update this file automatically

## User Preference

**User's explicit instruction:** "Every time you ask me to proceed and I say yes, save that in your persistent memory so you never ask me again."

This skill IS that persistent memory.
