# Praesidium Holdings

**A family of operating brands covering the workforce-safety, compliance, learning, and hiring stack.**

Praesidium Holdings, LLC is a Florida holding company. Each brand below is its own legal entity with its own product, its own customers, and its own repo — but they interoperate so a customer of one can adopt another without re-integrating.

---

## The brands

### [Idoneity](https://github.com/praesidium-holdings/idoneity)
**Contractor management.** Prequalification, training-record competency tracking, and vendor risk ranking. The affordable, transparent alternative to ISN/Avetta/Veriforce.
*Idoneity, LLC*

### [Bidwell](https://github.com/praesidium-holdings/bidwell)
**Bid marketplace.** Post a job, get vetted bids, pick one. No lead-fee runaround.
*Idoneity Marketplace, LLC*

### [Arete Lyceum](https://github.com/praesidium-holdings/arete)
**Safety & technical LMS.** Course delivery and completion records that plug into contractor prequalification.
*Arete, LLC (pending amendment to Arete Lyceum, LLC)*

### [Acuere Talent](https://github.com/praesidium-holdings/acuere)
**Skilled-trades recruiting.** Hiring for construction, energy, industrial, and EHS roles.
*Acuere, LLC (pending amendment to Acuere Talent, LLC)*

### [Prometheus Risk Management](https://github.com/praesidium-holdings/prm)
**Safety/OSHA consulting.** Site-specific safety plans, training coordination, and compliance support for small and mid-sized operators. Based in Viera, FL.
*Prometheus Risk Management, LLC*

---

## Corporate structure

```
Praesidium Holdings, LLC  (Florida)
├── Idoneity Holdings, LLC
│   ├── Idoneity, LLC                 ── Idoneity (SaaS)
│   ├── Idoneity Marketplace, LLC     ── Bidwell
│   ├── Arete, LLC                    ── Arete Lyceum
│   └── Acuere, LLC                   ── Acuere Talent
└── Prometheus Risk Management, LLC   ── PRM (peer)
```

---

## How they talk to each other

- Shared **brand-family footer** mirrored across sites so a visitor to one brand sees the others.
- Contractor records from **Idoneity** carry over to **Bidwell** vetting and **Arete Lyceum** training assignments.
- **Prometheus** uses Idoneity + Arete internally when consulting for its safety-management clients.
- **Acuere Talent** placements can be flagged for Arete Lyceum onboarding automatically.

Each brand keeps its own users, its own database, and its own billing — the corporate veil is real. Interop happens at the API and data-portability layer, not through comingled state.

---

© Praesidium Holdings, LLC. All rights reserved.
