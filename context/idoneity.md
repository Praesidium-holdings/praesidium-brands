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
## Auto facts (synced 2026-11-01)
### What it is / offer
- **Idoneity CMS** — contractor management: prequalification (PQF), training-record competency tracking, vendor risk ranking. Tagline: "Contractor management, without the ISN price tag" [idoneity-cms/README.md]
- Four modules: Risk Engine, Portable PQF, Insurance/COI, Site-Specific Safety. One flat annual fee, paid by either side [idoneity-cms/marketing/ads/launch-pack/idoneity-ad-copy.md]
- Two-sided: contractors pay by workforce size, hiring clients by number of contractors managed [idoneity-cms/src/lib/pricing-tiers.ts; https://idoneity-cms.com/pricing]
- Live homepage: subscription "sized by their own workforce — from $1,050 a year, and the first 500 signups pay no onboarding fee" [https://idoneity-cms.com — 200 on 2026-11-01]
- **Idoneity-EHS** — per-site EHS platform: incidents/investigation, CAPA, inspections, observations, permits to work, PSM (MOC/PSSR, PHA, LOPA, SIL, bow-tie), chemicals + Tier II, waste clocks, obligations, RACI/programme acknowledgements, audit trail; plus a back office (ledger, billing, funnel, 26 propose-only agents) [idoneity-ehs/README.md; AGENTS.md]
- EHS tiers: Essential, Compliance, Complete, Assurance (adds ISO 9001/14001/45001 as one integrated system) [idoneity-ehs/ledger/billing.py; site/public/pricing.html]
- EHS pitch: "the sticker is the whole price" — published per-site price, first 99 users per site included, renewal cap in contract [idoneity-ehs/sales/talk-track.md]
- Marketplace success fee tracked but not billed; collection waits on regulatory review [idoneity-cms/src/lib/pricing-tiers.ts; CORPORATE_STRUCTURE.md §3]

### Customers & market
- CMS buyers: EHS, safety and procurement managers at industrial firms; secondary: contractors re-qualifying on every client portal [idoneity-cms/marketing/ads/launch-pack/idoneity-ad-copy.md]
- LinkedIn targeting: Construction, Oil & Gas, Manufacturing, Utilities; 51–1,000 employees [idoneity-cms/marketing/ads/launch-pack/idoneity-ad-copy.md]
- Outbound lead universe: EPA TRI facilities [leadgen/PLAYBOOK.md]
- EHS buyer: safety/EHS owner at an operator with 3–30 sites and 200–5,000 workers; published pricing covers sites up to 250 employees [idoneity-ehs/sales/talk-track.md; ledger/billing.py]
- No customers recorded: $0 revenue, no employees; EHS outputs run on seeded demo data [idoneity-cms/docs/COMPLIANCE_CALENDAR.md; idoneity-ehs/AGENTS.md]
- CMS prod snapshot (2026-10-10, loaded into D1): 150 tables, 3,640 rows — no customer count derived [idoneity-cms/.claude/worktrees/d1-port/docs/D1_CUTOVER.md]
- Standing rule (2026-09-13): no customer counts, testimonials or client-implying copy until real customers exist [idoneity-cms/docs/TODO.md]

### Pricing (as published)
- CMS live /pricing **now loads (200, 2026-11-01)** and matches the repo card, annual:
  - Contractor: Solo (1–5) $1,050 · Small (6–25) $2,100 · Mid-market (26–49) $3,050 · Large (50–149) $5,700 · National (150–499) $7,800 · National+ (500–1,999) $15,600 · Enterprise (2,000+) contact sales
  - Hiring client: Starter (≤5 contractors) $4,700 · Small (6–10) $9,450 · Growth (11–14) $13,150 · Large (15–20) $18,700 · National (21–30) contact/MSA · Enterprise (31+) contact
  [https://idoneity-cms.com/pricing; idoneity-cms/src/lib/pricing-tiers.ts]
- CMS fees/add-ons: onboarding $975 one-time, shown struck-through "waived · First 500"; Training Records Portal $1,250/yr; Orientation Hosting $650/yr; video price DB-stored (seed $499 vs $199 live drift) [https://idoneity-cms.com/pricing; idoneity-cms/src/lib/pricing-tiers.ts]
- CMS: price locked at signup year; new-signup list rises 5% each January [idoneity-cms/src/lib/pricing-tiers.ts]
- EHS per site per month: Essential $595 (setup $495) · Compliance $995 (setup $995) · Complete $1,450 (setup $2,495) · Assurance $1,450 + $650 per ISO standard (setup $4,995) [idoneity-ehs/ledger/billing.py; site/public/pricing.html]
- EHS terms: first 99 users/site included; above that one 15% size band + $4/user/mo. List +7% each January; existing-customer increase capped at 4.5%; 3-yr terms −3%/yr, 5-yr −5%/yr; 3% off for CMS customers [idoneity-ehs/ledger/billing.py; site/public/pricing.html]
- EHS multi-site: repo = 1–3 site slider, no multi-site discount. **Live page still shows 1–25 site slider, 15% off >5 sites, 28% off >10 sites** (not redeployed) [idoneity-ehs/site/public/pricing.html; https://idoneity-ehs.praesidium-holdings.workers.dev/pricing, 2026-11-01]
- EHS "whole price" (5-year) page in repo; still 404 live [idoneity-ehs/site/public/whole-price.html; live check 2026-11-01]
- EHS visitor/site access add-on $525/site/mo, included in Complete/Assurance — code only [idoneity-ehs/ledger/billing.py]

### Product / tech status
- CMS stack: Next.js 16, React 19, TypeScript 7, Drizzle, Turso/libSQL, Stripe, Tailwind 4; Cloudflare Workers via OpenNext. Worker `idoneity` on idoneity-cms.com; plus `praesidium-admin`, `idoneity-dev` [idoneity-cms/package.json; wrangler.jsonc]
- **CMS live health recovered:** /api/health `{"ok":true}` and /pricing 200 on 2026-11-01 (were ok:false / 500 on 10-25). Coincides with the Turso read-quota reset due 11-01; cause not confirmed [https://idoneity-cms.com/api/health; D1_CUTOVER.md]
- **D1 cutover still not live:** main `wrangler.jsonc` has no `DB_BACKEND` var, so prod still runs on Turso. `d1-port` worktree had file activity 11-01 but D1_CUTOVER.md still reads "ready but inert"; D1 holds only the 10-10 snapshot; migrations 0110/0111 unapplied; LIKE 50-byte limit (17 sites), >1,000-queries-per-invocation and dev-env D1 still open [idoneity-cms/wrangler.jsonc; .claude/worktrees/d1-port/docs/D1_CUTOVER.md]
- Root cause of the Turso read-quota burn still not found (suspect: 15-min crons scanning `job_runs`) — risk of repeat in November [D1_CUTOVER.md]
- No idoneity-cms commits this week; local checkout on `main` [gitlog-idoneity.txt; idoneity-cms/.git/logs/HEAD]
- CMS Tyler-only TODOs still open: prod migrations 0104/0106/0107/0108; RESEND_API_KEY / IDONEITY_OUTBOUND_UNLOCK; rotate exposed secrets; verify prod AI key; find the other deployer. Security: SEC-3b, SEC-11, ARC-1..3, PERF items [idoneity-cms/docs/TODO.md — unchanged since 10-25]
- EHS stack: Python 3.9, FastAPI, Jinja2, SQLite [idoneity-ehs/requirements.txt; CLAUDE.md]
- EHS live = marketing site only (Worker at idoneity-ehs.praesidium-holdings.workers.dev, 200). Portal has no host; idoneity-ehs.com still does not resolve (2026-11-01) [idoneity-ehs/deploy/GO-LIVE.md; live check]
- EHS daily builder ran daily through 11-01. 11-01 fixed a RACI bug (any account could record that a colleague had read a revision); reviewer logged 2 medium follow-ups (consult responses not bound to consulted person; no BEFORE DELETE trigger on raci_consult). **Gate FAIL 11-01**: `idoneity_ehs.selftest` (1 failure, "sample cannot have been taken in the future", likely date-related, uninvestigated); 30 other suites pass [idoneity-ehs/.claude/daily-builder/reports/2026-11-01.md]
- Daily branches remain unmerged into base `feat/ehs-top10-raci-gap` [idoneity-ehs/.claude/daily-builder/reports/2026-11-01.md]
- EHS self-identified gaps: no mobile/offline, CMMS integration, bulk import, MOC approval chain, permit-conflict/LOTO object, direct OSHA ITA submission; 300A view current-year only, no "annual average employees" box [idoneity-ehs/concept/SALES-BATTLECARDS.md §5.1; marketing/proposals/2026-10-20/SUMMARY.md]

### Sales & marketing activity
- Outbound **HOLD** still in force (since 2026-08-08); hourly campaign job logs "HALTED" (latest 2026-11-01 16:26) [leadgen/HOLD; leadgen/out/_campaign_log.txt]
- Only send to date: 150 emails to Florida contacts on 2026-08-08 [leadgen/campaign_state.json]
- Daily lead job last ran 2026-11-01 07:30 [leadgen/heartbeat.json]
- **Opt-out sync failed every day 10-26 → 10-31** (Turso "SQL read operations are forbidden"); log: "do not send until this succeeds". Recovered 11-01; suppression.txt up to date; 1 opt-out record still matches no contact held [leadgen/out/_optouts.log]
- About 10,830 contacts; Florida 727 sendable; cadence Thursdays, 5 states/week, ≤150/state; 3-email sequence still DRAFT [leadgen/RULES.md; SEQUENCE.md]
- LinkedIn blocked on creating the Company Page; audiences ready (2,808 companies / 4,646 contacts in FL, TX, LA, GA, NC) [leadgen/LINKEDIN-CAMPAIGN.md]
- Meta/LinkedIn ad pack ready; 10-second video blocked on Replicate credit [idoneity-cms/marketing/ads/launch-pack/idoneity-ad-copy.md]
- On-site lead capture: /scorecard, "learn more" popup, lead triage queue; nothing emailed to leads [idoneity-cms/docs/TODO.md]
- EHS desk (week of 10-27) drafted item 4: weekly federal rulemaking digest (spec, real sample issue Oct 12–18, quiet-week template, "regulatory watch" page copy, 6-slide LinkedIn deck, cron note). Findings: only 6 OSHA Federal Register docs in 8 weeks, so it is realistically an EPA + hazmat digest; "we track this for you" not claimable; needs a weekly human review gate and a postal address. Drafted-but-unbuilt backlog now **seven** packages; Feb 1 300A window is the clock. Next: 4-week LinkedIn calendar [idoneity-ehs/marketing/proposals/2026-10-27/SUMMARY.md]
- Slide covers and 300A worksheet mockup committed 10-29 (direction only, not for external use) [gitlog-idoneity.txt; marketing/proposals/2026-10-20, 2026-10-27]

### Competitors
- CMS: ISN, Avetta, Veriforce. Internal-only price refs: ISN ~$875+/sub/yr, Avetta ~$450–900/sub/yr [idoneity-cms/README.md; docs/TODO.md]
- EHS (Capterra top 10, Aug 2026): SafetyCulture, Novara Flex, HSI Donesafe, SafetyAmp, SafetyIQ, Dakota ProActivity, VelocityEHS, Cority, Benchmark Gensuite, Intelex; enterprise: Enablon, Sphera, ProcessMAP/UL, Origami Risk, Ideagen, Evotix, Quentic [idoneity-ehs/concept/COMPETITIVE-RESEARCH.md]
- EHS sourced price points: SafetyIQ $2,500/yr; SafetyAmp $4,800/yr; SafetyCulture $24/seat/mo; Intelex $44/user/mo (25-user min); VelocityEHS $1,455/yr [idoneity-ehs/concept/SALES-BATTLECARDS.md §3]
- Rule: never name competitors or their prices in public copy [leadgen/RULES.md §7; idoneity-ehs/CLAUDE.md]

### Key tools & systems
- Cloudflare: Workers, R2 (nightly backups), Email Routing, D1 (EHS leads; `idoneity-cms-prod` staged); Turso `idoneity-prod` (still prod DB; reads blocked 10-26 → 10-31); Stripe; Resend; Anthropic usage ledger with `AI_DISABLED` kill switch [idoneity-cms/CLAUDE.md; D1_CUTOVER.md; leadgen/out/_optouts.log]
- Off-box backup script `~/Scripts/backup-db-cloud.sh` broken (hardcodes removed `~/Projects/idoneity` path) [D1_CUTOVER.md]
- Owner console at /admin, scoped by `entity_id` [praesidium-brands/docs/OWNER_CONSOLE.md]
- leadgen: Python on launchd, EPA TRI data, suppression synced from opt-outs (opt-out list lives in Turso) [leadgen/PLAYBOOK.md; out/_optouts.log]
- EHS: 26 propose-only agents on cron → proposals.json; daily builder + gate; planned prod host a VM [idoneity-ehs/AGENTS.md; deploy/GO-LIVE.md]
- Federal Register API used for digest drafts; Replicate (Ideogram) for mockups [idoneity-ehs/marketing/proposals/2026-10-27/SUMMARY.md]

### Regulatory / compliance notes
- Sunbiz: "IDONEITY LIMITED LIABILITY COMPANY" filed 2026-07-17, ownership to confirm; invoices hard-code "Idoneity SaaS, LLC"; first annual report due by 2027-05-01 [idoneity-cms/docs/COMPLIANCE_CALENDAR.md; docs/TODO.md]
- Idoneity recorded as disregarded, no W-2 wages (migration 0107, not applied in prod) [idoneity-cms/docs/TODO.md]
- CAN-SPAM: PO Box address; US-only; opt-outs within 24h. Opt-out sync was down 6 days (10-26 → 10-31) — no sends occurred (HOLD) [idoneity-cms/docs/EMAIL_SEND_HALT.md; leadgen/RULES.md; out/_optouts.log]
- CMS OSHA mapping: 1910.146/147/134/1030, 1926 Subpart M, HAZWOPER; no official OSHA 10/30 cards [idoneity-cms/src/lib/pricing-tiers.ts]
- EHS: 1904 recordability, 300/300A/301 generated, ITA computed not filed; PSM 1910.119; RCRA 90-day clock; Tier II [idoneity-ehs/README.md]
- CMS: SOC 2 / ISO 27001 "on the roadmap"; SSO "planned before paid GA" [https://idoneity-cms.com; src/lib/pricing-tiers.ts]
- EHS legal docs all drafts (Terms under attorney review; no privacy policy); uploads go to Anthropic with no customer disclosure yet [idoneity-ehs/legal/]
- OSHA 2026 civil penalties held at 2025 levels ($16,550 serious; $165,514 willful/repeat); January adjustment due [https://www.osha.gov/memos/2026-05-21/2026-annual-adjustments-osha-civil-penalties]
- Heat: revised heat NEP issued 2026-04-10 and extended five years (resolves last week's conflicting reports); federal heat rule still not final, secondary source cites DOL target Oct 2027 [https://www.mondaq.com/unitedstates/health-safety/1775642/osha-updates-and-extends-its-heat-program-for-five-more-years; https://beancount.io/blog/2026/08/12/osha-heat-rule-enforcement-2026-guide]
- EPA items found by EHS desk: GHG reporting deadline for 2025 moved 2026-10-30 → 2027-03-10; facility response plan compliance date 2027-06-01 → 2030-06-01 (effective Dec 14); TCE compliance-date extension proposed, comments due Nov 13 [idoneity-ehs/marketing/proposals/2026-10-27/SUMMARY.md (Federal Register)]
- OSHA NPRM (2026-04-06) to remove the fixed-ladder fall-arrest compliance deadline [https://www.jdsupra.com/topics/rulemaking-process/osh-act/osha/]

## Changed this week
- CMS live recovered: idoneity-cms.com/pricing now 200 (was 500) and /api/health `{"ok":true}` (was ok:false). Live prices match the repo card. Timing coincides with the Turso quota reset due 11-01; cause not confirmed [live checks 2026-11-01]
- D1 cutover still NOT live: no `DB_BACKEND` in main wrangler.jsonc; prod still on Turso. Quota-burn root cause still unknown [idoneity-cms/wrangler.jsonc; d1-port/docs/D1_CUTOVER.md]
- NEW: leadgen opt-out sync failed daily 10-26 → 10-31 (Turso reads blocked); recovered 11-01. No sends happened (HOLD). 1 unmatched opt-out record persists [leadgen/out/_optouts.log]
- NEW: EHS desk drafted item 4, a weekly federal rulemaking digest + "regulatory watch" page + LinkedIn deck. OSHA feed nearly empty, so it would be EPA/hazmat-heavy. Unbuilt backlog now 7 packages (was 6) [idoneity-ehs/marketing/proposals/2026-10-27/SUMMARY.md]
- NEW: EHS daily builder gate FAILED 11-01 (1 failure in `idoneity_ehs.selftest`, likely date-related); same run fixed a RACI acknowledgement spoofing bug and logged 2 medium follow-ups [idoneity-ehs/.claude/daily-builder/reports/2026-11-01.md]
- Unchanged: EHS live pricing still shows 25-site slider + 15%/28% multi-site discount; /whole-price 404; idoneity-ehs.com unresolved; outbound HOLD; no idoneity-cms or leadgen commits [live checks; gitlog-idoneity.txt]
- Regulatory: heat NEP confirmed revised 2026-04-10 and extended five years (clears last week's conflict); new EPA date changes (GHG reporting → 2027-03-10; FRP → 2030-06-01; TCE comments due Nov 13) [WebSearch; EHS desk SUMMARY]

## Open questions for Tyler
- Turso is readable again and the CMS site is healthy, but the quota-burn cause is unknown and November's quota could run out the same way. Do you run the D1 cutover now, and is reconciling the 10-10 → now data gap into D1 still the plan?
- The leadgen opt-out list lives in Turso and its sync was down for 6 days. Should that move to D1 (or local) before the outbound HOLD lifts? What's the decision on the unmatched opt-out record?
- EHS live pricing still offers 15%/28% multi-site discounts and up to 25 sites, while the repo says max 3 sites with no discount. Which is correct, and should the repo version plus the "whole price" page be deployed?
- The EHS marketing backlog is now 7 drafted, unbuilt packages. Do you want an engineering session on the 300A tools (3a–3c) before the Feb 1 window? And is the weekly digest worth a weekly human review if it would mostly cover EPA/hazmat rather than OSHA?
- What are this year's Idoneity targets (first paying customer date, CMS vs EHS focus, revenue)? The OWNER section is still blank.
