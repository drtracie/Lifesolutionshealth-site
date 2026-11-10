# CLAUDE.md — Life Solutions Health Platform

Project context for Claude Code. Read this before making changes.

## What this is

Digital platform for **Life Solutions Health** (LSH) — a Chicago-based telehealth clinic offering provider-led GLP-1 medical weight loss and virtual primary care. Founded by **Dr. Tracie Clisby, DNP, FNP** (DePaul University; Chicago academic medical center background).

Client is replatforming off Square Online. Brand architecture (client-directed):

- **lifesolutionshealth.com** — primary landing / main site (this repo)
- **Dr. Tracie Clisby** (drtracieclisby.com) — sister brand, provider identity, lives as a section within the main site
- **Life Solution Labs** — sister brand, diagnostic/lab arm, lives as a section within the main site

Open strategic question (do not resolve unilaterally): whether drtracieclisby.com 301s into the main site or stays as a co-branded one-pager to preserve domain equity. Flag, don't decide.

## Current state

- `prototype/index.html` — **approved design direction (v2)**. Single-file HTML prototype with JS view routing. 7 views: home, weight loss, primary care, Dr. Clisby, Labs, pricing, eligibility quiz.
- v1 (dark navy, card-grid heavy) was **rejected** as "cookie cutter / AI repetitive." Do not regress toward it.
- Reference aesthetic: forhers.com / ro.com — light, warm, editorial, photography-led. Not flashy.

## Design system (non-negotiable unless client redirects)

Tokens live in `:root` of `prototype/index.html` and in `docs/DESIGN_SYSTEM.md`.

- Background: warm paper `#FBF9F5`, section tints `#F3EDE3` / `#EFE6D8`
- Brand navy `#12134B` is **ink/type color only — never a full-bleed dark background**
- Accent: apricot `#E7A576` / `#D98D57` (CTAs, highlights); sage `#B4C4AE` reserved for Labs
- Type: Fraunces (display serif, weight 400–500) + Figtree (UI sans)
- Shapes: arch-top photo frames (`border-radius: 200px 200px 28px 28px`), pill buttons, 28px card radius
- Section rhythm must **alternate** (hero → strip → tiles → editorial split → steps → spotlight → quotes → FAQ → CTA). Never stack three card-grids in a row.
- Primary CTA is always the literal string **"Am I eligible?"**

## Content rules (healthcare — these are liabilities, not style choices)

1. **No fabricated patient testimonials.** Placeholders are clearly marked `[Placeholder]` and must be replaced with verified reviews (Google Business profile / intake surveys) before anything ships.
2. **No efficacy or outcome claims** beyond what the client's clinical team approves. "May," "can," provider-determines language.
3. Dr. Clisby's bio is placeholder pending her approved copy. Verified facts only: DNP (DePaul), FNP, Chicago, academic medical center experience, telehealth, accepting new patients.
4. Keep the emergency disclaimer (911 line) and the "informational, not medical advice" legal block in the footer of every page.
5. Pricing is placeholder (`$XX`/`$XXX`) until client confirms. Strategy: radical transparency — one number per program.
6. No PHI ever enters this repo, logs, or client-side storage. The eligibility quiz is a pre-screen only; production intake must run on HIPAA-eligible infrastructure.

## Image assets

Square Online blocks scraping — assets **cannot** be pulled programmatically. Client exports from Square admin (Website → Media Library) into `assets/square-exports/`. Every placeholder in the prototype is labeled with which asset belongs there. Until real photos land, keep the soft gradient placeholder blocks.

## Target production stack (Phase 1+, per docs/PROJECT_ANALYSIS.md)

Next.js (App Router) + Tailwind · Supabase (Postgres/auth, HIPAA-eligible Business tier + BAA) · Stripe subscriptions · Vercel hosting · Doxy.me or Daily.co for telehealth video · Canvas Medical (EHR, later phase). Lovable may be used for UX iteration; exports must conform to the design tokens above.

## Working agreements

- Prototype stays a **single self-contained HTML file** until the Next.js migration is explicitly started. Don't split it into a framework preemptively.
- When migrating to Next.js: tokens → `tailwind.config` / CSS custom properties first, then componentize per section (Hero, TrustStrip, Tiles, EditorialSplit, Steps, Spotlight, Quotes, FAQ, BigCTA, Footer).
- Mobile-first checks at 380px; no horizontal scroll; 16px minimum side gutters.
- Commit style: conventional commits (`feat:`, `fix:`, `docs:`, `chore:`).
- Challenge weak ideas; the client (KLC Consulting Group) expects pushback with rationale, not silent compliance.
