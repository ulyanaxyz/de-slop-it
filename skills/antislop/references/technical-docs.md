# Technical Documentation lens

Technical writing plays by different rules. README files, API references,
tutorials, runbooks, guides, code comments, and changelogs are judged on whether
a reader can *do the thing afterward* — not on voice, stance, or personality.

Apply this lens when the text is clearly documentation. It overrides parts of the
general rubric: some "AI tells" are correct here, and docs have slop of their own.

## How to tell it's technical documentation

Signals: code blocks, commands, file paths, API/parameter names, version numbers,
install/setup steps, "how to" framing, error messages, configuration keys, or it
lives in a README/docs site. When unsure, ask the user, or score both lenses and
say which you applied.

## What is NOT slop in docs (don't penalize these)

The general rubric flags these; in documentation they're often *good practice*:

- **Repeated terminology.** Use the same word for the same thing every time.
  "Variety" here causes bugs — calling it "token", then "key", then "credential"
  for one concept is worse than repetition. Don't dock vocabulary diversity for
  consistent technical terms.
- **Parallel structure.** Steps, parameter lists, and option tables *should* look
  uniform. Symmetry aids scanning. Don't flag it as robotic.
- **Definitional sentences.** "A webhook is an HTTP callback that…" is fine when
  the reader needs the definition. Wikipedia Rehash only applies if the
  definition is padding with no purpose, not when it's genuinely needed.
- **No personal voice / stance / lived experience.** Docs are usually
  impersonal by design. Don't ask for opinions, anecdotes, or a "disagreeable
  stance." The antidote qualities map differently here (see below).
- **Domain vocabulary used precisely.** "idempotent", "leverage" (as in
  financial/technical leverage), "robust" (with a concrete meaning) — fine when
  the word is exact, not decorative.

## Documentation slop (DO flag these)

- **Marketing creep.** Sales language leaking into reference material:
  "powerful", "blazingly fast", "seamless", "effortless", "simply", "world-class",
  "game-changing". Docs describe; they don't sell.
- **Confidence words that hide difficulty.** "simply", "just", "easily",
  "obviously", "of course", "trivial". They shame the reader when the step turns
  out to be hard, and add nothing. Cut them.
  - *Before:* "Simply configure the webhook and you're done."
  - *After:* "Configure the webhook (steps below)."
- **Vague instructions.** "Configure the settings appropriately," "set up your
  environment as needed." Replace with the exact command, file, key, or value.
- **Filler and throat-clearing.** Same as the general rubric: "It's important to
  note that…", "In this section, we will…". Get to the instruction.
- **Unexplained jargon and undefined acronyms.** First use should define or link.
- **Missing concretes.** No example, no code snippet, no expected output, no
  version. A doc with zero copy-pasteable specifics is the technical form of
  "content substance = empty."
- **Passive, agentless steps.** "The file should be edited." Who edits it? Use
  imperative: "Edit `config.yaml`."
- **Stale hedging.** "This may or may not work depending on your setup" with no
  guidance on which setup. Tell the reader how to know.
- **Long, overloaded sentences.** Multi-clause sentences cramming several ideas.
  Split them; aim for ~15–20 words and one idea each.
- **Ambiguous pronouns.** "It returns this, which you pass to that." Name the
  things — readers shouldn't have to guess what "it"/"this" points to.
- **Non-descriptive link text.** "Click here", "this link", "see this." Link text
  should say where it goes when read out of context.

## The antidote, mapped to docs

The four qualities still apply, just translated:

- **Specificity** → exact commands, file paths, parameter names, version numbers,
  and real values. If the reader can copy-paste it, that's the win.
- **Lived experience** → replaced by **accuracy and completeness**: correct
  steps, real expected output, the gotchas that actually bite people. (Still
  never fabricate — if you don't know the real command or output, say so and ask
  the author.)
- **Cited sources** → links to the API reference, the relevant config docs, the
  spec, or the source file.
- **Information gain** → after reading, the reader can complete the task. The
  test: could someone follow this and succeed without guessing?

## Principles of good docs — the Three Cs

Score and rewrite toward these. They come from established technical-writing
practice (e.g. MDN's guidance).

**Clarity**
- One idea per sentence; one main idea per paragraph, each sentence connecting to
  the last.
- Use simple words and plain language — assume some readers are non-native
  English speakers.
- Introduce and define every new term before building on it.
- Specify pronouns. Replace "it", "this", "these" with the actual noun when more
  than one thing could be meant — ambiguity in docs causes real errors.
- Use active voice when it clarifies *who does the action* (does the user call the
  function, or does an event trigger it?). Passive is fine only when the actor is
  irrelevant.

**Conciseness**
- Keep sentences short — roughly 15–20 words is a good target. Short sentences
  raise clarity automatically.
- Cut redundancy (same idea twice) and repetitiveness (same word/phrase overused
  as filler) — but never at the cost of consistent *terminology*.

**Consistency**
- Same term for the same concept, everywhere. Same casing, same formatting.

**Structure**
- Open with a short intro: what the feature is and why the reader should care.
- Progress from foundational → advanced; establish the *what* before the *why*
  and *how*; follow concepts with how-to examples.
- Lists: numbered for ordered steps, bulleted otherwise. Always lead a list with
  a sentence of context.
- Links: make link text descriptive and clear out of context — "see the
  [config reference]", not "click [here]".

## What good docs look like (positive standard)

Aim for the qualities that strong docs share. Two good models: the Aave protocol
docs and the Claude/Anthropic platform docs.

- **Progressive complexity.** An overview/"101" before internals, so newcomers
  and experts both find their level.
- **Task-oriented entry points.** Lead with what the reader wants to *do* —
  "Get started", "Build with X", "Quickstart" — not a feature catalogue. Action
  verbs over noun piles.
- **Concrete examples early.** A quickstart with a real, runnable snippet (with
  the actual install command and expected output) before abstract theory.
- **Separate concept from how-to.** Conceptual explanation and step-by-step
  guides are distinct, so readers can learn or just execute.
- **Precise, consistent terminology.** Define the core concept once, plainly, and
  reuse the exact terms — e.g. "a decentralised non-custodial liquidity protocol
  where users participate as suppliers or borrowers."
- **Explain the mechanism without dumbing it down.** "Suppliers provide liquidity
  while earning interest; borrowers access liquidity by providing collateral that
  exceeds the borrowed amount." Specific, accurate, readable.
- **Exact, copy-pasteable specifics.** Real model/version IDs, parameter names,
  and values — not "the appropriate model" or "your settings."
- **Meet readers where they are.** Where relevant, cover the different languages
  or pathways a reader might use (e.g. React, TypeScript, Solidity, cURL).
- **Orientation cues / reading paths.** Tell readers where to start and when to
  come back, instead of dumping everything at once — e.g. "If you're new, start
  with model capabilities and tools. Return to the other sections when you're
  ready to optimize cost, latency, or scale."
- **Verb-led, one-line descriptions.** In overviews and feature lists, each entry
  says what it does in a single scannable line, ideally with a concrete number —
  e.g. "Batch API calls cost 50% less than standard API calls." or "Up to 1M
  tokens for processing large documents." Not "a powerful batching solution."
- **Define your status/jargon terms.** Don't assume "Beta", "GA", "deprecated",
  or domain acronyms are understood — define them once (a small table works well).

When rewriting, move the text toward this standard — but only with the author's
real facts. Don't invent example code, parameters, or outputs.

## Scoring adjustments

- **Vocabulary diversity (dim. 4):** largely waive for consistent technical
  terminology. Only flag genuinely lazy repetition (the same filler sentence
  opener every step), not repeated domain nouns.
- **Sentence structure (dim. 3):** don't penalize parallel steps or lists.
  Still flag marketing cadence, rule-of-three hype, and "it's not just X, it's Y".
- **Content substance (dim. 5):** weight this *heavily* — for docs, missing
  commands/examples/outputs is the cardinal sin.
- Keep slop vocabulary (dim. 1) and cliché phrases (dim. 2), and add the
  marketing-creep and confidence-word checks above.

## Rewrite priorities for docs

1. Make every instruction concrete and copy-pasteable.
2. Cut marketing and confidence words.
3. Keep terminology consistent — don't "improve" it with synonyms.
4. Use imperative voice for steps.
5. Preserve all technical accuracy; never alter a command, value, or API name to
   make prose flow. When something looks wrong, flag it — don't silently fix it.
