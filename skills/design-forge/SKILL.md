---
name: design-forge
description: >
  End-to-end UI forge: orchestrates taste-skill (anti-slop design), awesome-design-md (brand design systems),
  ponytail (lazy senior dev / YAGNI lean build), web-design-guidelines (Vercel best practices), and Playwright
  (live browser verification) into a single pipeline. Use when building ANY web UI, landing page, web app,
  dashboard, or frontend project. The agent handles design direction, lean implementation, browser testing,
  and quality review automatically — no back-and-forth fixes, no bloat.
metadata:
  author: design-forge
  version: "2.0.0"
---

# Design Forge

One skill to rule them all. Brief in, verified UI out. No manual fixes, no "try again" loops, no bloat.

This skill orchestrates five sub-systems into a single automated pipeline:

| Phase | Source | What it does |
|-------|--------|--------------|
| **1. Read** | taste-skill | Infers design direction from the brief |
| **2. Style** | awesome-design-md | Loads brand-specific design tokens if applicable |
| **3. Build** | taste-skill + **ponytail** | Implements with anti-slop discipline AND lazy-senior-dev leanness |
| **4. Verify** | Playwright CLI | Opens in real browser, screenshots, checks rendering |
| **5. Audit** | web-design-guidelines + **ponytail-review** | Vercel UI best practices + lean/safety review |
| **6. Fix** | All sources | Fixes issues and re-verifies until clean |

### Ponytail layer (the lazy senior dev)

Ponytail keeps the build honest: the smallest change that fully solves the task.

- Ladder before writing: need it? already in repo? stdlib/platform? installed dep? one line? only then minimal code
- Reuse the house `Input`/`Button`/layout before inventing a new one
- Never cut: trust-boundary validation, error handling, security, accessibility, real hardware calibration
- Non-trivial logic (branch/loop/parser/money/security) leaves one small test
- End the reply with what was skipped or unchecked and any real risk

Design quality is non-negotiable. Code volume is. Ponytail never justifies generic AI slop — that is taste-skill's job. Ponytail only removes unnecessary code, abstraction, and dependency weight.

---

## WHEN TO USE

Trigger on ANY of:
- "Build me a landing page / web app / dashboard / portfolio / UI"
- "Make this look like [brand/website]"
- "Design and build X"
- "Create a frontend for X"
- "I want a [style] website"
- Any request that produces visible web UI

Do NOT trigger for:
- Backend-only work with no UI
- CLI tools or scripts
- Database schemas
- API-only endpoints

---

## PHASE 0: BRIEF INTERPRETATION

Before touching any code, read the user's request and output a **Design Read** — one line that states your interpretation:

```
Reading this as: [page kind] for [audience], with [vibe] language, leaning toward [design system/aesthetic].
```

### Signals to extract:
1. **Page kind** — landing, portfolio, dashboard, app, editorial, e-commerce, blog, admin
2. **Vibe words** — minimalist, premium, playful, brutalist, editorial, dark tech, Apple-y, Linear-style
3. **Brand references** — any brand names, URLs, or screenshots mentioned
4. **Audience** — developers, consumers, enterprise buyers, designers, general public
5. **Constraints** — accessibility-first, public-sector, regulated industry

### If ambiguous:
Ask ONE clarifying question. Never more. If you can confidently infer, proceed without asking.

### Anti-Default Rule:
NEVER default to: AI-purple gradients, centered hero over dark mesh, three equal feature cards, generic glassmorphism, Inter + slate-900. These are LLM defaults — reach past them deliberately.

---

## PHASE 1: DESIGN SYSTEM SELECTION

Based on the Design Read, decide: **brand-specific** or **aesthetic-driven**.

### 1.A Brand-Specific (match an existing brand)

If the user mentions a brand or wants to match an existing product's look:

1. Check if the brand exists in the awesome-design-md collection:
   ```
   skills/awesome-design-md/<brand>/DESIGN.md
   ```
2. If found, READ the full DESIGN.md file
3. Extract and apply: colors, typography, spacing, component styles, layout rules
4. These tokens OVERRIDE taste-skill defaults for the duration of the build

**Available brands (74):** Apple, Stripe, Linear, Vercel, Figma, Notion, Shopify, Spotify, Tesla, Nike, Airbnb, Supabase, Cursor, Vercel, Raycast, Framer, Webflow, MongoDB, Sentry, PostHog, Intercom, Cal, Resend, Binance, Coinbase, Kraken, Revolut, Wise, Mastercard, BMW, Ferrari, Lamborghini, Bugatti, Tesla, SpaceX, Uber, HP, IBM, NVIDIA, Pinterest, PlayStation, Meta, Zapier, Miro, and more.

Browse `skills/awesome-design-md/` for the full list.

### 1.B Aesthetic-Driven (no specific brand)

Use taste-skill's framework:

| Vibe | Design Direction |
|------|-----------------|
| "minimalist / clean / calm / editorial" | Tailwind + Geist font, restrained motion, tight spacing |
| "premium consumer / Apple-y / luxury" | SF Pro / custom font, cinematic imagery, generous whitespace |
| "playful / wild / Dribbble / agency" | Bold colors, kinetic type, high motion, asymmetric layouts |
| "brutalist / raw / hacker" | Monospace, sharp borders, no rounded corners, high contrast |
| "dark tech / terminal" | Dark background, neon accents, mono font, code-first |
| "editorial / magazine" | Serif type, asymmetric grid, generous whitespace, image-heavy |
| "trust-first / public-sector" | Low variance, high accessibility, conservative colors |

### 1.C Design System Package Selection

| If the brief reads as... | Use |
|--------------------------|-----|
| Microsoft / enterprise SaaS | `@fluentui/react-components` |
| Google / Material flavored | `@material/web` + Material 3 tokens |
| IBM / enterprise analytics | `@carbon/react` |
| Shopify app | Polaris |
| GitHub / devtool | `@primer/css` or `@primer/react-brand` |
| Public-sector UK | `govuk-frontend` |
| US public-sector | `uswds` |
| Fast MVP / agency | Bootstrap 5.3 |
| Modern React foundation | `@radix-ui/themes` or shadcn/ui |
| Modern SaaS / indie | Tailwind v4 (default) |

**One system per project.** Never mix design systems.

---

## PHASE 2: THREE DIALS CONFIGURATION

Set three dials based on the Design Read. These control ALL subsequent decisions.

| Dial | Range | What it controls |
|------|-------|-----------------|
| `DESIGN_VARIANCE` | 1-10 | Layout symmetry → chaos (1=perfect grid, 10=artsy chaos) |
| `MOTION_INTENSITY` | 1-10 | Animation level (1=static, 10=cinematic/physics) |
| `VISUAL_DENSITY` | 1-10 | Content density (1=airy gallery, 10=data cockpit) |

### Default: 8 / 6 / 4

### Presets:
| Use case | VAR | MOT | DEN |
|----------|-----|-----|-----|
| SaaS Landing | 7 | 6 | 4 |
| Agency/Creative | 9 | 8 | 3 |
| Premium Consumer | 7 | 6 | 3 |
| Designer Portfolio | 8 | 7 | 3 |
| Developer Portfolio | 6 | 5 | 4 |
| Editorial/Blog | 6 | 4 | 3 |
| Dashboard/App | 4 | 3 | 7 |
| Public-sector | 3 | 2 | 5 |

---

## PHASE 3: IMPLEMENTATION

Build lean. Ponytail ladder applies to every file you create or touch:

1. Does it need to exist? Skip features nobody asked for.
2. Already in this codebase (helper, component, pattern)? Use it.
3. Standard library or platform feature (e.g. `<input type="date">`)? Use it.
4. An installed dependency? Use it. Never add a dep for a few lines.
5. Can it be one clear line? One line.
6. Otherwise: the minimum code that works, with one small test if it has real logic.

No wrapper, no "for later" abstraction, no config for one value. Deletion beats addition. Keep the structure the repo already has.

### 3.A Stack Defaults
- **Framework:** React or Next.js (Server Components by default)
- **Styling:** Tailwind v4 (default), or the design system chosen in Phase 1
- **Animation:** Motion (from `motion/react`), intensity gated by MOTION_INTENSITY dial
- **Fonts:** `next/font` or self-hosted `@font-face`. NEVER link Google Fonts via `<link>` in production
- **Icons:** `@phosphor-icons/react`, `@radix-ui/react-icons`, or `@tabler/icons-react`. One family per project. NEVER hand-roll SVG icons

### 3.B Layout Rules (gated by DESIGN_VARIANCE)
- **Variance 1-3:** Symmetric grid, centered content, predictable structure
- **Variance 4-6:** Slight asymmetry, mixed grid sizes, intentional white space breaks
- **Variance 7-8:** Asymmetric layouts, overlapping elements, bento grids
- **Variance 9-10:** Full creative chaos — diagonal cuts, kinetic type, overlapping sections

### 3.C Motion Rules (gated by MOTION_INTENSITY)
- **1-2:** Static, no animations. Maybe subtle hover states.
- **3-4:** Gentle fades, simple transitions, subtle scroll reveals
- **5-6:** Scroll-driven animations, staggered reveals, parallax hints
- **7-8:** Physics-based spring animations, magnetic hover effects, smooth scroll hijacking
- **9-10:** Cinematic sequences, 3D transforms, complex choreographed animations

### 3.D Component Discipline
- Every component must have proper hover, focus, active, and disabled states
- Buttons: minimum 44px touch target on mobile
- Cards: consistent padding, proper shadow/elevation hierarchy
- Forms: visible labels, proper error states, clear focus indicators
- Navigation: clear active state, accessible keyboard navigation

### 3.E Typography Hierarchy
Apply the selected brand's type scale OR use this default:
- Display: 48-64px, weight 700
- H1: 36-48px, weight 700
- H2: 28-36px, weight 600
- H3: 22-28px, weight 600
- Body: 16px, weight 400, line-height 1.5-1.6
- Small: 14px, weight 400
- Caption: 12px, weight 500, uppercase tracking

### 3.F Color System
If a brand DESIGN.md was loaded, use its exact tokens. Otherwise:
- Primary: One vibrant accent (not AI-purple by default)
- Neutral: Full gray scale from 50-950
- Semantic: success (green), warning (amber), error (red), info (blue)
- Surface: canvas, surface-1, surface-2, elevated
- All colors must pass WCAG AA contrast ratios

---

## PHASE 4: BROWSER VERIFICATION (Playwright)

After implementation, verify in a REAL browser. This catches issues that static analysis misses.

### 4.A Open and Screenshot

```bash
# Start dev server if not running
npm run dev &

# Open in browser
npx @playwright/cli open http://localhost:3000

# Take initial screenshot
npx @playwright/cli screenshot --full-page
```

### 4.B Visual Checks

Open the page and verify:
1. **Layout renders correctly** — no overflow, no broken grid, proper spacing
2. **Typography loads** — custom fonts render, no FOUT flash, correct hierarchy
3. **Colors match spec** — brand tokens applied correctly, contrast sufficient
4. **Images load** — no broken images, proper aspect ratios, alt text present
5. **Interactive states work** — hover effects, focus rings, button states
6. **Responsive behavior** — resize viewport to mobile (375px), tablet (768px), desktop (1440px)

### 4.C Screenshot at Multiple Viewports

```bash
# Desktop
npx @playwright/cli open http://localhost:3000
npx @playwright/cli screenshot --full-page

# Tablet
npx @playwright/cli open http://localhost:3000 --viewport-size="768,1024"
npx @playwright/cli screenshot --full-page

# Mobile
npx @playwright/cli open http://localhost:3000 --viewport-size="375,812"
npx @playwright/cli screenshot --full-page
```

### 4.D Interaction Testing

```bash
# Snapshot to get element refs
npx @playwright/cli snapshot

# Test key interactions
npx @playwright/cli click <nav-ref>
npx @playwright/cli snapshot

# Test form submission if present
npx @playwright/cli fill <input-ref> "test@example.com"
npx @playwright/cli click <submit-ref>
npx @playwright/cli screenshot
```

---

## PHASE 5: QUALITY AUDIT

### 5.A Web Design Guidelines Review

Fetch the latest Vercel Web Interface Guidelines and audit the code:

```
https://raw.githubusercontent.com/vercel-labs/web-interface-guidelines/main/command.md
```

Check against all rules. Output findings in `file:line` format.

### 5.A2 Ponytail Lean Review

After the guideline pass, review like the senior dev who gets paged when it breaks:

- Is every line needed? Name anything that can be cut or merged
- Trust-boundary validation present (forms, URL params, API bodies, file uploads)
- Error handling that prevents data loss is intact
- Security and accessibility not traded for brevity
- Non-trivial logic has a small test or assert
- Slow paths and real-load failure modes called out

Each finding: what the code does, what goes wrong, how to fix it, what happens if you skip it.

### 5.B Taste-Skill Pre-Flight Checklist

Before declaring "done", verify ALL of these honestly:

- [ ] No AI-purple default gradient (unless intentional)
- [ ] No generic glassmorphism applied to everything
- [ ] No Inter font as default (unless explicitly chosen)
- [ ] No centered-hero-over-dark-mesh as default layout
- [ ] No infinite-loop micro-animations
- [ ] Typography hierarchy is clear and intentional
- [ ] Color palette has purpose, not random Tailwind defaults
- [ ] Spacing is consistent (not arbitrary padding values)
- [ ] Components have proper states (hover, focus, active, disabled)
- [ ] Mobile layout works and isn't just a squished desktop
- [ ] Images have proper aspect ratios and aren't stretched
- [ ] No placeholder text (Lorem ipsum, "Click here", etc.)
- [ ] Accessibility: focus visible, contrast ratios pass, semantic HTML

### 5.C Accessibility Audit

- All images have alt text
- Color contrast meets WCAG AA (4.5:1 for text, 3:1 for large text)
- Focus indicators visible on all interactive elements
- Keyboard navigation works throughout
- Form inputs have associated labels
- Headings follow logical hierarchy (h1 > h2 > h3)
- ARIA attributes used correctly where needed
- Touch targets minimum 44x44px on mobile

---

## PHASE 6: FIX AND RE-VERIFY

If any issues found in Phase 4 or 5:

1. **Fix** the issues in the code
2. **Re-run Phase 4** — take fresh screenshots
3. **Re-run Phase 5** — verify the fixes pass audit
4. **Repeat** until clean

### Fix Priority:
1. **Broken layout** — anything that causes overflow, overlap, or missing content
2. **Accessibility failures** — contrast, focus, keyboard nav, alt text
3. **Visual slop** — AI defaults, inconsistent spacing, generic patterns
4. **Polish** — animation timing, hover states, responsive refinements

### When to stop:
- All screenshots render correctly at all viewports
- Pre-flight checklist passes 100%
- No critical or high-severity guideline violations
- The design has a clear, intentional identity (not generic AI output)

---

## WORKFLOW SUMMARY

```
User Brief
    │
    ▼
┌─────────────────┐
│ PHASE 0: READ   │  Interpret brief → Design Read line
└────────┬────────┘
         ▼
┌─────────────────┐
│ PHASE 1: STYLE  │  Select brand DESIGN.md or aesthetic direction
└────────┬────────┘
         ▼
┌─────────────────┐
│ PHASE 2: DIALS  │  Set Variance / Motion / Density
└────────┬────────┘
         ▼
┌─────────────────┐
│ PHASE 3: BUILD  │  Implement with taste-skill rules + brand tokens
└────────┬────────┘
         ▼
┌─────────────────┐
│ PHASE 4: VERIFY │  Playwright → screenshots at 3 viewports
└────────┬────────┘
         ▼
┌─────────────────┐
│ PHASE 5: AUDIT  │  Web guidelines + pre-flight + accessibility
└────────┬────────┘
         ▼
┌─────────────────┐
│ PHASE 6: FIX    │  Fix issues → re-verify → repeat until clean
└─────────────────┘
```

---

## QUICK COMMANDS

### Build a brand-matched UI:
> "Build a landing page that looks like Stripe's design"

→ Loads `awesome-design-md/stripe/DESIGN.md`, applies Stripe's tokens, builds with taste-skill discipline, verifies with Playwright.

### Build with a vibe:
> "Make me a brutalist portfolio site"

→ Sets dials to 9/3/3, applies brutalist aesthetic rules, builds, verifies.

### Build a specific product:
> "Create a SaaS dashboard for project management"

→ Sets dials to 4/3/7, uses Tailwind v4 + shadcn/ui, builds data-dense layout, verifies responsive behavior.

### Redesign existing:
> "This page looks generic, make it premium"

→ Audits current state, identifies slop patterns, applies premium aesthetic, re-verifies.

---

## INSTALLATION PATHS

This skill is installed at:
- `~/.agents/skills/design-forge/` (MiMoCode agents / shared agent skills)
- `~/.codex/skills/design-forge/` (OpenAI Codex)
- `~/.mimocode/skills/design-forge/` (MiMoCode user)
- `~/.config/opencode/skill/design-forge/` (OpenCode)
- `~/.gemini/config/skills/design-forge/` (Antigravity / Gemini global)

Sub-skills used (install as siblings in the same skills root):
- `taste-skill/` — Anti-slop frontend framework
- `awesome-design-md/` — 74 brand DESIGN.md files
- `ponytail/` — Lazy senior dev / YAGNI lean-build ladder
- `ponytail-review/` — Lean + safety review of a change
- `ponytail-audit/` — Whole-repo lean + quality audit
- `web-design-guidelines/` — Vercel UI best practices
- `playwright/` — Browser automation and verification