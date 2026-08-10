---
name: adhd-friendly-formatting
description: >-
  Use when a message ends in adhd — reformat the reply.
---

# ADHD-Friendly Formatting

A formatting overlay. It changes how the answer is *presented*, not what's in it — never drop substance or accuracy to hit a format.

## When this triggers

- The last word of the user's message is "adhd" (case-insensitive), optionally followed by punctuation or whitespace. Examples that trigger: `explain how compound interest works adhd`, `fix this bug ADHD!`, `whats the best way to learn spanish adhd?`
- The user's entire message is just `adhd` on its own — reformat the response immediately above it using the rules below, don't ask what they mean.
- "adhd" appearing mid-sentence, not at the end (e.g. "I have adhd, should I..."), is NOT a trigger by itself — treat it as context about the user, not a formatting command.

## Before responding

1. Strip the trigger word off — it's a formatting instruction, not part of the actual question. Answer the real request underneath it.
2. Do the normal thinking/research/work needed to get the answer right.
3. Apply the formatting rules below to how it's presented.

## Formatting rules

- **Kill walls of text.** Any paragraph longer than ~2 sentences gets broken into short bullets.
- **Numbered steps for anything sequential** — a process, a setup, instructions with an order. Break big steps into smaller sub-steps rather than one dense step.
- **Bold the load-bearing words** — key terms, action items, numbers, warnings/caveats — so someone scanning instead of reading top-to-bottom still catches the important parts.
- **One idea per line.** Avoid stacking multiple clauses into one bullet with commas and "and"s.
- **Short section headers** (bold text or `##`) to chunk distinct topics instead of one continuous answer, if the response covers more than one topic.
- **Code stays code.** Don't bullet-ify code blocks or break syntax apart — only the prose *around* the code (explanations, setup steps, "why this works") gets the treatment.
- **Don't inflate short answers.** If the honest answer is one line, give one bolded line — don't manufacture bullets or steps to look more "formatted."
- Substance stays intact: this is a restructure, not a summary. If the un-triggered answer would include five considerations, the triggered answer still includes all five — just as five scannable bullets instead of one paragraph.

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
