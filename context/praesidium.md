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
## Auto facts (synced 2026-10-25)
### What it is / offer
- Praesidium Holdings, LLC is a Florida holding company for "a family of operating brands covering the workforce-safety, compliance, learning, and hiring stack" [praesidium-brands/README.md]
- Brands: Idoneity (contractor-management SaaS + EHS module), Bidwell (bid marketplace), Arete Lyceum (safety/technical LMS), Acuere Talent (specialist recruiting), Prometheus Risk Management (OSHA/safety consulting, Viera FL) [praesidium-brands/README.md]
- Planned structure: Praesidium → Idoneity Holdings, LLC → Idoneity SaaS / Idoneity Marketplace (Bidwell) / Arete / Acuere; PRM alongside as a peer. Praesidium has no customer revenue; Idoneity Holdings is meant to own brand/IP and take license + management fees [praesidium-brands/README.md; idoneity-cms/CORPORATE_STRUCTURE.md]
- Each brand keeps its own users, database and billing; interop via API and data portability [praesidium-brands/README.md]
- No public Praesidium website; the holdings console runs as worker `praesidium-admin` (owner-only) [idoneity-cms/CLAUDE.md; praesidium-brands/docs/OWNER_CONSOLE.md]

### Customers & market
- Holding company has no customers [idoneity-cms/CORPORATE_STRUCTURE.md]
- Portfolio roll-up, still no paying customers recorded at any brand:
  - Idoneity: $0 revenue, no employees [idoneity-cms/docs/COMPLIANCE_CALENDAR.md]
  - Acuere: 0 placements, 1 application on record [acuere/data/analytics/latest.json]
  - Bidwell, PRM: counts unavailable — prod DB health checks failing for a second week; Arete is a waitlist [live /api/health checks 2026-10-25]
- Common market: industrial/construction contractors and the operators who hire them, Florida-first [brand repos]

### Pricing (as published)
- Holding company: n/a
- Roll-up:
  - Idoneity CMS: from $1,050/yr; /pricing page still returns 500 [https://idoneity-cms.com]
  - Idoneity-EHS: from $595/site/month [https://idoneity-ehs.praesidium-holdings.workers.dev/]
  - Bidwell: 7.25% → 5% → 3% success fee on wins, 3.5% prepay lane [https://bidwell.praesidium-holdings.workers.dev/]
  - Acuere: no public pricing; employer-email terms line 19.5% direct hire [acuere/CLAUDE.md]
  - Arete, PRM: no published prices [live sites]
- Intercompany plan: subs pay Holdings a quarterly IP license fee (typically 10–20% of net revenue) plus a management fee [idoneity-cms/CORPORATE_STRUCTURE.md]

### Product / tech status
- Live custom domains: idoneity-cms.com, acueretalent.com. Bidwell, Arete, PRM and Idoneity-EHS on *.praesidium-holdings.workers.dev; idoneity-ehs.com and prometheusriskmgmt.com still unreachable [live checks 2026-10-25]
- **Database platform shift:** Tyler decided 2026-10-25 that "all data lives in Cloudflare; stay off paid Turso." Turso reads are quota-blocked until the Nov 1 reset. Idoneity CMS has a D1 cutover prepared but not live [idoneity-cms/.claude/worktrees/d1-port/docs/D1_CUTOVER.md]. Acuere is already on D1 (since 10-17) [acuere/CLAUDE.md]. Bidwell, PRM and Arete still use Turso, and Arete shares Idoneity's DB [brand wrangler/db configs]
- Health 2026-10-25: Bidwell and PRM `/api/health` fail (DB not ok); Idoneity /api/health ok:false and /pricing 500; Arete coming-soon only; EHS portal not hosted [live checks]
- Common stack: Next.js 16 + OpenNext on Cloudflare Workers; Idoneity-EHS is Python/FastAPI [brand package.json / requirements.txt]
- Commit activity 10-18 → 10-25: Acuere 13 commits since 10-19 (cloud desk on Cloudflare, candidate portal, Thursday invoicing); Idoneity-EHS 8 marketing-doc autosaves plus daily-builder branches; idoneity-cms 1 autosave; praesidium-brands 1 autosave (the 10-18 context write); none in Bidwell, Arete, PRM, leadgen [runs/2026-10-25/gitlog-*.txt]
- Shared owner console (books separated by `entity_id`): corporate vault, compliance calendar, audit log, AP, AR, 9-step close, cash-basis P&L, CSV exports [praesidium-brands/docs/OWNER_CONSOLE.md]

### Sales & marketing activity
- Outbound paused everywhere: Idoneity leadgen HOLD since 2026-08-08 (hourly runs halted, latest 2026-10-25); Acuere COLD_OUTREACH last set off and no email-provider key; EHS mail blocked; LinkedIn company pages not created [leadgen/out/_campaign_log.txt; acuere/CLAUDE.md; idoneity-ehs/deploy/GO-LIVE.md]
- EHS marketing desk keeps drafting (six packages awaiting review; 300A tools aimed at the Jan–Feb posting season) [idoneity-ehs/marketing/proposals/2026-10-20/SUMMARY.md]
- Brand-family footer mirrored across sites; Acuere still without it; Bidwell/PRM show Arete as "coming-soon" [praesidium-brands/README.md; live acueretalent.com]
- PRM positioned as design-partner/referral channel for Idoneity [idoneity-cms/CORPORATE_STRUCTURE.md]

### Competitors
- (no source found) at the holding-company level — see the per-brand files

### Key tools & systems
- Cloudflare (Workers, D1, R2, Email Routing, Workers AI, Workflows, Browser Rendering), Turso (being phased out per 10-25 decision), Stripe (planned/partial), Resend (keys missing at several brands), Anthropic (CMS/Bidwell/PRM; Acuere moved to Workers AI) [brand CLAUDE.md / wrangler configs; D1_CUTOVER.md]
- Shared R2 bucket `praesidium-db-backups` for offsite DB dumps (Acuere uses it) [acuere/CLAUDE.md]
- GitHub org praesidium-holdings (Acuere excluded from GitHub by decision) [praesidium-brands/README.md; acuere/CLAUDE.md]
- Accounting: QuickBooks Online or Xero planned [idoneity-cms/CORPORATE_STRUCTURE.md]

### Regulatory / compliance notes
- Sunbiz (looked up 2026-09-13):
  - PRAESIDIUM HOLDINGS LLC filed 2026-07-14; first annual report due by 2027-05-01
  - IDONEITY LIMITED LIABILITY COMPANY filed 2026-07-17 (ownership to confirm)
  - PROMETHEUS HOLDINGS LLC (PRM, renamed 2026-07-16) filed 2025-04-28, two managing members
  - Idoneity Holdings, Bidwell/Idoneity Marketplace, Arete Lyceum, Acuere Talent not filed
  [idoneity-cms/docs/COMPLIANCE_CALENDAR.md]
- Acuere's live footer still prints "Acuere Talent, LLC" (unfiled) [https://acueretalent.com]
- FL annual report window 1 Jan–1 May; $400 late fee after 1 May [idoneity-cms/docs/COMPLIANCE_CALENDAR.md]
- Structure: FL-only "Path B", Praesidium single-member; attorney + CPA review recommended before intercompany agreements [idoneity-cms/CORPORATE_STRUCTURE.md]
- Kids-FICA exemption depends on PRM staying a separate disregarded/peer entity; Sunbiz two-member record conflicts [prm/docs/OWNER_CONSOLE.md; idoneity-cms/docs/TODO.md]
- Industry: OSHA 2026 penalties unchanged from 2025; federal heat rule not final; heat NEP status conflicting across sources; April 2026 NPRM to drop the fixed-ladder fall-arrest deadline [https://www.osha.gov/memos/2026-05-21/2026-annual-adjustments-osha-civil-penalties; https://www.jdsupra.com/legalnews/what-s-the-status-of-osha-s-heat-stress-9226045/; https://www.jdsupra.com/topics/rulemaking-process/osh-act/osha/]

## Changed this week
- NEW portfolio decision (2026-10-25): "all data lives in Cloudflare; stay off paid Turso." Turso reads are quota-blocked until Nov 1. The Idoneity D1 cutover is prepared but not live. Bidwell, PRM and Arete are still on Turso [idoneity-cms/.claude/worktrees/d1-port/docs/D1_CUTOVER.md]
- Bidwell and PRM prod DBs have now failed health checks for a second straight week. Idoneity /pricing is still 500 [live checks 2026-10-25]
- Acuere moved most of its desk onto Cloudflare (12 cloud jobs) and added a candidate portal [gitlog-acuere.txt]
- EHS: pricing-page fix and new "whole price" page are in the repo but not deployed. Marketing drafted a 300A worksheet tool [idoneity-ehs]
- praesidium-brands: only the 2026-10-18 context-file autosave; no other changes [gitlog-praesidium.txt]

## Open questions for Tyler
- Does "stay off paid Turso" apply to every brand? Bidwell and PRM DBs have failed for two weeks and Arete shares Idoneity's Turso DB. Should they all move to D1, and in what order?
- Which entities are actually filed today, and which are still planned? Sunbiz shows Praesidium, Idoneity and PRM only. Should the README and site copyright lines (e.g. "Acuere Talent, LLC") stop naming unfiled LLCs?
- PRM's Sunbiz record lists two managing members, which conflicts with the single-member/kids-FICA plan. Has this gone to the CPA?
- Which brand gets focus and money this quarter? Acuere had nearly all the build activity, and outbound is paused everywhere. What portfolio targets (revenue, runway, first-customer dates) should the CFO/analyst skills track?
- Is the Path B structure still the plan? Has the attorney/CPA review or the founder IP assignment happened?
