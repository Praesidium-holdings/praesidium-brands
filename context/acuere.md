# acuere — company context
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
- Specialist recruiting for aerospace, defense, industrial and construction employers. Places contract engineers, technicians and safety staff (1099 or W-2) and runs confidential direct-hire searches. HQ on Florida's Space Coast, recruiting nationwide [acuere/src/lib/site-facts.ts; acuere/CLAUDE.md; https://acueretalent.com/]
- Services: contract and contract-to-hire; direct-hire search ("a few searches at a time"); executive/leadership search; confidential replacement searches; relocation help [acuere/CLAUDE.md; https://acueretalent.com/]
- Live site 2026-11-08: homepage returns 200; headline and copy unchanged since last week [https://acueretalent.com/]
- Entity:
  - README: "Acuere, LLC (pending amendment to Acuere Talent, LLC)" [acuere/README.md]
  - Sunbiz: no Acuere entity ("planned") [idoneity-cms/docs/COMPLIANCE_CALENDAR.md]
  - Live footer still reads "Acuere Talent, LLC" [https://acueretalent.com/, 2026-11-08]

### Customers & market
- No placements recorded. Desk run of 2026-11-08 [acuere/data/desk-status.json]:
  - 0 active contracts, 0 placements, 0 fees received, 0 referrals earned
  - 1 candidate in the pool
- Sourcing volume (2026-11-08) [acuere/data/desk-status.json]:
  - 16,717 live sourced postings; 1,471 new in the last 3 days
  - 63 matches total; today's match run saved 25 matches (8 strong) for the 1 candidate
- Market research (14-day window): 7,453 postings, 6,662 fee-worthy, 19 on the Space Coast. Daily target CSVs written 11-02 → 11-08 [desk-status.json; data/research/targets-2026-11-0*.csv]
- Pitch re-screen (11-08): 39 queued pitches scanned, all 39 in lane; estimated fees $1,468,311. On 10-17 it was 31 kept / $1.13M [desk-status.json; acuere/CLAUDE.md]
- Live /jobs: 51 roles (51 jobs pushed by site-sync 11-08). Last week, 14 of the 51 were counted as off-lane; not re-counted this week [desk-status.json; runs/2026-11-01/acuere.auto.md]
- Target lanes: aerospace, defense, industrial, construction only; healthcare, finance, education, marketing, sales and software are never pitched [acuere/src/lib/sourcing/lanes.ts via CLAUDE.md]

### Pricing (as published)
- Website: no fees, rates or pay ("Don't show pricing. Ever."). Candidates are never charged [acuere/CLAUDE.md; https://acueretalent.com/]
- Employer emails and referral intros carry one terms line: direct hire at 19.5% of first-year base salary with a 90-day replacement guarantee; contract work billed hourly at a per-role rate [acuere/CLAUDE.md; src/lib/automation/email-templates.ts]
- The DB column default is still 2000 bps (20%); the code always passes 19.5% [acuere/CLAUDE.md]
- Trades tier: 12% fee in estimates [acuere/CLAUDE.md; src/lib/sourcing/fee-tier.ts]
- Internal defaults, not published [acuere/CLAUDE.md]:
  - 17% expense markup; 4% discount for veteran-owned clients; 14% W-2 burden
  - Net-7 invoices
  - Pitch floors: $28/hr for contract roles; $15k estimated fee for direct hire
- Client invoices go out weekly on Thursday (New York time) [acuere/src/lib/contractors/billing.ts]
- Referral bonuses are in code, not on the site: $500 per placed candidate (after 90 days); $1,000 per new client (after first paid invoice) [acuere/CLAUDE.md]

### Product / tech status
- Stack: Next.js 16, React 19, Tailwind 4, Drizzle; OpenNext on Cloudflare; D1 `acuere-db`, R2, Workers AI (free allowance only) [acuere/CLAUDE.md; package.json]
- Live health 2026-11-08 ~22:00 UTC [https://acueretalent.com/api/health]:
  - `ok: true` on D1 (`d1-binding`); latest migration `0029_spec_consent.sql`
  - `site.dbAvailable: false`: forms and portal still use the R2 relay
  - Email provider `stub` (live: false); autonomyMode `manual`
  - **36 pending approvals**
  - AI model `@cf/google/gemma-4-26b-a4b-it`; 0 AI calls in 24h
- Desk run 2026-11-08: 1 of ~22 steps failed. **"BD pitch drafts" fails on a `sourced_postings` query**, and the desk warns "1471 new postings in 3 days but 0 pitches drafted — pitch step may be stalled" [acuere/data/desk-status.json; desk-issues.txt]
- CTO brief (11-08) [desk-status.json]:
  - Tests: FAILING, last run ~11-02
  - End-to-end scenario backtest FAILING: 98/101 passed, last run ~11-02. This is the deploy gate
  - Backup drive not reachable; the D1 dump still went offsite to R2. D1 dumps were written locally on 11-07 and 11-08 [data/backups/]
- IndexNow pings return HTTP 403 for 8 URLs [desk-status.json site-sync]
- Workers [acuere/CLAUDE.md]:
  - `acuere` (site), `acuere-inbound` (email), `acuere-watchdog` (*/30), `acuere-cron`
  - The watchdog's local `wrangler.json` was modified this week [file mtime]
- No git commits this week [gitlog-acuere.txt]
- Still blocked [desk-issues.txt; setup-services log; /api/health]:
  - No email-provider key (setup-services reports `resend=false` every day through 11-08)
  - No mailing/remit-to address
  - No LinkedIn app (LINKEDIN_CLIENT_ID/SECRET unset)
  - LIVE_DB=1 not set

### Sales & marketing activity
- COLD_OUTREACH last documented **off** (2026-10-16). Nothing can send anyway: 40 approved emails held in the send queue for "no email provider configured" [acuere/CLAUDE.md; desk-status.json]
- Review queue: 34 drafts waiting for approval in /admin/review; 35 approved emails overdue to send [desk-status.json desk-hygiene]
- Spec jobs: 50 open, 0 published this run (capacity 0) [desk-status.json]
- LinkedIn agent not connected [desk-status.json]
- Desk aliases (pen names, no invented bios) [acuere/CLAUDE.md]:
  - Claudia (Talent Acquisition), Vivian (Business Development), Rebecca (Recruiting)
  - Genevieve (Contractor Services), Eleanor (Executive Search)
  - Margaret (Accounting), Nora (Billing)
- SEO: sitemap, AI-crawler robots, JSON-LD, llms.txt, local job pages (Melbourne, Titusville, Cape Canaveral, Space Coast, clearance), IndexNow (currently 403 on 8 URLs) [acuere/CLAUDE.md; desk-status.json]
- Planned ads: free listings → Google/LinkedIn/Meta (~$45/day) → ChatGPT ads in month 2 [acuere/docs/NEXT_STEPS.md]

### Competitors
- Excluded from pitching as competitors: Robert Half, Kforce, Aerotek, Adecco, Randstad, Manpower, Kelly, Insight Global, TEKsystems, CyberCoders, Motion Recruitment, Apex Systems, Actalent, Allegis, Hays, Michael Page, Korn Ferry, Heidrick, Spencer Stuart, Jobot [acuere/src/lib/sourcing/enrich.ts]
- Site design modeled on Robert Half and Shirley Parsons [acuere/CLAUDE.md]

### Key tools & systems
- Cloudflare: Workers, D1, R2, Workers AI (Gemma 4 / Llama 3.1 8B / bge-m3 embeddings; 9,500-neuron daily cap), Email Routing, WAF (USA-only), Turnstile, Workflows, Browser Rendering [acuere/CLAUDE.md; /api/health]
- Data and sourcing: Adzuna, The Muse, JSearch, Apollo, Hunter, Firecrawl, Wikidata. Resend, Cal.com and Stripe are built but stay off until keys exist [acuere/docs/DATA_FEEDS_SETUP.md]
- Mac desk runner (launchd) ran daily and the quick pass ran every 30 min this week. Nightly offsite D1 backups go to R2 `praesidium-db-backups` [acuere/CLAUDE.md; data/desk-daily.log; data/backups/]
- No GitHub for Acuere (decision 2026-10-17) [acuere/CLAUDE.md]
- Owner finance in Idoneity admin under `ent_acuere` [acuere/docs/OWNER_CONSOLE.md]

### Regulatory / compliance notes
- Florida: minimum wage $15.00/hr from 2026-09-30; no state employment-agency license; E-Verify for 25+ staff; CHOICE Act noncompetes up to 4 years [acuere/docs/compliance/florida-ledger.md]
- Florida new-hire reporting also covers independent contractors paid $600+ in a calendar year (reported to the FL Dept. of Revenue). The repo ledger doesn't mention it [https://www.constangy.com/newsroom/newsletters/Florida-expands-requirement-for-reporting-new-hires-independent-contractors-to-Department-of-Revenue]
- Federal independent-contractor rule: DOL proposed (2026-02-26) rescinding the 2024 rule in favor of a modified 2021 "economic reality" framework. Comments closed 2026-04-28. **No final rule confirmed as of 2026-11-08** [https://www.jdsupra.com/legalnews/dol-publishes-proposed-rule-to-rescind-1320616/; WebSearch 2026-11-08]
- TCPA: the FCC revoke-all rule starts 2027-01-31. FL FTSA: calls 8am–8pm, max 3 per 24h; no autodialer or AI voice to cell phones; no cold texts [acuere/docs/compliance/florida-ledger.md; docs/COLD_CALLING.md]
- CAN-SPAM: a postal address and one-click unsubscribe are required; no sends to Canada/EU/UK; warm-up caps 15/30/50 per day, then 80 [acuere/CLAUDE.md]
- 1099/W-9: payouts held until a W-9 is on file; 1099-NEC threshold $2,000 from 2026; CA forced to W-2; 30% tax reserve [acuere/CLAUDE.md]
- EEO footer; pay-range rules by state; ITAR/clearance screening only when the posting requires it; client referrers certify they have no hiring role [acuere/CLAUDE.md]
- Before the first placement: attorney, CPA, GL + E&O insurance, payroll/EOR partner [acuere/docs/NEXT_STEPS.md]

## Changed this week
- NEW: "BD pitch drafts" fails on a `sourced_postings` query; 0 pitches drafted from 1,471 new postings in 3 days [acuere/data/desk-status.json; desk-issues.txt]
- NEW: the deploy-gate scenario backtest is FAILING (98/101) and tests are failing, both last run ~11-02, so auto-deploys are gated [desk-status.json CTO brief]
- Queue now visible: 36 pending approvals live, 34 drafts awaiting review, 40 approved emails held for "no email provider" [/api/health; desk-status.json]
- Pitch re-screen: 39 queued pitches, all in lane, estimated fees $1.47M (10-17: 31 / $1.13M) [desk-status.json]
- Pool still 1 candidate; 16,717 live postings sourced; daily target and rescreen CSVs written 11-02 → 11-08 [desk-status.json; data/research/]
- IndexNow returns 403 for 8 URLs; external backup drive unplugged (R2 offsite backup still ran) [desk-status.json]
- Live AI model shown as Gemma 4 26B on Workers AI [/api/health]
- Regulatory: no final DOL independent-contractor rule found as of 11-08 (its target was October 2026) [WebSearch]
- Unchanged: no git commits; email provider stub; footer "Acuere Talent, LLC"; no pricing on site

## Open questions for Tyler
- 40 approved emails and 34 drafts are piling up, and nothing can send without an email-provider key and mailing address. When will those be set, and when should COLD_OUTREACH come back on? Should stale drafts be cleared first?
- The pool has 1 candidate against 16,717 sourced postings. Is candidate sourcing (resumes, job-board posting, LinkedIn app) the priority over more employer pitches?
- The deploy-gate backtest (98/101) and the BD pitch-drafts step are both failing. Do you want an engineering session to fix them, given that finished work can't auto-deploy until the gate is green?
- Which fee applies to trades clients: the 12% in estimates or the 19.5% / 90-day terms line? And what target gross margin should contract placements hit?
- The footer says "Acuere Talent, LLC", but Sunbiz has no Acuere entity. When will it be filed, and which name should the site use until then?
