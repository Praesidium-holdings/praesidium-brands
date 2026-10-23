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
## Auto facts (synced 2026-10-18)
### What it is / offer
- **Idoneity CMS** — contractor management: prequalification (PQF), training-record competency tracking, vendor risk ranking. Tagline: "Contractor management, without the ISN price tag" [idoneity-cms/README.md]
- Four modules: Risk Engine, Portable PQF, Insurance/COI, Site-Specific Safety. One flat annual fee, paid by either side [idoneity-cms/marketing/ads/launch-pack/idoneity-ad-copy.md]
- Two-sided: contractors pay by workforce size, hiring clients by number of contractors managed [idoneity-cms/src/lib/pricing-tiers.ts]
- Live homepage: "Contractor management, made simple — The proof clients demand and contractors earn — in one place"; "from $1,050 a year"; EHS shown as "Soon" [https://idoneity-cms.com]
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
- Standing rule (2026-09-13): no customer counts, testimonials or client-implying copy until real customers exist [idoneity-cms/docs/TODO.md]

### Pricing (as published)
- CMS repo card (2026 base, after the 35% cut on 2026-09-28), annual:
  - Contractor tiers: Solo (1–5 workers) $1,050 · Small (6–25) $2,100 · Mid-market (26–49) $3,050 · Large (50–149) $5,700 · National (150–499) $7,800 · National+ (500–1,999) $15,600 · Enterprise (2,000+) contact sales
  - Hiring-client tiers: Starter (≤5 contractors) $4,700 · Small (6–10) $9,450 · Growth (11–14) $13,150 · Large (15–20) $18,700 · National (21–30) contact/MSA · Enterprise (31+) contact
  [idoneity-cms/src/lib/pricing-tiers.ts]
- CMS fees/add-ons: onboarding $975 one-time; Training Records Portal $1,250/yr (hiring client); Orientation Hosting $650/yr; video price stored in DB (seed $499 vs $199 live noted as drift) [idoneity-cms/src/lib/pricing-tiers.ts]
- CMS promo "First 500": no onboarding fee for the first 500 subscriptions (replaced "Founding 25"). Price locked at signup year; new-signup list rises 5% each January [idoneity-cms/src/lib/pricing-tiers.ts]
- CMS live: **/pricing returns HTTP 500** (checked 2026-10-18). Homepage shows "from $1,050 a year", the $975 onboarding fee (FAQ) and the First-500 promo; /compare shows no dollar figures [https://idoneity-cms.com/pricing; https://idoneity-cms.com]
- EHS (code = live), per site per month: Essential $595 (setup $495) · Compliance $995 (setup $995) · Complete $1,450 (setup $2,495) · Assurance $1,450 + $650 per ISO standard (setup $4,995) [idoneity-ehs/ledger/billing.py; https://idoneity-ehs.praesidium-holdings.workers.dev/pricing.html]
- EHS terms: first 99 users per site included; above that +15% size band + $4/user/mo. List price +7% each January; existing-customer increase capped at 4.5%; 3-yr terms step down 3%/yr and 5-yr terms 5%/yr; 3% off for CMS customers [idoneity-ehs/ledger/billing.py; live pricing.html]
- EHS multi-site: code caps published pricing at 3 sites with no multi-site discount; the live page still offers 15% off >5 sites and 28% off >10 sites (slider to 25 sites) [idoneity-ehs/ledger/billing.py vs site/public/pricing.html]
- EHS visitor/site access add-on $525/site/mo, included in Complete/Assurance — in code only, not on the live page [idoneity-ehs/ledger/billing.py]
- EHS live homepage: "From $595 per site / month · 99 users included per site · 30-day trial · no demo call required" [https://idoneity-ehs.praesidium-holdings.workers.dev/]

### Product / tech status
- CMS stack: Next.js 16.3.5, React 19.3, TypeScript 7, Drizzle, Turso/libSQL, Stripe, Anthropic SDK, Tailwind 4; Cloudflare Workers via OpenNext. Worker `idoneity` on idoneity-cms.com + www, plus `praesidium-admin` and `idoneity-dev` [idoneity-cms/package.json; wrangler.jsonc]
- CMS live (coming-soon flag off). Current branch `feat/cms-buildout-1005`; main last merged 2026-09-28 (pricing cut), fast-forward around 2026-10-12 [idoneity-cms/wrangler.jsonc; .git/logs]
- CMS Tyler-only TODOs: push/deploy the buildout branch; run prod migrations 0104/0106/0107/0108; re-enter email/outbound worker secrets; rotate exposed secrets; verify the prod AI key (401 on 2026-08-17); find what deletes worktrees [idoneity-cms/docs/TODO.md]
- CMS open security items: SEC-3b (MFA secret stored plaintext), SEC-11 (full CSP), ARC-1..3, PERF-1/2/4/6 [idoneity-cms/docs/TODO.md]
- CMS app email limited to account holders (sign-in code, password reset, admin lead alerts); inactive until secrets are set [idoneity-cms/docs/EMAIL_SEND_HALT.md]
- EHS stack: Python 3.9, FastAPI, Jinja2, SQLite (Postgres-portable) [idoneity-ehs/requirements.txt; README.md]
- EHS live = marketing site only (Worker at idoneity-ehs.praesidium-holdings.workers.dev; leads → D1). The portal/app has no host yet — blocked on a VM + domain; idoneity-ehs.com does not resolve [idoneity-ehs/deploy/GO-LIVE.md; WebFetch]
- EHS has no billing code (quote/invoice/subscription); outbound mail blocked (email-provider domain unverified; outbox flush needs owner unlock) [idoneity-ehs/deploy/GO-LIVE.md; deploy/crontab]
- EHS daily builder 2026-10-18: selftest 548/548, ui_selftest 292/292; ~13 backlog items open, 6 blocked on Tyler [idoneity-ehs/.claude/daily-builder/reports/2026-10-18.md]
- EHS self-identified gaps: no mobile/offline, no CMMS integration, no bulk import, no MOC approval chain, no permit-conflict/LOTO object, no direct OSHA ITA submission [idoneity-ehs/concept/SALES-BATTLECARDS.md §5.1]

### Sales & marketing activity
- Outbound **HOLD** in force since 2026-08-08 ("DO NOT SEND ANY EMAILS ON THIS UNTIL I TELL YOU TO") [leadgen/HOLD]
- Only send to date: 150 emails to Florida contacts on 2026-08-08, 0 failed; campaign not complete [leadgen/campaign_state.json]
- Lead pulls done for all 50 states (last WY 2026-09-13); daily job last ran 2026-10-18 07:30 [leadgen/queue_state.json; heartbeat.json]
- About 10,830 contacts total; Florida had 727 sendable; 12 foreign-domain rows await decision [leadgen/RULES.md; docs/TODO.md]
- Planned cadence: sends Thursdays 08:01 recipient-local, 5 states/week, max 150 per state; stop at 3% bounce / 0.1% complaint; annual refresh Mar 3, new-filer sweep Jul 15 [leadgen/RULES.md]
- 3-email sequence (Day 0/4/11) still marked DRAFT [leadgen/SEQUENCE.md]
- LinkedIn blocked on creating the Company Page. Audiences ready (2,808 companies / 4,646 contacts in FL, TX, LA, GA, NC); plan is $20–30/day [leadgen/LINKEDIN-CAMPAIGN.md; LINKEDIN-PAGE-SETUP.md]
- Meta/LinkedIn ad pack ready; 10-second video blocked on Replicate credit [idoneity-cms/marketing/ads/launch-pack/idoneity-ad-copy.md]
- On-site lead capture: /scorecard, 60-second "learn more" popup, unified lead triage queue; nothing emailed to leads [idoneity-cms/docs/TODO.md]
- EHS: leads land in D1 and "NOTHING else happens" (no email, login or pricing). 8-item growth playbook not started; blocked on domain + email DNS [idoneity-ehs/site/worker.js; marketing/GROWTH-PLAYBOOK.md]
- EHS weekly proposal drafts (08-04 → 10-13: quote email, deadline calendar, TRIR/DART calculator, injury-cost estimator) await review; none shipped. 09-01 to 09-22 folders empty [idoneity-ehs/marketing/proposals/]

### Competitors
- CMS: ISN, Avetta, Veriforce [praesidium-brands/README.md; idoneity-cms/README.md]. Internal-only price refs (secondary sources): ISN ~$875+/sub/yr, Avetta ~$450–900/sub/yr [idoneity-cms/docs/TODO.md 2026-09-12]
- EHS (Capterra top 10, Aug 2026): SafetyCulture, Novara Flex, HSI Donesafe, SafetyAmp, SafetyIQ, Dakota ProActivity, VelocityEHS, Cority, Benchmark Gensuite, Intelex. Enterprise: Enablon, Sphera, ProcessMAP/UL, Origami Risk, Ideagen, Evotix, Quentic. PHA: PHAWorks, PHA-Pro. SDS: MSDSonline, Chemwatch [idoneity-ehs/concept/COMPETITIVE-RESEARCH.md]
- EHS sourced price points: SafetyIQ $2,500/yr; SafetyAmp $4,800/yr; SafetyCulture $24/seat/mo; Intelex $44/user/mo (25-user min); VelocityEHS $1,455/yr (one order form) [idoneity-ehs/concept/SALES-BATTLECARDS.md §3]
- Rule: never name competitors or their prices in public copy [leadgen/RULES.md §7; idoneity-ehs/CLAUDE.md]

### Key tools & systems
- Cloudflare: Workers, R2 (nightly backups), Email Routing, D1 (`idoneity-outbound` backup; EHS leads); Turso `idoneity-prod`; Stripe; Resend; Anthropic usage ledger with `AI_DISABLED` kill switch [idoneity-cms/SECURITY.md; CLAUDE.md; idoneity-ehs/site/wrangler.jsonc]
- Owner console at /admin hosts every LLC's corporate vault, compliance calendar, AP/AR, close and reports, scoped by `entity_id` [praesidium-brands/docs/OWNER_CONSOLE.md]
- leadgen: Python on launchd, EPA Envirofacts TRI data, suppression file synced from opt-outs [leadgen/PLAYBOOK.md; RULES.md]
- EHS: 44 agents defined in code (read/propose only → proposals.json; last batch 2026-09-19); planned prod host is a Debian/Ubuntu VM with systemd timers [idoneity-ehs/automation/; deploy/GO-LIVE.md]
- Planned: QuickBooks or Xero [idoneity-cms/CORPORATE_STRUCTURE.md]

### Regulatory / compliance notes
- Sunbiz: "IDONEITY LIMITED LIABILITY COMPANY" filed 2026-07-17 with no authorized person on record ("confirm it's ours"). Invoices/quotes hard-code "Idoneity SaaS, LLC". Idoneity Holdings not filed. First annual report due by 2027-05-01 [idoneity-cms/docs/COMPLIANCE_CALENDAR.md]
- EHS contracting entity in draft Terms: Idoneity Limited Liability Company (FL) [idoneity-ehs/legal/terms.md]
- CAN-SPAM: PO Box postal address; US-only sending; opt-outs honored within 24h; 6 opt-outs from 2026-08-08 suppressed; footer address used on the 08-08 send was not recorded (audit gap); CA §17529.5 not checked in code [idoneity-cms/docs/EMAIL_SEND_HALT.md; leadgen/RULES.md]
- OSHA mapping: training records map to 1910.146/147/134/1030, 1926 Subpart M, HAZWOPER; no official OSHA 10/30 cards [idoneity-cms/src/lib/pricing-tiers.ts]
- EHS: 1904 recordability computed, 300/300A/301 generated, ITA obligation computed but not filed; PSM 1910.119; RCRA 90-day clock, manifest 45/60-day exception logic; Tier II aggregation [idoneity-ehs/README.md]
- EHS legal docs are all drafts: Terms under attorney review; Security Addendum and Subprocessors marked "NOT FOR PUBLICATION"; no privacy policy; data cap unset until cyber/tech E&O is bound; no SOC 2/ISO 27001 [idoneity-ehs/legal/]
- EHS uploads go automatically to Anthropic with no customer disclosure or opt-out; must be gated before PSM accepts real data [idoneity-ehs/legal/subprocessors.md]
- CMS: SOC 2 / ISO 27001 "on the roadmap"; SSO "planned before paid GA" [https://idoneity-cms.com; src/lib/pricing-tiers.ts]
- OSHA 2026 civil penalties held at 2025 levels ($16,550 serious; $165,514 willful/repeat) [https://www.osha.gov/memos/2026-05-21/2026-annual-adjustments-osha-civil-penalties]
- Federal heat illness rule still not final [https://www.cozen.com/news-resources/news/2026/osha-states-step-up-scrutiny-of-workplace-exposure-to-heat-hazards]

## Changed this week
- First sync — no previous context file existed, so there is no baseline to compare against. All facts above are new.
- This week's commits: CMS structure cleanup; Claude config (deny .env/db edits, session + post-edit hooks); TODO for pushing/deploying `feat/cms-buildout-1005` (2026-10-17). EHS structure cleanup (2026-10-17). No leadgen commits [gitlog-idoneity.txt]
- Observed this run: idoneity-cms.com/pricing returns HTTP 500 [live check 2026-10-18]

## Open questions for Tyler
- Did you know idoneity-cms.com/pricing returns 500? Is the buildout branch plus migrations 0104–0108 deploy the planned fix?
- When should the outbound HOLD (since 2026-08-08) lift? The other Thursday states are queued.
- Which contract name should invoices and the site use: "Idoneity SaaS, LLC" (hard-coded on invoices) or the Sunbiz record "Idoneity Limited Liability Company"? Is that Sunbiz record (no authorized person listed) confirmed as yours?
- EHS multi-site pricing: the code caps published pricing at 3 sites with no discount, but the live page offers 15%/28% off above 5/10 sites. Which is current?
- Who is first-priority as a customer: hiring clients or contractors? And what are this year's revenue, customer and margin targets for CMS and EHS?
