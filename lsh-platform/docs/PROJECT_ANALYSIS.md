# Life Solutions Health — Project Analysis & Prototype Blueprint
*Prepared: June 2026*

---

## 1. What We Know About the Business

**lifesolutionshealth.me** (current site on Square Online) is a **telehealth primary care + weight loss clinic**. Based on the site metadata, OG tags, and search-indexed content, the core offering is:

- **Telehealth primary care** — virtual consultations with licensed providers
- **Medical weight loss** — GLP-1 programs (Semaglutide / Tirzepatide / compounded options)
- **Subscription/recurring model** — patients return monthly for refills, dose adjustments, check-ins
- **Direct-to-consumer** — no insurance friction implied (typical in this space)

**Current tech stack:** Square Online (basic eComm CMS — severely limiting for a healthcare brand competing with LifeMD, Lemonaid, Hims, etc.)

---

## 2. Competitive Landscape Snapshot

| Competitor | Differentiator | Weakness |
|---|---|---|
| LifeMD | Slick platform, NASDAQ-listed | $19/mo membership gate feels corporate |
| Lemonaid (23andMe) | Compounded GLP-1s from $129/mo | Brand feels transactional |
| Hims & Hers | Strong brand, massive ad spend | No real clinical depth messaging |
| Form Health | Dietitian-led + physician combos | Limited reach, clunky UX |
| **LSH opportunity** | Personal, local feel + full clinical trust | Needs a real digital platform |

---

## 3. Project Scope Recommendation

### Phase 1 — Marketing Site + Intake Flow (MVP)
The core prototype and Lovable-powered UX work lives here.

**Pages needed:**
1. **Home** — Hero with weight loss value prop, social proof, CTA to start
2. **Services** — GLP-1 Weight Loss, Primary Care, optional: hormone/wellness
3. **How It Works** — 3-step intake: intake form → provider review → prescription shipped
4. **Pricing** — Transparent, simple tiers (competitive advantage in this space)
5. **About / Providers** — Builds trust; faces + credentials matter enormously in telehealth
6. **FAQ** — Addresses insurance, compounding quality, side effects, eligibility
7. **Patient Portal Login** — Link to/embed patient management system

**Intake funnel (the money flow):**
- Eligibility quiz (BMI, health history, goals — 5-7 questions)
- ID verification step
- Provider assignment
- Checkout / subscription setup

### Phase 2 — Patient Portal
- Appointment scheduling
- Secure messaging with provider
- Rx refill requests
- Progress tracking (weight, labs, dosing history)
- Subscription management

### Phase 3 — Automation & Growth
- Email/SMS drip sequences (onboarding, check-ins, refill reminders)
- Referral program
- Lab order integration (Labcorp/Quest)
- Insurance eligibility check (optional)

---

## 4. Recommended Stack

### Frontend / UX
**→ Lovable** for rapid UX prototyping and iteration ✅
- Perfect for this use case — healthcare landing pages + intake forms
- Export to React when ready to productionize
- Pair with shadcn/ui component library

**→ Next.js (React)** for production frontend
- SEO-critical for healthcare (Google organic is major patient acquisition)
- App Router for fast page loads + streaming
- Tailwind CSS for styling

### Backend / API
**→ Supabase**
- Postgres database (patient records, intake forms, appointments)
- Row-level security (critical for HIPAA considerations)
- Auth built in
- Realtime for messaging

**→ Node.js / Express** or **Next.js API Routes** for business logic
- Intake form processing
- Webhook handling (payments, pharmacy, comms)

### Payments & Subscriptions
**→ Stripe**
- Subscription billing (monthly GLP-1 programs)
- Usage-based billing if à la carte consults added
- Stripe Checkout for fastest MVP checkout flow

### Telehealth / Video
**→ Doxy.me** (HIPAA-compliant, no install required for patients) — simplest
*or*
**→ Daily.co** API if you want branded in-app video

### EHR / Clinical Workflow
**→ Canvas Medical** (API-first EHR built for telehealth startups) — top pick
*or*
**→ Elation Health** (more established, slightly heavier)
*or*
**→ Simple Practice** (if keeping it lightweight at first)

### Pharmacy / Rx Fulfillment
**→ Belmar Pharmacy** or **PharMedium** for compounded GLP-1s
- Need a pharmacy partner relationship — this is the clinical backbone
- Some clinics use **Truepill** (now Cornerstone) as pharmacy infrastructure layer

### Communications
**→ Twilio** — SMS appointment reminders, refill alerts
**→ SendGrid / Resend** — transactional email (confirmations, welcome flows)
**→ Customer.io** — automated patient journey sequences

### Hosting / Infra
**→ Vercel** — Next.js frontend (zero config, fast CDN globally)
**→ Supabase Cloud** — managed Postgres
**→ Cloudflare** — DNS, DDoS, edge caching

### HIPAA Compliance Notes ⚠️
- Supabase has a HIPAA-eligible plan (Business tier + BAA)
- Vercel also offers BAA for Enterprise
- Do NOT store PHI in Stripe or unsecured logs
- Consider **Aptible** if you want managed HIPAA infrastructure from day one

---

## 5. Items to Add (Gaps in Current Offering)

Based on competitive analysis, here's what LSH should consider adding that competitors miss or do poorly:

### Clinical Differentiators
- **Lab integration at intake** — order baseline metabolic panel before first dose; positions LSH as more clinically rigorous
- **Body composition tracking** — not just weight; add InBody or Withings scale integration
- **Muscle preservation protocol** — GLP-1 patients lose muscle; add protein/resistance guidance as a premium add-on
- **Side effect management module** — guided protocol for nausea, fatigue; reduces churn significantly

### Product / Revenue Expansion
- **GLP-1 companion supplements** — branded anti-nausea, electrolyte, protein bundles (margin-rich)
- **Nutrition coaching add-on** — RD check-ins quarterly; $49/mo upsell
- **Annual wellness visit** — primary care hook that keeps patients long-term even after weight loss goal reached
- **Corporate wellness B2B track** — employers paying for employee GLP-1 access is a massive emerging market

### UX / Trust Builders
- **Real-time eligibility check** — "See if you qualify in 60 seconds" widget on homepage
- **Provider bios with video intros** — highest trust signal in telehealth, almost no one does this well
- **Live chat** (not just a form) — Intercom or Crisp; dramatically increases conversion on landing pages
- **Patient progress stories** — HIPAA-compliant testimonials with before/after metrics (not photos, but data)
- **Transparent pricing page** — this is a massive trust gap competitors exploit; be the most transparent

---

## 6. Lovable Strategy

For Lovable specifically, here's the recommended build order:

1. **Marketing homepage** — hero, services grid, how-it-works, pricing teaser, social proof, CTA
2. **Intake/eligibility quiz** — multi-step form with conditional logic
3. **Pricing page** — plan comparison table
4. **Services detail pages** — GLP-1, primary care
5. **Provider bios page**

Export from Lovable → clean React/Next.js codebase → wire to Supabase + Stripe backend.

**Lovable prompting tips:**
- Give it your brand hex codes upfront (`#12134b` navy + a warm accent)
- Provide competitor URLs (Lemonaid, Hims) as style references to differentiate FROM
- Specify "no stock photo of smiling doctors" — use illustration or real patient/provider photography

---

## 7. Prototype Priority Order

```
Week 1-2:  Lovable → Homepage + Services pages (pure marketing)
Week 2-3:  Lovable → Intake quiz + Pricing page
Week 3-4:  Next.js setup → wire intake form to Supabase
Week 4-5:  Stripe subscription checkout integration
Week 5-6:  Provider portal MVP (basic dashboard, patient list)
Week 6-8:  Telehealth video integration + messaging
```

---

## 8. One-Line Summary

**LSH is a real clinical business stuck on a Square website.** The prototype should feel like a premium, trustworthy digital health brand — think the clinical credibility of Form Health with the design confidence of Hims — built on a modern stack that can actually scale subscriptions, support HIPAA compliance, and automate the patient journey from first click to shipped medication.

---

*Next step: Share brand assets (logo, colors, any copy) and we can kick off the Lovable prototype immediately.*
