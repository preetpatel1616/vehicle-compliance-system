# Vendored skills: mattpocock/skills

Matt Pocock's agent skills, vendored into this repo so they load automatically in
every Claude Code session here — CLI, web, and for anyone else who clones the repo.

- **Source:** https://github.com/mattpocock/skills
- **Plugin version:** 1.2.3
- **Upstream commit:** `8b78b531ab965735c5dc74f6f7a219e1e37326df` (2026-08-13)
- **License:** MIT — see `LICENSE-mattpocock-skills`

The 25 skills here are exactly the set listed in the upstream `.claude-plugin/plugin.json`,
flattened out of their `engineering/` and `productivity/` category folders. Upstream's
`in-progress/`, `misc/`, and `deprecated/` skills are intentionally not included.

## First-time setup

Run once in this repo to configure issue tracker, triage labels, and doc layout:

```
/setup-matt-pocock-skills
```

## Skills

**Engineering — you invoke:** `ask-matt`, `grill-with-docs`, `triage`,
`improve-codebase-architecture`, `setup-matt-pocock-skills`, `to-spec`, `to-tickets`,
`implement`, `wayfinder`

**Engineering — Claude invokes:** `prototype`, `diagnosing-bugs`, `research`, `tdd`,
`domain-modeling`, `codebase-design`, `code-review`, `resolving-merge-conflicts`, `wizard`

**Productivity — you invoke:** `grill-me`, `handoff`, `teach`, `to-questionnaire`, `wait-what`

**Productivity — Claude invokes:** `grilling`, `writing-for-agents`

## Note on `code-review`

Claude Code ships its own built-in `code-review` skill. The one here is Matt's
dual-axis version (standards + spec compliance) and shares the name, so `/code-review`
may be ambiguous depending on your setup. Rename this directory (and the `name:` field
in its `SKILL.md`) if you want them clearly separated.

## Updating

Re-clone upstream and re-copy the skills named in its `plugin.json`:

```sh
git clone --depth 1 https://github.com/mattpocock/skills.git /tmp/mp-skills
node -e "console.log(require('/tmp/mp-skills/.claude-plugin/plugin.json').skills.join('\n'))" \
  | while read -r p; do
      rm -rf ".claude/skills/$(basename "$p")"
      cp -r "/tmp/mp-skills/${p#./}" ".claude/skills/$(basename "$p")"
    done
```

Then update the version and commit recorded above.
