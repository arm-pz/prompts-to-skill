# prompts-to-skill

An agent skill that turns a list of your own prompts into a finished, tested skill. You paste the
prompts you keep reusing; it interviews you on intent, checks that no installed skill already covers
them, drafts with `skill-creator`, writes trigger test cases, then hardens the draft with `tune-skill`
and hands it to `findable` for naming and listing.

It is a fixed pipeline with two confirmation points and two pass/fail gates, so the output is a skill
that actually fires on the phrasings you use — not a plausible-looking file.

Works with Qoder, Claude Code and other agents that load skills. Needs `skill-creator` and `tune-skill`
installed; it stops and says so if either is missing.

**Heads up before you install:** neither `skill-creator` nor `tune-skill` is published as an `arm-pz`
repo, so installing this one does not give you those two. They have to come from wherever your agent
ships its own skill-authoring tools. Step 1 of this pipeline cannot run on a machine that lacks them.

## Install

```
npx skills add arm-pz/prompts-to-skill --skill prompts-to-skill
```

Or copy the `prompts-to-skill/` folder into `~/.qoder/skills/` (Qoder) or `~/.claude/skills/` (Claude
Code), then start a new session.

## Ask it things like

- "Here are twelve prompts I keep pasting — make a skill out of them."
- "Turn these instructions into a reusable skill."
- "I have a batch of example requests, package them as one skill."

## Sibling

`arm-pz/prompts-to-skill-release` does the next step: packaging, versioning, README and install
checklist once the skill is drafted and tuned. Drafting and tuning belong to this skill;
edge-case polish of an existing skill belongs to `tune-skill`.

## Layout

```
prompts-to-skill/
├── SKILL.md
└── references/
    ├── pipeline.md     # detail for each of the four steps
    └── gates.md        # pass/fail rules for Gate A and Gate B
```

## Status

Built from the author's own prompt list on 2026-10-19. `SKILL.md` passes `tune-skill`'s validator with
no FAIL. The skill's own trigger test cases have not been run in a live session — running them is
step 1 of the sibling release skill, not something already claimed here.

## License

MIT. See `LICENSE`.
