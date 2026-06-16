---
name: antislop
description: >-
  Edits text, copy, and content to read more naturally and less like it was
  written by AI. Strips out generic "AI tells" (filler transitions, hedging,
  inflated phrasing, em-dash overuse, "it's not just X, it's Y" constructions,
  empty conclusions) while preserving the author's meaning and voice. Use this
  whenever the user asks to make writing "sound less like AI," "sound more
  human," "more natural," "less robotic/generic/corporate," to "de-slop,"
  proofread, tighten, or punch up any text, email, blog post, landing page,
  caption, or document — even if they don't say the word "AI."
---

# Antislop

Make written text read like a real person wrote it. Remove the patterns that
make writing feel machine-generated, without flattening the author's voice or
changing what they're trying to say.

> **Status:** starter draft. The detailed rules, the AI-tell catalogue, and the
> editing workflow are being built out. See `references/ai-tells.md` for the
> running list of patterns to catch.

## What this skill does

Given a piece of text, return a cleaner version that a discerning reader
wouldn't peg as AI-written. The goal is not to follow a rigid checklist but to
develop judgment about *why* certain phrasings feel artificial and fix them.

## Default behavior

Unless the user says otherwise:

1. **Make surgical edits.** Preserve the author's voice, structure, and intent.
   Change what's actually off; leave the rest alone. The output should still
   sound like the same person — just sharper.
2. **Return the rewritten text**, followed by a short, plain-language note on
   the main things you changed and why.
3. **Don't invent facts.** Never add claims, numbers, or details that weren't in
   the original to make it "flow." Flag anything you're unsure about instead.

## Workflow (to be expanded)

1. Read the text once for meaning and voice. Identify what the author is
   actually trying to say and who they're saying it to.
2. Pass through for AI tells using `references/ai-tells.md` as a guide.
3. Rewrite surgically.
4. Re-read the result cold: does it sound like a person? Is the meaning intact?
5. Return the result + change notes.

## References

- `references/ai-tells.md` — the catalogue of patterns that make text read as
  AI-generated, with before/after examples. Read this before editing.
