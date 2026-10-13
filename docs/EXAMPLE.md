# Design Forge — Example: brand-matched pricing page

This is a condensed walkthrough of what a real design-forge run looks like.

---

**You:**

> Build a pricing page that looks like Linear.

---

**Agent (Design Read):**

```
Reading this as: pricing page for developers / SaaS buyers,
with premium-minimal language, leaning toward Linear design system.
```

**Phase 1 — Style**

Loads `awesome-design-md/linear.app/DESIGN.md`:

- accent: `#5E6AD2`
- type: Inter Variable, tight tracking
- radius: 8px, subtle borders, no heavy shadows
- motion: restrained fades

**Phase 2 — Dials**

| Dial | Value | Why |
|------|-------|-----|
| DESIGN_VARIANCE | 7 | Linear-like subtle asymmetry |
| MOTION_INTENSITY | 5 | scroll reveals, no spectacle |
| VISUAL_DENSITY | 4 | pricing needs air |

**Phase 3 — Build (ponytail ladder)**

| Need | Decision |
|------|----------|
| Pricing cards | Reuse repo `Card` if present; else one `PricingTier` |
| Monthly/annual toggle | Platform `<button>` + CSS — **not** a switch library |
| Currency formatting | `Intl.NumberFormat` — **not** a helper |
| Icons | Existing icon family — **not** new SVGs |

Result: ~12 files, lean diff. Skipped: animated plan switch (nobody asked).

**Phase 4 — Verify**

Playwright screenshots at 375 / 768 / 1440. Checks overflow, font load, contrast.

**Phase 5 — Audit**

- Vercel web guidelines pass
- ponytail-review: muted caption fails WCAG AA → fix
- ponytail-review: tab focus ring missing → fix
- taste-skill pre-flight: no AI-purple, no generic glass, intentional type scale

**Phase 6 — Fix & re-verify**

Both findings fixed. Fresh screenshots clean. Done.

---

## Checklist output (honest)

```
Done. Skipped: no annual/monthly animation (not asked).
Risk  : none. Pricing values are hardcoded mock data — wire to real data before ship.
```

---

## Try it

```
Build me a landing page for a fintech startup
Make this look like Stripe
Create a brutalist portfolio site
This page looks generic, make it premium
```
