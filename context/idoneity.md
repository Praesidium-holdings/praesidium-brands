# idoneity — company context
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
- **Idoneity CMS** — contractor management: prequalification (PQF), training-record competency tracking, vendor risk ranking. Tagline: "Contractor management, without the ISN price tag" [idoneity-cms/README.md]
- Four modules: Risk Engine, Portable PQF, Insurance/COI, Site-Specific Safety. One flat annual fee, paid by either side [idoneity-cms/marketing/ads/launch-pack/idoneity-ad-copy.md]
- Two-sided: contractors pay by workforce size, hiring clients by number of contractors managed [idoneity-cms/src/lib/pricing-tiers.ts]
- Live homepage: "Contractor management, made simple"; "from $1,050 a year"; EHS shown as "Soon" [https://idoneity-cms.com — 200 on 2026-10-25]
- **Idoneity-EHS** — per-site EHS platform: incidents/investigation, CAPA, inspections, observations, permits to work, PSM (MOC/PSSR, PHA, LOPA, SIL, bow-tie, PSE tiers), chemicals + Tier II, waste accumulation clocks, obligations, audit trail; plus a back office (double-entry ledger, billing, funnel state machine, scheduled agents) [idoneity-ehs/README.md]
- EHS tiers: Essential, Compliance, Complete, Assurance. Assurance adds ISO 9001/14001/45001 as one integrated management system [idoneity-ehs/ledger/billing.py; site/public/pricing.html]
- EHS pitch: "the sticker is the whole price" — published per-site price, first 99 users per site included, renewal cap in contract [idoneity-ehs/sales/talk-track.md]
- Marketplace success fee is tracked but not billed; collection waits on regulatory review [idoneity-cms/src/lib/pricing-tiers.ts; CORPORATE_STRUCTURE.md §3]

### Customers & market
- CMS buyers: EHS, safety and procurement managers at industrial firms; secondary: contractors tired of re-qualifying on every client portal [idoneity-cms/marketing/ads/launch-pack/idoneity-ad-copy.md]
- LinkedIn targeting: Construction, Oil & Gas, Manufacturing, Utilities; 51–1,000 employees [idoneity-cms/marketing/ads/launch-pack/idoneity-ad-copy.md]
- Outbound lead universe: EPA TRI facilities (manufacturing, mining, utilities, chemicals, petroleum, hazardous waste) [leadgen/PLAYBOOK.md]
- EHS buyer: safety/EHS owner at an operator with 3–30 sites and 200–5,000 workers. Published pricing is for sites up to 250 employees [idoneity-ehs/sales/talk-track.md; ledger/billing.py]
- No customers recorded: compliance calendar notes $0 revenue and no employees; EHS outputs run on seeded demo data [idoneity-cms/docs/COMPLIANCE_CALENDAR.md; idoneity-ehs/AGENTS.md]
- CMS prod data snapshot (2026-10-10, loaded into D1): 150 tables, 3,640 rows — no customer count derived [idoneity-cms/.claude/worktrees/d1-port/docs/D1_CUTOVER.md]
- Standing rule (2026-09-13): no customer counts, testimonials or client-implying copy until real customers exist [idoneity-cms/docs/TODO.md]

### Pricing (as published)
- CMS repo card (2026 base, after the 35% cut on 2026-09-28), annual:
  - Contractor tiers: Solo (1–5 workers) $1,050 · Small (6–25) $2,100 · Mid-market (26–49) $3,050 · Large (50–149) $5,700 · National (150–499) $7,800 · National+ (500–1,999) $15,600 · Enterprise (2,000+) contact sales
  - Hiring-client tiers: Starter (≤5 contractors) $4,700 · Small (6–10) $9,450 · Growth (11–14) $13,150 · Large (15–20) $18,700 · National (21–30) contact/MSA · Enterprise (31+) contact
  [idoneity-cms/src/lib/pricing-tiers.ts]
- CMS fees/add-ons: onboarding $975 one-time; Training Records Portal $1,250/yr (hiring client); Orientation Hosting $650/yr; video price stored in DB (seed $499 vs $199 live noted as drift) [idoneity-cms/src/lib/pricing-tiers.ts]
- CMS promo "First 500": no onboarding fee for the first 500 subscriptions. Price locked at signup year; new-signup list rises 5% each January [idoneity-cms/src/lib/pricing-tiers.ts]
- CMS live: **/pricing still returns HTTP 500** (re-checked 2026-10-25). Homepage shows "from $1,050 a year" [https://idoneity-cms.com/pricing; https://idoneity-cms.com]
- EHS per site per month: Essential $595 (setup $495) · Compliance $995 (setup $995) · Complete $1,450 (setup $2,495) · Assurance $1,450 + $650 per ISO standard (setup $4,995) [idoneity-ehs/ledger/billing.py; site/public/pricing.html; live /pricing]
- EHS terms: first 99 users per site included; above that one 15% size band + $4/user/mo. List price +7% each January; existing-customer increase capped at 4.5%; 3-yr terms step down 3%/yr and 5-yr terms 5%/yr; 3% off for CMS customers [idoneity-ehs/ledger/billing.py; site/public/pricing.html]
- EHS multi-site: repo pricing page now matches code — slider 1–3 sites, multi-site discount 0. **Live page still shows a 1–25 site slider with 15% off >5 sites and 28% off >10 sites** (repo change not deployed) [idoneity-ehs/site/public/pricing.html; https://idoneity-ehs.praesidium-holdings.workers.dev/pricing, checked 2026-10-25]
- EHS new page "The whole price — Five years. Every line of it." exists in repo (whole-price.html) but returns 404 live [idoneity-ehs/site/public/whole-price.html; live check 2026-10-25]
- EHS visitor/site access add-on $525/site/mo, included in Complete/Assurance — in code only [idoneity-ehs/ledger/billing.py]

### Product / tech status
- CMS stack: Next.js 16.3.5, React 19.3, TypeScript 7 (pinned 7.0.2 on the buildout branch), Drizzle, Turso/libSQL, Stripe, Tailwind 4; Cloudflare Workers via OpenNext. Worker `idoneity` on idoneity-cms.com + www, plus `praesidium-admin` and `idoneity-dev` [idoneity-cms/package.json; wrangler.jsonc; .git/logs/HEAD]
- CMS local checkout moved from `feat/cms-buildout-1005` back to `main` on 2026-10-25; buildout branch still exists, not shown as merged [idoneity-cms/.git/logs/HEAD; .git/refs/heads/feat]
- **Turso → Cloudflare D1 cutover prepared 2026-10-25 (worktree `d1-port`), not live.** Tyler decision: "all data lives in Cloudflare; stay off paid Turso." D1 `idoneity-cms-prod` holds the 2026-10-10 backup; Turso reads are quota-blocked until the Nov 1 reset; rows written to Turso after 10-10 are not in D1 and must be reconciled later. Cutover = set `DB_BACKEND=d1` + migrations 0110/0111 + deploy, Tyler-only. Local tests 484/0 pass; remote D1, deployed worker and D1 100-parameter / LIKE-length limits not verified [idoneity-cms/.claude/worktrees/d1-port/docs/D1_CUTOVER.md]
- CMS live /api/health returns `{"ok":false}` (detail now behind the jobs secret) [https://idoneity-cms.com/api/health, 2026-10-25; idoneity-cms/docs/TODO.md]
- CMS Tyler-only TODOs still open: run prod migrations (0104/0106/0107/0108); re-enter RESEND_API_KEY / IDONEITY_OUTBOUND_UNLOCK; rotate exposed secrets; verify prod AI key; find the other deployer [idoneity-cms/docs/TODO.md]
- CMS open security items: SEC-3b (MFA secret plaintext until MFA_SECRET_KEY set), SEC-11 (full CSP), ARC-1..3, PERF-1/2/4/6 [idoneity-cms/docs/TODO.md]
- EHS stack: Python 3.9, FastAPI, Jinja2, SQLite (Postgres-portable) [idoneity-ehs/requirements.txt; CLAUDE.md]
- EHS live = marketing site only (Worker at idoneity-ehs.praesidium-holdings.workers.dev; leads → D1). Portal/app has no host; idoneity-ehs.com still does not resolve (2026-10-25) [idoneity-ehs/deploy/GO-LIVE.md; live check]
- EHS daily builder: one item per day on `ehs/daily-<date>` branches; 2026-10-25 item = structure check for rules imports; full gate PASS (31 suites). Branches 10-19 → 10-24 are not merged into the base `feat/ehs-top10-raci-gap`, so dependent backlog items keep getting skipped [idoneity-ehs/.claude/daily-builder/reports/2026-10-25.md; backlog.md]
- EHS self-identified gaps: no mobile/offline, no CMMS integration, no bulk import, no MOC approval chain, no permit-conflict/LOTO object, no direct OSHA ITA submission [idoneity-ehs/concept/SALES-BATTLECARDS.md §5.1]
- EHS 300A product gaps found 10-20: in-app 300A view shows only the current calendar year, company-wide, on estimated hours; no "annual average employees" box [idoneity-ehs/marketing/proposals/2026-10-20/SUMMARY.md]

### Sales & marketing activity
- Outbound **HOLD** still in force (since 2026-08-08). Campaign job runs hourly and logs "HALTED: a HOLD file exists" (latest 2026-10-25 16:26) [leadgen/HOLD; leadgen/out/_campaign_log.txt]
- Only send to date: 150 emails to Florida contacts on 2026-08-08 [leadgen/campaign_state.json]
- Daily lead job last ran 2026-10-25 07:30 [leadgen/heartbeat.json]
- Opt-out sync (10-23 → 10-25) flags 1 opt-out record that matches no contact held — log says check before the next send [leadgen/out/_optouts.log]
- About 10,830 contacts total; Florida had 727 sendable; 12 foreign/vanity-domain rows await decision [leadgen/RULES.md; idoneity-cms/docs/TODO.md]
- Planned cadence: Thursdays 08:01 recipient-local, 5 states/week, max 150 per state; stop at 3% bounce / 0.1% complaint [leadgen/RULES.md]
- 3-email sequence (Day 0/4/11) still marked DRAFT [leadgen/SEQUENCE.md]
- LinkedIn blocked on creating the Company Page; audiences ready (2,808 companies / 4,646 contacts in FL, TX, LA, GA, NC); plan $20–30/day [leadgen/LINKEDIN-CAMPAIGN.md]
- Meta/LinkedIn ad pack ready; 10-second video blocked on Replicate credit [idoneity-cms/marketing/ads/launch-pack/idoneity-ad-copy.md]
- On-site lead capture: /scorecard, "learn more" popup, lead triage queue; nothing emailed to leads [idoneity-cms/docs/TODO.md]
- EHS: leads land in D1, nothing else happens (no email/login). Weekly desk drafted tool 3c, a Form 300A worksheet (honesty design, page copy, 18-fixture spec, 8-slide LinkedIn deck planned for 2027-01-04). Six drafted-but-unbuilt packages now waiting on Tyler (speed-to-lead, calendar, 3a, 3b, 3c, calendar deck); recommendation is to build 3a–3c by mid-December for the Jan–Feb 300A season. Next increment: weekly OSHA/EPA regulatory digest [idoneity-ehs/marketing/proposals/2026-10-20/SUMMARY.md]

### Competitors
- CMS: ISN, Avetta, Veriforce [praesidium-brands/README.md; idoneity-cms/README.md]. Internal-only price refs (secondary sources): ISN ~$875+/sub/yr, Avetta ~$450–900/sub/yr [idoneity-cms/docs/TODO.md]
- EHS (Capterra top 10, Aug 2026): SafetyCulture, Novara Flex, HSI Donesafe, SafetyAmp, SafetyIQ, Dakota ProActivity, VelocityEHS, Cority, Benchmark Gensuite, Intelex. Enterprise: Enablon, Sphera, ProcessMAP/UL, Origami Risk, Ideagen, Evotix, Quentic [idoneity-ehs/concept/COMPETITIVE-RESEARCH.md]
- EHS sourced price points: SafetyIQ $2,500/yr; SafetyAmp $4,800/yr; SafetyCulture $24/seat/mo; Intelex $44/user/mo (25-user min); VelocityEHS $1,455/yr [idoneity-ehs/concept/SALES-BATTLECARDS.md §3]
- EHS pricing page compares against unnamed categories only ("Enterprise EHS suites $100,000+", "Quality-management platforms $15,000–$100,000+") [idoneity-ehs/site/public/pricing.html]
- Rule: never name competitors or their prices in public copy [leadgen/RULES.md §7; idoneity-ehs/CLAUDE.md]

### Key tools & systems
- Cloudflare: Workers, R2 (nightly backups), Email Routing, D1 (EHS leads; `idoneity-cms-prod` staged for the CMS cutover); Turso `idoneity-prod` (reads quota-blocked until Nov 1); Stripe; Resend; Anthropic usage ledger with `AI_DISABLED` kill switch [idoneity-cms/CLAUDE.md; d1-port/docs/D1_CUTOVER.md]
- Owner console at /admin hosts every LLC's corporate vault, compliance calendar, AP/AR, close and reports, scoped by `entity_id` [praesidium-brands/docs/OWNER_CONSOLE.md]
- leadgen: Python on launchd, EPA Envirofacts TRI data, suppression file synced from opt-outs [leadgen/PLAYBOOK.md]
- EHS: 26 agents on cron (read/propose only → proposals.json); daily builder + gate script; planned prod host is a VM with systemd timers [idoneity-ehs/AGENTS.md; .claude/daily-builder/; deploy/GO-LIVE.md]
- Replicate (Ideogram) used for design-direction mockups [idoneity-ehs/marketing/proposals/2026-10-20/SUMMARY.md]

### Regulatory / compliance notes
- Sunbiz: "IDONEITY LIMITED LIABILITY COMPANY" filed 2026-07-17, ownership still to confirm. Invoices/quotes hard-code "Idoneity SaaS, LLC". First annual report due by 2027-05-01 [idoneity-cms/docs/COMPLIANCE_CALENDAR.md; docs/TODO.md]
- Idoneity recorded as disregarded, no W-2 wages (migration 0107, not yet applied in prod) [idoneity-cms/docs/TODO.md]
- CAN-SPAM: PO Box postal address; US-only sending; opt-outs honored within 24h [idoneity-cms/docs/EMAIL_SEND_HALT.md; leadgen/RULES.md]
- CMS OSHA mapping: training records map to 1910.146/147/134/1030, 1926 Subpart M, HAZWOPER; no official OSHA 10/30 cards [idoneity-cms/src/lib/pricing-tiers.ts]
- EHS: 1904 recordability computed, 300/300A/301 generated, ITA obligation computed but not filed; PSM 1910.119; RCRA 90-day clock and manifest exception logic; Tier II aggregation [idoneity-ehs/README.md]
- CMS: SOC 2 / ISO 27001 "on the roadmap"; SSO "planned before paid GA" [https://idoneity-cms.com; src/lib/pricing-tiers.ts]
- EHS 300A worksheet design rules: worksheet only, never a postable/certified-looking form; sources checked against the agency's recordkeeping forms package but still need a browser re-read before build [idoneity-ehs/marketing/proposals/2026-10-20/SUMMARY.md]
- EHS legal docs all drafts (Terms under attorney review; no privacy policy; no SOC 2/ISO 27001); EHS uploads go to Anthropic with no customer disclosure yet [idoneity-ehs/legal/]
- OSHA 2026 civil penalties held at 2025 levels ($16,550 serious; $165,514 willful/repeat) [https://www.osha.gov/memos/2026-05-21/2026-annual-adjustments-osha-civil-penalties]
- Federal heat rule still not final; no target date for final action. Reports conflict on whether the heat NEP expired 2026-04-08 or was renewed to 2031 [https://www.jdsupra.com/legalnews/what-s-the-status-of-osha-s-heat-stress-9226045/; https://osha.gov/heat-exposure/rulemaking]
- OSHA NPRM (2026-04-06) proposes removing the compliance deadline for fall-arrest/ladder-safety systems on fixed ladders — relevant to inspection checklists [https://www.jdsupra.com/topics/rulemaking-process/osh-act/osha/]

## Changed this week
- NEW: Turso → Cloudflare D1 cutover for Idoneity CMS prepared 2026-10-25 (worktree `d1-port`). It is ready but not live. Tyler decided to stay off paid Turso. Turso reads are quota-blocked until Nov 1, and D1 holds only the 2026-10-10 snapshot, so there is a data gap to reconcile [idoneity-cms/.claude/worktrees/d1-port/docs/D1_CUTOVER.md]
- CMS local checkout moved from `feat/cms-buildout-1005` to `main` (2026-10-25); the buildout branch pinned TypeScript 7.0.2 (autosave) [idoneity-cms/.git/logs/HEAD]
- Unchanged: idoneity-cms.com/pricing still returns 500. /api/health now returns only `{"ok":false}` [live checks 2026-10-25]
- EHS pricing page in repo now matches the code: max 3 sites, no multi-site discount. **Not deployed**: the live page still offers 15%/28% off and up to 25 sites [idoneity-ehs/site/public/pricing.html vs live /pricing]
- EHS: new "whole price" (5-year cost) page added in the repo. It is not live (404) [idoneity-ehs/site/public/whole-price.html]
- EHS marketing desk (10-20) drafted tool 3c, the Form 300A worksheet. Six drafted packages are now waiting on Tyler, and a mid-December build is recommended for the Jan–Feb 300A season [idoneity-ehs/marketing/proposals/2026-10-20/SUMMARY.md]
- EHS daily builder ran every day 10-19 → 10-25, and the gate passed 10-25. Daily branches since 10-19 are not merged into the base [idoneity-ehs/.claude/daily-builder/]
- leadgen: HOLD still in force. New log warning: 1 opt-out record matches no contact we hold [leadgen/out/_optouts.log]
- Regulatory: sources disagree on whether the OSHA heat NEP was renewed. OSHA also proposed (April 2026) removing the fixed-ladder fall-arrest compliance deadline [WebSearch]
- Condensed: some carry-over bullets were shortened, but no facts were retracted

## Open questions for Tyler
- When will you run the D1 cutover (merge `d1-port` → migrate → set `DB_BACKEND=d1` → deploy)? Will it go before or after Turso's Nov 1 quota reset? And is the 10-10 → now data gap acceptable to reconcile afterwards? /pricing is still returning 500 in the meantime.
- The EHS pricing page in the repo drops the multi-site discount and caps at 3 sites, but the live page still offers 15%/28% off and up to 25 sites. Should the repo version (plus the new "whole price" page) be deployed?
- When should the outbound HOLD (since 2026-08-08) lift? Before any send, the opt-out log has one record that matches no contact, and it needs a decision.
- Which name goes on contracts and invoices: "Idoneity SaaS, LLC" (hard-coded) or the Sunbiz record "Idoneity Limited Liability Company"? Is that Sunbiz record confirmed as yours?
- Do you want the EHS free 300A tools (3a–3c) built by mid-December for the January posting season? And which comes first as a customer, CMS hiring clients or contractors, with what revenue/customer targets this year?
