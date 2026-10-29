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
## Auto facts (synced 2026-10-25)
### What it is / offer
- Safety & technical LMS — "Safety and technical training your team will actually finish": course delivery, competency tracking, completion records that plug into contractor prequalification, "without the enterprise LMS pricing" [arete/README.md]
- Positioning: "Practical, OSHA-anchored workforce training that auto-writes the compliance record" [arete/src/app/page.tsx; src/app/layout.tsx]
- Mechanic: passing a course quiz writes an OSHA training record tied to the course's standard and issues an `ARE-…` certificate [arete/src/lib/lms.ts]
- Entity: "Arete, LLC (pending amendment to Arete Lyceum, LLC)" [arete/README.md]; not on Sunbiz — status "planned" [idoneity-cms/docs/COMPLIANCE_CALENDAR.md]

### Customers & market
- Target: crews of industrial/construction contractors; contractor → workers model [arete/src/app/demo/walkthrough.tsx; src/app/admin/page.tsx]
- Planned buyer roles: Employer Admin, Learning Admin, Instructor, Finance Admin [arete/src/lib/autonomy-policy.ts]
- Corporate plan: two-sided — contractors per worker seat, hiring clients per assigned worker [idoneity-cms/CORPORATE_STRUCTURE.md §4]
- No real customers named; waitlist size not readable (waitlist lives in Idoneity's DB, whose Turso reads are quota-blocked until Nov 1) [arete/src/app/api/waitlist/route.ts; idoneity-cms/.claude/worktrees/d1-port/docs/D1_CUTOVER.md]

### Pricing (as published)
- Live site: no pricing [https://arete.praesidium-holdings.workers.dev]
- Repo (Arete): no price figures; `plans`/`subscriptions` tables exist but unseeded; billing "scaffolded" [arete/src/db/schema.ts; src/app/autonomy/page.tsx]
- Planning doc (not published): $5/user/month standard catalog; +$3/user/month advanced pack (HAZWOPER, Confined Space Entrant, NFPA 70E, API 510/653/570 prep); free for hiring-client plans with 25+ active contractor seats [idoneity-cms/CORPORATE_STRUCTURE.md §4]

### Product / tech status
- Stack: Next.js 16.2.9, React 19.2.4, Tailwind 4, Drizzle, zod, SQLite local / Turso via @libsql/client; Cloudflare Workers via OpenNext [arete/package.json]
- Worker `arete`, no custom domain/route [arete/wrangler.jsonc]
- LMS data shares Idoneity's DB (Turso `idoneity-prod` in prod). If Idoneity cuts over to D1, Arete's prod data source would need the same change — no Arete-side change found [arete/src/db/client.ts; idoneity-cms/.claude/worktrees/d1-port/docs/D1_CUTOVER.md]
- Live: https://arete.praesidium-holdings.workers.dev returns 200 — "coming soon" page with interest-list form [live check 2026-10-25; arete/src/app/page.tsx]
- Demo tiles: HazCom 1910.1200, LOTO 1910.147, Fall Protection 1926.501, Hearing 1910.95, Confined Space 1910.146 [arete/src/app/demo/walkthrough.tsx]
- Open TODO: provision Turso `arete-autonomy-prod` + Worker secrets; until then DB-backed autonomy routes 500 on Workers [arete/CLOUDFLARE_TODO.md]
- Cron (GitHub Actions): daily cert-expiring sweep, weekly Friday cohort-health digest [arete/.github/workflows/cron.yml]
- Last commits about 2026-08-08; tag v1.0.0; no commits or file changes since 2026-10-18 [runs/2026-10-25/gitlog-arete.txt; file mtimes]

### Sales & marketing activity
- Only live channel: waitlist form (source `arete-coming-soon`) → shared `waitlist_signups` table, managed in Idoneity admin [arete/src/app/api/waitlist/route.ts]
- Internal Autonomy Command Center (leads, CRM, walkthroughs, quotes/cohort proposals, AR/AP) — quotes/billing scaffolded [arete/src/app/autonomy/page.tsx]
- Sister-brand footers show Arete as "coming-soon" [bidwell/src/components/brand-family-footer.tsx; prm/src/components/brand-family-footer.tsx]

### Competitors
- (no source found) in the Arete repo — only "enterprise LMS pricing" implied [arete/README.md]
- Corporate doc uses RedVector and Coggno as pricing benchmarks [idoneity-cms/CORPORATE_STRUCTURE.md §4]

### Key tools & systems
- Cloudflare Workers / R2 / Workers Logs; Turso/libSQL; GitHub Actions [arete/wrangler.jsonc; .github/workflows/]
- Stripe planned (price/subscription ID fields, webhook stubs) [arete/src/db/schema.ts]
- Owner finance in Idoneity admin, `entity_id = ent_arete` [arete/docs/OWNER_CONSOLE.md]

### Regulatory / compliance notes
- No OSHA Outreach (10/30) authorization, IACET/ANSI or CEU accreditation claimed; optional `ceu_credits` field exists [arete/src/db/schema.ts]
- Corporate plan: no official OSHA 10/30 cards in v1 [idoneity-cms/CORPORATE_STRUCTURE.md §4]
- Certificates read "Certificate of Completion… Aligned to {standard}" with a "Valid through" date; trainer recorded as "Arete (online)" [arete/src/app/certificates/[enrollmentId]/page.tsx; src/lib/lms.ts]
- Copy promises "digital signature" and "what the regulator expects" [arete/src/components/onboarding-tour.tsx; src/app/demo/walkthrough.tsx]
- Autonomy: course publishing, refunds and write-offs need approval; automatic credential issuance on by default [arete/src/lib/autonomy-policy.ts]
- Liability plan: training-delivery E&O ($800–$1,500/yr estimate) plus content provenance logs [idoneity-cms/CORPORATE_STRUCTURE.md §4]
- Name chosen to avoid conflict with Areté Associates; Sunbiz amendment to "Arete Lyceum, LLC" pending [idoneity-cms/CORPORATE_STRUCTURE.md]

## Changed this week
- No changes. There were no commits or file changes in the repo since 2026-10-18 [gitlog-arete.txt; file mtimes]. The live coming-soon page is unchanged (200)
- New context, not a change: Arete's prod LMS data and waitlist live in Idoneity's Turso DB. That DB is quota-blocked until Nov 1, and Idoneity has a D1 cutover prepared that doesn't mention Arete [idoneity-cms/.claude/worktrees/d1-port/docs/D1_CUTOVER.md]

## Open questions for Tyler
- Arete reads Idoneity's Turso DB (waitlist + LMS). When Idoneity moves to D1, should Arete follow or stay on Turso? The D1 cutover plan doesn't cover it.
- Is the $5 + $3 per user per month plan in CORPORATE_STRUCTURE.md still the intended pricing, or will it be per course or cohort?
- When should Arete launch relative to the other brands, and on which domain?
- Is an OSHA Outreach (10/30) authorization or any accreditation (IACET/CEU) planned? The copy promises "what the regulator expects".
- Has the Sunbiz filing or amendment for Arete Lyceum, LLC been started?
