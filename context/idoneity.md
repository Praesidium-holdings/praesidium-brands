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
## Auto facts (synced 2026-11-08)
### What it is / offer
- **Idoneity CMS**: contractor management, covering prequalification (PQF), training-record competency tracking and vendor risk ranking. Tagline: "Contractor management, without the ISN price tag" [idoneity-cms/README.md]
- Four modules: Risk Engine, Portable PQF, Insurance/COI, Site-Specific Safety. One flat annual fee, paid by either side [idoneity-cms/marketing/ads/launch-pack/idoneity-ad-copy.md]
- Two-sided pricing: contractors pay by workforce size; hiring clients pay by the number of contractors managed [idoneity-cms/src/lib/pricing-tiers.ts]
- Homepage copy: subscription "sized by their own workforce — from $1,050 a year, and the first 500 signups pay no onboarding fee". Homepage returned 200 on 2026-11-08 [https://idoneity-cms.com]
- **Idoneity-EHS**: per-site EHS platform covering incidents, CAPA, inspections, observations, permits to work, PSM (MOC/PSSR, PHA, LOPA, SIL, bow-tie), chemicals and Tier II, waste clocks, obligations, RACI acknowledgements and an audit trail. Plus a back office: ledger, billing, funnel and 26 propose-only agents [idoneity-ehs/README.md; AGENTS.md]
- EHS tiers: Essential, Compliance, Complete, Assurance. Assurance adds ISO 9001/14001/45001 as one integrated system [idoneity-ehs/ledger/billing.py; site/public/pricing.html]
- EHS pitch: "the sticker is the whole price". Per-site price is published, the first 99 users per site are included, and the renewal cap is in the contract [idoneity-ehs/sales/talk-track.md]
- Marketplace success fee is tracked but not billed; collection waits on regulatory review [idoneity-cms/src/lib/pricing-tiers.ts; CORPORATE_STRUCTURE.md §3]

### Customers & market
- CMS buyers: EHS, safety and procurement managers at industrial firms. Secondary: contractors re-qualifying on every client portal [idoneity-cms/marketing/ads/launch-pack/idoneity-ad-copy.md]
- LinkedIn targeting: Construction, Oil & Gas, Manufacturing, Utilities; 51–1,000 employees [idoneity-cms/marketing/ads/launch-pack/idoneity-ad-copy.md]
- Outbound lead universe: EPA TRI facilities [leadgen/PLAYBOOK.md]
- EHS buyer: the safety/EHS owner at an operator with 3–30 sites and 200–5,000 workers. Published pricing covers sites up to 250 employees [idoneity-ehs/sales/talk-track.md; ledger/billing.py]
- No customers recorded: $0 revenue, no employees. EHS outputs run on seeded demo data [idoneity-cms/docs/COMPLIANCE_CALENDAR.md; idoneity-ehs/AGENTS.md]
- Standing rule (2026-09-13): no customer counts, testimonials or client-implying copy until real customers exist [idoneity-cms/docs/TODO.md]

### Pricing (as published)
- CMS /pricing **returned 500 again on 2026-11-08**; it loaded (200) on 11-01. Repo card, annual [idoneity-cms/src/lib/pricing-tiers.ts; live check 2026-11-08]:
  - Contractor: Solo (1–5) $1,050 · Small (6–25) $2,100 · Mid-market (26–49) $3,050 · Large (50–149) $5,700 · National (150–499) $7,800 · National+ (500–1,999) $15,600 · Enterprise (2,000+) contact sales
  - Hiring client: Starter (≤5 contractors) $4,700 · Small (6–10) $9,450 · Growth (11–14) $13,150 · Large (15–20) $18,700 · National (21–30) contact/MSA · Enterprise (31+) contact
- CMS fees and add-ons [idoneity-cms/src/lib/pricing-tiers.ts]:
  - Onboarding $975 one-time, shown struck through as "waived · First 500"
  - Training Records Portal $1,250/yr; Orientation Hosting $650/yr
  - Video price is stored in the DB; the seed says $499 but live showed $199 (drift)
- CMS: price is locked at the signup year; the new-signup list rises 5% each January [idoneity-cms/src/lib/pricing-tiers.ts]
- EHS per site per month: Essential $595 (setup $495) · Compliance $995 (setup $995) · Complete $1,450 (setup $2,495) · Assurance $1,450 + $650 per ISO standard (setup $4,995) [idoneity-ehs/ledger/billing.py; site/public/pricing.html]
- EHS terms [idoneity-ehs/ledger/billing.py; site/public/pricing.html]:
  - First 99 users per site included; above that, one 15% size band plus $4/user/mo
  - List price +7% each January; increase for existing customers capped at 4.5%
  - Multi-year: 3-yr terms −3%/yr, 5-yr terms −5%/yr; 3% off for CMS customers
- EHS multi-site: the repo has a 1–3 site slider and no multi-site discount. **The live page still shows a 25-site slider and 15%/28% multi-site discounts** (re-checked 2026-11-08, not redeployed) [idoneity-ehs/site/public/pricing.html; https://idoneity-ehs.praesidium-holdings.workers.dev/pricing]
- EHS "whole price" (5-year) page is in the repo but still 404 live (2026-11-08) [idoneity-ehs/site/public/whole-price.html; live check]
- EHS visitor/site access add-on: $525/site/mo, included in Complete and Assurance. Code only [idoneity-ehs/ledger/billing.py]

### Product / tech status
- CMS stack: Next.js 16, React 19, TypeScript 7, Drizzle, Turso/libSQL, Stripe, Tailwind 4, on Cloudflare Workers via OpenNext. Workers: `idoneity` (idoneity-cms.com), `praesidium-admin`, `idoneity-dev` [idoneity-cms/package.json; wrangler.jsonc]
- **CMS prod is degraded again.** On 2026-11-08 ~22:00 UTC, /api/health returned `{"ok":false}` and /pricing returned 500; the homepage returned 200. One week earlier, after the 11-01 Turso quota reset, both were healthy. Cause not confirmed: the quota burn is the leading suspect, but the leadgen opt-out sync read the Turso opt-out list without error every day 11-02 → 11-08 [https://idoneity-cms.com/api/health; leadgen/out/_optouts.log]
- **D1 cutover still not live.** The main `wrangler.jsonc` has no `DB_BACKEND`, so prod still runs on Turso. D1_CUTOVER.md is unchanged since 11-01 ("ready but inert"; D1 holds only the 10-10 snapshot). In the `d1-port` worktree, `scripts/apply-migrations.mjs` was edited 11-05 (Turso and D1 targets via `resolveBackend`) [idoneity-cms/wrangler.jsonc; .claude/worktrees/d1-port/]
- Root cause of the Turso read-quota burn still not found (suspected: 15-minute crons scanning `job_runs`) [D1_CUTOVER.md]
- No idoneity-cms commits this week [gitlog-idoneity.txt]
- CMS TODOs only Tyler can do, unchanged [idoneity-cms/docs/TODO.md]:
  - Apply prod migrations 0104/0106/0107/0108
  - Set RESEND_API_KEY / IDONEITY_OUTBOUND_UNLOCK
  - Rotate exposed secrets; verify the prod AI key; find the other deployer
  - Security items: SEC-3b, SEC-11, ARC-1..3, PERF
- EHS stack: Python 3.9, FastAPI, Jinja2, SQLite [idoneity-ehs/requirements.txt; CLAUDE.md]
- EHS live is the marketing site only: Worker at idoneity-ehs.praesidium-holdings.workers.dev (200). The portal has no host, and idoneity-ehs.com still does not resolve (2026-11-08) [idoneity-ehs/deploy/GO-LIVE.md; live check]
- EHS daily builder ran 11-02, 11-04, 11-05, 11-07 and 11-08 (no reports for 11-03 or 11-06) [idoneity-ehs/.claude/daily-builder/reports/]
  - Gate failed 11-01 → 11-05 on the date-dependent `idoneity_ehs.selftest` check
  - 11-07 and 11-08: **gate PASS**, all 31 suites. 11-08 fixed that check (commit 9190000)
- Builder work this week [daily-builder/reports/2026-11-04.md, 11-05.md, 11-07.md]:
  - 11-04: unlinking a written programme now removes its clause evidence
  - 11-05: BEFORE DELETE trigger on raci_consult (closes an 11-01 follow-up)
  - 11-07: crosswalk card surfaces real query errors
- Daily branches remain unmerged into base `feat/ehs-top10-raci-gap`. Several backlog items are blocked on unmerged prerequisites, including the 11-04 cascade commit and the 10-19 → 10-24 branches. Open medium: role_code-only people are invisible to owner suggestions [daily-builder/reports/2026-11-08.md]
- EHS self-identified gaps [idoneity-ehs/concept/SALES-BATTLECARDS.md §5.1]:
  - No mobile/offline, CMMS integration, bulk import, MOC approval chain, permit-conflict/LOTO object, or direct OSHA ITA submission
  - 300A view is current-year only, with no "annual average employees" box

### Sales & marketing activity
- Outbound **HOLD** still in force (since 2026-08-08). The hourly campaign job logs "HALTED" through 2026-11-08 16:27 [leadgen/HOLD; leadgen/out/_campaign_log.txt]
- Only send to date: 150 emails to Florida contacts on 2026-08-08 [leadgen/campaign_state.json]
- Daily lead job ran every day; last run 2026-11-08 07:30 [leadgen/heartbeat.json; out/_run_log.txt]
- Opt-out sync ran clean every day 11-02 → 11-08; suppression.txt is up to date [leadgen/out/_optouts.log; _optout_sync.log]
  - 1 opt-out record still matches no contact held
  - Opt-out routing check on 11-08: "VERIFIED — every advertised opt-out channel has a live route"; Cloudflare routing settings unreadable (403), so the check relied on the catch-all rule
- About 10,830 contacts; 727 sendable in Florida. Cadence: Thursdays, 5 states/week, ≤150 per state. The 3-email sequence is still a DRAFT [leadgen/RULES.md; SEQUENCE.md]
- LinkedIn is blocked on creating the Company Page. Audiences are ready: 2,808 companies / 4,646 contacts in FL, TX, LA, GA, NC [leadgen/LINKEDIN-CAMPAIGN.md]
- Meta/LinkedIn ad pack ready; the 10-second video is blocked on Replicate credit [idoneity-cms/marketing/ads/launch-pack/idoneity-ad-copy.md]
- **EHS desk, week of 11-03 (item 5): LinkedIn document/carousel pipeline** [idoneity-ehs/marketing/proposals/2026-11-03/SUMMARY.md]
  - Built: a 4-week calendar (9 slots, 10 Nov – 10 Dec: 5 READY, 1 skip, 3 HOLD); a deck on injury-log retention (5-year rule, quoted verbatim from 29 CFR 1904.33); a deck on 3 management-of-change questions; 3 text posts; a 6-slide template; a copy gate
  - TRIR deck not built: the formula could not be sourced from an OSHA page
  - Nothing was posted or scheduled. Tyler decides who posts (the desk recommends the company page) and must approve every post
  - Live 404s noted: /compliance-calendar/2027/, /regulatory-watch/, /tools/..., /security, /faq, /about; the December slots wait on the 2027 calendar page
  - "Do-not-claim" memory file is still missing from the EHS memory dir
  - Drafted-but-unbuilt backlog is now **eight** packages (was seven)
- On-site lead capture: /scorecard, a "learn more" popup and a lead triage queue; nothing has been emailed to leads [idoneity-cms/docs/TODO.md]

### Competitors
- CMS: ISN, Avetta, Veriforce. Internal-only price references: ISN ~$875+/sub/yr, Avetta ~$450–900/sub/yr [idoneity-cms/README.md; docs/TODO.md]
- EHS (Capterra top 10, Aug 2026): SafetyCulture, Novara Flex, HSI Donesafe, SafetyAmp, SafetyIQ, Dakota ProActivity, VelocityEHS, Cority, Benchmark Gensuite, Intelex. Enterprise: Enablon, Sphera, ProcessMAP/UL, Origami Risk, Ideagen, Evotix, Quentic [idoneity-ehs/concept/COMPETITIVE-RESEARCH.md]
- EHS sourced price points: SafetyIQ $2,500/yr; SafetyAmp $4,800/yr; SafetyCulture $24/seat/mo; Intelex $44/user/mo (25-user min); VelocityEHS $1,455/yr [idoneity-ehs/concept/SALES-BATTLECARDS.md §3]
- Rule: never name competitors or their prices in public copy [leadgen/RULES.md §7; idoneity-ehs/CLAUDE.md]

### Key tools & systems
- Cloudflare: Workers, R2 (nightly backups), Email Routing, D1 (EHS leads; `idoneity-cms-prod` staged). Turso `idoneity-prod` is still the prod DB. Also Stripe, Resend, and an Anthropic usage ledger with an `AI_DISABLED` kill switch [idoneity-cms/CLAUDE.md; D1_CUTOVER.md]
- Off-box backup script `~/Scripts/backup-db-cloud.sh` is broken: it hardcodes the removed `~/Projects/idoneity` path [D1_CUTOVER.md]
- Owner console at /admin, scoped by `entity_id` [praesidium-brands/docs/OWNER_CONSOLE.md]
- leadgen: Python on launchd, EPA TRI data, suppression synced from opt-outs (the opt-out list lives in Turso) [leadgen/PLAYBOOK.md; out/_optouts.log]
- EHS: 26 propose-only agents on cron write to proposals.json; daily builder plus gate; planned prod host is a VM [idoneity-ehs/AGENTS.md; deploy/GO-LIVE.md]
- Taplio is connected, but scheduling a post stays with Tyler. No image model was used for the 11-03 decks (typography template) [idoneity-ehs/marketing/proposals/2026-11-03/SUMMARY.md]

### Regulatory / compliance notes
- Sunbiz: "IDONEITY LIMITED LIABILITY COMPANY" filed 2026-07-17, ownership to confirm. Invoices hard-code "Idoneity SaaS, LLC". First annual report due by 2027-05-01 [idoneity-cms/docs/COMPLIANCE_CALENDAR.md; docs/TODO.md]
- Idoneity is recorded as disregarded with no W-2 wages (migration 0107, not applied in prod) [idoneity-cms/docs/TODO.md]
- CAN-SPAM: PO Box address; US-only; opt-outs honoured within 24h. The opt-out sync ran clean all week [idoneity-cms/docs/EMAIL_SEND_HALT.md; leadgen/RULES.md; out/_optouts.log]
- CMS OSHA mapping: 1910.146/147/134/1030, 1926 Subpart M, HAZWOPER; no official OSHA 10/30 cards [idoneity-cms/src/lib/pricing-tiers.ts]
- EHS: 1904 recordability; 300/300A/301 generated; ITA computed but not filed; PSM 1910.119; RCRA 90-day clock; Tier II [idoneity-ehs/README.md]
- Injury-log retention: 5 years, quoted verbatim from 29 CFR 1904.33; re-check on posting day [idoneity-ehs/marketing/proposals/2026-11-03/fixtures/source-retention-1904-33.md]
- CMS: SOC 2 / ISO 27001 "on the roadmap"; SSO "planned before paid GA" [idoneity-cms/src/lib/pricing-tiers.ts]
- EHS legal docs are all drafts (Terms under attorney review; no privacy policy). Uploads go to Anthropic with no customer disclosure yet [idoneity-ehs/legal/]
- OSHA 2026 civil penalties held at 2025 levels ($16,550 serious; $165,514 willful/repeat); the January adjustment is due [https://www.osha.gov/memos/2026-05-21/2026-annual-adjustments-osha-civil-penalties]
- Heat:
  - The revised heat NEP was issued 2026-04-10 [https://www.mondaq.com/unitedstates/employee-rights-labour-relations/1778956/osha-refines-heat-enforcement-strategy-while-federal-heat-rule-remains-pending]
  - The federal heat rule is still not final, with no target date; a House subcommittee hearing on the proposal was held in early September 2026 [https://jjkellercompliancenetwork.com/news/oshas-proposed-heat-rule-debated-during-house-subcommittee-hearing; https://safetyregulatory.com/updates/osha-heat-illness-rulemaking-2026/]
- OSHA expects a final rule on the use of subpoenas in investigations in November 2026 [J.J. Keller roundup via WebSearch 2026-11-08]
- EPA items from the 10-27 digest (GHG reporting → 2027-03-10; FRP → 2030-06-01): the desk now flags them as needing re-verification against the Federal Register before any use. The TCE comment deadline (Nov 13) has been dropped as stale [idoneity-ehs/marketing/proposals/2026-11-03/SUMMARY.md]
- OSHA NPRM (2026-04-06) would remove the fixed-ladder fall-arrest compliance deadline [https://www.jdsupra.com/topics/rulemaking-process/osh-act/osha/]

## Changed this week
- **CMS prod is degraded again.** /api/health is `{"ok":false}` and /pricing is 500 (both were OK on 11-01); the homepage still returns 200. Cause not confirmed. The Turso quota is the leading suspect, but the leadgen opt-out sync read Turso without error all week [live checks 2026-11-08 ~22:00 UTC; leadgen/out/_optouts.log]
- D1 cutover still not live (no `DB_BACKEND`). The only d1-port activity was an `apply-migrations.mjs` edit on 11-05 (Turso and D1 targets) [idoneity-cms/wrangler.jsonc; d1-port/scripts/apply-migrations.mjs]
- EHS gate is green again: PASS 11-07 and 11-08 after failing 11-01 → 11-05. 11-08 fixed the date-dependent selftest; 11-05 added the raci_consult BEFORE DELETE trigger (last week's follow-up). Daily branches are still unmerged [idoneity-ehs/.claude/daily-builder/reports/]
- NEW: EHS desk built the LinkedIn document/carousel pipeline [idoneity-ehs/marketing/proposals/2026-11-03/SUMMARY.md]
  - 4-week calendar from 10 Nov, 2 decks (log retention; MOC questions), 3 text posts, slide template
  - Nothing posted; waiting on Tyler's who-posts decision and approval
  - Unbuilt backlog is now 8 packages (was 7)
- Leadgen opt-out sync ran clean every day (it failed 10-26 → 10-31 last week). HOLD continues; nothing sent [leadgen/out/_optouts.log; _campaign_log.txt]
- Regulatory: no federal heat rule action in November (Sept House hearing noted). OSHA subpoena final rule expected in November. EPA dates from last week's digest now flagged for re-verification [WebSearch; EHS SUMMARY 11-03]
- Unchanged: EHS live pricing still shows the 25-site slider and 15%/28% discounts; /whole-price is 404; idoneity-ehs.com does not resolve; no idoneity-cms or leadgen commits

## Open questions for Tyler
- idoneity-cms.com/pricing is 500 again and health is ok:false, one week after the 11-01 recovery. Do you want the D1 cutover run now (accepting the 10-10 → now data gap to reconcile), or a Turso plan upgrade as a stopgap?
- The EHS LinkedIn pipeline has 5 posts ready from Tue 10 Nov. Who posts: the company page (desk recommendation, but no Company Page exists yet) or your personal profile? Should the first post go out 10 Nov?
- EHS live pricing still offers 15%/28% multi-site discounts and up to 25 sites, while the repo says max 3 sites with no discount. Which is correct, and should the repo version (plus /whole-price) be deployed?
- The EHS daily builder's work is spread across unmerged daily branches, and items are now being skipped because of that. Do you want a merge session into `feat/ehs-top10-raci-gap` (or main)?
- What are this year's Idoneity targets (first paying customer date, CMS vs EHS focus, revenue)? The OWNER section is still blank.
