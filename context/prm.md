# prm — company context
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
- Solo safety/OSHA consultancy for Florida industrial contractors — "delivered solo, with the discipline of a much larger firm"; "If OSHA shows up, I show up" [prm/src/app/page.tsx]
- Four services on the homepage: written safety programs (IIPP, HAZCOM, LOTO, confined space, fall protection); site audits & gap analysis; training & toolbox talks (OSHA 10/30); incident response (root cause, CAPA, follow-up filings) [prm/src/app/page.tsx; https://prm.praesidium-holdings.workers.dev]
- Brand-family footer card also lists fractional safety leadership, citation defense, incident forensics [prm/src/components/brand-family-footer.tsx]
- README describes a broader offer incl. training coordination and "OSHA/EPA compliance support" for construction, energy, industrial clients [prm/README.md]
- Engagement flow: free 30-min discovery call → scoped proposal → field work/documents → signed programs + audit-ready binder [prm/src/app/page.tsx]

### Customers & market
- Target: small industrial contractors, 10–150 crew (mechanical, electrical, controls, insulation, millwright), no full-time safety hire [prm/src/app/page.tsx]
- Also: crews needing ISN/Avetta/Veriforce approval; firms recovering from an incident [prm/src/app/page.tsx]
- Geography: site says "FL-only practice area"; README says "across the Southeast" [prm/src/app/page.tsx; prm/README.md]
- No clients table yet — active clients inferred from unpaid AR + "Closed Won" opportunities [prm/src/lib/osha-deadlines.ts]
- Client/engagement counts not readable this week (prod DB health check failing) [https://prm.praesidium-holdings.workers.dev/api/health]
- Corporate doc positions PRM as Idoneity's design-partner / referral channel [idoneity-cms/CORPORATE_STRUCTURE.md]

### Pricing (as published)
- No dollar figures in repo or on live site; model stated as "scoped fees for one-time deliverables, monthly retainer for ongoing coverage" / "fixed fee or monthly retainer" [prm/src/app/page.tsx; live site]
- Discovery call is free [prm/src/app/page.tsx]
- No rate card in repo; changing a rate card is an approval-gated action (CHANGE_RATE_CARD) [prm/src/lib/autonomy-policy.ts]

### Product / tech status
- Stack: Next.js 16.2.9, React 19, Tailwind v4, Drizzle, Turso (prod) / SQLite (local), Anthropic SDK; OpenNext on Cloudflare Workers [prm/package.json; prm/CLAUDE.md]
- Live only on workers.dev (https://prm.praesidium-holdings.workers.dev); no custom domain/route in wrangler config [prm/wrangler.jsonc]
- Prod health 2026-10-18: ok:false, DB not ok, no latest migration reported, Anthropic key not configured; marketing page still renders [/api/health; live site]
- Last commit fixed lockfile drift; notes typecheck PR #1 open since 07-24 [prm/.git/COMMIT_EDITMSG]
- No commits in the last 8 days [runs/2026-10-18/gitlog-prm.txt]
- Billing and proposals modules marked "scaffolded"; Stripe webhook stubs only [prm/src/app/autonomy/page.tsx]
- Scheduled jobs: nightly AR aging (08:00 UTC), weekly OSHA-deadline recommender (Mon 10:00 UTC), defined in both GitHub Actions and wrangler crons [prm/.github/workflows/cron.yml; prm/wrangler.jsonc]
- `/api/leads` imports zod, which is not in package.json [prm/src/app/api/leads/route.ts; prm/package.json]

### Sales & marketing activity
- Only CTA: "Book a discovery call" (mailto at prometheusriskmgmt.com) [prm/src/app/page.tsx]
- prometheusriskmgmt.com did not resolve (DNS ENOTFOUND) when fetched 2026-10-18 [WebFetch]
- `/api/leads` capture endpoint exists, but no public form posts to it [prm/src/app/api/leads/route.ts]
- Header nav/CTAs point public visitors to the internal "Autonomy" login [prm/src/app/layout.tsx; live site]
- Lead scoring/marketing module in /autonomy; counts unavailable (DB down) [prm/src/app/autonomy/marketing/page.tsx]
- Brand-family footer cross-promotes Idoneity, Bidwell, Acuere; Arete hidden as "coming-soon" [prm/src/components/brand-family-footer.tsx]

### Competitors
- (no source found) — no competitors named in repo; ISN/Avetta/Veriforce appear only as platforms clients need approval on [prm/src/app/page.tsx]

### Key tools & systems
- Finance (AP, invoices, proposals, compliance calendar) in Idoneity owner console at idoneity.com/admin, scoped `entity_id = ent_prm` [prm/docs/OWNER_CONSOLE.md]
- PRM /autonomy hub: approvals, tasks, discovery calls, marketing, CRM, quotes, billing, AR, AP, client health, AI usage [prm/src/app/autonomy/page.tsx]
- Cloudflare Workers + R2 cache, Turso, GitHub Actions cron (opens `cron-failure` issue on failure), Anthropic claude-haiku-4-5 default [prm/wrangler.jsonc; prm/docs/AI_OPERATIONS.md]
- Repo agent `prm-safety-consultant`; skill `prm-status` [prm/.claude/]

### Regulatory / compliance notes
- Labeling rule: deadline/AR recommenders are rules-based, never "AI-powered"; only `osha_brief` is AI and titled "(AI-drafted)"; AI output is "a planning aid, not compliance advice" and is human-reviewed before reaching clients [prm/CLAUDE.md; prm/docs/AI_OPERATIONS.md; prm/src/lib/osha-deadlines.ts]
- 12 sensitive actions require principal approval (sending audit findings, OSHA notices, invoices, refunds, legal escalation) [prm/src/lib/autonomy-policy.ts]
- Live hero art shows "29 CFR 1910 COMPLIANT" seal plus "AUDIT CLEAR" badges; no disclaimer on the page — conflicts with the repo's own no-certifying-compliance rule [prm/src/app/page.tsx; prm/.claude/agents/prm-safety-consultant.md; live site]
- No consultant credentials (CSP, OSHA Outreach trainer) referenced in repo while site advertises OSHA 10/30 delivery [prm/src/app/page.tsx]
- Hardcoded deadlines: 300A posting Feb 1–Apr 30 (10+ employees); ITA e-filing by Mar 2 (≥250, or ≥20 in listed NAICS); quarterly TRIR review [prm/src/lib/osha-deadlines.ts]
- PRM docs say it stays a single-member disregarded LLC, peer (not subsidiary) of Idoneity Holdings, to preserve the FICA/FUTA exemption for wages to children under 18 (IRC §3121(b)(3)(A), §3306(c)(5)) [prm/docs/OWNER_CONSOLE.md; prm/CLAUDE.md]
- Sunbiz lookup (2026-09-13): record is PROMETHEUS HOLDINGS LLC (renamed 2026-07-16; formerly Stephens Risk Management Services LLC), filed 2025-04-28. It shows **two managing members**, which means partnership (1065) treatment by default, not disregarded. Tax treatment is left unset pending CPA [idoneity-cms/docs/COMPLIANCE_CALENDAR.md]
- 2026 FL annual report filed 2026-01-22. Next one is due between 1 Jan and 1 May 2027; a $400 late fee applies after 1 May [idoneity-cms/docs/COMPLIANCE_CALENDAR.md]
- OSHA 2026 civil penalties: no inflation increase; 2025 maximums continue ($16,550 serious; $165,514 willful/repeat) [https://www.osha.gov/memos/2026-05-21/2026-annual-adjustments-osha-civil-penalties]
- Federal heat illness rule not final; sources conflict on next step (supplemental proposal Dec 2026 vs finalization Oct 2027); Heat NEP was set to expire 2026-04-08 [https://jjkellercompliancenetwork.com/news/proposed-heat-illness-prevention-rule-reaches-omb-for-review; https://www.ogletree.com/insights-resources/blog-posts/oshas-heat-program-to-expire-while-heat-standard-stalls/]

## Changed this week
- First sync — no previous context file existed, so there is no baseline to compare against. All facts above are new.
- No PRM commits in the last 8 days [gitlog-prm.txt]
- Observed this run: prod /api/health failing (DB not ok, AI key missing); prometheusriskmgmt.com not resolving [live checks 2026-10-18]

## Open questions for Tyler
- What is PRM's legal name, and how is it taxed? Sunbiz shows "Prometheus Holdings LLC" with two managing members, which means partnership treatment by default. The PRM docs instead say "Stephens Risk Management Consulting Services, LLC", single-member and disregarded, for the kids-FICA exemption. The site footer also says "© Praesidium Holdings, LLC". Which is right?
- Is prometheusriskmgmt.com registered and set up for email? It didn't resolve today, and it is the only discovery-call contact on the site.
- What are the actual retainer and scoped-fee rates (and target margin) that sales/CFO skills should quote? Nothing is published.
- Is the practice area Florida-only or Southeast-wide, and are EPA compliance / energy-sector work in scope?
- Should the "29 CFR 1910 COMPLIANT" / "AUDIT CLEAR" hero art stay? Which credentials (CSP, OSHA Outreach trainer authorization) back the advertised OSHA 10/30 training?
