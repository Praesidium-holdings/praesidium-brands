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
## Auto facts (synced 2026-11-08)
### What it is / offer
- Praesidium Holdings, LLC is a Florida holding company for "a family of operating brands covering the workforce-safety, compliance, learning, and hiring stack" [praesidium-brands/README.md]
- Brands: Idoneity (contractor-management SaaS + EHS module), Bidwell (bid marketplace), Arete Lyceum (safety/technical LMS), Acuere Talent (specialist recruiting), Prometheus Risk Management (OSHA/safety consulting, Viera FL) [praesidium-brands/README.md]
- Planned structure: Praesidium → Idoneity Holdings, LLC → Idoneity SaaS / Idoneity Marketplace (Bidwell) / Arete / Acuere, with PRM alongside as a peer. Praesidium has no customer revenue; Idoneity Holdings is meant to own the brand/IP and take license + management fees [praesidium-brands/README.md; idoneity-cms/CORPORATE_STRUCTURE.md]
- Each brand keeps its own users, database and billing; brands interoperate via API and data portability [praesidium-brands/README.md]
- No public Praesidium website. The holdings console runs as worker `praesidium-admin` (owner-only) [idoneity-cms/CLAUDE.md; praesidium-brands/docs/OWNER_CONSOLE.md]

### Customers & market
- The holding company has no customers [idoneity-cms/CORPORATE_STRUCTURE.md]
- Portfolio roll-up: still no paying customers recorded at any brand [runs/2026-11-08/*.auto.md]
  - Idoneity: $0 revenue, no employees
  - Acuere: 0 placements, 0 active contracts, 1 candidate; 16,717 sourced postings; 39 in-lane pitches queued (est. fees $1.47M), none sent
  - Bidwell: counts can't be read (prod DB down 11-08)
  - PRM: counts can't be read (prod DB down 4 weeks running)
  - Arete: coming-soon page with an interest-list form only
- Common market: industrial and construction contractors and the operators who hire them, Florida first [brand repos]

### Pricing (as published)
- Holding company: n/a
- Roll-up:
  - Idoneity CMS: from $1,050/yr; the /pricing page is 500 again as of 2026-11-08 [https://idoneity-cms.com/pricing]
  - Idoneity-EHS: from $595/site/month; the live page still shows the old 25-site slider with 15%/28% discounts [https://idoneity-ehs.praesidium-holdings.workers.dev/pricing]
  - Bidwell: success fee of 7.25% → 5% → 3% on wins, plus a 3.5% prepay lane [https://bidwell.praesidium-holdings.workers.dev/]
  - Acuere: no public pricing [https://acueretalent.com]
  - Arete, PRM: no published prices [live sites]
- Intercompany plan: subs pay Holdings a quarterly IP license fee (typically 10–20% of net revenue) plus a management fee [idoneity-cms/CORPORATE_STRUCTURE.md]

### Product / tech status
- Live custom domains: idoneity-cms.com and acueretalent.com. Bidwell, Arete, PRM and Idoneity-EHS run on *.praesidium-holdings.workers.dev; idoneity-ehs.com and prometheusriskmgmt.com still don't resolve [live checks 2026-11-08]
- Health 2026-11-08 ~22:00 UTC [live checks]:
  - **Idoneity CMS: ok:false, /pricing 500** (was healthy on 11-01)
  - **Bidwell: ok:false, DB not ok, /opportunities 500** (was healthy on 11-01)
  - PRM: ok:false, DB down, fourth weekly check in a row
  - Acuere: ok:true on D1 (migration 0029)
  - Arete: coming-soon page returns 200; no health route
- All three Turso-backed brands are failing; the only D1 brand (Acuere) is healthy. The Turso quota is suspected but not confirmed [live checks; D1_CUTOVER.md]
- Database decision of 2026-10-25: "all data lives in Cloudflare; stay off paid Turso" [D1_CUTOVER.md]
  - Idoneity's D1 cutover is still not live; in the d1-port worktree, the migration runner gained D1 support (edited 11-05) [idoneity-cms/wrangler.jsonc; d1-port/scripts/apply-migrations.mjs]
  - Bidwell, PRM and Arete are still on Turso, and Arete shares Idoneity's DB [brand configs]
- Idoneity-EHS: gate back to PASS on 11-07 and 11-08; daily builder branches still not merged [idoneity-ehs/.claude/daily-builder/reports/]
- Acuere: deploy-gate backtest failing (98/101) and the BD pitch-drafts step failing [acuere/data/desk-status.json]
- Common stack: Next.js 16 + OpenNext on Cloudflare Workers; Idoneity-EHS is Python/FastAPI [brand package.json / requirements.txt]
- Commits 11-01 → 11-08 [gitlog-*.txt]:
  - idoneity-ehs: marketing-doc autosaves on 11-03, plus daily-builder branches
  - praesidium-brands: the 11-02 context sync
  - none in idoneity-cms, leadgen, Bidwell, Arete, Acuere or PRM
- Shared owner console (books separated by `entity_id`): corporate vault, compliance calendar, audit log, AP, AR, 9-step close, cash-basis P&L, CSV exports [praesidium-brands/docs/OWNER_CONSOLE.md]

### Sales & marketing activity
- Outbound is paused everywhere [runs/2026-11-08/idoneity.auto.md; acuere.auto.md]:
  - Idoneity leadgen: HOLD since 2026-08-08; opt-out sync ran clean all week
  - Acuere: 40 approved emails held because no email provider is set
- Idoneity-EHS desk: LinkedIn document-post pipeline drafted, with a 4-week calendar from 10 Nov and 5 posts ready. Waiting on Tyler to decide who posts and to approve. Unbuilt backlog is now 8 packages [idoneity-ehs/marketing/proposals/2026-11-03/SUMMARY.md]
- No LinkedIn Company Page or app exists for Idoneity or Acuere [leadgen/LINKEDIN-CAMPAIGN.md; acuere desk-status.json]
- Dead contact paths [live sites 2026-11-08]:
  - Bidwell's "Book a walkthrough" still opens an email to hello@bidwell.com
  - PRM's only contact runs through the dead prometheusriskmgmt.com domain
- PRM is positioned as a design-partner/referral channel for Idoneity [idoneity-cms/CORPORATE_STRUCTURE.md]

### Competitors
- (no source found) at the holding-company level; see the per-brand files

### Key tools & systems
- Cloudflare: Workers, D1, R2, Email Routing, Workers AI, Workflows, Browser Rendering [brand CLAUDE.md / wrangler configs]
- Turso is being phased out under the 10-25 decision, but is still prod for 3 brands [brand configs]
- Stripe (planned/partial) [brand repos]
- Resend: keys missing at several brands [brand configs; live health endpoints]
- AI providers [brand configs; live health endpoints]:
  - Anthropic at CMS, Bidwell and PRM; keys unset on live Bidwell and PRM
  - Acuere uses Workers AI
- Shared R2 bucket `praesidium-db-backups` for offsite DB dumps [acuere/CLAUDE.md]
- GitHub org praesidium-holdings (Acuere excluded by decision) [praesidium-brands/README.md; acuere/CLAUDE.md]
- Taplio connected for LinkedIn; publishing stays with Tyler [idoneity-ehs/marketing/proposals/2026-11-03/SUMMARY.md]
- Accounting: QuickBooks Online or Xero planned [idoneity-cms/CORPORATE_STRUCTURE.md]

### Regulatory / compliance notes
- Sunbiz (looked up 2026-09-13) [idoneity-cms/docs/COMPLIANCE_CALENDAR.md]:
  - PRAESIDIUM HOLDINGS LLC filed 2026-07-14; first annual report due by 2027-05-01
  - IDONEITY LIMITED LIABILITY COMPANY filed 2026-07-17 (ownership to confirm)
  - PROMETHEUS HOLDINGS LLC (PRM, renamed 2026-07-16) filed 2025-04-28, two managing members
  - Idoneity Holdings, Bidwell/Idoneity Marketplace, Arete Lyceum and Acuere Talent are not filed
- Live footers: Acuere's still prints "Acuere Talent, LLC" (unfiled); Arete's prints the filed "Praesidium Holdings, LLC" [https://acueretalent.com; https://arete.praesidium-holdings.workers.dev, 2026-11-08]
- FL annual report window: 1 Jan – 1 May; $400 late fee after 1 May [idoneity-cms/docs/COMPLIANCE_CALENDAR.md]
- Structure: FL-only "Path B", Praesidium single-member; attorney + CPA review recommended before intercompany agreements [idoneity-cms/CORPORATE_STRUCTURE.md]
- The kids-FICA exemption depends on PRM staying a separate disregarded/peer entity; the two-member Sunbiz record conflicts with that [prm/docs/OWNER_CONSOLE.md; idoneity-cms/docs/TODO.md]
- Industry:
  - Federal heat rule still not final, with no target date (House hearing early September 2026); revised heat NEP from 2026-04-10 in force [https://jjkellercompliancenetwork.com/news/oshas-proposed-heat-rule-debated-during-house-subcommittee-hearing; mondaq 1778956]
  - OSHA subpoena final rule expected November 2026 [J.J. Keller via WebSearch 2026-11-08]
  - 2026 OSHA penalties unchanged from 2025; January adjustment due [https://www.osha.gov/memos/2026-05-21/2026-annual-adjustments-osha-civil-penalties]
- Employment:
  - Florida requires reporting contractors paid $600+ in a year to the Dept. of Revenue [constangy.com]
  - DOL independent-contractor rule: proposed 2026-02-26, comments closed 2026-04-28, no final rule confirmed as of 2026-11-08 [https://www.jdsupra.com/legalnews/dol-publishes-proposed-rule-to-rescind-1320616/; WebSearch]

## Changed this week
- **All three Turso-backed brands are failing again** (Idoneity CMS, Bidwell, PRM), one week after the 11-01 reset brought Idoneity and Bidwell back. Acuere (D1) is healthy. Idoneity /pricing and Bidwell /opportunities are both 500 [live checks 2026-11-08]
- Idoneity D1 cutover still not live; the migration runner gained a D1 target in the d1-port worktree (11-05) [idoneity-cms]
- Idoneity-EHS gate back to green (11-07, 11-08). The marketing desk drafted a LinkedIn document-post pipeline with 5 posts ready from 10 Nov, waiting on Tyler [idoneity-ehs]
- Acuere: pitch-drafts step and deploy-gate backtest failing; 40 approved emails held for no email provider; 1 candidate in the pool [acuere/data/desk-status.json]
- Regulatory: no final DOL independent-contractor rule found (target was October); no heat rule action; OSHA subpoena rule expected in November [WebSearch]
- Commits this week: idoneity-ehs docs/builder only, plus the 11-02 context sync; nothing in idoneity-cms, leadgen, Bidwell, Arete, Acuere or PRM [gitlog-*.txt]

## Open questions for Tyler
- Idoneity, Bidwell and PRM, all on Turso, are down again a week after the reset, while Acuere on D1 is fine. Do you want a D1 migration sprint for all three now? In what order: Idoneity + Arete first, then Bidwell, then PRM?
- Which brand gets focus and money this quarter? What portfolio targets should the CFO and analyst skills track (revenue, runway, first-customer dates)?
- LinkedIn is the one channel both Idoneity-EHS and Acuere are waiting on, and it needs Company Pages. Should the company pages be created, and under which entity names (filed vs. unfiled)?
- Entities: Sunbiz shows only Praesidium, Idoneity and PRM. Should Acuere's footer stop printing "Acuere Talent, LLC", or is that entity being filed?
- PRM's two-member Sunbiz record vs. the single-member/kids-FICA plan, and the Path B attorney/CPA review: has either been done?
