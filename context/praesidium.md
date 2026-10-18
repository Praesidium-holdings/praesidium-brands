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
## Auto facts (synced 2026-10-18)
### What it is / offer
- Praesidium Holdings, LLC is a Florida holding company for "a family of operating brands covering the workforce-safety, compliance, learning, and hiring stack" [praesidium-brands/README.md]
- Brands: Idoneity (contractor-management SaaS + EHS module), Bidwell (bid marketplace), Arete Lyceum (safety/technical LMS), Acuere Talent (specialist recruiting), Prometheus Risk Management (OSHA/safety consulting, Viera FL) [praesidium-brands/README.md]
- Planned structure: Praesidium → Idoneity Holdings, LLC → Idoneity SaaS / Idoneity Marketplace (Bidwell) / Arete / Acuere; PRM sits alongside as a peer. Praesidium has no customer revenue; Idoneity Holdings is meant to own brand/IP and take license + management fees [praesidium-brands/README.md; idoneity-cms/CORPORATE_STRUCTURE.md]
- Each brand keeps its own users, database and billing; interop happens via API and data portability [praesidium-brands/README.md]
- No public Praesidium website found in repo; the holdings console runs as worker `praesidium-admin` (owner-only) [idoneity-cms/CLAUDE.md; praesidium-brands/docs/OWNER_CONSOLE.md]

### Customers & market
- Holding company has no customers [idoneity-cms/CORPORATE_STRUCTURE.md]
- Portfolio roll-up, no paying customers recorded at any brand:
  - Idoneity: $0 revenue, no employees [idoneity-cms/docs/COMPLIANCE_CALENDAR.md]
  - Acuere: 0 placements, 1 candidate in pool [acuere/data/analytics/latest.json; docs/NEXT_STEPS.md]
  - Bidwell, Arete, PRM: counts unavailable (Bidwell/PRM prod DBs failing health checks; Arete is a waitlist) [live /api/health checks 2026-10-18]
- Common market: industrial/construction contractors and the operators who hire them, Florida-first [brand repos — see per-brand files]

### Pricing (as published)
- Holding company: n/a
- Roll-up of published pricing:
  - Idoneity CMS: from $1,050/yr; /pricing page currently returns 500 [https://idoneity-cms.com]
  - Idoneity-EHS: from $595/site/month [https://idoneity-ehs.praesidium-holdings.workers.dev/]
  - Bidwell: 7.25% → 5% → 3% success fee on wins, 3.5% prepay lane [https://bidwell.praesidium-holdings.workers.dev/]
  - Acuere: no public pricing; emailed terms 19.5% direct hire [acuere/src/lib/automation/email-templates.ts]
  - Arete, PRM: no published prices [live sites]
- Intercompany plan: subs pay Holdings a quarterly IP license fee (typically 10–20% of net revenue) plus a management fee [idoneity-cms/CORPORATE_STRUCTURE.md]

### Product / tech status
- Live custom domains: idoneity-cms.com (Idoneity CMS), acueretalent.com (Acuere). Bidwell, Arete, PRM and Idoneity-EHS are on *.praesidium-holdings.workers.dev [brand wrangler configs; live checks]
- Health 2026-10-18: Bidwell and PRM `/api/health` fail (DB not ok); Idoneity /pricing returns 500; Arete is coming-soon only; EHS portal not hosted [live checks]
- Common stack: Next.js 16 + OpenNext on Cloudflare Workers with Turso/D1. Idoneity-EHS is Python/FastAPI [brand package.json / requirements.txt]
- Commit activity, last 8 days: Acuere heavy (~35 commits); Idoneity CMS/EHS structure cleanup and config only; none in Bidwell, Arete, PRM, leadgen or praesidium-brands [runs/2026-10-18/gitlog-*.txt]
- Shared owner console (single UI, books separated by `entity_id`): corporate vault, compliance calendar, audit log, AP, AR, 9-step close, cash-basis P&L, CSV exports [praesidium-brands/docs/OWNER_CONSOLE.md]

### Sales & marketing activity
- Brand-family footer mirrored across sites to cross-promote [praesidium-brands/README.md]. Acuere removed it 2026-10-17; Bidwell/PRM footers show Arete as "coming-soon" [acuere gitlog; bidwell/prm brand-family-footer.tsx]
- Outbound is paused or blocked at every brand: Idoneity HOLD since 2026-08-08; Acuere COLD_OUTREACH off and no email-provider key; EHS mail blocked; LinkedIn company pages not created [leadgen/HOLD; acuere/CLAUDE.md; idoneity-ehs/deploy/GO-LIVE.md]
- PRM is positioned as the design-partner/referral channel for Idoneity [idoneity-cms/CORPORATE_STRUCTURE.md]

### Competitors
- (no source found) at the holding-company level — see the per-brand files

### Key tools & systems
- Cloudflare (Workers, D1, R2, Email Routing, Workers AI), Turso, Stripe (planned/partial), Resend (keys missing at several brands), Anthropic (metered via `trackedMessagesCreate` / `ai_usage` ledger) [brand CLAUDE.md / wrangler configs]
- GitHub org praesidium-holdings [praesidium-brands/README.md]
- Owner console route list: /admin/corporate, /admin/calendar, /admin/audit, /admin/ap, /autonomy/ar, /admin/close, /admin/reports [praesidium-brands/docs/OWNER_CONSOLE.md]
- Accounting: QuickBooks Online or Xero planned [idoneity-cms/CORPORATE_STRUCTURE.md]

### Regulatory / compliance notes
- Sunbiz (looked up 2026-09-13):
  - PRAESIDIUM HOLDINGS LLC filed 2026-07-14; no EIN on record; first annual report due by 2027-05-01
  - IDONEITY LIMITED LIABILITY COMPANY filed 2026-07-17 (ownership to confirm)
  - PROMETHEUS HOLDINGS LLC (PRM, renamed 2026-07-16) filed 2025-04-28, two managing members
  - Idoneity Holdings, Bidwell/Idoneity Marketplace, Arete Lyceum, Acuere Talent not filed
  [idoneity-cms/docs/COMPLIANCE_CALENDAR.md]
- README presents the full sub-entity tree as if it exists, and both the Acuere and PRM sites print entity names in copyright lines (Acuere Talent, LLC; Praesidium Holdings, LLC) that don't match Sunbiz [praesidium-brands/README.md; https://acueretalent.com; prm footer]
- FL annual report window is 1 Jan–1 May; $400 late fee after 1 May; administrative dissolution after the third Friday of September [idoneity-cms/docs/COMPLIANCE_CALENDAR.md]
- Structure decision: FL-only "Path B", Praesidium as a single-member LLC, with a Path C migration trigger. Attorney + CPA review is recommended before signing intercompany agreements [idoneity-cms/CORPORATE_STRUCTURE.md]
- Kids-FICA exemption posture depends on PRM staying a separate disregarded/peer entity. The Sunbiz two-member record conflicts with this [prm/docs/OWNER_CONSOLE.md; idoneity-cms/docs/COMPLIANCE_CALENDAR.md]
- Industry: OSHA 2026 penalties unchanged from 2025; federal heat rule not final [https://www.osha.gov/memos/2026-05-21/2026-annual-adjustments-osha-civil-penalties; https://www.ogletree.com/insights-resources/blog-posts/oshas-heat-program-to-expire-while-heat-standard-stalls/]

## Changed this week
- First sync — no previous context file existed, so there is no baseline to compare against. All facts above are new.
- No praesidium-brands commits in the last 8 days [gitlog-praesidium.txt]
- Portfolio this week: Acuere had a large release (see acuere file); Acuere dropped the shared brand-family footer [gitlog-acuere.txt]

## Open questions for Tyler
- Which entities are actually filed today, and which are still planned? Sunbiz shows Praesidium, Idoneity and PRM only. Should the README and site copyright lines stop naming unfiled LLCs until they exist?
- PRM's Sunbiz record ("Prometheus Holdings LLC") lists two managing members. Is that intended? It affects the kids-FICA exemption and partnership-return treatment, so it should go to the CPA.
- Which brand gets focus and money this quarter? Only Acuere had real commit activity this week, and outbound is paused everywhere.
- What portfolio-level targets should the CFO and analyst skills track (revenue, cash runway, first-customer dates)?
- Is the Path B structure (Praesidium → Idoneity Holdings → subs, PRM as a peer) still the plan? Has the attorney/CPA review or the founder IP assignment happened?
