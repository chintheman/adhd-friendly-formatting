# adhd-friendly-formatting

A formatting overlay skill for AI agents (Claude Code, Hermes, any agent that reads SKILL.md). It changes how an answer is *presented*, not what's in it — never drop substance or accuracy to hit a format.

## Trigger

Applies whenever the user's message ends with the word **"adhd"** (case-insensitive, with or without trailing punctuation):

- `explain how compound interest works adhd`
- `fix this bug ADHD!`
- `whats the best way to learn spanish adhd?`

Also triggers when the user's entire message is just `adhd` on its own — that means *"reformat your previous response this way."*

**Not a trigger:** "adhd" appearing mid-sentence (e.g. "I have adhd, should I...") — that's context about the user, not a formatting command.

## How to use it

1. Install the skill into your agent's skills directory (e.g. `~/.hermes/skills/productivity/adhd-friendly-formatting/SKILL.md` for Hermes, or `.claude/skills/` for Claude Code).
2. End any prompt with the word `adhd`.
3. The agent strips the trigger word, answers the real request, and reformats the presentation.

## Formatting rules

- **Kill walls of text.** Any paragraph longer than ~2 sentences gets broken into short bullets.
- **Numbered steps for anything sequential** — break big steps into smaller sub-steps rather than one dense step.
- **Bold the load-bearing words** — key terms, action items, numbers, warnings/caveats — so someone scanning still catches the important parts.
- **One idea per line.** Avoid stacking multiple clauses into one bullet with commas and "and"s.
- **Short section headers** (bold text or `##`) to chunk distinct topics.
- **Code stays code.** Don't bullet-ify code blocks — only the prose around the code gets the treatment.
- **Don't inflate short answers.** If the honest answer is one line, give one bolded line.
- **Substance stays intact** — this is a restructure, not a summary.

## Example

**Without trigger** ("why does my sourdough starter smell like acetone?"):

> This usually happens when your starter is hungry and has run out of food, causing it to produce excess alcohol and acidic byproducts that give off that sharp, nail-polish-remover smell. It's most common when starters are left too long between feedings, kept somewhere too warm, or fed with too little flour relative to the amount of starter. The good news is this doesn't mean it's dead — you can usually revive it by discarding most of it and feeding it more frequently for a day or two...

**With trigger** ("why does my sourdough starter smell like acetone adhd"):

> **Short answer: it's hungry, not dead.**
>
> That smell = alcohol + acid byproducts from an **overdue** starter.
>
> **Usual causes:**
> - Left too long between feedings
> - Kept somewhere **too warm**
> - Fed too little flour for how much starter you have
>
> **Fix it:**
> 1. Discard most of the starter (keep ~2 tbsp)
> 2. Feed it 1:1:1 (starter:flour:water)
> 3. Repeat every 12 hrs for 1–2 days
> 4. Smell should turn tangy-yeasty again, not sharp

## License

MIT
