# praesidium — company context
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
## Auto facts (synced 2026-11-01)
### What it is / offer
- Praesidium Holdings, LLC is a Florida holding company for "a family of operating brands covering the workforce-safety, compliance, learning, and hiring stack" [praesidium-brands/README.md]
- Brands: Idoneity (contractor-management SaaS + EHS module), Bidwell (bid marketplace), Arete Lyceum (safety/technical LMS), Acuere Talent (specialist recruiting), Prometheus Risk Management (OSHA/safety consulting, Viera FL) [praesidium-brands/README.md]
- Planned structure: Praesidium → Idoneity Holdings, LLC → Idoneity SaaS / Idoneity Marketplace (Bidwell) / Arete / Acuere; PRM alongside as a peer. Praesidium has no customer revenue; Idoneity Holdings is meant to own brand/IP and take license + management fees [praesidium-brands/README.md; idoneity-cms/CORPORATE_STRUCTURE.md]
- Each brand keeps its own users, database and billing; interop via API and data portability [praesidium-brands/README.md]
- No public Praesidium website; holdings console runs as worker `praesidium-admin` (owner-only) [idoneity-cms/CLAUDE.md; praesidium-brands/docs/OWNER_CONSOLE.md]

### Customers & market
- Holding company has no customers [idoneity-cms/CORPORATE_STRUCTURE.md]
- Portfolio roll-up — still no paying customers recorded at any brand:
  - Idoneity: $0 revenue, no employees [idoneity-cms/docs/COMPLIANCE_CALENDAR.md]
  - Acuere: 0 placements, $0 booked, 1 application (analytics file dated 2026-07-17); 51 roles on /jobs, 14 outside its four lanes [acuere/data/analytics/latest.json; https://acueretalent.com/jobs]
  - Bidwell: DB reachable again but user/job/award counts not yet pulled [runs/2026-11-01/bidwell.auto.md]
  - PRM: counts unavailable — prod DB still failing [live /api/health 2026-11-01]
  - Arete: coming-soon page with an interest-list form only [https://arete.praesidium-holdings.workers.dev]
- Common market: industrial/construction contractors and the operators who hire them, Florida-first [brand repos]

### Pricing (as published)
- Holding company: n/a
- Roll-up:
  - Idoneity CMS: from $1,050/yr; /pricing page loads again (200) [https://idoneity-cms.com/pricing]
  - Idoneity-EHS: from $595/site/month; live page still shows the old 25-site slider with 15%/28% multi-site discounts [https://idoneity-ehs.praesidium-holdings.workers.dev/]
  - Bidwell: success fee of 7.25% → 5% → 3% on wins, plus a 3.5% prepay lane [https://bidwell.praesidium-holdings.workers.dev/]
  - Acuere: no public pricing [https://acueretalent.com]
  - Arete, PRM: no published prices [live sites]
- Intercompany plan: subs pay Holdings a quarterly IP license fee (typically 10–20% of net revenue) plus a management fee [idoneity-cms/CORPORATE_STRUCTURE.md]

### Product / tech status
- Live custom domains: idoneity-cms.com, acueretalent.com. Bidwell, Arete, PRM and Idoneity-EHS run on *.praesidium-holdings.workers.dev; idoneity-ehs.com and prometheusriskmgmt.com still don't resolve [live checks 2026-11-01]
- Health 2026-11-01, after the 11-01 Turso quota reset:
  - Idoneity CMS /api/health ok:true, /pricing 200 [live checks]
  - Bidwell /api/health ok:true, DB ok; live DB at migration 0015, 0016 not applied [live checks; bidwell/drizzle]
  - PRM /api/health ok:false — DB down for a third week, so the outage isn't explained by the quota alone [live check]
  - Acuere is up on D1 (migration 0029) [live check]
  - Arete is a coming-soon page; it has no health route [live check]
- Database platform: decision of 2026-10-25 is "all data lives in Cloudflare; stay off paid Turso" [D1_CUTOVER.md]
  - Idoneity's D1 cutover is still not live; prod still runs on Turso, and nobody has found what used up the read quota [idoneity-cms/wrangler.jsonc; runs/2026-11-01/idoneity.auto.md]
  - Bidwell, PRM and Arete are still on Turso, and Arete shares Idoneity's DB; only Acuere is on D1 [brand configs]
- Idoneity-EHS: one test failed in the 11-01 run (date-related); daily builder branches still not merged [runs/2026-11-01/idoneity.auto.md]
- Common stack: Next.js 16 + OpenNext on Cloudflare Workers; Idoneity-EHS is Python/FastAPI [brand package.json / requirements.txt]
- Commits 10-25 → 11-01 [runs/2026-11-01/gitlog-*.txt]:
  - idoneity-ehs: marketing-doc commits only (10-27 to 10-29)
  - acuere: the 3 commits dated 10-25 (acuere-cron Worker auto-deploy), already covered last week
  - praesidium-brands: the 10-29 context sync
  - none in idoneity-cms, leadgen, Bidwell, Arete or PRM
- Shared owner console (books separated by `entity_id`): corporate vault, compliance calendar, audit log, AP, AR, 9-step close, cash-basis P&L, CSV exports [praesidium-brands/docs/OWNER_CONSOLE.md]

### Sales & marketing activity
- Outbound is paused everywhere [runs/2026-11-01/idoneity.auto.md; acuere.auto.md; leadgen/out/_campaign_log.txt]
  - Idoneity leadgen on HOLD since 2026-08-08; its opt-out sync failed every day 10-26 → 10-31 (Turso reads blocked) and recovered 11-01, with nothing sent
  - Acuere: email provider is a stub, so nothing can send
- EHS marketing desk: 7 drafted packages not yet built, including a new weekly federal rulemaking digest; the deadline is the Feb 1 Form 300A season [idoneity-ehs/marketing/proposals/]
- Bidwell's "Book a walkthrough" still opens an email to hello@bidwell.com; PRM's only contact runs through the dead prometheusriskmgmt.com domain [live sites]
- PRM is positioned as a design-partner/referral channel for Idoneity [idoneity-cms/CORPORATE_STRUCTURE.md]

### Competitors
- (no source found) at the holding-company level — see the per-brand files

### Key tools & systems
- Cloudflare (Workers, D1, R2, Email Routing, Workers AI, Workflows, Browser Rendering); Turso being phased out under the 10-25 decision; Stripe (planned/partial); Resend (keys missing at several brands); Anthropic (CMS/Bidwell/PRM, though keys are unset on live Bidwell and PRM; Acuere uses Workers AI) [brand CLAUDE.md / wrangler configs; live health endpoints]
- Shared R2 bucket `praesidium-db-backups` for offsite DB dumps [acuere/CLAUDE.md]
- GitHub org praesidium-holdings (Acuere excluded from GitHub by decision) [praesidium-brands/README.md; acuere/CLAUDE.md]
- Accounting: QuickBooks Online or Xero planned [idoneity-cms/CORPORATE_STRUCTURE.md]

### Regulatory / compliance notes
- Sunbiz (looked up 2026-09-13) [idoneity-cms/docs/COMPLIANCE_CALENDAR.md]:
  - PRAESIDIUM HOLDINGS LLC filed 2026-07-14; first annual report due by 2027-05-01
  - IDONEITY LIMITED LIABILITY COMPANY filed 2026-07-17 (ownership to confirm)
  - PROMETHEUS HOLDINGS LLC (PRM, renamed 2026-07-16) filed 2025-04-28, two managing members
  - Idoneity Holdings, Bidwell/Idoneity Marketplace, Arete Lyceum and Acuere Talent are not filed
- Acuere's live footer still prints "Acuere Talent, LLC" (unfiled); Arete's footer prints the filed "Praesidium Holdings, LLC" [https://acueretalent.com; https://arete.praesidium-holdings.workers.dev]
- FL annual report window 1 Jan–1 May; $400 late fee after 1 May [idoneity-cms/docs/COMPLIANCE_CALENDAR.md]
- Structure: FL-only "Path B", Praesidium single-member; attorney + CPA review recommended before intercompany agreements [idoneity-cms/CORPORATE_STRUCTURE.md]
- Kids-FICA exemption depends on PRM staying a separate disregarded/peer entity; the two-member Sunbiz record conflicts with that [prm/docs/OWNER_CONSOLE.md; idoneity-cms/docs/TODO.md]
- Industry:
  - OSHA revised its heat-hazard enforcement program on 2026-04-10 and extended it five years, which settles last week's conflicting reports; the federal heat rule is still only proposed [https://www.mondaq.com/unitedstates/health-safety/1775642/osha-updates-and-extends-its-heat-program-for-five-more-years]
  - 2026 OSHA penalties unchanged from 2025 [https://www.osha.gov/memos/2026-05-21/2026-annual-adjustments-osha-civil-penalties]
- Employment:
  - Florida requires reporting contractors paid $600+ in a year to the Department of Revenue [https://www.constangy.com/newsroom/newsletters/Florida-expands-requirement-for-reporting-new-hires-independent-contractors-to-Department-of-Revenue]
  - The federal Labor Department's final independent-contractor rule was targeted for October 2026; nothing found confirming it is final [https://www.jdsupra.com/legalnews/deja-vu-for-employers-dol-moves-to-4368674/]

## Changed this week
- Turso quota reset on 11-01: the Idoneity CMS and Bidwell databases are healthy again (/api/health ok:true; Idoneity /pricing 200, was 500) [live checks 2026-11-01]
- PRM's prod DB is still failing after the reset (third week), so the outage isn't just the quota [live check]
- Idoneity's D1 cutover is still not live, and nobody has found what used up the Turso read quota, so it could run out again in November [runs/2026-11-01/idoneity.auto.md]
- Idoneity's leadgen opt-out sync failed 10-26 → 10-31 and recovered 11-01; nothing was sent (outbound still on HOLD) [leadgen]
- Heat enforcement program: OSHA revised it 2026-04-10 and extended it 5 years, which settles last week's conflicting sources [Mondaq]
- New employment rule noted: Florida requires reporting contractors paid $600+ to the Department of Revenue (relevant to Acuere/1099 work) [Constangy]
- Commits this week: idoneity-ehs marketing docs only; nothing in idoneity-cms, leadgen, Bidwell, Arete or PRM; the 3 Acuere commits dated 10-25 were already covered last week; holding docs (README, structure, owner console) unchanged [gitlog-*.txt; file dates]

## Open questions for Tyler
- The Turso quota reset brought Idoneity and Bidwell back, but the D1 cutover isn't live and nobody knows what used up the quota. Do you want all brands moved to D1 before the quota runs out again, and in what order (Idoneity + Arete, Bidwell, PRM)?
- PRM's DB is still down after the reset (third week), and prometheusriskmgmt.com doesn't resolve. Is PRM's site parked on purpose, or should it be fixed?
- Which brand gets focus and money this quarter? What portfolio targets should the CFO and analyst skills track: revenue, runway, first-customer dates?
- Entities: Sunbiz shows only Praesidium, Idoneity and PRM. Should Acuere's footer stop printing "Acuere Talent, LLC", or is that entity being filed?
- PRM's two-member Sunbiz record vs. the single-member/kids-FICA plan, and the Path B attorney/CPA review: has either been done?
