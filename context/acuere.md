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
## Auto facts (synced 2026-10-18)
### What it is / offer
- Specialist recruiting for aerospace, defense, industrial and construction employers. It places contract engineers, technicians and safety staff (1099 or W-2) and runs confidential direct-hire searches. Based on Florida's Space Coast, recruiting nationwide [acuere/src/lib/site-facts.ts; https://acueretalent.com/]
- Services: contract and contract-to-hire; direct-hire search ("a small number of searches at a time"); executive/leadership search; confidential replacement searches; relocation help [acuere/src/lib/site-facts.ts; https://acueretalent.com/hire]
- Live headline: "Specialist recruiting for the people who build, test and launch." Boutique repositioning on 2026-10-17: no counters, testimonials or named people [https://acueretalent.com/; acuere/CLAUDE.md]
- Site paths: /hire ("Discuss a search"), /join ("Introduce yourself"), /jobs; /employers is a 404 [https://acueretalent.com]
- Entity: "Acuere, LLC (pending amendment to Acuere Talent, LLC)" [acuere/README.md]. Not on Sunbiz ("planned") [idoneity-cms/docs/COMPLIANCE_CALENDAR.md]. Live footer reads "© 2026 Acuere Talent, LLC" [https://acueretalent.com/]

### Customers & market
- No placements recorded: 0 perm, 0 contract, $0 booked, 1 application [acuere/data/analytics/latest.json, generated 2026-07-17]
- As of 2026-10-17: 1 candidate in the pool; 416 drafted emails waiting on the email-provider key [acuere/docs/NEXT_STEPS.md]
- Pitch re-screen (2026-10-17) cut the queue from 677 to 31 and estimated fees from $37.3M to $1.13M; many earlier pitches were outside the four target industries [acuere/CLAUDE.md]
- About 359 pitches drafted before 2026-10-12 lack the one-click engage link [acuere/docs/NEXT_STEPS.md]
- Live /jobs: 51 roles, all "Confidential client", no pay shown. Some are off-target (e.g., revenue marketing, CRNA, automotive tech) [https://acueretalent.com/jobs]

### Pricing (as published)
- Website: no fees or rates. FAQ: "Terms are discussed directly with each client"; "Candidates are never charged anything" [https://acueretalent.com/faq; /hire; /llms.txt]
- Employer emails, /hire acknowledgement and referral intros carry one terms line: direct hire 19.5% of first-year base salary, invoiced at start, 90-day replacement guarantee; contract (1099/W-2) billed hourly at a per-role rate on one weekly invoice [acuere/src/lib/automation/email-templates.ts; src/app/api/hire/route.ts; src/lib/referrals.ts]
- Direct-hire fee changed to 19.5% on 2026-10-17; the DB column default is still 2000 bps (20%) [acuere/CLAUDE.md; src/lib/automation/agreements.ts]
- Trades tier: 12% fee used in estimates, 30-day guarantee [acuere/src/lib/roles/market.ts; src/lib/pipeline/hire.ts]
- Internal defaults (not published): 17% expense markup; 4% veteran-owned-client discount; invoices net 7; 14% W-2 burden; contract pitch floor $28/hr pay; direct-hire pitch floor $15k estimated fee [acuere/src/lib/contractors/billing.ts; src/lib/sourcing/fee-tier.ts]
- Referral bonuses in code: $500 per placed candidate (after 90 days); $1,000 per new client (after first paid invoice). Amounts removed from live /refer [acuere/src/lib/referrals.ts; CLAUDE.md]

### Product / tech status
- Stack: Next.js 16.2.9, React 19.2.4, Tailwind 4, Drizzle, zod; OpenNext for Cloudflare + wrangler 4 [acuere/package.json]
- Worker `acuere` on acueretalent.com + www; D1 `acuere-db`, R2 uploads/cache, Workers AI, edge form rate limit; plus `acuere-inbound`, `acuere-watchdog` (every 30 min) and `acuere-cron` workers [acuere/wrangler.jsonc; CLAUDE.md]
- D1 cut-over 2026-10-17 (10.5k rows). Forms and portal still relay through R2 until LIVE_DB=1 [acuere/CLAUDE.md]
- AI moved to Cloudflare Workers AI on the free allowance (capped at 9,500 of 10,000 neurons per day). Matching uses SQL FTS5/bm25 + bge-m3 embeddings. The Anthropic SDK is still in package.json but no longer imported [acuere/docs/WORKERS_AI.md; package.json]
- Client + contractor portal (timesheets, approvals, invoices) renders from R2 snapshots; actions queue and apply on the next desk pass [acuere/gitlog 2026-10-17]
- Deploy gate: scenario backtest passed 105/105 on 2026-10-18 [acuere/CLAUDE.md]
- Not live yet: nurture Workflow (pilot, not deployed); Turnstile (enforced only once its key is set); cloud jobs list is empty [acuere/CLAUDE.md]
- Blocked: email-provider key missing (nothing sends); mailing and remit-to addresses not set; Cloudflare token lacks Bot Management permission; LinkedIn page/app not set up; repo not pushed to GitHub [acuere/docs/NEXT_STEPS.md]

### Sales & marketing activity
- COLD_OUTREACH last set **off** 2026-10-16 ("no emailing right now, I don't have an address"). Cold mail is also held until a real mailing address is set. Live env value not verified [acuere/CLAUDE.md; src/lib/automation/dispatcher.ts]
- Owner removed from website and outbound email. Seven desk aliases, pen names with no invented bios: Claudia (Talent Acquisition), Vivian (Business Development), Rebecca (Recruiting), Genevieve (Contractor Services), Eleanor (Executive Search), Margaret (Accounting, weekly W-9 reminders), Nora (Billing) [acuere/src/lib/mailboxes.ts; CLAUDE.md]
- Role mailboxes (talent@, recruiting@, contractors@, ap@, ar@/billing@, referrals@, hello@, press@, privacy@, optout@, etc.) route through the `acuere-inbound` worker [acuere/CLAUDE.md]
- SEO: sitemap, AI-crawler robots, JSON-LD, llms.txt; local job pages (Melbourne, Titusville, Cape Canaveral, Space Coast, clearance); IndexNow 422 fixed; OpenSEO audit found 50 pages, no errors [acuere/CLAUDE.md]
- Job board: up to 50 open roles nationwide, US-only [acuere/gitlog 2026-10-17]
- Admin Growth workspace with Cloudflare traffic + all lead sources [acuere/gitlog 2026-10-17]
- Planned ads: free listings → Google/LinkedIn/Meta (about $45/day) → ChatGPT ads in month 2 [acuere/docs/NEXT_STEPS.md]
- Praesidium sister-brands footer removed from the site 2026-10-17 [acuere/gitlog]

### Competitors
- Excluded from pitching as competitors: Robert Half, Kforce, Aerotek, Adecco, Randstad, Manpower, Kelly, Insight Global, TEKsystems, CyberCoders, Motion Recruitment, Apex Systems, Actalent, Allegis, Hays, Michael Page, Korn Ferry, Heidrick, Spencer Stuart, Jobot [acuere/src/lib/sourcing/enrich.ts]
- Site design modeled on Robert Half and Shirley Parsons; "Shirley Parsons lane" = EHS/engineering roles [acuere/CLAUDE.md; src/lib/seo/specialties.ts]

### Key tools & systems
- Cloudflare: Workers, D1, R2, Workers AI, Email Routing, WAF (USA-only), Turnstile, Workflows, Browser Rendering [acuere/wrangler.jsonc; CLAUDE.md]
- Data/sourcing: Adzuna, The Muse, JSearch, Apollo, Hunter, Firecrawl, Wikidata. Built but off until keys are added: Resend, Cal.com, Stripe [acuere/docs/DATA_FEEDS_SETUP.md; docs/GO_LIVE_RUNBOOK.md]
- Mac desk runner (launchd daily + every 30 min). Offsite D1 backups: R2 nightly + weekly local copy [acuere/CLAUDE.md; gitlog 2026-10-18]
- Owner finance in Idoneity admin, `ent_acuere` [acuere/docs/OWNER_CONSOLE.md]

### Regulatory / compliance notes
- Florida: minimum wage $15.00/hr from 2026-09-30; no state employment-agency license; E-Verify for employers with 25+ staff; CHOICE Act noncompetes up to 4 years [acuere/docs/compliance/florida-ledger.md]
- TCPA: opt-outs stop all marketing; FCC revoke-all rule starts 2027-01-31. FL FTSA: calls 8am–8pm, max 3 per 24h; hand-dial only, no autodialer/AI voice to cells, no cold texts [acuere/docs/compliance/florida-ledger.md; docs/COLD_CALLING.md]
- CAN-SPAM: postal address required, one-click unsubscribe headers; no Canada/EU/UK sends; warm-up caps of 15/30/50 per day, then 80 [acuere/CLAUDE.md]
- 1099/W-9: substitute W-9 with encrypted tax ID; payouts held until W-9 on file; 1099-NEC threshold $2,000 from 2026; CA forced to W-2, warnings for MA/NJ/IL/CT/VT/NH; 30% tax reserve [acuere/CLAUDE.md]
- EEO footer live; pay-range rules by state; ITAR/clearance screening only when the posting requires it; client referrers certify no hiring role (anti-kickback) [acuere/src/components/SiteFooter.tsx; CLAUDE.md]
- Before the first placement: attorney, CPA, GL + E&O insurance, payroll/EOR partner [acuere/docs/NEXT_STEPS.md]

## Changed this week
- First sync — no previous context file existed, so there is no baseline to compare against. All facts above are new. Notable changes in this week's commits [gitlog-acuere.txt]:
- Boutique repositioning: no counters, testimonials or named people. Owner removed from the website and outbound email; seven desk aliases and role mailboxes added (2026-10-17)
- Pricing split: website is price-free; employer emails carry one terms line. Direct-hire fee set to 19.5%; no public pay anywhere (2026-10-17)
- Praesidium sister-brands footer removed from the Acuere site (2026-10-17)
- Moved to D1 (2026-10-17); AI moved to Workers AI free tier; resume↔JD matching added; job board expanded to 50 roles nationwide
- Client + contractor portal served from R2 snapshots (2026-10-17)
- 101-scenario backtest added as a deploy gate (2026-10-17); 105/105 passing 2026-10-18
- Offsite D1 backups, Turnstile, edge rate limit, admin server-action auth, nurture Workflow pilot (2026-10-18)

## Open questions for Tyler
- When will the mailing address and email-provider key be set and COLD_OUTREACH turned on? 416 drafts are waiting.
- Which fee applies to trades clients: the 12% fee with a 30-day guarantee used in estimates, or the 19.5% with 90 days in the terms line? And what target gross margin should contract placements hit?
- The live footer says "© 2026 Acuere Talent, LLC", but Sunbiz has no Acuere entity. When will it be filed or amended, and should the site use a different name until then?
- Is Acuere now exempt from the five-brand family footer rule, since the footer was removed on 10-17? Or should it come back?
- Is energy still a target industry? The README lists it, but the site shows aerospace, defense, industrial and construction only. Should off-target roles (CRNA, marketing, automotive) be pulled from /jobs?
