# Akanksha's Claude Skills Collection

Personal skills for Claude Code that persist across all sessions and repositories.

## Skills Included

### Development Skills

#### `reading-before-calling`
Prevents common coding errors through proactive verification.

**Prevents:**
- Tuple unpacking in wrong order
- Parameter name mismatches
- Stale documentation bugs
- Assuming return structures

**Impact:** 10 seconds prevention vs 15 minutes debugging

#### `auto-trust-paths`
Automatically adds common directory patterns to trusted paths configuration.

**Auto-trusts:**
- Standard development directories (src/, test/, scripts/)
- Virtual environments
- Build artifacts
- Plugin directories

**Benefit:** Never manually approve common operations again

#### `proceed-without-asking`
Records user consent patterns so similar operations proceed automatically.

**Tracks:**
- Plugin/skill creation consent
- Testing & development workflows
- Configuration modifications
- Git operations

**Result:** One "yes" = permanent consent for that pattern

## Installation

Copy skills to your personal skills directory:

```bash
cp -r * ~/.claude/skills/
```

## Usage

Skills activate automatically based on code patterns and operations. No manual invocation needed.

## Author

Akanksha Bindal

## License

MIT
