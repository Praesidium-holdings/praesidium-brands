# arete — company context
_Read by every role skill. Top section is yours; everything below the line is rebuilt weekly by context-sync._

<!-- OWNER:START -->
## Owner-confirmed (Tyler edits this — the sync never changes it)
- Ideal customer:
- Pricing / target margins:
- Top 3 priorities right now:
- Tone / voice:
- Things we will not do:
- Key people & roles:
<!-- OWNER:END -->

---
## Auto facts (synced 2026-11-08)
### What it is / offer
- Safety and technical LMS: "Safety and technical training your team will actually finish". Covers course delivery, competency tracking, and completion records that plug into contractor prequalification, "without the enterprise LMS pricing" [arete/README.md]
- Positioning: "OSHA-anchored competency training that auto-writes the compliance record. Coming soon." [arete/src/app/layout.tsx; https://arete.praesidium-holdings.workers.dev]
- Mechanic: passing a course quiz writes an OSHA training record tied to the course's standard and issues an `ARE-…` certificate [arete/src/lib/lms.ts]
- Entity:
  - Repo: "Arete, LLC (pending amendment to Arete Lyceum, LLC)" [arete/README.md]
  - Sunbiz: not filed, status "planned" [idoneity-cms/docs/COMPLIANCE_CALENDAR.md]
  - Live footer: "© 2026 Praesidium Holdings, LLC." [https://arete.praesidium-holdings.workers.dev, 2026-11-08]

### Customers & market
- Target: crews of industrial and construction contractors, on a contractor → workers model [arete/src/app/demo/walkthrough.tsx; src/app/admin/page.tsx]
- Planned buyer roles: Employer Admin, Learning Admin, Instructor, Finance Admin [arete/src/lib/autonomy-policy.ts]
- Corporate plan is two-sided: contractors pay per worker seat, hiring clients per assigned worker [idoneity-cms/CORPORATE_STRUCTURE.md §4]
- No real customers named. Waitlist count not read; the waitlist lives in Idoneity's shared DB, which is degraded as of 2026-11-08 [arete/src/app/api/waitlist/route.ts; https://idoneity-cms.com/api/health]

### Pricing (as published)
- Live site: no pricing [https://arete.praesidium-holdings.workers.dev]
- Repo: no price figures. `plans`/`subscriptions` tables exist but are unseeded; billing is "scaffolded" [arete/src/db/schema.ts; src/app/autonomy/page.tsx]
- Unpublished planning doc [idoneity-cms/CORPORATE_STRUCTURE.md §4]:
  - $5/user/month for the standard catalog
  - +$3/user/month for the advanced pack (HAZWOPER, Confined Space Entrant, NFPA 70E, API 510/653/570 prep)
  - Free for hiring-client plans with 25+ active contractor seats

### Product / tech status
- Stack: Next.js 16.2.9, React 19.2.4, Tailwind 4, Drizzle, zod, SQLite locally / Turso via @libsql/client; Cloudflare Workers via OpenNext [arete/package.json]
- Worker `arete`, with no custom domain or route [arete/wrangler.jsonc]
- LMS data shares Idoneity's DB (Turso `idoneity-prod` in prod) [arete/src/db/client.ts]
  - That DB failed Idoneity's health check on 2026-11-08 [https://idoneity-cms.com/api/health]
  - Idoneity's D1 cutover is still "ready but inert" and does not mention Arete [idoneity-cms/.claude/worktrees/d1-port/docs/D1_CUTOVER.md]
- Live 2026-11-08: the "Coming soon" page with interest-list form returns 200. There is no `/api/health` route [live check]
- Demo tiles: HazCom 1910.1200, LOTO 1910.147, Fall Protection 1926.501, Hearing 1910.95, Confined Space 1910.146 [arete/src/app/demo/walkthrough.tsx]
- Open TODO: provision Turso `arete-autonomy-prod` and the Worker secrets. Until then, DB-backed autonomy routes return 500 on Workers [arete/CLOUDFLARE_TODO.md]
- Cron (GitHub Actions): daily cert-expiring sweep; weekly Friday cohort-health digest [arete/.github/workflows/cron.yml]
- Dormant: no commits since ~2026-08-08 (tag v1.0.0), and no files modified since 2026-11-01 [gitlog-arete.txt; file mtimes]

### Sales & marketing activity
- The only live channel is the waitlist form (source `arete-coming-soon`). Signups go to the shared `waitlist_signups` table, managed in Idoneity admin [arete/src/app/api/waitlist/route.ts]
- Internal Autonomy Command Center: leads, CRM, walkthroughs, quotes/cohort proposals, AR/AP. Quotes and billing are scaffolded [arete/src/app/autonomy/page.tsx]
- Sister-brand footers list Arete as "coming-soon" [bidwell/src/components/brand-family-footer.tsx; prm/src/components/brand-family-footer.tsx]

### Competitors
- (no source found) in the Arete repo, beyond an implied "enterprise LMS pricing" [arete/README.md]
- The corporate doc uses RedVector and Coggno as pricing benchmarks [idoneity-cms/CORPORATE_STRUCTURE.md §4]

### Key tools & systems
- Cloudflare Workers / R2 / Workers Logs; Turso/libSQL; GitHub Actions [arete/wrangler.jsonc; .github/workflows/]
- Stripe planned (price/subscription ID fields, webhook stubs) [arete/src/db/schema.ts]
- Owner finance in Idoneity admin, `entity_id = ent_arete` [arete/docs/OWNER_CONSOLE.md]

### Regulatory / compliance notes
- No OSHA Outreach (10/30) authorization, IACET/ANSI or CEU accreditation is claimed; an optional `ceu_credits` field exists [arete/src/db/schema.ts]
- Corporate plan: no official OSHA 10/30 cards in v1 [idoneity-cms/CORPORATE_STRUCTURE.md §4]
- Certificates read "Certificate of Completion… Aligned to {standard}" with a "Valid through" date; the trainer is recorded as "Arete (online)" [arete/src/app/certificates/[enrollmentId]/page.tsx; src/lib/lms.ts]
- Copy promises a "digital signature" and "what the regulator expects" [arete/src/components/onboarding-tour.tsx; src/app/demo/walkthrough.tsx]
- Autonomy: course publishing, refunds and write-offs need approval; automatic credential issuance is on by default [arete/src/lib/autonomy-policy.ts]
- Liability plan: training-delivery E&O (estimated $800–$1,500/yr) plus content provenance logs [idoneity-cms/CORPORATE_STRUCTURE.md §4]
- Name chosen to avoid conflict with Areté Associates; the Sunbiz amendment to "Arete Lyceum, LLC" is pending [idoneity-cms/CORPORATE_STRUCTURE.md]
- Training-record retention rule relevant to the product: OSHA injury logs are kept 5 years (29 CFR 1904.33) [idoneity-ehs/marketing/proposals/2026-11-03/fixtures/source-retention-1904-33.md]

## Changed this week
- No product or site changes: no commits and no file changes; the coming-soon page still returns 200 [gitlog-arete.txt; live check 2026-11-08]
- Indirect: the Idoneity DB that Arete's waitlist and LMS share failed its health check again on 2026-11-08, so waitlist writes may be failing [https://idoneity-cms.com/api/health]

## Open questions for Tyler
- Arete's waitlist writes to Idoneity's DB, which is failing again. Should Arete move with Idoneity in the D1 cutover, or get its own DB? The cutover plan still doesn't cover Arete.
- Is the $5 + $3 per user per month plan in CORPORATE_STRUCTURE.md still the intended pricing, or will it be per course or per cohort?
- When should Arete launch relative to the other brands, and on which domain? It has had no commits since August.
- Is an OSHA Outreach (10/30) authorization or any accreditation (IACET/CEU) planned? The copy promises "what the regulator expects".
- Has the Sunbiz filing or amendment for Arete Lyceum, LLC been started?
