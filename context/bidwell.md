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
## Auto facts (synced 2026-10-18)
### What it is / offer
- Bid marketplace — "A bid marketplace where the price is the price." Operated by Idoneity Marketplace, LLC (planned entity) [bidwell/README.md]
- For industrial contractors: geo-radius opportunity search, AI-drafted bids ("Bid with Claude"), client-confirmed awards, platform invoicing; "pay 7.25% only when you win" [bidwell/src/app/page.tsx]
- Loop: map your radius → Bid with Claude → "We confirm with the client" → pay only when you win [bidwell/src/app/page.tsx]
- Integrates with Idoneity: contractor PQF, COI, training records attach to bids [bidwell/src/app/page.tsx]
- Live homepage hero: "Find work in your area. Bid on what you can actually take." [https://bidwell.praesidium-holdings.workers.dev/]

### Customers & market
- Two sides: small/mid-size industrial contractors; industrial operators + GCs hiring subs [bidwell/src/app/page.tsx]
- Florida primary: BidNet adapter defaults to FL; demo sources FL DMS, Brevard County, FPL, Port Canaveral, Mosaic [bidwell/src/lib/ingestion/bidnet.ts; web-search.ts]
- PlanetBids adapter targets CA/Western-US municipal agencies; SAM.gov defaults to construction NAICS 236/237/238 [bidwell/src/lib/ingestion/planetbids.ts; sam-gov.ts]
- No customer, user, bid or award counts in any source; prod DB unreachable this run [bidwell/api/health]

### Pricing (as published)
- Success fee, volume-tiered on trailing-12-month awarded: Starter 7.25% (<$250k) → Established 5.00% ($250k–$1M) → Anchor 3.00% ($1M+) [bidwell/src/lib/fees.ts; live homepage]
- Annual-prepay lane: flat 3.5% override [bidwell/src/lib/fees.ts; live homepage]; code default prepay commitment $1,200/yr — not shown on site [bidwell/src/lib/fees.ts]
- "0 Subscription — no listing fees, ever"; fees "billed 30 days after award via Stripe" [bidwell/src/app/page.tsx; live homepage]
- Code: invoice 30 days after award, Stripe `days_until_due: 14`, delinquent at >60 days past due → platform access cut [bidwell/src/lib/invoicing.ts]
- No /pricing page (404 live; none in repo) [https://bidwell.praesidium-holdings.workers.dev/pricing]
- Corporate doc: success-fee collection stays "tracked" (not billed) until a FL construction attorney reviews [idoneity-cms/CORPORATE_STRUCTURE.md §3]

### Product / tech status
- Stack: Next.js 16.2.9, React 19.2.4, Tailwind v4, Drizzle, Turso (prod) / SQLite (local), Anthropic SDK (Haiku 4.5 default), Stripe, Leaflet/OSM, Mapbox, Playwright [bidwell/package.json; CLAUDE.md]
- Hosting: Cloudflare Worker `bidwell` via OpenNext; AWS Amplify kept as alternate, not live [bidwell/DEPLOY.md; wrangler.jsonc]
- Live only at bidwell.praesidium-holdings.workers.dev; bidwell.com "not yet bound" [bidwell/DEPLOY.md]
- Prod health 2026-10-18: ok:false, DB not ok, no latest migration; Anthropic, admin-secret, SAM.gov keys not configured [https://bidwell.praesidium-holdings.workers.dev/api/health]
- Live /opportunities returns HTTP 500; /post-opportunity loads (sign-in required) [live site]
- 17 migrations (0000–0016); 9 scheduled cron jobs (GitHub Actions / EventBridge); `run-signal-promotion` not scheduled [bidwell/drizzle; .github/workflows/cron.yml; docs/AI_OPERATIONS.md]
- Stubs: AP payment providers (Bill.com, Modern Treasury, BoA CashPro) not wired; Stripe invoicing stubbed when key unset [bidwell/src/lib/ap/providers/index.ts; src/lib/invoicing.ts]
- Scraper hardening TODO (PlanetBids, BidNet pagination/selector drift) [bidwell/src/lib/ingestion/]
- Backlog from competitor research: win/loss analytics, contact book, addenda tab, unpublish jobs, RFI log, scope normalization [bidwell/docs/COMPETITOR_RESEARCH_2026-07.md]
- No commits in the last 8 days [runs/2026-10-18/gitlog-bidwell.txt]

### Sales & marketing activity
- CTAs: "Book a walkthrough", "Browse open work", "Post a job", waitlist "Add me to the list" [bidwell/src/app/page.tsx; live homepage]
- Live "Book a walkthrough" opens a mailto to hello@bidwell.com, not the Idoneity booking flow (idoneity-cms.com/walkthrough?brand=bidwell) configured in wrangler [live homepage; bidwell/wrangler.jsonc]
- Automated outreach pipeline: weekly Claude web_search prospect discovery, AI-drafted cold emails, admin send queue at /admin/outreach; signals from permits, SEC EDGAR, press releases [bidwell/src/lib/outreach/discover.ts; docs/AI_OPERATIONS.md]
- No record of sent campaigns, social posts or ad spend [repo-wide]

### Competitors
- Named: BuildingConnected, iSqFt/ConstructConnect, PlanHub, SmartBid, Procore, Buildertrend, TradeTapp [bidwell/docs/COMPETITOR_RESEARCH_2026-07.md]
- Cited points: PlanHub add-ons $91–141/mo; Procore renewal hikes 12–15%; BuildingConnected 100-mile free-tier cap [bidwell/docs/COMPETITOR_RESEARCH_2026-07.md]
- Patterns adopted 2026-07-17: single-screen bid leveling, invite tracking, loser notifications, one-click bid/no-bid, ungated Q&A, deadline reminders [bidwell/docs/COMPETITOR_RESEARCH_2026-07.md]

### Key tools & systems
- Ingestion: SAM.gov API, RSS, Claude web_search → Brave → SerpAPI → demo waterfall, FL DMS scrape, Socrata permits, SEC EDGAR full-text, Business Wire / PR Newswire RSS, PlanetBids, BidNet Direct [bidwell/src/lib/ingestion/*.ts]
- Cloudflare Workers + 2 R2 buckets + Workers Logs; Turso [bidwell/wrangler.jsonc]
- Email: AWS SES → Resend → console stub [bidwell/src/lib/messaging.ts]
- Stripe (success fees), Plaid read-only (bank data), AP automation module [bidwell/src/lib/invoicing.ts; src/lib/ap/providers/plaid.ts]
- AI metered via `trackedMessagesCreate()` + `ai_usage` ledger; `AI_DISABLED` kill switch; 14 sensitive actions behind /autonomy/approvals [bidwell/docs/AI_OPERATIONS.md]
- Owner finance in Idoneity admin, `entity_id = ent_bidwell` [bidwell/docs/OWNER_CONSOLE.md]

### Regulatory / compliance notes
- Entity: Idoneity Marketplace, LLC is not on Sunbiz (status "planned") [idoneity-cms/docs/COMPLIANCE_CALENDAR.md]
- Success-fee risk: FL Ch. 489 contractor licensing and broker-finder rules — written opinion from a FL construction attorney needed before billing [idoneity-cms/CORPORATE_STRUCTURE.md §3]
- Source policy: only government open data and vendors' own public bid portals. Dodge, ConstructConnect, BuildingConnected and Blue Book are banned because their ToS prohibit scraping. Scrapers must respect robots.txt; SEC EDGAR needs a descriptive User-Agent [bidwell/.claude/agents/bidwell-ingestion-reviewer.md; src/lib/ingestion/scrape.ts; sec-edgar.ts]
- No terms-of-service or privacy pages in repo [repo-wide]
- Marketing claims without a repo data source: "~70% of the draft kept", "12s average AI bid draft", "submit 5x more bids" [bidwell/src/app/page.tsx]

## Changed this week
- First sync — no previous context file existed, so there is no baseline to compare against. All facts above are new.
- No Bidwell commits in the last 8 days [gitlog-bidwell.txt]
- Observed this run: prod /api/health failing (DB not ok); /opportunities returns 500 [live checks 2026-10-18]

## Open questions for Tyler
- Is the live Bidwell database meant to be down or unmigrated right now? The health check fails and /opportunities returns 500. Are there any real users, bids or awards yet?
- Is the $1,200/yr prepay commitment in fees.ts the intended price? It isn't published anywhere.
- The site advertises 7.25% fees "billed via Stripe", but the corporate doc says billing stays off until a FL construction attorney signs off. Has that review happened, and should the site say "tracked, not billed" until then?
- Do you own bidwell.com, or is there another domain planned? The footer and the walkthrough email point to it, but it currently serves an ad page.
- Which side do you want first, contractors or GCs/operators? And what is the target number of awarded-contract dollars for the first year?
