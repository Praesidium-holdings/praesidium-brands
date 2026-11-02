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
## Auto facts (synced 2026-11-01)
### What it is / offer
- Bid marketplace — "A bid marketplace where the price is the price." Operated by Idoneity Marketplace, LLC (planned entity) [bidwell/README.md]
- For industrial contractors: geo-radius opportunity search, AI-drafted bids ("Bid with Claude"), client-confirmed awards, platform invoicing; "pay 7.25% only when you win" [bidwell/src/app/page.tsx]
- Loop: map your radius → Bid with Claude → "We confirm with the client" → pay only when you win [bidwell/src/app/page.tsx]
- Integrates with Idoneity: contractor PQF, COI, training records attach to bids [bidwell/src/app/page.tsx]
- Live hero unchanged: "Find work in your area. Bid on what you can actually take." Homepage returned 200 on 2026-11-01 [https://bidwell.praesidium-holdings.workers.dev/]

### Customers & market
- Two sides: small/mid-size industrial contractors; industrial operators + GCs hiring subs [bidwell/src/app/page.tsx]
- Florida primary: BidNet adapter defaults to FL; demo sources FL DMS, Brevard County, FPL, Port Canaveral, Mosaic [bidwell/src/lib/ingestion/bidnet.ts; web-search.ts]
- PlanetBids adapter targets CA/Western-US municipal agencies; SAM.gov defaults to construction NAICS 236/237/238 [bidwell/src/lib/ingestion/planetbids.ts; sam-gov.ts]
- No customer, user, bid or award counts in any source. Prod DB is reachable again, but no counts were queried this run [bidwell /api/health 2026-11-01]
- Prod approval queue: 0 pending; AI calls in last 24h: 0 [https://bidwell.praesidium-holdings.workers.dev/api/health]

### Pricing (as published)
- Success fee, volume-tiered on trailing-12-month awarded: Starter 7.25% (<$250k) → Established 5.00% ($250k–$1M) → Anchor 3.00% ($1M+) [bidwell/src/lib/fees.ts; live homepage "drops to 5% then 3% as you win more"]
- Annual-prepay lane: flat 3.5% override [bidwell/src/lib/fees.ts; live homepage]. Code default prepay commitment is $1,200/yr; not shown on site [bidwell/src/lib/fees.ts]
- "0 Subscription — no listing fees, ever"; fees "billed 30 days after award via Stripe" [bidwell/src/app/page.tsx; live homepage]
- Code: invoice 30 days after award, Stripe `days_until_due: 14`, delinquent at >60 days past due → platform access cut [bidwell/src/lib/invoicing.ts]
- No /pricing page [bidwell repo]
- Corporate doc: success-fee collection stays "tracked" (not billed) until a FL construction attorney reviews [idoneity-cms/CORPORATE_STRUCTURE.md §3]

### Product / tech status
- Stack: Next.js 16.2.9, React 19.2.4, Tailwind v4, Drizzle, Turso (prod) / SQLite (local), Anthropic SDK (Haiku 4.5 default), Stripe, Leaflet/OSM, Mapbox, Playwright [bidwell/package.json; CLAUDE.md]
- Hosting: Cloudflare Worker `bidwell` via OpenNext; only at bidwell.praesidium-holdings.workers.dev; bidwell.com "not yet bound" [bidwell/DEPLOY.md; wrangler.jsonc]
- Prod health 2026-11-01: **ok:true, DB ok**, latestMigration `0015_ai_usage.sql`. Anthropic, admin-secret and SAM.gov keys are still not configured. Job, NextAuth and ingest secrets are set [https://bidwell.praesidium-holdings.workers.dev/api/health]
- Prod is one migration behind the repo: `0016_invites_questions_reminders.sql` exists locally but is not applied [bidwell/drizzle/; /api/health]
- Live /opportunities now returns HTTP 200; it returned 500 on 10-18 and 10-25 [live check 2026-11-01]
- Recovery coincides with the scheduled 2026-11-01 Turso quota reset. No Bidwell commit explains it [idoneity-cms/.claude/worktrees/d1-port/docs/D1_CUTOVER.md; runs/2026-11-01/gitlog-bidwell.txt]
- Still on Turso. No D1 port is in the repo, despite the 2026-10-25 "stay off paid Turso" decision [bidwell/wrangler.jsonc; praesidium context 2026-10-25]
- 17 migrations (0000–0016); 9 scheduled cron jobs; `run-signal-promotion` not scheduled [bidwell/drizzle; .github/workflows/cron.yml; docs/AI_OPERATIONS.md]
- Stubs: AP payment providers (Bill.com, Modern Treasury, BoA CashPro) not wired; Stripe invoicing stubbed when key unset [bidwell/src/lib/ap/providers/index.ts; src/lib/invoicing.ts]
- Backlog from competitor research: win/loss analytics, contact book, addenda tab, unpublish jobs, RFI log, scope normalization [bidwell/docs/COMPETITOR_RESEARCH_2026-07.md]
- No commits in the week to 2026-11-01. Most recent top-level file changes date from Sep 12 [runs/2026-11-01/gitlog-bidwell.txt; file mtimes]

### Sales & marketing activity
- CTAs: "Book a walkthrough", "Browse open work", "Post a job", waitlist "Add me to the list" [bidwell/src/app/page.tsx]
- "Book a walkthrough" still opens a mailto to hello@bidwell.com [live homepage 2026-11-01]
- Automated outreach pipeline (weekly Claude web_search prospect discovery, AI-drafted cold emails, admin send queue) needs the AI key, which is still unset in prod [bidwell/src/lib/outreach/discover.ts; /api/health]
- No record of sent campaigns, social posts or ad spend [repo-wide]

### Competitors
- Named: BuildingConnected, iSqFt/ConstructConnect, PlanHub, SmartBid, Procore, Buildertrend, TradeTapp [bidwell/docs/COMPETITOR_RESEARCH_2026-07.md]
- Cited points: PlanHub add-ons $91–141/mo; Procore renewal hikes 12–15%; BuildingConnected 100-mile free-tier cap [bidwell/docs/COMPETITOR_RESEARCH_2026-07.md]

### Key tools & systems
- Ingestion: SAM.gov API, RSS, Claude web_search → Brave → SerpAPI → demo waterfall, FL DMS scrape, Socrata permits, SEC EDGAR full-text, Business Wire / PR Newswire RSS, PlanetBids, BidNet Direct [bidwell/src/lib/ingestion/*.ts]
- Cloudflare Workers + 2 R2 buckets + Workers Logs; Turso [bidwell/wrangler.jsonc]
- Email: AWS SES → Resend → console stub [bidwell/src/lib/messaging.ts]
- Stripe (success fees), Plaid read-only, AP automation module [bidwell/src/lib/invoicing.ts; src/lib/ap/providers/plaid.ts]
- AI metered via `trackedMessagesCreate()` + `ai_usage`; `AI_DISABLED` kill switch (currently not disabled); 14 sensitive actions behind /autonomy/approvals [bidwell/docs/AI_OPERATIONS.md; /api/health]
- Owner finance in Idoneity admin, `entity_id = ent_bidwell` [bidwell/docs/OWNER_CONSOLE.md]

### Regulatory / compliance notes
- Entity: Idoneity Marketplace, LLC is not on Sunbiz (status "planned") [idoneity-cms/docs/COMPLIANCE_CALENDAR.md]
- Success-fee risk: FL Ch. 489 contractor licensing and broker-finder rules. A written opinion from a FL construction attorney is needed before billing [idoneity-cms/CORPORATE_STRUCTURE.md §3]
- Source policy: only government open data and vendors' own public bid portals; Dodge, ConstructConnect, BuildingConnected, Blue Book banned (ToS); robots.txt respected; SEC EDGAR needs descriptive User-Agent [bidwell/.claude/agents/bidwell-ingestion-reviewer.md; src/lib/ingestion/]
- No terms-of-service or privacy pages in repo [repo-wide]
- Marketing claims without a repo data source: "~70% of the draft kept", "12s average AI bid draft", "submit 5x more bids" [bidwell/src/app/page.tsx]

## Changed this week
- Prod recovered: /api/health is now ok:true with DB ok, after failing on 10-18 and 10-25 [https://bidwell.praesidium-holdings.workers.dev/api/health 2026-11-01]
- Live /opportunities now returns 200; it was 500 the previous two weeks [live check 2026-11-01]
- Newly visible: prod is at migration 0015, and repo migration 0016_invites_questions_reminders is not applied [/api/health; bidwell/drizzle/]
- Recovery lines up with the 2026-11-01 Turso quota reset. There were no Bidwell commits this week, so the reset is the likely cause. Bidwell is still on Turso, and the same quota could block it again [gitlog-bidwell.txt; D1_CUTOVER.md]
- Unchanged: Anthropic, admin and SAM.gov secrets are still unset in prod; pricing and homepage copy are the same as last week

## Open questions for Tyler
- Prod came back on 11-01, most likely because the Turso quota reset; it is still on Turso. Should Bidwell move to D1 under the "stay off paid Turso" decision, and when? Should migration 0016 (invites/questions/reminders) go to prod first?
- Now that the DB is reachable, are there any real users, posted jobs, bids or awards in it, or is it all demo data?
- The site says fees are "billed via Stripe", but the corporate doc keeps billing off until a FL construction attorney signs off. Has that review happened, and should the site say "tracked, not billed" until it does?
- Is the $1,200/yr prepay commitment in fees.ts the intended price? It isn't published. Do you own bidwell.com? The walkthrough CTA mails hello@bidwell.com.
- Which side comes first, contractors or GCs/operators? And what is the first-year target for awarded-contract dollars?
