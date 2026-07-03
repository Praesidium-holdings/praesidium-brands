# Owner Console (holding-level pointer)

The Praesidium Holdings structure runs on a **single multi-entity owner
console** that lives inside the Idoneity codebase at `/admin/*`. Every LLC
in the family — Praesidium Holdings, Idoneity Holdings, Idoneity SaaS,
Idoneity Marketplace / Bidwell, Arete Lyceum, Acuere Talent, and Stephens
Risk Management Consulting Services / Prometheus Risk Management — shares
this UI while keeping books legally separate via `entity_id` scoping.

- **Live URL:** https://idoneity.com/admin (owner login only)
- **Source repo:** [`idoneity`](https://github.com/praesidium-holdings/idoneity) → `docs/OWNER_CONSOLE.md`
- **Per-LLC pointers:** [`bidwell`](https://github.com/praesidium-holdings/bidwell/blob/main/docs/OWNER_CONSOLE.md), [`arete`](https://github.com/praesidium-holdings/arete/blob/main/docs/OWNER_CONSOLE.md), [`acuere`](https://github.com/praesidium-holdings/acuere/blob/main/docs/OWNER_CONSOLE.md), [`prm`](https://github.com/praesidium-holdings/prm/blob/main/docs/OWNER_CONSOLE.md)

## Surfaces shared across every LLC

| Surface | Route | Purpose |
|---|---|---|
| Corporate vault | `/admin/corporate` | Per-entity EIN, Sunbiz doc, filed status, doc set |
| Compliance calendar | `/admin/calendar` | FL annual reports, tax filings, insurance & domain renewals |
| Audit log | `/admin/audit` | Immutable who-did-what stream, filter + CSV export |
| AP | `/admin/ap` | Vendor invoices, OCR review, GL coding, bulk approve |
| AR | `/autonomy/ar` | Invoices out, aging, deposit matching, dunning |
| Close | `/admin/close` | 9-step month-end checklist per period |
| Reports | `/admin/reports` | Cash-basis P&L (BS + CF coming) |
| Exports | `/api/admin/exports/[dataset]` | Universal CSV — all list surfaces |

## Corporate-veil discipline

Every finance table carries an `entity_id` FK to `entities`. Every query
scopes by `entity_id`. That is what keeps books legally separate — not
codebase count. A single owner UI is operational convenience for a solo
owner; it does not comingle books.
