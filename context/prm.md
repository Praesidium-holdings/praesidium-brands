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
## Auto facts (synced 2026-11-08)
### What it is / offer
- Solo safety/OSHA consultancy for Florida industrial contractors, "delivered solo, with the discipline of a much larger firm". Tagline: "If OSHA shows up, I show up" [prm/src/app/page.tsx]
- Four services on the homepage [prm/src/app/page.tsx; https://prm.praesidium-holdings.workers.dev]:
  - Written safety programs (IIPP, HAZCOM, LOTO, confined space, fall protection)
  - Site audits & gap analysis
  - Training & toolbox talks (OSHA 10/30)
  - Incident response (root cause, CAPA, follow-up filings)
- The brand-family footer card also lists fractional safety leadership, citation defense and incident forensics [prm/src/components/brand-family-footer.tsx]
- The README's offer is broader, adding training coordination and "OSHA/EPA compliance support" for construction, energy and industrial clients [prm/README.md]
- Engagement flow: free 30-min discovery call → scoped proposal → field work/documents → signed programs + audit-ready binder [prm/src/app/page.tsx]

### Customers & market
- Target: small industrial contractors with 10–150 crew (mechanical, electrical, controls, insulation, millwright) and no full-time safety hire [prm/src/app/page.tsx]
- Also: crews needing ISN/Avetta/Veriforce approval, and firms recovering from an incident [prm/src/app/page.tsx]
- Geography: the live site still says the practice area is "FL-only"; the README says "across the Southeast" [https://prm.praesidium-holdings.workers.dev 2026-11-08; prm/README.md]
- No clients table yet; active clients are inferred from unpaid AR plus "Closed Won" opportunities [prm/src/lib/osha-deadlines.ts]
- Client and engagement counts can't be read: the prod DB health check is failing (2026-11-08) [https://prm.praesidium-holdings.workers.dev/api/health]
- The corporate doc positions PRM as Idoneity's design-partner and referral channel [idoneity-cms/CORPORATE_STRUCTURE.md]

### Pricing (as published)
- No dollar figures in the repo or on the live site. Model: "scoped fees for one-time deliverables, monthly retainer for ongoing coverage" [prm/src/app/page.tsx]
- The discovery call is free [prm/src/app/page.tsx]
- No rate card in the repo; changing a rate card is approval-gated (CHANGE_RATE_CARD) [prm/src/lib/autonomy-policy.ts]

### Product / tech status
- Stack: Next.js 16.2.9, React 19, Tailwind v4, Drizzle, Turso (prod) / SQLite (local), Anthropic SDK; OpenNext on Cloudflare Workers [prm/package.json; prm/CLAUDE.md]
- Live only on workers.dev, with no custom domain or route. Homepage returned 200 on 2026-11-08 [prm/wrangler.jsonc; live check]
- Prod health 2026-11-08 ~22:00 UTC: **ok:false**, DB not ok, latestMigration null, aiDisabled:true. This is the **fourth straight weekly check** with the DB failing [https://prm.praesidium-holdings.workers.dev/api/health]
  - ANTHROPIC_API_KEY not set; Turso URL/token, cron, cookie and principal secrets are set
- Still on Turso. The portfolio decision of 2026-10-25 is "all data lives in Cloudflare; stay off paid Turso" [prm/wrangler.jsonc; D1_CUTOVER.md]
- Notes typecheck PR #1 has been open since 07-24 [prm/.git/COMMIT_EDITMSG]
- No commits since 2026-10-18, and no files modified since 2026-11-01 [gitlog-prm.txt; file mtimes]
- Billing and proposals modules are "scaffolded"; Stripe webhooks are stubs only [prm/src/app/autonomy/page.tsx]
- Scheduled jobs: nightly AR aging (08:00 UTC) and a weekly OSHA-deadline recommender (Mon 10:00 UTC), in GitHub Actions and wrangler crons [prm/.github/workflows/cron.yml; prm/wrangler.jsonc]
- `/api/leads` imports zod, which is not in package.json [prm/src/app/api/leads/route.ts; prm/package.json]

### Sales & marketing activity
- The only CTA is "Book a discovery call", a mailto at prometheusriskmgmt.com [https://prm.praesidium-holdings.workers.dev]
- prometheusriskmgmt.com still doesn't resolve (2026-11-08), so the site's only contact address is dead [live check]
- A `/api/leads` capture endpoint exists, but no public form posts to it [prm/src/app/api/leads/route.ts]
- Header nav and CTAs send public visitors to the internal "Autonomy" login [prm/src/app/layout.tsx]
- The brand-family footer cross-promotes Idoneity, Bidwell and Acuere; Arete is hidden as "coming-soon" [prm/src/components/brand-family-footer.tsx]
- Seasonal hook: the 300A posting window (Feb 1 – Apr 30) and ITA e-filing (by Mar 2) are about 3 months away [prm/src/lib/osha-deadlines.ts]

### Competitors
- (no source found). The repo names no competitors; ISN/Avetta/Veriforce appear only as platforms clients need approval on [prm/src/app/page.tsx]

### Key tools & systems
- Finance (AP, invoices, proposals, compliance calendar) runs in the Idoneity owner console, scoped to `entity_id = ent_prm` [prm/docs/OWNER_CONSOLE.md]
- PRM /autonomy hub: approvals, tasks, discovery calls, marketing, CRM, quotes, billing, AR, AP, client health, AI usage [prm/src/app/autonomy/page.tsx]
- Cloudflare Workers + R2 cache, Turso, GitHub Actions cron; Anthropic claude-haiku-4-5 is the default model [prm/wrangler.jsonc; prm/docs/AI_OPERATIONS.md]
- Repo agent `prm-safety-consultant`; skill `prm-status` [prm/.claude/]

### Regulatory / compliance notes
- AI labeling rule: the deadline and AR recommenders are rules-based and never called "AI-powered". Only `osha_brief` is AI, and it is titled "(AI-drafted)". AI output is "a planning aid, not compliance advice" [prm/CLAUDE.md; prm/docs/AI_OPERATIONS.md]
- 12 sensitive actions require principal approval (audit findings, OSHA notices, invoices, refunds, legal escalation) [prm/src/lib/autonomy-policy.ts]
- Hero art conflicts with the repo's no-certifying-compliance rule. No disclaimer is shown [prm/src/app/page.tsx; live page 2026-11-08; prm/.claude/agents/prm-safety-consultant.md]:
  - "29 CFR 1910 COMPLIANT" seal (in the repo)
  - "AUDIT CLEAR" badges (still on the live page)
- The site advertises OSHA 10/30 delivery but cites no consultant credentials (CSP, OSHA Outreach trainer) [prm/src/app/page.tsx]
- Hardcoded deadlines: 300A posting Feb 1 – Apr 30; ITA e-filing by Mar 2; quarterly TRIR review [prm/src/lib/osha-deadlines.ts]
- Injury logs must be kept 5 years (29 CFR 1904.33, verbatim fixture) [idoneity-ehs/marketing/proposals/2026-11-03/fixtures/source-retention-1904-33.md]
- PRM docs: a single-member disregarded LLC, a peer of Idoneity Holdings, for the FICA/FUTA exemption on wages paid to children under 18 [prm/docs/OWNER_CONSOLE.md; prm/CLAUDE.md]
- Sunbiz (2026-09-13 lookup): PROMETHEUS HOLDINGS LLC (renamed 2026-07-16), filed 2025-04-28, with **two managing members**. That means partnership (1065) treatment by default; tax treatment is unset pending the CPA [idoneity-cms/docs/COMPLIANCE_CALENDAR.md; docs/TODO.md]
- The 2026 FL annual report was filed 2026-01-22; the next is due 1 Jan – 1 May 2027 [idoneity-cms/docs/COMPLIANCE_CALENDAR.md]
- OSHA 2026 civil penalties are held at 2025 levels ($16,550 serious; $165,514 willful/repeat). The January adjustment is due [https://www.osha.gov/memos/2026-05-21/2026-annual-adjustments-osha-civil-penalties]
- Heat:
  - The revised Heat NEP was issued 2026-04-10 [https://www.mondaq.com/unitedstates/employee-rights-labour-relations/1778956/osha-refines-heat-enforcement-strategy-while-federal-heat-rule-remains-pending]
  - The federal heat rule is still not final, with no target date. A House subcommittee hearing on it was held in early September 2026, and a January 2026 bill would bar finalizing it [https://jjkellercompliancenetwork.com/news/oshas-proposed-heat-rule-debated-during-house-subcommittee-hearing; https://aggregatesandminingtoday.com/2026/01/bill-aimed-at-ending-osha-efforts-to-finalize-proposed-heat-rule/]
  - Florida preempts local heat ordinances [osha.gov/heat-exposure/rulemaking; mondaq 1778956]
- OSHA expects a final rule on subpoenas in investigations in November 2026, relevant to citation-defense work [J.J. Keller roundup via WebSearch 2026-11-08]
- OSHA NPRM (2026-04-06) on Walking-Working Surfaces would drop the fixed-ladder fall-arrest deadline [https://www.jdsupra.com/topics/rulemaking-process/osh-act/osha/]

## Changed this week
- Prod DB health still failing, now the fourth straight weekly check. Idoneity CMS and Bidwell, both also on Turso, failed again this week too [/api/health 2026-11-08]
- prometheusriskmgmt.com still doesn't resolve (fourth week); "AUDIT CLEAR" art is still on the live page [live check]
- Regulatory notes added: no federal heat rule action (early-September House hearing; January 2026 bill to block it); OSHA subpoena final rule expected November 2026 [J.J. Keller; Aggregates and Mining Today]
- No repo changes: no commits since 2026-10-18 and no file changes this week [gitlog-prm.txt; file mtimes]

## Open questions for Tyler
- PRM's prod DB has now failed four weekly checks in a row and its contact domain doesn't resolve. Is PRM deliberately parked? If not, should it move to D1 and get a working contact address before the 300A season (Feb 1)?
- What is PRM's legal name, and how is it taxed? Sunbiz shows "Prometheus Holdings LLC" with two managing members (partnership by default), while the PRM docs say single-member disregarded, for the kids-FICA exemption. Has the CPA weighed in?
- What retainer and scoped-fee rates (and target margin) should the sales/CFO skills quote? Nothing is published. Do you want a 300A/ITA-season offer before Feb 1?
- Should the "29 CFR 1910 COMPLIANT" / "AUDIT CLEAR" hero art stay? And which credentials back the advertised OSHA 10/30 training?
- Is PRM's practice area Florida-only (as the live site says) or the Southeast (as the README says)?
