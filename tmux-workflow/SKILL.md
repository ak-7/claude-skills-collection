---
name: tmux-workflow
description: >
  Named tmux session management for context switching between tasks.
  Auto-invokes when user wants to create, list, switch, or manage tmux sessions.
  Provides naming conventions and quick commands without modifying shell config.
---

# Tmux Workflow Skill

## When to Invoke

Activate when the user:
- Wants to create a new tmux session
- Asks to switch between tasks/contexts
- Wants to see active sessions
- Says "new session", "switch context", "tmux"

## Commands Reference

### Create Named Session
```bash
tmux new -s <descriptive-name>
```

### Create in Background (detached)
```bash
tmux new -d -s <name>
```

### List All Sessions
```bash
tmux ls
```

### Attach to Session
```bash
tmux attach -t <name>
```

### Switch Sessions (inside tmux)
- `Ctrl-b s` — interactive session picker
- `Ctrl-b (` — previous session
- `Ctrl-b )` — next session

### Detach (keep alive)
- `Ctrl-b d`

### Rename Current Session
```bash
tmux rename-session <new-name>
# or Ctrl-b $
```

### Kill a Session
```bash
tmux kill-session -t <name>
```

## Naming Convention

Use `<category>-<specific-task>` format:

| Category | Example Session Names |
|---|---|
| E6 mocks | `e6-delivery-estimation`, `e6-fraud-detection`, `e6-recsys` |
| Coding prep | `coding-beam-search`, `coding-attention-scratch` |
| Behavioral | `behavioral-stories`, `behavioral-pitch` |
| Skills/setup | `claude-skills-setup`, `drive-org` |
| General | `research-loss-functions`, `debug-mcp-server` |

## Workflow Pattern

```
1. Starting a new task:
   tmux new -s e6-search-ranking

2. Need to context switch:
   Ctrl-b d                          # detach current
   tmux new -s coding-softmax        # start new task

3. Coming back later:
   tmux ls                           # see all sessions
   tmux attach -t e6-search-ranking  # resume

4. Done with a task:
   tmux kill-session -t coding-softmax
```
