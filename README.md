# antislop

A Claude skill that scores text for "AI slop," then rewrites it to read like a
person wrote it — without changing your meaning or flattening your voice.

> **Status:** early but working. The scoring and rewrite flow run end to end; the
> pattern catalogue is still growing. See
> [`skills/antislop/references/ai-tells.md`](skills/antislop/references/ai-tells.md).

## Quick start

Install it into Claude Code with the [`skills`](https://www.npmjs.com/package/skills)
CLI:

```bash
npx skills add ulyanaxyz/antislop
```

Restart Claude Code, paste some text, and ask it to "score this for slop." That's
it. See [Installation](#installation) for project vs. global scope, other agents,
and manual setup.

## What it does

Two steps, in order:

1. **Score it.** Rates the text 0–100 (higher means more slop) across five things:
   slop vocabulary, cliché phrases, sentence structure, vocabulary diversity, and
   content substance. It quotes the exact words that triggered each flag and gives
   a verdict — *Not Slop*, *Some Slop*, or *Heavy Slop* — naming the slop type
   where one fits (Generic, Pseudo-Insight, Fake Authority, Wikipedia Rehash,
   Wellness).
2. **Then ask, then rewrite.** It asks before touching your text. Say yes and it
   makes surgical edits that keep your voice, hands back the rewrite with a note
   on what changed, and shows the new score (say, 68 → 12).

It won't invent facts to pad the score. When a piece has no real substance, it
tells you where a number, source, or example is missing instead of making one up.

Ask for it however feels natural:

- "Does this sound like AI? Score it."
- "Rate this copy for slop."
- "Make this sound more human."
- "De-slop this landing page."
- "Tighten this email so it reads less robotic."
- "Clean up this README so it doesn't sound AI-written."

It's **genre-aware**: for technical documentation (READMEs, API docs, tutorials,
runbooks) it switches to a doc-tuned rubric that rewards concrete, copy-pasteable
instructions and flags marketing creep ("blazingly fast") and hand-wavy filler
("simply", "just") — without penalizing the consistent terminology and parallel
structure that good docs need.

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

The skill uses the standard `skills/<name>/SKILL.md` layout so the
[`skills`](https://www.npmjs.com/package/skills) CLI discovers and installs it
directly from GitHub.

## Installation

The main path is the [`skills`](https://www.npmjs.com/package/skills) CLI — it
installs straight from this repo, no clone or copying. Manual options follow for
anyone who'd rather not use it.

### With the `skills` CLI (recommended)

```bash
# this project only (drops it in ./.claude/skills/)
npx skills add ulyanaxyz/antislop

# all your projects (installs to ~/.claude/skills/)
npx skills add ulyanaxyz/antislop -g

# see what's in the repo before installing
npx skills add ulyanaxyz/antislop --list
```

By default it targets Claude Code. Add `-a` to target other agents the CLI
supports (Cursor, Codex, Cline, Continue, Windsurf, and more), e.g.
`-a cursor`. Other handy commands:

```bash
npx skills list                 # what's installed
npx skills update antislop      # pull the latest version
npx skills remove antislop      # uninstall
```

Restart Claude Code after installing, then ask it to "score this for slop."

### Manual — clone the repo

```bash
git clone https://github.com/ulyanaxyz/antislop.git
cd antislop

# symlink so `git pull` keeps it current…
ln -s "$(pwd)/skills/antislop" ~/.claude/skills/antislop
# …or just copy it
cp -r skills/antislop ~/.claude/skills/antislop
```

For one project only, copy into that project's `.claude/skills/`:

```bash
mkdir -p .claude/skills
cp -r /path/to/antislop/skills/antislop .claude/skills/antislop
```

### Manual — Claude.ai

Zip the skill folder and upload it under **Settings → Capabilities → Skills**:

```bash
cd skills
zip -r antislop.skill antislop
```

## Usage

Paste your text and ask:

```
Score this for slop:

"In today's fast-paced world, it's important to note that our cutting-edge
platform doesn't just streamline your workflow — it revolutionizes it."
```

You get a score with the specific flags, then a prompt to de-slop it. Say yes and
you get the rewrite, a note on what changed, and the new score.

To skip the prompt, ask up front: "score this and fix it." To set the intensity:
"light pass, keep my voice" or "full rewrite, make it punchy."

## Updating

Installed with the CLI? Run `npx skills update antislop`. Symlinked? `git pull` in
the cloned repo. Copied the folder? Copy it again after pulling.

## Contributing

The rules live in
[`skills/antislop/references/ai-tells.md`](skills/antislop/references/ai-tells.md)
(detection) and
[`skills/antislop/references/rewrite-guide.md`](skills/antislop/references/rewrite-guide.md)
(the fix); the skill itself is in
[`skills/antislop/SKILL.md`](skills/antislop/SKILL.md). Test cases go in
`skills/antislop/evals/`. Pull requests with good before/after examples or new
tells are welcome.

## License

[MIT](LICENSE).
