# Akanksha's Claude Skills Collection

Personal skills for Claude Code that persist across all sessions and repositories.

## Skills Included

### Core Development Skills (3)

#### `reading-before-calling`
Prevents common coding errors through proactive verification.
- Tuple unpacking in wrong order
- Parameter name mismatches
- Stale documentation bugs

#### `auto-trust-paths`
Automatically adds common directory patterns to trusted paths.
- Standard development directories
- Virtual environments
- Build artifacts

#### `proceed-without-asking`
Records user consent patterns for automatic approval.
- One "yes" = permanent consent for that pattern

### Compound Engineering Skills (10)

Based on [Compound Engineering](https://every.to/guides/compound-engineering) principles.

#### 1. `systems-thinking-over-code-output`
10x engineers don't write code 10x faster — they make architecture decisions that result in dramatically better downstream impact.

#### 2. `ai-augmented-workflow-mastery`
Master the new programmable layer: agents, subagents, prompts, contexts, memory, modes, permissions, tools, plugins, MCP, and IDE integrations.

#### 3. `architecture-90-10-rule`
Spend 90% of time on planning and architecture because good structure dramatically improves LLM effectiveness and future development speed.

#### 4. `context-control-and-codebase-mastery`
The biggest leverage is context control — knowing how to write good code AND knowing your codebase deeply to provide the right context to LLMs.

#### 5. `problem-selection-and-prioritization`
Taste in choosing what to build is the ultimate multiplier. Know what is valuable, get it done, and ship to market.

#### 6. `ai-as-amplifier-mindset`
AI is an amplifier of strengths and weaknesses — if you're fast, you're faster; fundamentals matter more than ever.

#### 7. `prompting-and-eval-intuition`
Build intuition about AI models' personalities, strengths, blind spots, and quirks. Sharpen both "agency" (prompt) and "taste" (eval).

#### 8. `deep-reading-engineering-blogs`
Read engineering blogs from Google Research, Meta, Netflix, Spotify, Uber, OpenAI, and Cloudflare to stay at the frontier of system design thinking.

#### 9. `10x-leadership-force-multiplier`
Leaders who can get 10x more out of the people they work with are more rare and valuable than 10x individual contributors.

#### 10. `exposure-to-true-excellence`
The challenge for most who want to become great is that they never meet true greatness — finding "bar setters" is the first job.

## Installation

Copy skills to your personal skills directory:

```bash
# Clone the repo
git clone https://github.com/ak-7/claude-skills-collection.git
cd claude-skills-collection

# Install all skills
cp -r * ~/.claude/skills/
```

## Usage

Skills activate automatically based on code patterns, operations, and contexts. No manual invocation needed.

## Updating

```bash
cd claude-skills-collection
git pull
cp -r * ~/.claude/skills/
```

## Author

Akanksha Bindal

## License

MIT
