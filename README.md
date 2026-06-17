# antislop

A Claude skill that first **scores** text for "AI slop" — the way
[slopdetector.org](https://slopdetector.org) does — and then, if you want,
**rewrites** it to read like a real person wrote it, without changing what it
says or flattening your voice.

> **Status:** early but working. Scoring + rewrite flow and the rules are in
> place; we're still expanding the catalogue. See
> [`skills/antislop/references/ai-tells.md`](skills/antislop/references/ai-tells.md).

## What it does

Two steps, in order:

1. **Detect & score** — rates the text **0–100** (higher = more slop) across five
   dimensions: slop vocabulary, cliché phrases, sentence structure, vocabulary
   diversity, and content substance. It shows the exact words and phrases that
   triggered each flag, and a verdict (*Not Slop* / *Some Slop* / *Generic Slop*).
2. **Ask, then rewrite** — it asks whether you want it de-slopped. If yes, it
   makes **surgical edits** by default (your voice preserved), returns the
   rewritten text, a short note on what changed, and the new score (e.g. 68 → 12).

It triggers on requests like:

- "Does this sound like AI? Score it."
- "Rate this copy for slop."
- "Make this sound less like AI / more human / more natural."
- "De-slop this landing page copy."
- "Tighten this email so it doesn't read so robotic."

## Repository layout

```
antislop/
├── README.md                     ← you are here
└── skills/
    └── antislop/                 ← the installable skill folder
        ├── SKILL.md              ← skill definition (frontmatter + instructions)
        ├── references/
        │   ├── ai-tells.md       ← catalogue of AI patterns to fix
        │   └── rewrite-guide.md  ← the antidote: how to fix slop
        ├── scripts/              ← helper scripts (added as needed)
        └── evals/                ← test cases for iterating on the skill
```

The skill follows the standard `skills/<name>/SKILL.md` layout so the
[`npx skills`](https://github.com/vercel-labs/skills) CLI can auto-install it.

## Installation

Pick the method that matches how you use Claude.

### Option A — `npx skills` (recommended, auto-install)

The [`npx skills`](https://github.com/vercel-labs/skills) CLI installs straight
from this GitHub repo — no clone, no manual copying:

```bash
# install into Claude Code (personal/global)
npx skills add ulyanaxyz/antislop -a claude-code -g

# or into the current project only (drops it in ./.claude/skills/)
npx skills add ulyanaxyz/antislop -a claude-code

# preview what's in the repo first
npx skills add ulyanaxyz/antislop --list
```

It also targets other agents (`cursor`, `codex`, `continue`, …) via `-a`.
Restart Claude Code, then ask it to "score this for slop."

### Option B — Claude Code, manual clone

```bash
git clone https://github.com/ulyanaxyz/antislop.git
cd antislop

# symlink so `git pull` keeps it up to date…
ln -s "$(pwd)/skills/antislop" ~/.claude/skills/antislop
# …or copy it in
cp -r skills/antislop ~/.claude/skills/antislop
```

For a single project instead, copy into that project's `.claude/skills/`:

```bash
mkdir -p .claude/skills
cp -r /path/to/antislop/skills/antislop .claude/skills/antislop
```

### Option C — Claude.ai (upload a packaged skill)

1. Package the skill into a `.skill` file (a zip of the skill folder).
2. In Claude.ai, go to **Settings → Capabilities → Skills** and upload it.

```bash
cd skills          # the skill folder's parent
zip -r antislop.skill antislop
```

## Usage

Once installed, just paste text and ask:

```
Score this for slop:

"In today's fast-paced world, it's important to note that our cutting-edge
platform doesn't just streamline your workflow — it revolutionizes it."
```

Claude returns a slop score with the specific flags, then asks if you want it
de-slopped. Say yes and you get a clean rewrite, a note on what changed, and the
new score.

To skip the ask, tell it up front: "score this and fix it." To control intensity:
"light pass, keep my voice" or "full rewrite, make it punchy."

## Updating

If you symlinked (Option A), `git pull` is enough. If you copied, re-copy the
folder after pulling.

## Contributing / developing the skill

The editing rules live in [`skills/antislop/references/ai-tells.md`](skills/antislop/references/ai-tells.md)
and the skill instructions in [`skills/antislop/SKILL.md`](skills/antislop/SKILL.md). Test
cases for iterating go in `skills/antislop/evals/`. PRs that add good before/after
examples or new tells are welcome.

## License

See [LICENSE](LICENSE).
