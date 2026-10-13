# Install

Pick your agent. Design-forge is skill-based: copy `skills/*` into the agent's skill directory, plus the sibling skills it orchestrates.

## Prerequisites

Sibling skills (install next to design-forge in the same skills root):

| Skill | Source |
|-------|--------|
| `taste-skill` | anti-slop frontend framework |
| `awesome-design-md` | 74 brand DESIGN.md files |
| `web-design-guidelines` | Vercel UI best practices |
| `playwright` | browser automation |
| `ponytail` | bundled in this repo |
| `ponytail-review` | bundled in this repo |

Node.js must be on PATH for Playwright verification.

## Windows PowerShell (MiMoCode example)

```powershell
git clone https://github.com/hulktm13/design-forge.git $env:TEMP\design-forge
$dst = "$env:USERPROFILE\.mimocode\skills"
Copy-Item "$env:TEMP\design-forge\skills\*" $dst -Recurse -Force
Remove-Item $env:TEMP\design-forge -Recurse -Force
```

Repeat with the right `$dst` for each agent you use.

## Agent paths

| Agent | Skills path |
|-------|-------------|
| MiMoCode | `~/.mimocode/skills/` |
| Claude Code | `~/.claude/skills/` |
| Codex | `~/.codex/skills/` |
| OpenCode | `~/.config/opencode/skill/` |
| Gemini / Antigravity | `~/.gemini/config/skills/` |
| Shared agents | `~/.agents/skills/` |

## Antigravity (ponytail plugin)

```bash
agy plugin install https://github.com/DietrichGebert/ponytail
```

This registers ponytail skills and converts its commands to slash skills.

## Verify

Start a new session and run:

```
/ponytail-help
```

or say:

```
Build me a simple landing page
```

You should see a **Design Read** line first, then the pipeline phases.

## Uninstall

Delete the `design-forge/` and `ponytail*/` folders from your skills directory.
