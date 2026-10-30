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
## Auto facts (synced 2026-10-25)
### What it is / offer
- Specialist recruiting for aerospace, defense, industrial and construction employers. Places contract engineers, technicians and safety staff (1099 or W-2) and runs confidential direct-hire searches. Based on Florida's Space Coast, recruiting nationwide [acuere/src/lib/site-facts.ts; https://acueretalent.com/]
- Services: contract and contract-to-hire; direct-hire search ("a few searches at a time"); executive/leadership search; confidential replacement searches; relocation help [acuere/CLAUDE.md; https://acueretalent.com/]
- Live headline (unchanged): "Specialist recruiting for the people who build, test and launch." No counters, testimonials or named people [https://acueretalent.com/, 2026-10-25]
- Live nav: Specialties, Insights, Current searches (/jobs), Contract talent (/hire), Discuss a search (/hire), Portal (/portal); footer adds Client portal / Contractor portal: hours [https://acueretalent.com/]
- Entity: "Acuere, LLC (pending amendment to Acuere Talent, LLC)" [acuere/README.md]. Not on Sunbiz ("planned") [idoneity-cms/docs/COMPLIANCE_CALENDAR.md]. Live footer reads "© 2026 Acuere Talent, LLC" [https://acueretalent.com/]

### Customers & market
- No placements recorded: 0 perm, 0 contract, $0 booked, 1 application. The file was refreshed 2026-10-24, but its contents are still generated 2026-07-17 [acuere/data/analytics/latest.json]
- As of 2026-10-17: 1 candidate in the pool; 416 drafted emails waiting on the email-provider key [acuere/docs/NEXT_STEPS.md]
- Pitch re-screen (2026-10-17) cut the queue from 677 to 31 and estimated fees from $37.3M to $1.13M [acuere/CLAUDE.md]
- Live /jobs: 51 roles, all "Confidential client", no pay shown. Off-lane roles still listed (e.g., CFO, revenue marketing, CRNA, automotive service technician, digital-audio content) [https://acueretalent.com/jobs, 2026-10-25]

### Pricing (as published)
- Website: no fees or rates ("Don't show pricing. Ever." on the site); candidates never charged [acuere/CLAUDE.md; https://acueretalent.com/]
- Employer emails and referral intros carry one terms line: direct hire 19.5% of first-year base salary, 90-day replacement guarantee; contract billed hourly at a per-role rate [acuere/CLAUDE.md; src/lib/automation/email-templates.ts]
- DB column default still 2000 bps (20%); code always passes 19.5% [acuere/CLAUDE.md]
- Trades tier: 12% fee in estimates [acuere/CLAUDE.md; src/lib/sourcing/fee-tier.ts]
- Internal defaults (not published): 17% expense markup; 4% veteran-owned-client discount; invoices net 7; 14% W-2 burden; contract pitch floor $28/hr; direct-hire pitch floor $15k est. fee [acuere/CLAUDE.md]
- Client invoices now go out once a week, on Thursday (New York time); other billing steps still run daily [acuere/src/lib/contractors/billing.ts; gitlog 2026-10-19]
- Referral bonuses in code: $500 per placed candidate (after 90 days); $1,000 per new client (after first paid invoice); not shown on site [acuere/CLAUDE.md]

### Product / tech status
- Stack: Next.js 16, React 19, Tailwind 4, Drizzle; OpenNext on Cloudflare; D1 `acuere-db` (live since 2026-10-17), R2, Workers AI (free allowance only) [acuere/CLAUDE.md; package.json]
- Workers: `acuere` (site), `acuere-inbound` (email), `acuere-watchdog` (*/30), `acuere-cron` (hourly cloud desk + `acuere-nurture` Workflow) [acuere/CLAUDE.md; workers/cron/wrangler.json]
- **Cloud desk expanded this week:** acuere-cron `CLOUD_JOBS` now lists 12 jobs: contractor-billing, fee-protection, referrals, interview-scheduler, intake-backlog, sql-match, semantic-match, match-candidates, pitch-drafts, desk-hygiene, sourcing-all, crawl-targets. Commit 10-25: "run every network-only desk step on Cloudflare". acuere-cron auto-deploys when workers/cron changes on main [acuere/workers/cron/wrangler.json; gitlog 2026-10-24/25]
- Contractor billing runs on Cloudflare alongside the Mac desk for one cycle, with a double-invoice guard [gitlog 2026-10-19]
- Cloud-only intake: /join writes D1+R2 from the Worker; inbound email keeps attachments; new employers routed as client leads; reply agent on acuere-cron [gitlog 2026-10-19]
- Candidate portal: /portal Candidates card and /portal/me/<token> (open jobs, one-click apply, application status, resume replace, My work) [gitlog 2026-10-19; live /portal 200]
- Persona/voice stored in the database so Worker jobs use the same voice as the Mac [gitlog 2026-10-19]
- Cloudflare Browser Run renders JS careers pages for sourcing; DESK_SKIP_STEPS lets the Mac skip steps moved to the cloud [gitlog 2026-10-19]
- Spec-pitch consent: candidates are asked automatically whether they already applied to an employer before any pitch [gitlog 2026-10-19]
- Admin login: daily lockout no longer blocks previously-successful IPs [gitlog 2026-10-18]
- Deploy gate: scenario backtest (101+ scenarios); browser-run scenarios fixed 2026-10-19 [gitlog]
- Still blocked (last documented 10-17): email-provider key missing (nothing sends); mailing/remit-to address not set; Cloudflare token lacks Bot Management; LinkedIn page/app not set up; LIVE_DB=1 not set (forms/portal on R2 relay until set) [acuere/docs/NEXT_STEPS.md; CLAUDE.md]

### Sales & marketing activity
- COLD_OUTREACH last documented **off** (2026-10-16, "no emailing right now, I don't have an address"); cold mail also held until a real mailing address is set. Live env value not verified [acuere/CLAUDE.md]
- Desk aliases (pen names, no invented bios): Claudia (Talent Acquisition), Vivian (Business Development), Rebecca (Recruiting), Genevieve (Contractor Services), Eleanor (Executive Search), Margaret (Accounting), Nora (Billing) [acuere/CLAUDE.md]
- Role mailboxes routed through `acuere-inbound` [acuere/CLAUDE.md]
- SEO: sitemap, AI-crawler robots, JSON-LD, llms.txt, local job pages (Melbourne, Titusville, Cape Canaveral, Space Coast, clearance); IndexNow fixed [acuere/CLAUDE.md]
- Planned ads: free listings → Google/LinkedIn/Meta (~$45/day) → ChatGPT ads in month 2 [acuere/docs/NEXT_STEPS.md]
- Praesidium sister-brands footer still absent from the live site [https://acueretalent.com/]

### Competitors
- Excluded from pitching as competitors: Robert Half, Kforce, Aerotek, Adecco, Randstad, Manpower, Kelly, Insight Global, TEKsystems, CyberCoders, Motion Recruitment, Apex Systems, Actalent, Allegis, Hays, Michael Page, Korn Ferry, Heidrick, Spencer Stuart, Jobot [acuere/src/lib/sourcing/enrich.ts]
- Site design modeled on Robert Half and Shirley Parsons [acuere/CLAUDE.md]

### Key tools & systems
- Cloudflare: Workers, D1, R2, Workers AI, Email Routing, WAF (USA-only), Turnstile, Workflows, Browser Rendering (Browser Run) [acuere/CLAUDE.md; workers/cron/wrangler.json]
- Data/sourcing: Adzuna, The Muse, JSearch, Apollo, Hunter, Firecrawl, Wikidata. Built but off until keys are added: Resend, Cal.com, Stripe [acuere/docs/DATA_FEEDS_SETUP.md]
- Mac desk runner (launchd) still runs Mac-only steps; offsite D1 backups to R2 nightly + weekly local copy [acuere/CLAUDE.md]
- No GitHub for Acuere (by decision 2026-10-17) [acuere/CLAUDE.md]
- Owner finance in Idoneity admin, `ent_acuere` [acuere/docs/OWNER_CONSOLE.md]

### Regulatory / compliance notes
- Florida: minimum wage $15.00/hr from 2026-09-30; no state employment-agency license; E-Verify for 25+ staff; CHOICE Act noncompetes up to 4 years [acuere/docs/compliance/florida-ledger.md]
- TCPA: FCC revoke-all rule starts 2027-01-31. FL FTSA: calls 8am–8pm, max 3 per 24h; no autodialer/AI voice to cells, no cold texts [acuere/docs/compliance/florida-ledger.md; docs/COLD_CALLING.md]
- CAN-SPAM: postal address required, one-click unsubscribe; no Canada/EU/UK sends; warm-up caps 15/30/50 per day, then 80 [acuere/CLAUDE.md]
- 1099/W-9: payouts held until W-9 on file; 1099-NEC threshold $2,000 from 2026; CA forced W-2; 30% tax reserve [acuere/CLAUDE.md]
- EEO footer; pay-range rules by state; ITAR/clearance screening only when posting requires; client referrers certify no hiring role [acuere/CLAUDE.md]
- Before the first placement: attorney, CPA, GL + E&O insurance, payroll/EOR partner [acuere/docs/NEXT_STEPS.md]

## Changed this week
- The cloud desk grew. acuere-cron now runs 12 desk jobs on Cloudflare, including sourcing-all, pitch-drafts, desk-hygiene, match-candidates and crawl-targets. Last week CLAUDE.md said those had to stay on the Mac. acuere-cron now auto-deploys when workers/cron changes on main (10-24/10-25) [gitlog-acuere.txt; workers/cron/wrangler.json]
- Client invoices now go out only on Thursday (New York time). Contractor billing ran on Cloudflare for one cycle with a double-invoice guard (10-19) [gitlog; src/lib/contractors/billing.ts]
- Candidate portal added: /portal/me/<token> with open jobs, one-click apply, status, resume replace and My work (10-19) [gitlog; live /portal 200]
- Cloud-only intake: /join writes D1+R2 from the Worker, inbound email keeps attachments, new employers are routed as client leads, and the reply agent runs on acuere-cron (10-19) [gitlog]
- Spec-pitch consent: candidates are asked whether they already applied before any pitch goes out (10-19) [gitlog]
- Persona/voice moved into the database; Browser Run added for JS careers pages; DESK_SKIP_STEPS added (10-19) [gitlog]
- Admin login lockout fix (10-18) [gitlog]
- Unchanged live: same headline, no pricing, 51 confidential roles with off-lane roles still listed, "© 2026 Acuere Talent, LLC" footer [https://acueretalent.com, 2026-10-25]

## Open questions for Tyler
- When will the mailing address and email-provider key be set and COLD_OUTREACH turned on? Nothing has been able to send since the 10-17 count of 416 waiting drafts.
- Which fee applies to trades clients: 12% (used in estimates) or the 19.5% / 90-day terms line? And what target gross margin should contract placements hit?
- The live footer still says "© 2026 Acuere Talent, LLC", and Sunbiz has no Acuere entity. When will it be filed, and should the site use another name until then?
- Off-lane roles (CFO, revenue marketing, CRNA, automotive tech) are still on /jobs a week after the lane re-screen. Should they be pulled?
- Is the Mac desk being retired? 12 jobs now run on Cloudflare (including sourcing and desk-hygiene, which were "stay on the Mac" last week). And when should LIVE_DB=1 be set so forms and the portal stop relaying through R2?
