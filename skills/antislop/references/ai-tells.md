# AI Tells — the catalogue

The detailed patterns behind the five scoring dimensions in `SKILL.md`. Use this
to score text and to guide rewrites. These build *judgment*, not a rigid
find-and-replace list — context decides whether something is actually a problem.
Flag patterns and accumulation, not isolated instances.

> Five-dimension scoring system. Each dimension scores 0–20 (higher = more
> slop); the total is 0–100.

---

## Dimension 1 — Slop vocabulary (0–20)

Overused words that signal machine writing. A few are fine; a pile-up is the tell.

- **leverage** → use
- **utilize** → use
- **delve into** → look at / dig into
- **robust, seamless, cutting-edge, game-changing, world-class, best-in-class**
- **elevate, unlock, empower, supercharge, revolutionize, streamline**
- **realm, landscape, tapestry, testament, beacon**

*When it's fine:* technical writing where "robust" or "leverage" has a precise
meaning (e.g. financial leverage). Judge by whether the word earns its place.

## Dimension 2 — Cliché phrases (0–20)

Full phrases that add no information. Openers and throat-clearing are the worst.

- **Vapid openers & transitions** — "In today's fast-paced world…", "As
  technology continues to evolve…", "In the ever-evolving landscape of…"
- "It's important to note that…", "It's worth mentioning that…"
- "When it comes to…", "At the end of the day…", "Needless to say…"
- Empty closers: "In conclusion…", "Ultimately…", "By following these steps,
  you'll be well on your way to…"

## Dimension 3 — Sentence structure (0–20)

- **Uniform sentence length** — every sentence the same medium length and shape.
  Human writing varies: short punchy ones next to longer ones.
- **Transition-word crutches** — "Moreover", "Furthermore", "Additionally",
  "However", "Therefore" opening sentence after sentence.
- **Em-dash overuse** — em-dashes as the default connector throughout.
- **Snappy triads / rule-of-three** — three items or three short clauses to
  drive a point home, when one would do. "Fast, efficient, and reliable." "Think
  bigger. Act bolder. Move faster."
- **The "it's not just X, it's Y" move** — and "It's not about X. It's about Y."
  The signature LLM rhetorical flourish.
- **Unearned profundity** — grand, narrative-shifting beats dropped in from
  nowhere with nothing behind them. "Something shifted." "Everything changed."
  "But here's the thing." Cut these or replace with the actual concrete change.
- **Mid-sentence questions** — a rhetorical question-and-answer crammed into the
  flow to fake suspense. "The solution? It's simpler than you think." "But now?
  You won't be able to unsee this." Almost always rewrites to a plain statement.
- **Over-symmetry / parallelism** — suspiciously balanced structures, repeated
  sentence openings, every paragraph the same length.

## Dimension 4 — Vocabulary diversity (0–20)

- Repetitiveness: the same nouns ("solution", "platform") and verbs recurring.
- Repeated sentence openings and bigrams.
- Low variety overall — a rough mental proxy is type-token ratio (unique words ÷
  total words); below ~0.5 over a substantial passage is a flag.

*Rewrite tactic:* vary word choice and sentence openings, but don't reach for a
thesaurus — natural variety, not showing off.

## Dimension 5 — Content substance (0–20)

Does the text actually say anything?

- **No specifics** — no numbers, dates, names, examples, or data. Vague claims
  that could apply to any company or product.
- **Generic enthusiasm** — "This is a great way to…", "powerful", "exciting"
  with nothing concrete underneath.

*Critical rule for rewriting:* you may flag missing specifics, but **never
fabricate** numbers, names, or facts to fill the gap. Ask the author to supply
them.

---

## Slop archetypes (verdict flavor)

The five dimensions score *how* sloppy text is. These archetypes name *what kind*
of slop it is — use them to make the verdict specific and memorable (e.g.
"Verdict: Generic Slop + Fake Authority Slop"). A piece can have more than one.

The five canonical types. They overlap constantly — real slop usually combines
several.

### Generic Slop
*"The verbal equivalent of stock photos."* Templated, vague content with no
concrete details. Every sentence could apply to any topic.
Signature: *"In today's fast-paced world…"*
> "I'm thrilled to announce that I've learned a valuable lesson about leadership.
> In today's fast-paced world, it's more important than ever to stay authentic
> and leverage synergies. Here are 5 key takeaways that changed my perspective
> forever…"

*Why:* no specific lesson named, no concrete details. Often pairs with
**Pseudo-Insight Slop**.

### Pseudo-Insight Slop
*"Philosophy for people who don't read philosophy."* Sounds profound, delivers
zero information. Framed as a hard-won lesson, but the actual insight is missing
or banal.
Signature: *"The key is to find balance…"*

### Fake Authority Slop
*"Trust me, bro — in article form."* Confident, authoritative tone with no
sources or evidence.
Signature: *"Studies have shown…"*
> "Research has consistently demonstrated that implementing these strategies
> leads to significant improvements. Industry leaders have long recognized the
> importance of this approach. Studies show that organizations who adopt these
> methods see a 300% increase in results."

*Why:* "Studies show" with no citation, "industry leaders" with no names, a
"300% increase" in unnamed "results." Every claim is unfalsifiable.

*Rewrite note:* the fix is **not** to invent a citation — it's to cut the
unsupported claim or ask the author for the real source.

### Wikipedia Rehash
*"The first paragraph of Wikipedia, rephrased."* Presents a basic definition as
original insight, with no analysis or point of view.
Signature: *"X is defined as…"*

*Rewrite note:* the fix is to add an actual angle, opinion, or specific — or cut
the definitional throat-clearing entirely.

### Wellness Slop
*"The content equivalent of a live, laugh, love sign."* Universalized self-help
that comforts rather than helps.
Signature: *"Self-care isn't selfish…"*
> "Remember that self-care isn't selfish — it's necessary. Take time to breathe,
> practice gratitude, and honor your journey. You are exactly where you need to
> be. Embrace your authentic self and set healthy boundaries."

*Why:* no specific techniques, no personal experience, no actionable guidance.

---

## Human signals — what natural writing does

Useful as a target for rewrites:

- Varied sentence rhythm; the occasional fragment or one-liner.
- Concrete details and specific examples over abstractions.
- A point of view — opinions, mild asymmetry, the occasional aside.
- Plain words where a fancy one isn't needed.
- Not every paragraph wrapped in a neat summary bow.

## To add as we iterate

- Genre-specific tells (marketing vs. technical vs. casual).
- Formatting tells (excessive bolding, bullet-itis, emoji-as-punctuation).
- More before/after pairs drawn from real examples you provide.
