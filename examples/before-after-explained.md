# Same answer, two outputs — annotations explain what changed

The clearest demo of the output rules: one question, the default AI answer, and
the same answer under the rules. Annotations in **[brackets]** name the rule
that shaped each line — that's the "explanations baked into the output."

## The prompt

> "Why does my sourdough starter smell like acetone?"

## Before — a default AI answer

> This usually happens when your starter is hungry and has run out of food,
> causing it to produce excess alcohol and acidic byproducts that give off that
> sharp, nail-polish-remover smell. It's most common when starters are left too
> long between feedings, kept somewhere too warm, or fed with too little flour
> relative to the amount of starter. The good news is this doesn't mean it's
> dead — you can usually revive it by discarding most of it and feeding it more
> frequently for a day or two, after which the smell should return to the
> pleasant tangy-yeasty aroma you're used to. If the smell persists after
> several feedings or the starter shows no signs of activity, you may need to
> consider whether it has actually spoiled...

Wall of text. Answer buried in paragraph 2. Reads like a textbook, not help.

## After — under the Skim Master rules

> **Short answer: it's hungry, not dead.** **[Rule 1 — lead with the answer; Rule 0 — the line carries the fact]**
>
> That sharp smell = alcohol + acid byproducts from an **overdue** starter.
>
> **Usual causes:**
> - Left too long between feedings **[Rule 4 — one idea per line]**
> - Kept somewhere **too warm**
> - Fed too little flour for how much starter you have
>
> **Fix it:**
> 1. Discard most of the starter (keep ~2 tbsp) **[Rule 2 — numbered steps]**
> 2. Feed it 1:1:1 (starter:flour:water)
> 3. Repeat every 12 hrs for 1-2 days **[Rule 6 — concrete time, not "a while"]**
> 4. Smell should turn tangy-yeasty again, not sharp
>
> **No opener. No closer.** **[Rule 10 — nothing before the answer, nothing after the fix]**

## What the rules are doing, line by line

| Line in the "after" | Rule firing |
|---|---|
| "Short answer: it's hungry, not dead." | **Rule 1** lead with the answer — first line is the substance |
| Bold **terms**, short lines | **Rule 0** — every span carries a fact; scanning works |
| 3 causes, 1 idea each | **Rule 4** suppress tangents + one idea per line |
| Numbered 4-step fix | **Rule 2** numbered steps for anything sequential |
| "12 hrs, 1-2 days" | **Rule 6** specific time estimates in minutes/hours |
| List capped at 4 | **Rule 9** cap lists at 5, split do-now vs later |
| No "Great question!" / "Hope this helps!" | **Rule 10** no preamble, no recap, no closers |
| Nothing re-summarized at the end | **Pre-Send Check** — delete any closing recap |

Same facts as the "before" — all of them. Nothing summarized away. The rules
restructure the delivery; they never cut substance.

## Try it yourself

1. **Claude Code** — save `rules/skim-master-rules.md` to
   `~/.claude/rules/skim-master-rules.md`. Every session follows it.
2. **Claude app** — paste the slim version (`claude-app/instructions-for-claude.md`)
   into Settings → General → Profile → "Instructions for Claude".
3. **Ad-hoc** — end any prompt with the word `skim` to reformat that one answer
   (see `SKILL.md`).

Then ask the agent the same question again and watch the difference.

## Honest caveats

- These are **prompt-layer rules** — the model judges them per message. No code
  gate enforces them (on hosts without one). They're reliable, not infallible.
- The "before" above is representative, not a quote from any specific model —
  every model has its own default voice. The point is the *shape* of the change.
- Rules have explicit **off-switches**: when the user asks for a specific format,
  or a document/artifact is being produced, the rules step aside (Scope +
  Off-switches in the canonical block).
