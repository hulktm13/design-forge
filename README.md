# Design Forge

End-to-end UI forge: brief in, verified UI out — and now with **ponytail** so the code stays lean.

One skill to rule the whole frontend pipeline:

| Phase | Source | What it does |
|-------|--------|--------------|
| **1. Read** | taste-skill | Infers design direction from the brief |
| **2. Style** | awesome-design-md | Loads brand-specific design tokens if applicable |
| **3. Build** | taste-skill + **ponytail** | Anti-slop design, lazy-senior-dev leanness |
| **4. Verify** | Playwright | Real browser, screenshots, 3 viewports |
| **5. Audit** | web-design-guidelines + **ponytail-review** | Vercel UI rules + lean/safety review |
| **6. Fix** | All sources | Fix and re-verify until clean |

## What's inside

```
skills/
  design-forge/      # The orchestrator pipeline
  ponytail/          # Lazy senior dev: smallest complete change
  ponytail-review/   # Diff review: bugs, safety, what to cut
  ponytail-audit/    # Whole-repo ranked audit
  ponytail-debt/     # shortcut: comment ledger
  ponytail-gain/     # Measured savings scoreboard
  ponytail-help/     # Quick reference
```

Sibling skills you install separately (referenced by design-forge):

- [taste-skill](https://github.com/) — anti-slop frontend framework
- `awesome-design-md` — 74 brand DESIGN.md files
- `web-design-guidelines` — Vercel UI best practices
- `playwright` — browser automation and verification

## Why ponytail in a design forge?

Design quality is non-negotiable. Code volume is.

Ponytail forces the build ladder:

1. Does it need to exist?
2. Already in this codebase?
3. Standard library / platform feature?
4. Installed dependency?
5. One clear line?
6. Only then: minimum code that works + one small test if it has real logic.

It never cuts validation, error handling, security, accessibility, or hardware calibration. It only removes unnecessary abstraction, dependency weight, and "for later" code.

## Install

Copy the `skills/` folders into your agent's skill directory:

| Agent | Path |
|-------|------|
| MiMoCode | `~/.mimocode/skills/` |
| Claude Code | `~/.claude/skills/` |
| Codex | `~/.codex/skills/` |
| OpenCode | `~/.config/opencode/skill/` |
| Gemini / Antigravity | `~/.gemini/config/skills/` |
| Shared agents | `~/.agents/skills/` |

Then say: **"design-forge"** or *"Build me a landing page"*.

Ponytail can also be used alone: `/ponytail`, `/ponytail-review`, `/ponytail-audit`.

## License

MIT
