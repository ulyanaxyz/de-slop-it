# antislop

A Claude skill that edits text, copy, and content so it reads like a real person
wrote it — not like AI. It strips the generic "tells" (filler transitions,
hedging, inflated corporate words, em-dash overuse, the "it's not just X, it's Y"
move, empty conclusions) while keeping the author's meaning and voice intact.

> **Status:** early. The scaffold and install flow are in place; the editing
> rules are being built out. See [`antislop/references/ai-tells.md`](antislop/references/ai-tells.md).

## What it does

Paste in any text and ask Claude to make it sound more human. By default the
skill makes **surgical edits** (preserving your voice), returns the **rewritten
text**, and adds a **short note on what it changed and why**.

It triggers on requests like:

- "Make this sound less like AI / more human / more natural."
- "De-slop this landing page copy."
- "Tighten this email so it doesn't read so robotic."
- "Punch up this blog intro."

## Repository layout

```
antislop/
├── README.md                     ← you are here
└── antislop/                     ← the installable skill folder
    ├── SKILL.md                  ← skill definition (frontmatter + instructions)
    ├── references/
    │   └── ai-tells.md           ← catalogue of AI patterns to fix
    ├── scripts/                  ← helper scripts (added as needed)
    └── evals/                    ← test cases for iterating on the skill
```

The inner `antislop/` folder is the unit you install.

## Installation

The skill works anywhere Claude reads skills. Pick the method that matches how
you use Claude.

### Option A — Claude Code, personal (available in every project)

Copy or symlink the skill folder into your personal skills directory:

```bash
# clone this repo somewhere
git clone https://github.com/<your-username>/antislop.git
cd antislop

# copy it in
cp -r antislop ~/.claude/skills/antislop

# …or symlink so `git pull` keeps it up to date
ln -s "$(pwd)/antislop" ~/.claude/skills/antislop
```

Restart Claude Code (or start a new session). Confirm it loaded by asking Claude
to "make some text sound less like AI."

### Option B — Claude Code, single project only

Drop it into the project's `.claude/skills/` directory so only that repo sees it:

```bash
mkdir -p .claude/skills
cp -r /path/to/antislop/antislop .claude/skills/antislop
```

Commit `.claude/skills/antislop/` if you want your whole team to get it.

### Option C — Claude.ai (upload a packaged skill)

1. Package the skill into a `.skill` file (a zip of the skill folder).
2. In Claude.ai, go to **Settings → Capabilities → Skills** and upload it.

To package it manually:

```bash
cd antislop          # the inner skill folder's parent
zip -r antislop.skill antislop
```

## Usage

Once installed, just ask in plain language:

```
Make this sound less like AI:

"In today's fast-paced world, it's important to note that our cutting-edge
platform doesn't just streamline your workflow — it revolutionizes it."
```

Claude will return a cleaned-up version plus a short note on what changed.

To control intensity, say so: "light pass, keep my voice" or "full rewrite, make
it punchy."

## Updating

If you symlinked (Option A), `git pull` is enough. If you copied, re-copy the
folder after pulling.

## Contributing / developing the skill

The editing rules live in [`antislop/references/ai-tells.md`](antislop/references/ai-tells.md)
and the skill instructions in [`antislop/SKILL.md`](antislop/SKILL.md). Test
cases for iterating go in `antislop/evals/`. PRs that add good before/after
examples or new tells are welcome.

## License

See [LICENSE](LICENSE).
