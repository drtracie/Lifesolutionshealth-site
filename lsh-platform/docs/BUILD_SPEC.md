# BUILD_SPEC — Phase 1: Marketing Site + Intake Funnel

Scope for the production build of the approved v2 prototype. Claude Code: work this spec top-down; `CLAUDE.md` rules bind every task.

## Objective

Ship lifesolutionshealth.com as a Next.js site on Vercel that reproduces the v2 prototype design exactly, with a working eligibility quiz persisted to Supabase and a Stripe checkout stub behind a feature flag.

## Stack

- **Next.js 15+ (App Router), TypeScript, Tailwind CSS** — tokens migrated from `prototype/index.html` `:root` into CSS custom properties + Tailwind theme
- **Supabase** — `eligibility_submissions` table (no PHI fields beyond the quiz pre-screen; see data rules below), Row Level Security on
- **Stripe** — Checkout session for subscription plans; **flagged off** until client confirms pricing
- **Vercel** — preview deploys per PR; production behind client approval
- Fonts: Fraunces + Figtree via `next/font` (self-hosted, no layout shift)

## Routes

| Route | Source view in prototype |
|---|---|
| `/` | Home |
| `/weight-loss` | Weight loss |
| `/primary-care` | Primary care |
| `/dr-tracie-clisby` | Dr. Clisby (sister brand) |
| `/labs` | Life Solution Labs (sister brand) |
| `/pricing` | Pricing |
| `/eligibility` | Quiz / intake entry |

Family bar links map to routes (not separate domains) for now; see CLAUDE.md on the open drtracieclisby.com domain-equity question.

## Component inventory (build in this order)

1. `FamilyBar`, `Nav`, `Footer` (shared shell)
2. `Hero` (variant prop: default / clisby / labs palettes)
3. `TrustStrip`
4. `CategoryTiles`
5. `EditorialSplit` (photo side + checklist side, mirrored variant)
6. `Steps`
7. `ProviderSpotlight` (sand panel, pull quote)
8. `TestimonialCards` (renders only verified entries from `content/testimonials.json`; empty array → section hidden)
9. `FAQ` (accordion, native `<details>`)
10. `PlanCards`
11. `EligibilityQuiz` (multi-step, client component → server action → Supabase)
12. `BigCTA`

## Eligibility quiz — data rules

- Fields: reason, height, weight, diagnosis bucket (enum), state. **No name/DOB/contact at this phase** — contact capture happens only after legal review of privacy policy + consent language.
- Store: Supabase with RLS; no third-party analytics on quiz pages; no quiz data in URL params, localStorage, or logs.
- Result screen copy must keep "your provider makes all final clinical decisions."

## SEO / performance

- Per-route metadata + OpenGraph; JSON-LD `MedicalBusiness` on `/`, `Physician` on `/dr-tracie-clisby`
- Target Lighthouse ≥ 95 performance / 100 accessibility / 100 SEO on `/`
- Images: `next/image`, AVIF/WebP, arch mask via CSS `border-radius` (not image crops)

## Definition of done (Phase 1)

- [ ] All 7 routes pixel-faithful to prototype at 380px / 768px / 1280px
- [ ] Quiz submissions land in Supabase (verified in staging)
- [ ] Stripe checkout behind `NEXT_PUBLIC_CHECKOUT_ENABLED=false`
- [ ] Zero fabricated testimonials or unapproved claims in shipped copy
- [ ] Legal footer + 911 disclaimer on every route
- [ ] Client sign-off on staging URL

## Explicitly out of scope (Phase 1)

Patient portal, telehealth video, EHR integration, SMS/email automation, B2B track — see `PROJECT_ANALYSIS.md` Phases 2–3.
