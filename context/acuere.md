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
## Auto facts (synced 2026-11-01)
### What it is / offer
- Specialist recruiting for aerospace, defense, industrial and construction employers. Places contract engineers, technicians and safety staff (1099 or W-2) and runs confidential direct-hire searches. Headquartered on Florida's Space Coast, recruiting nationwide [acuere/src/lib/site-facts.ts; acuere/CLAUDE.md 2026-10-15; https://acueretalent.com/]
- Services: contract and contract-to-hire; direct-hire search ("a few searches at a time"); executive/leadership search; confidential replacement searches; relocation help [acuere/CLAUDE.md; https://acueretalent.com/]
- Live headline (unchanged): "Specialist recruiting for the people who build, test and launch." Homepage mentions per diem and "One invoice a week" for contract work, with no amounts [https://acueretalent.com/, 2026-11-01]
- Entity: README says "Acuere, LLC (pending amendment to Acuere Talent, LLC)" [acuere/README.md]. No Acuere entity on Sunbiz ("planned") [idoneity-cms/docs/COMPLIANCE_CALENDAR.md]. Live footer: "© 2026 Acuere Talent, LLC. All rights reserved." [https://acueretalent.com/, 2026-11-01]

### Customers & market
- No placements recorded: 0 perm, 0 contract, $0 booked, $0 AR, 1 application. The file's mtime is 2026-10-24, but its contents are still `generated_at` 2026-07-17 [acuere/data/analytics/latest.json]
- Last documented pool: 1 candidate; 416 drafted emails waiting on the email provider (as of 2026-10-17) [acuere/docs/NEXT_STEPS.md]
- Pitch re-screen (2026-10-17) cut the queue from 677 to 31 and estimated fees from $37.3M to $1.13M [acuere/CLAUDE.md]
- Live /jobs: 51 roles, all "Confidential client", no pay shown. 14 are clearly off-lane: CFO, revenue marketing, 3 automotive service tech roles, 2 CRNA roles, clinical ops, neurology account director, ambulatory business manager, digital-audio content, CRE investment analytics, and 2 tax roles [https://acueretalent.com/jobs, 2026-11-01]
- Target lanes: aerospace/defense/industrial/construction only; healthcare, finance, education, marketing, sales and software are never pitched [acuere/src/lib/sourcing/lanes.ts via CLAUDE.md]

### Pricing (as published)
- Website: no fees, rates or pay ("Don't show pricing. Ever."). Re-verified 2026-11-01: none on the home page or /jobs. Candidates are never charged [acuere/CLAUDE.md; https://acueretalent.com/]
- Employer emails and referral intros carry one terms line: direct hire 19.5% of first-year base salary, 90-day replacement guarantee; contract billed hourly at a per-role rate [acuere/CLAUDE.md; src/lib/automation/email-templates.ts]
- DB column default is still 2000 bps (20%); code always passes 19.5% [acuere/CLAUDE.md]
- Trades tier: 12% fee in estimates [acuere/CLAUDE.md; src/lib/sourcing/fee-tier.ts]
- Internal defaults (not published): 17% expense markup; 4% veteran-owned-client discount; net-7 invoices; 14% W-2 burden; contract pitch floor $28/hr; direct-hire pitch floor $15k estimated fee [acuere/CLAUDE.md]
- Client invoices go out weekly on Thursday (New York time) [acuere/src/lib/contractors/billing.ts]
- Referral bonuses in code, not shown on the site: $500 per placed candidate (after 90 days); $1,000 per new client (after first paid invoice) [acuere/CLAUDE.md]

### Product / tech status
- Stack: Next.js 16, React 19, Tailwind 4, Drizzle; OpenNext on Cloudflare; D1 `acuere-db`, R2, Workers AI (free allowance only) [acuere/CLAUDE.md; package.json]
- Live health 2026-11-01:
  - `ok: true`, db `d1-binding` ok, latest migration `0029_spec_consent.sql`
  - `site.dbAvailable: false`, so public forms and the portal still use the R2 relay (LIVE_DB not on)
  - email provider `stub`, `live: false`: nothing sends
  [https://acueretalent.com/api/health]
- Workers: `acuere` (site), `acuere-inbound` (email), `acuere-watchdog` (*/30), `acuere-cron` [acuere/CLAUDE.md]
- `acuere-cron`:
  - Crons: */15, hourly, daily 12:00, Mon 13:00, Mon/Wed/Fri 14:00
  - `CLOUD_JOBS` (12): contractor-billing, fee-protection, referrals, interview-scheduler, intake-backlog, sql-match, semantic-match, match-candidates, pitch-drafts, desk-hygiene, sourcing-all, crawl-targets
  - `acuere-nurture` Workflow bound
  - Auto-deploys when workers/cron changes on main
  [acuere/workers/cron/wrangler.json (mtime 2026-10-25); gitlog-acuere.txt]
- No commits since the 2026-10-25 sync. The 3 commits in this week's log (dated 10-25) were already captured last week [runs/2026-11-01/gitlog-acuere.txt]
- Candidate portal (/portal/me/<token>), client/contractor portals, cloud-only intake, spec-pitch consent, Browser Run careers crawl: unchanged since last week [acuere/CLAUDE.md; gitlog 2026-10-19]
- Deploy gate: scenario backtest (101+ scenarios) [acuere/CLAUDE.md]
- Still blocked (last documented 10-17; email still stub live):
  - No email-provider key
  - No mailing/remit-to address
  - Cloudflare token lacks Bot Management
  - No LinkedIn page/app
  - LIVE_DB=1 not set
  [acuere/docs/NEXT_STEPS.md; CLAUDE.md; live /api/health]

### Sales & marketing activity
- COLD_OUTREACH last documented **off** (2026-10-16, "no emailing right now, I don't have an address"). Live email provider is a stub, so nothing can send regardless [acuere/CLAUDE.md; https://acueretalent.com/api/health]
- Desk aliases (pen names, no invented bios):
  - Claudia (Talent Acquisition)
  - Vivian (Business Development)
  - Rebecca (Recruiting)
  - Genevieve (Contractor Services)
  - Eleanor (Executive Search)
  - Margaret (Accounting)
  - Nora (Billing)
  [acuere/CLAUDE.md]
- SEO: sitemap, AI-crawler robots, JSON-LD, llms.txt, local job pages (Melbourne, Titusville, Cape Canaveral, Space Coast, clearance), IndexNow [acuere/CLAUDE.md]
- Planned ads: free listings → Google/LinkedIn/Meta (~$45/day) → ChatGPT ads in month 2 [acuere/docs/NEXT_STEPS.md]
- Praesidium sister-brands footer still absent from the live site [https://acueretalent.com/, 2026-11-01]

### Competitors
- Excluded from pitching as competitors: Robert Half, Kforce, Aerotek, Adecco, Randstad, Manpower, Kelly, Insight Global, TEKsystems, CyberCoders, Motion Recruitment, Apex Systems, Actalent, Allegis, Hays, Michael Page, Korn Ferry, Heidrick, Spencer Stuart, Jobot [acuere/src/lib/sourcing/enrich.ts]
- Site design modeled on Robert Half and Shirley Parsons [acuere/CLAUDE.md]

### Key tools & systems
- Cloudflare: Workers, D1, R2, Workers AI, Email Routing, WAF (USA-only), Turnstile, Workflows, Browser Rendering (Browser Run) [acuere/CLAUDE.md; workers/cron/wrangler.json]
- Data/sourcing: Adzuna, The Muse, JSearch, Apollo, Hunter, Firecrawl, Wikidata. Resend, Cal.com and Stripe are built but off until keys exist [acuere/docs/DATA_FEEDS_SETUP.md]
- Mac desk runner (launchd) for Mac-only steps; nightly offsite D1 backups to R2 `praesidium-db-backups`, plus a weekly local copy [acuere/CLAUDE.md]
- No GitHub for Acuere (decision 2026-10-17) [acuere/CLAUDE.md]
- Owner finance lives in Idoneity admin under `ent_acuere` [acuere/docs/OWNER_CONSOLE.md]

### Regulatory / compliance notes
- Florida: minimum wage $15.00/hr from 2026-09-30; no state employment-agency license; E-Verify for 25+ staff; CHOICE Act noncompetes up to 4 years [acuere/docs/compliance/florida-ledger.md]
- Florida new-hire reporting also covers independent contractors paid $600+ in a calendar year (reported to FL Dept. of Revenue; in effect since 2021). Not found in the repo's compliance ledger [https://www.constangy.com/newsroom/newsletters/Florida-expands-requirement-for-reporting-new-hires-independent-contractors-to-Department-of-Revenue; https://www.hinshawlaw.com/en/insights/blogs/employment-law-observer/florida-boosts-minimum-wage-rate-mandates-reporting-requirements-for-businesses-using-independent-contractors]
- Federal: DOL proposed (2026-02-26) a return to the five-factor "economic reality" independent-contractor test. Its regulatory agenda targets a final rule in October 2026; no source found confirming it is final. This matters for the 1099-first default [https://www.jdsupra.com/legalnews/deja-vu-for-employers-dol-moves-to-4368674/; https://jjkellercompliancenetwork.com/news/wage-and-hour-division-publishes-its-2026-regulatory-agenda]
- TCPA: FCC revoke-all rule starts 2027-01-31. FL FTSA: calls 8am–8pm, max 3 per 24h; no autodialer/AI voice to cell phones; no cold texts [acuere/docs/compliance/florida-ledger.md; docs/COLD_CALLING.md]
- CAN-SPAM: postal address required plus one-click unsubscribe; no sends to Canada/EU/UK; warm-up caps 15/30/50 per day, then 80 [acuere/CLAUDE.md]
- 1099/W-9: payouts held until a W-9 is on file; 1099-NEC threshold $2,000 from 2026; CA forced to W-2; 30% tax reserve [acuere/CLAUDE.md]
- EEO footer; pay-range rules by state; ITAR/clearance screening only when the posting requires it; client referrers certify they have no hiring role [acuere/CLAUDE.md]
- Before the first placement: attorney, CPA, GL + E&O insurance, payroll/EOR partner [acuere/docs/NEXT_STEPS.md]

## Changed this week
- No new commits since the 2026-10-25 sync. The 3 commits in this week's log (dated 10-25: acuere-cron auto-deploy, cloud desk on Cloudflare, an autosave) were already captured last week [gitlog-acuere.txt]
- Live health now reports clearly: `ok: true` on D1 (`d1-binding`), latest migration 0029_spec_consent. It also confirms email provider = `stub` (live: false) and `site.dbAvailable: false`, so forms and the portal are still on the R2 relay [https://acueretalent.com/api/health]
- Off-lane roles on /jobs counted more fully: 14 of 51 (healthcare, automotive, finance/tax, marketing, media, CRE). The total is still 51 [https://acueretalent.com/jobs]
- Regulatory notes added: FL independent-contractor new-hire reporting ($600+, to DOR), which the repo ledger doesn't mention; and the DOL independent-contractor final rule, targeted for October 2026 but with no source confirming it is final [constangy.com; jdsupra.com]
- Unchanged live: headline, no pricing, "© 2026 Acuere Talent, LLC" footer, no sister-brand footer [https://acueretalent.com/]

## Open questions for Tyler
- The live site still shows email provider = stub, so nothing has been able to send since 10-17. When will the email-provider key and mailing address be set, and when do you want COLD_OUTREACH back on?
- 14 of the 51 roles on /jobs are off-lane (CRNA, automotive techs, tax, CFO, marketing), two weeks after the lane re-screen. Should they come off the public board?
- Which fee applies to trades clients: the 12% in estimates or the 19.5% / 90-day terms line? And what target gross margin should contract placements hit?
- The footer says "Acuere Talent, LLC", but Sunbiz has no Acuere entity. When will it be filed, and which name should the site use until then?
- The 1099-first default: has a CPA or attorney reviewed it against the pending DOL five-factor test? And is FL contractor new-hire reporting ($600+) covered by your payroll/EOR plan?
