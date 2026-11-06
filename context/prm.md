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
## Auto facts (synced 2026-11-01)
### What it is / offer
- Solo safety/OSHA consultancy for Florida industrial contractors, "delivered solo, with the discipline of a much larger firm"; tagline "If OSHA shows up, I show up" [prm/src/app/page.tsx]
- Four services on the homepage: written safety programs (IIPP, HAZCOM, LOTO, confined space, fall protection); site audits & gap analysis; training & toolbox talks (OSHA 10/30); incident response (root cause, CAPA, follow-up filings) [prm/src/app/page.tsx; https://prm.praesidium-holdings.workers.dev]
- The brand-family footer card also lists fractional safety leadership, citation defense and incident forensics [prm/src/components/brand-family-footer.tsx]
- The README describes a broader offer, including training coordination and "OSHA/EPA compliance support" for construction, energy and industrial clients [prm/README.md]
- Engagement flow: free 30-min discovery call → scoped proposal → field work/documents → signed programs + audit-ready binder [prm/src/app/page.tsx]

### Customers & market
- Target: small industrial contractors with 10–150 crew (mechanical, electrical, controls, insulation, millwright) and no full-time safety hire [prm/src/app/page.tsx]
- Also: crews that need ISN/Avetta/Veriforce approval, and firms recovering from an incident [prm/src/app/page.tsx]
- Geography: the live site still says "FL-only" practice area; the README says "across the Southeast" [https://prm.praesidium-holdings.workers.dev 2026-11-01; prm/README.md]
- No clients table yet; active clients are inferred from unpaid AR plus "Closed Won" opportunities [prm/src/lib/osha-deadlines.ts]
- Client and engagement counts can't be read because the prod DB health check is failing (2026-11-01) [https://prm.praesidium-holdings.workers.dev/api/health]
- The corporate doc positions PRM as Idoneity's design-partner / referral channel [idoneity-cms/CORPORATE_STRUCTURE.md]

### Pricing (as published)
- No dollar figures in the repo or on the live site; "scoped fees for one-time deliverables, monthly retainer for ongoing coverage" [prm/src/app/page.tsx]
- The discovery call is free [prm/src/app/page.tsx]
- No rate card in the repo; changing a rate card is approval-gated (CHANGE_RATE_CARD) [prm/src/lib/autonomy-policy.ts]

### Product / tech status
- Stack: Next.js 16.2.9, React 19, Tailwind v4, Drizzle, Turso (prod) / SQLite (local), Anthropic SDK; OpenNext on Cloudflare Workers [prm/package.json; prm/CLAUDE.md]
- Live only on workers.dev (homepage returned 200 on 2026-11-01); no custom domain or route [prm/wrangler.jsonc; live check]
- Prod health 2026-11-01 22:00 UTC: ok:false, DB not ok, latestMigration null, aiDisabled:true, ANTHROPIC_API_KEY not set. The Turso URL/token, cron, cookie and principal secrets are set [https://prm.praesidium-holdings.workers.dev/api/health]
- The DB was still failing on the day the Turso quota was expected to reset (Nov 1), so the quota block isn't confirmed as the cause [/api/health; idoneity-cms/.claude/worktrees/d1-port/docs/D1_CUTOVER.md]
- PRM is still on Turso; the portfolio decision of 2026-10-25 is "all data lives in Cloudflare; stay off paid Turso" [prm/wrangler.jsonc; D1_CUTOVER.md]
- Notes typecheck PR #1 has been open since 07-24 [prm/.git/COMMIT_EDITMSG]
- No commits since 2026-10-18; newest top-level file change is next-env.d.ts on 2026-09-07 [runs/2026-11-01/gitlog-prm.txt; file mtimes]
- Billing and proposals modules are "scaffolded"; Stripe webhooks are stubs only [prm/src/app/autonomy/page.tsx]
- Scheduled jobs: nightly AR aging (08:00 UTC) and weekly OSHA-deadline recommender (Mon 10:00 UTC), in GitHub Actions and wrangler crons [prm/.github/workflows/cron.yml; prm/wrangler.jsonc]
- `/api/leads` imports zod, which is not in package.json [prm/src/app/api/leads/route.ts; prm/package.json]

### Sales & marketing activity
- The only CTA is "Book a discovery call", a mailto at prometheusriskmgmt.com [https://prm.praesidium-holdings.workers.dev]
- prometheusriskmgmt.com still doesn't resolve (curl exit 6, host not found, 2026-11-01), so the only contact address on the site is dead [live check]
- A `/api/leads` capture endpoint exists, but no public form posts to it [prm/src/app/api/leads/route.ts]
- Header nav/CTAs send public visitors to the internal "Autonomy" login [prm/src/app/layout.tsx]
- The brand-family footer cross-promotes Idoneity, Bidwell and Acuere; Arete is hidden as "coming-soon" [prm/src/components/brand-family-footer.tsx]

### Competitors
- (no source found). The repo names no competitors; ISN/Avetta/Veriforce appear only as platforms clients need approval on [prm/src/app/page.tsx]

### Key tools & systems
- Finance (AP, invoices, proposals, compliance calendar) runs in the Idoneity owner console, scoped to `entity_id = ent_prm` [prm/docs/OWNER_CONSOLE.md]
- PRM /autonomy hub: approvals, tasks, discovery calls, marketing, CRM, quotes, billing, AR, AP, client health, AI usage [prm/src/app/autonomy/page.tsx]
- Cloudflare Workers + R2 cache, Turso, GitHub Actions cron; Anthropic claude-haiku-4-5 is the default model [prm/wrangler.jsonc; prm/docs/AI_OPERATIONS.md]
- Repo agent `prm-safety-consultant`; skill `prm-status` [prm/.claude/]

### Regulatory / compliance notes
- Labeling rule: the deadline/AR recommenders are rules-based and never called "AI-powered". Only `osha_brief` is AI, and it is titled "(AI-drafted)". AI output is "a planning aid, not compliance advice" [prm/CLAUDE.md; prm/docs/AI_OPERATIONS.md]
- 12 sensitive actions require principal approval (audit findings, OSHA notices, invoices, refunds, legal escalation) [prm/src/lib/autonomy-policy.ts]
- The hero art shows a "29 CFR 1910 COMPLIANT" seal (in the repo) and "AUDIT CLEAR" badges (still on the live page 2026-11-01), with no disclaimer. This conflicts with the repo's no-certifying-compliance rule [prm/src/app/page.tsx; live page; prm/.claude/agents/prm-safety-consultant.md]
- The site advertises OSHA 10/30 delivery, but no consultant credentials (CSP, OSHA Outreach trainer) are referenced [prm/src/app/page.tsx]
- Hardcoded deadlines: 300A posting Feb 1–Apr 30; ITA e-filing by Mar 2; quarterly TRIR review. The 300A/ITA season is ~3 months out [prm/src/lib/osha-deadlines.ts]
- PRM docs: single-member disregarded LLC, peer of Idoneity Holdings, for the FICA/FUTA exemption on wages paid to children under 18 [prm/docs/OWNER_CONSOLE.md; prm/CLAUDE.md]
- Sunbiz (2026-09-13 lookup): PROMETHEUS HOLDINGS LLC (renamed 2026-07-16), filed 2025-04-28, **two managing members**, which means partnership (1065) treatment by default; tax treatment is unset pending the CPA [idoneity-cms/docs/COMPLIANCE_CALENDAR.md; docs/TODO.md]
- 2026 FL annual report filed 2026-01-22; the next is due 1 Jan–1 May 2027 [idoneity-cms/docs/COMPLIANCE_CALENDAR.md]
- OSHA 2026 civil penalties are held at 2025 levels ($16,550 serious; $165,514 willful/repeat) [https://www.osha.gov/memos/2026-05-21/2026-annual-adjustments-osha-civil-penalties]
- Federal heat rule: still proposed, not final. Hearing ran Jun 16–Jul 2, 2025; post-hearing comments closed 2025-10-30. No federal heat standard in force; Florida preempts local heat ordinances [https://osha.gov/heat-exposure/rulemaking; https://www.mondaq.com/unitedstates/employee-rights-labour-relations/1778956/osha-refines-heat-enforcement-strategy-while-federal-heat-rule-remains-pending]
- Heat NEP: one source reports a revised Heat NEP issued 2026-04-10, which addresses last week's "expired vs renewed" conflict. Not yet confirmed on osha.gov [https://www.mondaq.com/unitedstates/employee-rights-labour-relations/1778956/osha-refines-heat-enforcement-strategy-while-federal-heat-rule-remains-pending]
- OSHA NPRM (2026-04-06) on Walking-Working Surfaces proposes dropping the fall-arrest/ladder-safety deadline for fixed ladders. 2026 enforcement priorities named in commentary: heat, silica, warehouses [https://www.jdsupra.com/topics/rulemaking-process/osh-act/osha/]
- Florida enforcement example: a FL roofing contractor was cited for willful fall-protection violations after a fatal fall (May 2026) [WebSearch 2026-11-01, OSHA enforcement coverage]

## Changed this week
- No repo changes: no commits since 2026-10-18, and no recent file changes [gitlog-prm.txt; file mtimes]
- Prod DB health is still failing for a third straight week (2026-11-01 22:00 UTC). It was still down on the day the Turso quota was expected to reset, so the quota block is now less likely to be the whole cause [/api/health]
- prometheusriskmgmt.com still doesn't resolve (DNS host not found), the third week running [live check]
- Regulatory update: a revised Heat NEP was reportedly issued 2026-04-10, which addresses last week's expired-vs-renewed conflict. The federal heat rule is still not final (post-hearing comments closed 2025-10-30) [mondaq 1778956; osha.gov/heat-exposure/rulemaking]
- Otherwise no changes to offer, pricing, market or tools

## Open questions for Tyler
- PRM's prod DB has now failed its health check for three weeks, and it was still down on the Nov 1 Turso reset day. Should PRM move to D1 now, under the "stay off paid Turso" decision, or is PRM parked?
- What is PRM's legal name, and how is it taxed? Sunbiz shows "Prometheus Holdings LLC" with two managing members (partnership by default). The PRM docs say single-member disregarded, for the kids-FICA exemption. Has the CPA weighed in?
- prometheusriskmgmt.com still doesn't resolve, and it is the only discovery-call contact on the site. Is the domain registered, and should the CTA point to a working address until it is?
- What retainer and scoped-fee rates (and target margin) should the sales/CFO skills quote? Nothing is published. Should PRM run a 300A/ITA-season offer before Feb 1?
- Should the "29 CFR 1910 COMPLIANT" / "AUDIT CLEAR" hero art stay? And which credentials back the advertised OSHA 10/30 training?
