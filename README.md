# Design Forge

**Brief in → verified UI out.** One skill pipeline for web UI: design direction, brand tokens, lean build, live browser proof, quality audit. No “try again” loops. No bloat.

```
 ┌─────────────────────────────────────────────────────────────┐
 │                     DESIGN FORGE v2                         │
 │         taste-skill · awesome-design-md · ponytail           │
 │              Playwright · web-design-guidelines              │
 └─────────────────────────────────────────────────────────────┘
          │
          ▼
   PHASE 0  READ      brief → Design Read (page kind, vibe, audience)
          │
          ▼
   PHASE 1  STYLE     brand DESIGN.md  ·  or aesthetic direction
          │
          ▼
   PHASE 2  DIALS     variance · motion · density   (default 8/6/4)
          │
          ▼
   PHASE 3  BUILD     anti-slop UI  +  ponytail lean ladder
          │
          ▼
   PHASE 4  VERIFY    Playwright → screenshots @ 375 / 768 / 1440
          │
          ▼
   PHASE 5  AUDIT     Vercel guidelines  +  ponytail-review
          │
          ▼
   PHASE 6  FIX       fix → re-verify → repeat until clean
```

## Why this exists

| Problem | How design-forge solves it |
|---------|----------------------------|
| AI UIs look generic (purple gradients, Inter, 3 cards) | taste-skill anti-default rules |
| Brand work is guesswork | 74 `awesome-design-md` brand token packs |
| Code comes out bloated | **ponytail** ladder: smallest complete change |
| “It looks fine” on your screen only | Playwright real-browser screenshots at 3 viewports |
| Accessibility is an afterthought | WCAG AA checklist + focus/keyboard audit |
| Review is vibes | `ponytail-review` findings: what breaks, how to fix, what happens if you skip |

## What's in the box

```
skills/
  design-forge/       ← the orchestrator (start here)
  ponytail/           ← lazy senior dev / YAGNI lean-build ladder
  ponytail-review/    ← diff review: bugs, safety, what to cut
  ponytail-audit/     ← whole-repo ranked audit
  ponytail-debt/      ← shortcut: comment ledger
  ponytail-gain/      ← measured savings scoreboard
  ponytail-help/      ← quick reference card
```

Install these as siblings in the same skills root (referenced, not bundled):

| Skill | Role |
|-------|------|
| `taste-skill` | Anti-slop frontend framework |
| `awesome-design-md` | 74 brand DESIGN.md files |
| `web-design-guidelines` | Vercel UI best practices |
| `playwright` | Browser automation & verification |

## Install

### One-liner (any agent that reads skills)

```bash
# clone and copy skills/ into your agent's skill directory
git clone https://github.com/hulktm13/design-forge.git
# then copy skills/* into the path for your agent (table below)
```

### Per agent

| Agent | Skills path |
|-------|-------------|
| **MiMoCode** | `~/.mimocode/skills/` |
| **Claude Code** | `~/.claude/skills/` |
| **Codex** | `~/.codex/skills/` |
| **OpenCode** | `~/.config/opencode/skill/` |
| **Gemini / Antigravity** | `~/.gemini/config/skills/` |
| **Shared agents** | `~/.agents/skills/` |

Windows example (PowerShell):

```powershell
git clone https://github.com/hulktm13/design-forge.git $env:TEMP\design-forge
$dst = "$env:USERPROFILE\.mimocode\skills"   # change per agent
Copy-Item "$env:TEMP\design-forge\skills\*" $dst -Recurse -Force
```

### Antigravity plugin (ponytail)

```bash
agy plugin install https://github.com/DietrichGebert/ponytail
```

## Quick start

Open a new agent session and say any of:

```
Build me a landing page for a fintech startup
Make this look like Stripe
Create a brutalist portfolio site
This page looks generic, make it premium
```

The agent will:
1. Print a **Design Read** one-liner (page kind, vibe, audience)
2. Load brand tokens or pick an aesthetic
3. Set the three dials
4. Build lean (ponytail ladder)
5. Open a real browser and screenshot 3 viewports
6. Audit guidelines + accessibility + leanness
7. Fix until clean

### Example session

> **You:** Build a pricing page that looks like Linear.

```
Reading this as: pricing page for developers, with premium-minimal
language, leaning toward Linear design system.

Style : awesome-design-md/linear.app (loaded)
Dials : variance 7 · motion 6 · density 4
Build : 12 files, 380 lines (ponytail: reused existing Card + Badge,
        skipped custom toggle — platform <button> + CSS)
Verify: 375 / 768 / 1440 screenshots — OK
Audit : 2 findings (contrast on muted text, missing focus ring on tab)
Fix   : both fixed, re-verified

Done. Skipped: no annual/monthly animation (not asked).
Risk  : none. Pricing values are hardcoded mock data.
```

## Ponytail layer

Design quality is non-negotiable. Code volume is.

Before every file, the ladder:

1. Does it need to exist?
2. Already in this codebase (helper, component, pattern)?
3. Standard library or platform feature? (`<input type="date">` exists.)
4. An installed dependency?
5. Can it be one clear line?
6. Only then: the minimum code that works + one small test if it has real logic.

**Never cut:** trust-boundary validation · data-loss error handling · security · accessibility · real hardware calibration.

## Commands (ponytail)

| Command | What it does |
|---------|--------------|
| `/ponytail lite\|full\|ultra\|off` | Set intensity |
| `/ponytail-review` | Review current diff like the on-call senior |
| `/ponytail-audit` | Same checks on the whole repo, ranked |
| `/ponytail-debt` | Harvest `shortcut:` comments into a ledger |
| `/ponytail-gain` | Measured savings scoreboard |
| `/ponytail-help` | Quick reference |

## Requirements

- An agent with skill support (MiMoCode, Claude Code, Codex, OpenCode, Gemini, Antigravity, …)
- Node.js on PATH (for Playwright verification)
- The sibling skills listed above

## License

MIT — the shortest license that works.
