# adhd-friendly-formatting — output rules for AI agents

Two layers that stop AI assistants from writing walls of text:

1. **Always-on output governance** — a rules block (Scope → Rule 0 → Rules →
   Pre-Send Check → Off-switches) that shapes *every* chat reply: answer first,
   plain English instead of system vocabulary, substance over format, no preamble,
   no recap, no closers.
2. **On-demand overlay** — end any prompt with the word `adhd` and the agent
   reformats *that one answer* (kill the wall, number the steps, bold the
   load-bearing words).

Built from months of real corrections — every rule traces to a specific moment
where a default AI answer wasted the reader's attention. Runs in production
across Hermes Agent (core), Claude Code, and the Claude app.

## What's inside

| Path | What it is |
|---|---|
| `rules/adhd-output-rules.md` | **Canonical rules block.** Drop-in file for any agent with standing instructions (Claude Code, Hermes, custom system prompts) |
| `claude-app/instructions-for-claude.md` | Slim version for the Claude app's account-level "Instructions for Claude" (~1,500-char cap) |
| `examples/before-after-explained.md` | The same answer before/after, with the rule firing on every line explained |
| `SKILL.md` | The `adhd`-suffix overlay as an installable skill |
| `LICENSE` | MIT |

## Install

**Claude Code** (governs every session):

```bash
mkdir -p ~/.claude/rules
cp rules/adhd-output-rules.md ~/.claude/rules/
```

Files in `~/.claude/rules/` auto-load at session start — no import line, no
CLAUDE.md edit. (You can also append the block to `~/.claude/CLAUDE.md`
directly.) New sessions only; a running session keeps its start-of-session
context.

**Claude app** (claude.ai):

Settings → General → Profile → "Instructions for Claude" → paste the slim
version from `claude-app/instructions-for-claude.md`. Applies to new chats.
For full governance on a work project, paste the complete block into that
Project's instructions instead (~8,000-char cap there).

**Hermes Agent**: shipped in core. `agent.adhd_output_rules: true` in
config.yaml (default on); `output_style: broadcast` suppresses it for
report-shaped sessions. `rules/adhd-output-rules.md` mirrors the production
constant.

**Any other agent**: paste the block into its system prompt / custom
instructions equivalent.

**Ad-hoc, one answer**: end your prompt with the word `adhd` — see `SKILL.md`
for trigger rules and the formatting overlay.

## The shape of it

The "after" answer in `examples/before-after-explained.md` is 40% shorter and
answers the question in its first line:

```
Before:  "This usually happens when your starter is hungry and has run out of
          food, causing it to produce excess alcohol and acidic byproducts..."
After:   "Short answer: it's hungry, not dead. Here's why + the 4-step fix."
```

Same facts. Better delivery. Nothing summarized away — the rules restructure,
they never cut substance (that's Rule 0's job).

## Mechanism notes (read before trusting it)

- **Prompt layer, not code.** The rules live in context and the model judges
  them per message. On hosts with a config flag (Hermes) that's a real switch;
  on Claude Code and the Claude app there is no code gate — the prompt is the
  whole mechanism. Reliable, not infallible.
- **Why not make it shorter?** Distilling the rules saves tokens but each line
  exists because a default answer failed without it. The full block costs
  roughly 850 tokens, loaded once per session, cached.
- **Explicit off-switches** (in the block): user asks for a specific format →
  that wins; producing a document/artifact/code → rules step aside inside the
  artifact; broadcast-style reports with their own templates → exempt.
- **On-demand ≠ import.** Claude Code `@imports` expand at launch (same context
  cost, just organization). True on-demand loading is *skills* — wrong for
  rules that must shape every reply.

## Credit

- Original 10-rule lineage: [ayghri/i-have-adhd](https://github.com/ayghri/i-have-adhd)
  (MIT) by jjacky — the Claude Code CLAUDE.md workflow this grew from.
- Structure patterns drawn from Ed Leeman's CLAUDE.md workflow.
- Playbook v2 (Scope, Rule 0, Pre-Send Check, Off-switches) refined through
  production use across Hermes Agent + Claude Code (Jul-Sep 2026), including an
  independent model review pass that fixed five real wording bugs.
- Sample "before" text is representative of default model output, not a quote.

## License

MIT
