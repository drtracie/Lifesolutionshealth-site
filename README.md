# Life Solutions Health — Digital Platform

Replatforming [Life Solutions Health](https://lifesolutionshealth.com) — a Chicago telehealth clinic (provider-led GLP-1 weight loss + virtual primary care) — from Square Online onto a modern, HIPAA-ready stack.

**Client engagement by [KLC Consulting Group](https://klccgrp.com).**

## Brand architecture

| Brand | Role |
|---|---|
| **Life Solutions Health** | Primary landing & main site |
| **Dr. Tracie Clisby, DNP** | Sister brand — founder/provider identity (section within site) |
| **Life Solution Labs** | Sister brand — diagnostic/lab arm (section within site) |

## Repo layout

```
lsh-platform/
├── CLAUDE.md                  # Claude Code project context — read first
├── README.md
├── prototype/
│   └── index.html             # Approved v2 design prototype (single file, 7 views)
├── docs/
│   ├── PROJECT_ANALYSIS.md    # Strategy, competitive landscape, stack, phase plan
│   ├── BUILD_SPEC.md          # Phase 1 build specification
│   └── DESIGN_SYSTEM.md       # Tokens, type, components, section rhythm
└── assets/
    └── square-exports/        # Client-exported images from Square admin (empty until delivery)
```

## Quick start

```bash
# View the prototype — no build step
open prototype/index.html        # macOS
# or
python3 -m http.server -d prototype 8080
```

## Phase plan (summary)

1. **Phase 1 — Marketing site + intake funnel** · Next.js + Tailwind on Vercel; eligibility quiz → Supabase; Stripe subscription checkout
2. **Phase 2 — Patient portal** · scheduling, secure messaging, refills, progress tracking
3. **Phase 3 — Automation & growth** · drips, referrals, lab integrations, B2B corporate wellness

Full detail: [`docs/PROJECT_ANALYSIS.md`](docs/PROJECT_ANALYSIS.md).

## Non-negotiables

- Design tokens and content/compliance rules live in [`CLAUDE.md`](CLAUDE.md) — they bind all contributors, human or agent.
- No PHI in this repo, ever. No fabricated testimonials. Placeholder pricing until client sign-off.

---
© KLC Consulting Group · Client: Life Solutions Health · Confidential
