# bidwell — company context
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
- Bid marketplace: "A bid marketplace where the price is the price." Operated by Idoneity Marketplace, LLC (planned entity) [bidwell/README.md]
- For industrial contractors: geo-radius opportunity search, AI-drafted bids ("Bid with Claude"), client-confirmed awards and platform invoicing; "pay 7.25% only when you win" [bidwell/src/app/page.tsx]
- How it works: map your radius → Bid with Claude → "We confirm with the client" → pay only when you win [bidwell/src/app/page.tsx]
- Integrates with Idoneity: the contractor's PQF, COI and training records attach to bids [bidwell/src/app/page.tsx]
- Live hero unchanged: "Find work in your area." Homepage returned 200 on 2026-11-08 [https://bidwell.praesidium-holdings.workers.dev/]

### Customers & market
- Two sides: small and mid-size industrial contractors; industrial operators and GCs hiring subs [bidwell/src/app/page.tsx]
- Florida first: the BidNet adapter defaults to FL; demo sources are FL DMS, Brevard County, FPL, Port Canaveral and Mosaic [bidwell/src/lib/ingestion/bidnet.ts; web-search.ts]
- The PlanetBids adapter targets CA/Western-US municipal agencies; SAM.gov defaults to construction NAICS 236/237/238 [bidwell/src/lib/ingestion/planetbids.ts; sam-gov.ts]
- No customer, user, bid or award counts in any source. The prod DB is unreachable again (2026-11-08), so it can't be counted [bidwell /api/health]

### Pricing (as published)
- Success fee, tiered by trailing-12-month awarded volume: Starter 7.25% (<$250k) → Established 5.00% ($250k–$1M) → Anchor 3.00% ($1M+) [bidwell/src/lib/fees.ts; live homepage 2026-11-08]
- Annual-prepay lane: flat 3.5% override [bidwell/src/lib/fees.ts; live homepage]
  - The code's default prepay commitment is $1,200/yr; it is not shown on the site [bidwell/src/lib/fees.ts]
- "0 Subscription — no listing fees, ever"; fees "billed 30 days after award via Stripe" [bidwell/src/app/page.tsx; live homepage]
- In code: invoice 30 days after award, Stripe `days_until_due: 14`, account delinquent at >60 days past due → platform access cut [bidwell/src/lib/invoicing.ts]
- No /pricing page [bidwell repo]
- Corporate doc: success-fee collection stays "tracked" (not billed) until a FL construction attorney reviews it [idoneity-cms/CORPORATE_STRUCTURE.md §3]

### Product / tech status
- Stack: Next.js 16.2.9, React 19.2.4, Tailwind v4, Drizzle, Turso (prod) / SQLite (local), Anthropic SDK (Haiku 4.5 default), Stripe, Leaflet/OSM, Mapbox, Playwright [bidwell/package.json; CLAUDE.md]
- Hosting: Cloudflare Worker `bidwell` via OpenNext, only at bidwell.praesidium-holdings.workers.dev; bidwell.com is "not yet bound" [bidwell/DEPLOY.md; wrangler.jsonc]
- **Prod health 2026-11-08 ~22:00 UTC: ok:false, DB not ok, latestMigration null.** It was ok:true on 11-01 after the Turso quota reset. Live /opportunities returns **500 again** [https://bidwell.praesidium-holdings.workers.dev/api/health; live check]
- Secrets set: job, NextAuth, ingest. Not set: Anthropic, admin, SAM.gov [/api/health]
- Prod was at migration 0015 on 11-01; repo migration `0016_invites_questions_reminders.sql` is unapplied [bidwell/drizzle/; runs/2026-11-01]
- Still on Turso; no D1 port in the repo, despite the 2026-10-25 "stay off paid Turso" decision [bidwell/wrangler.jsonc]
- 17 migrations (0000–0016) and 9 scheduled cron jobs; `run-signal-promotion` is not scheduled [bidwell/drizzle; .github/workflows/cron.yml; docs/AI_OPERATIONS.md]
- Stubs: AP payment providers (Bill.com, Modern Treasury, BoA CashPro) not wired; Stripe invoicing is stubbed when the key is unset [bidwell/src/lib/ap/providers/index.ts; src/lib/invoicing.ts]
- Backlog from competitor research: win/loss analytics, contact book, addenda tab, unpublish jobs, RFI log, scope normalization [bidwell/docs/COMPETITOR_RESEARCH_2026-07.md]
- No commits this week, and no files modified since 2026-11-01 [gitlog-bidwell.txt; file mtimes]

### Sales & marketing activity
- CTAs: "Book a walkthrough", "Browse open work", "Post a job", and a waitlist ("Add me to the list") [bidwell/src/app/page.tsx]
- "Book a walkthrough" still opens a mailto to hello@bidwell.com [live homepage 2026-11-08]
- The automated outreach pipeline needs the AI key, which is still unset in prod. It consists of weekly Claude web_search prospect discovery, AI-drafted cold emails and an admin send queue [bidwell/src/lib/outreach/discover.ts; /api/health]
- No record of sent campaigns, social posts or ad spend [repo-wide]

### Competitors
- Named: BuildingConnected, iSqFt/ConstructConnect, PlanHub, SmartBid, Procore, Buildertrend, TradeTapp [bidwell/docs/COMPETITOR_RESEARCH_2026-07.md]
- Cited data points: PlanHub add-ons $91–141/mo; Procore renewal hikes of 12–15%; BuildingConnected's 100-mile free-tier cap [bidwell/docs/COMPETITOR_RESEARCH_2026-07.md]

### Key tools & systems
- Ingestion sources [bidwell/src/lib/ingestion/*.ts]:
  - Government and portals: SAM.gov API, FL DMS scrape, Socrata permits, PlanetBids, BidNet Direct
  - Filings and news: SEC EDGAR full-text, Business Wire / PR Newswire RSS, RSS
  - Search waterfall: Claude web_search → Brave → SerpAPI → demo
- Cloudflare Workers + 2 R2 buckets + Workers Logs; Turso [bidwell/wrangler.jsonc]
- Email: AWS SES → Resend → console stub [bidwell/src/lib/messaging.ts]
- Stripe (success fees), Plaid (read-only), AP automation module [bidwell/src/lib/invoicing.ts; src/lib/ap/providers/plaid.ts]
- AI is metered via `trackedMessagesCreate()` + `ai_usage`, with an `AI_DISABLED` kill switch (currently not disabled). 14 sensitive actions sit behind /autonomy/approvals [bidwell/docs/AI_OPERATIONS.md; /api/health]
- Owner finance lives in Idoneity admin, `entity_id = ent_bidwell` [bidwell/docs/OWNER_CONSOLE.md]

### Regulatory / compliance notes
- Entity: Idoneity Marketplace, LLC is not on Sunbiz (status "planned") [idoneity-cms/docs/COMPLIANCE_CALENDAR.md]
- Success-fee risk: FL Ch. 489 contractor licensing and broker/finder rules. A written opinion from a FL construction attorney is needed before billing [idoneity-cms/CORPORATE_STRUCTURE.md §3]
- Source policy: government open data and vendors' own public bid portals only. Dodge, ConstructConnect, BuildingConnected and Blue Book are banned (ToS); robots.txt is respected; SEC EDGAR needs a descriptive User-Agent [bidwell/.claude/agents/bidwell-ingestion-reviewer.md; src/lib/ingestion/]
- No terms-of-service or privacy pages in the repo [repo-wide]
- Homepage claims with no data source in the repo: "~70% of the draft kept", "12s average AI bid draft", "submit 5x more bids" [bidwell/src/app/page.tsx]

## Changed this week
- **Prod is down again.** /api/health is ok:false with DB not ok (it was ok:true on 11-01), and live /opportunities is 500 again (it was 200 on 11-01). This repeats the 10-18 / 10-25 pattern, and Bidwell is still on Turso [https://bidwell.praesidium-holdings.workers.dev/api/health 2026-11-08]
- Unchanged: no commits or file changes; Anthropic, admin and SAM.gov secrets still unset; homepage, pricing and the hello@bidwell.com walkthrough mailto are the same

## Open questions for Tyler
- Bidwell's DB went down again within a week of the 11-01 Turso reset (third outage in four weeks). Should Bidwell move to D1 now, and should migration 0016 be applied before or as part of that move?
- Are there any real users, posted jobs, bids or awards in the Bidwell DB, or is it all demo data?
- The site says fees are "billed via Stripe", but the corporate doc keeps billing off until a FL construction attorney signs off. Has that review happened? If not, should the site say "tracked, not billed" until it does?
- Is the $1,200/yr prepay commitment in fees.ts the intended price? And do you own bidwell.com? The walkthrough CTA mails hello@bidwell.com.
- Which side comes first, contractors or GCs/operators? And what is the first-year target for awarded-contract dollars?
