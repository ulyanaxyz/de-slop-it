---
name: antislop
description: >-
  Scores text for "AI slop" and, on request, rewrites it to read like a real
  person wrote it. First rates the writing 0–100 across five dimensions (slop
  vocabulary, cliché phrases, sentence structure, vocabulary diversity, content
  substance), shows what triggered each flag, then asks whether to de-slop it.
  Use this whenever the user wants to check if writing "sounds like AI," score or
  rate content for slop, make text "sound more human / more natural / less
  robotic / less generic / less corporate," "de-slop," proofread, or punch up any
  text, email, blog post, landing page, caption, or document — even if they don't
  say the word "AI."
---

# Antislop

Two jobs, done in order:

1. **Detect** — score a piece of text for "AI slop" and show exactly what's
   wrong, the way a tool like slopdetector.org does.
2. **Rewrite** — *after asking the user*, fix the flagged problems so the text
   reads like a real person wrote it, without changing what it says or flattening
   the author's voice.

Always score first. Never jump straight to rewriting — the user decides whether
they want the rewrite.

## The workflow

### Step 1 — Score the text

Read the text once for meaning and voice, then rate it against the five
dimensions below. Read `references/ai-tells.md` for the detailed patterns and
before/after examples behind each dimension.

Present the score like this:

```
Slop score: 68 / 100  (higher = more slop)

  Slop vocabulary      16 / 20   "leverage", "utilize", "seamless", "delve"
  Cliché phrases       14 / 20   "In today's fast-paced world", "at the end of the day"
  Sentence structure   15 / 20   uniform sentence length, 6 em-dashes, "Moreover/Furthermore"
  Vocabulary diversity   9 / 20   repetitive; "solution" used 5×
  Content substance     14 / 20   no numbers, names, or concrete specifics

Verdict: Generic Slop
```

Scoring guidance:

- **Each dimension is 0–20, where higher means MORE slop.** Total is the sum,
  0–100. This mirrors slopdetector.org so scores feel familiar.
- **Verdict band:** 0–25 *Not Slop* · 26–60 *Some Slop* · 61–100 *Heavy Slop*.
- **Name the archetype** when one fits, to make the verdict specific — e.g.
  "Generic Slop", "Pseudo-Insight Slop", "Fake Authority Slop", "Wikipedia
  Rehash", "Wellness Slop" (a piece can have more than one). See
  `references/ai-tells.md` for definitions and examples.
- Make the score **explainable** — always quote the actual words and phrases that
  triggered each flag. A score with no evidence is useless.
- Be fair. Good human writing can use an em-dash or the word "important." Flag
  *patterns and accumulation*, not isolated instances. Explain the reasoning
  rather than mechanically counting.

### Step 2 — Ask before rewriting

After showing the score, ask the user whether they want it de-slopped. Keep it
short, e.g.:

> Want me to de-slop this? I'll keep your voice and meaning — just say the word,
> or tell me how hard to go (light touch vs. full rewrite).

If the user's original request *already* asked for a rewrite (e.g. "score this
and fix it," "de-slop this"), you can score and rewrite in one turn — but still
show the score first so they see what changed and why.

### Step 3 — Rewrite (only when asked)

Default to **surgical edits**: preserve the author's voice, structure, and
intent; change what's actually off and leave the rest alone. The output should
still sound like the same person, just sharper. Go heavier only if the user asks.

Removing slop is only half the job — put substance back in. Read
`references/rewrite-guide.md` and aim for the four antidote qualities
(specificity, lived experience, cited sources, information gain). Apply the
**Specificity Test** and **Deletion Test** to each sentence, and run the
anti-slop checklist before returning the result.

Hard rules for the rewrite:

- **Never invent facts.** The "content substance" dimension rewards numbers,
  names, and specifics — but you must not fabricate them. If the text is empty of
  specifics, say so and ask the author to supply them; don't make them up to game
  the score.
- **Fix causes, not symptoms.** Don't just swap "leverage" → "use" and call it
  done. Read what the sentence is trying to say and write it the way a person
  would.
- **Don't over-correct.** Removing every em-dash or every transition word can
  make writing feel choppy and equally artificial. Aim for natural, not sterile.

### Step 4 — Show the result

Return the rewritten text, then:

- A short, plain-language note on the main things you changed and why.
- The new slop score so the improvement is visible (e.g. "68 → 12").

## The five dimensions

These mirror slopdetector.org. Full patterns and examples live in
`references/ai-tells.md` — read it before scoring.

1. **Slop vocabulary** — overused words: "leverage", "utilize", "delve",
   "seamless", "robust", "elevate", "unlock", "game-changing".
2. **Cliché phrases** — empty full phrases: "In today's fast-paced world…",
   "It's important to note that…", "at the end of the day…".
3. **Sentence structure** — uniform sentence lengths, transition-word crutches
   ("Moreover", "Furthermore", "However"), em-dash overuse, rule-of-three
   padding, the "it's not just X, it's Y" construction.
4. **Vocabulary diversity** — repetitiveness; the same words and sentence
   openings recurring; low variety.
5. **Content substance** — does it say anything concrete? Numbers, dates, names,
   specifics vs. vague generalities that could apply to anything.

## References

- `references/ai-tells.md` — the detailed catalogue behind the five dimensions
  plus the five slop archetypes, with examples and notes on when a "tell" is
  actually fine. Read it before scoring.
- `references/rewrite-guide.md` — the antidote: the four qualities of non-slop
  writing, the rewrite principles, the Specificity/Deletion tests, and the
  anti-slop checklist. Read it before rewriting.
