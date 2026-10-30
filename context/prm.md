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
## Auto facts (synced 2026-10-25)
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
- Client/engagement counts not readable (prod DB health check failing, 2026-10-25) [https://prm.praesidium-holdings.workers.dev/api/health]
- Corporate doc positions PRM as Idoneity's design-partner / referral channel [idoneity-cms/CORPORATE_STRUCTURE.md]

### Pricing (as published)
- No dollar figures in repo or on live site; "scoped fees for one-time deliverables, monthly retainer for ongoing coverage" [prm/src/app/page.tsx]
- Discovery call is free [prm/src/app/page.tsx]
- No rate card in repo; changing a rate card is approval-gated (CHANGE_RATE_CARD) [prm/src/lib/autonomy-policy.ts]

### Product / tech status
- Stack: Next.js 16.2.9, React 19, Tailwind v4, Drizzle, Turso (prod) / SQLite (local), Anthropic SDK; OpenNext on Cloudflare Workers [prm/package.json; prm/CLAUDE.md]
- Live only on workers.dev (homepage 200 on 2026-10-25); no custom domain/route [prm/wrangler.jsonc; live check]
- Prod health 2026-10-25: ok:false, DB not ok, latestMigration null, aiDisabled:true, Anthropic key not configured; Turso URL/token secrets are set [/api/health]
- Note: Idoneity's docs record that Turso reads on Tyler's account are quota-blocked until Nov 1; whether that causes PRM's DB failure is not confirmed [idoneity-cms/.claude/worktrees/d1-port/docs/D1_CUTOVER.md]
- Notes typecheck PR #1 open since 07-24 [prm/.git/COMMIT_EDITMSG]
- No commits or file changes since 2026-10-18 [runs/2026-10-25/gitlog-prm.txt; file mtimes]
- Billing and proposals modules "scaffolded"; Stripe webhook stubs only [prm/src/app/autonomy/page.tsx]
- Scheduled jobs: nightly AR aging (08:00 UTC), weekly OSHA-deadline recommender (Mon 10:00 UTC) in GitHub Actions and wrangler crons [prm/.github/workflows/cron.yml; prm/wrangler.jsonc]
- `/api/leads` imports zod, which is not in package.json [prm/src/app/api/leads/route.ts; prm/package.json]

### Sales & marketing activity
- Only CTA: "Book a discovery call" (mailto at prometheusriskmgmt.com) [prm/src/app/page.tsx]
- prometheusriskmgmt.com still did not respond on 2026-10-25 (no connection) [live check]
- `/api/leads` capture endpoint exists, but no public form posts to it [prm/src/app/api/leads/route.ts]
- Header nav/CTAs point public visitors to the internal "Autonomy" login [prm/src/app/layout.tsx]
- Brand-family footer cross-promotes Idoneity, Bidwell, Acuere; Arete hidden as "coming-soon" [prm/src/components/brand-family-footer.tsx]

### Competitors
- (no source found) — no competitors named in repo; ISN/Avetta/Veriforce appear only as platforms clients need approval on [prm/src/app/page.tsx]

### Key tools & systems
- Finance (AP, invoices, proposals, compliance calendar) in the Idoneity owner console, scoped `entity_id = ent_prm` [prm/docs/OWNER_CONSOLE.md]
- PRM /autonomy hub: approvals, tasks, discovery calls, marketing, CRM, quotes, billing, AR, AP, client health, AI usage [prm/src/app/autonomy/page.tsx]
- Cloudflare Workers + R2 cache, Turso, GitHub Actions cron, Anthropic claude-haiku-4-5 default [prm/wrangler.jsonc; prm/docs/AI_OPERATIONS.md]
- Repo agent `prm-safety-consultant`; skill `prm-status` [prm/.claude/]

### Regulatory / compliance notes
- Labeling rule: deadline/AR recommenders are rules-based, never "AI-powered"; only `osha_brief` is AI and titled "(AI-drafted)"; AI output is "a planning aid, not compliance advice" [prm/CLAUDE.md; prm/docs/AI_OPERATIONS.md]
- 12 sensitive actions require principal approval (audit findings, OSHA notices, invoices, refunds, legal escalation) [prm/src/lib/autonomy-policy.ts]
- Live hero art shows "29 CFR 1910 COMPLIANT" seal plus "AUDIT CLEAR" badges with no disclaimer — conflicts with the repo's no-certifying-compliance rule [prm/src/app/page.tsx; prm/.claude/agents/prm-safety-consultant.md]
- No consultant credentials (CSP, OSHA Outreach trainer) referenced while the site advertises OSHA 10/30 delivery [prm/src/app/page.tsx]
- Hardcoded deadlines: 300A posting Feb 1–Apr 30; ITA e-filing by Mar 2; quarterly TRIR review [prm/src/lib/osha-deadlines.ts]
- PRM docs: single-member disregarded LLC, peer of Idoneity Holdings, for the FICA/FUTA exemption on wages to children under 18 [prm/docs/OWNER_CONSOLE.md; prm/CLAUDE.md]
- Sunbiz (2026-09-13 lookup): PROMETHEUS HOLDINGS LLC (renamed 2026-07-16), filed 2025-04-28, **two managing members** → partnership (1065) by default; tax treatment unset pending CPA [idoneity-cms/docs/COMPLIANCE_CALENDAR.md; docs/TODO.md]
- 2026 FL annual report filed 2026-01-22; next due 1 Jan–1 May 2027 [idoneity-cms/docs/COMPLIANCE_CALENDAR.md]
- OSHA 2026 civil penalties held at 2025 levels ($16,550 serious; $165,514 willful/repeat) [https://www.osha.gov/memos/2026-05-21/2026-annual-adjustments-osha-civil-penalties]
- Federal heat rule still not final, no target date; sources conflict on whether the heat NEP expired 2026-04-08 or was renewed to 2031. Florida preempts local heat ordinances [https://www.jdsupra.com/legalnews/what-s-the-status-of-osha-s-heat-stress-9226045/; https://osha.gov/heat-exposure/rulemaking]
- OSHA NPRM (2026-04-06) proposes eliminating the compliance deadline for fall-arrest/ladder-safety systems on fixed ladders; OSHA enforcement priorities named in 2026 commentary: heat, silica, warehouses [https://www.jdsupra.com/topics/rulemaking-process/osh-act/osha/]

## Changed this week
- No changes. There were no commits or file changes in the repo since 2026-10-18 [gitlog-prm.txt; file mtimes]
- Re-checked live 2026-10-25: DB health still failing. /api/health now reports `aiDisabled: true` (last week only noted the AI key missing). prometheusriskmgmt.com is still unreachable [live checks]
- Regulatory additions: sources disagree on whether the heat NEP was renewed. OSHA proposed removing the fixed-ladder fall-arrest deadline. 2026 enforcement priorities are heat, silica and warehouses [WebSearch]

## Open questions for Tyler
- What is PRM's legal name, and how is it taxed? Sunbiz shows "Prometheus Holdings LLC" with two managing members (partnership by default). The PRM docs say single-member disregarded, for the kids-FICA exemption.
- prometheusriskmgmt.com is still unreachable, and it is the only discovery-call contact on the site. Is the domain registered, and when will email be set up?
- PRM's prod DB has failed its health check for two weeks. Is that the Turso quota block, and should PRM move to D1 along with Idoneity?
- What retainer and scoped-fee rates (and target margin) should sales/CFO skills quote? Nothing is published.
- Should the "29 CFR 1910 COMPLIANT" / "AUDIT CLEAR" hero art stay? And which credentials back the advertised OSHA 10/30 training?
