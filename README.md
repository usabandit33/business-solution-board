# Business Solution Board

**A structured community where business owners post real problems and get validated solutions.**

Not another social network. A living database of:

- Business problems
- Proposed solutions
- Validation signals ("I have this problem too")
- Willingness to test
- Willingness to pay
- Results from real tests

## Current Status

- **45 real HVAC problems** seeded in `data/seed-problems/` (from Reddit + industry sources 2023–2026)
- Soft-outreach templates and channel list ready in `docs/outreach/`
- Ready for first validation: confirm problems → “I’d test” → “I’d pay”

## Core Loop

1. Business owner posts a problem
2. Others click **I Have This Problem Too**
3. Members propose solutions
4. Businesses indicate **I'd Test This**
5. Businesses indicate **I'd Pay for This**
6. Builders claim a problem and build
7. Results are recorded

## Initial Target Market

**Home-service businesses:**

- HVAC ← **starting here**
- Plumbing
- Electrical
- Appliance repair
- Garage doors
- Pest control
- Cleaning
- Roofing
- Landscaping

### Primary Workflow to Investigate

`Lead received → customer contacted → estimate → scheduling → job → invoice → payment`

Common pain points: missed calls, slow lead response, estimate follow-up, scheduling, cancellations, no-shows, dispatch, technician routing, customer updates, parts availability, invoicing, collections.

## MVP Features

- [x] Post a problem
- [x] I Have This Problem Too
- [x] Propose a solution
- [x] Follow a problem
- [x] I'd Test This
- [x] I'd Pay for This
- [x] Categories
- [x] Search

**Out of scope for MVP:** complex profiles, messaging, social feed, ads, heavy AI features.

## User Types

| Type | Can do |
|------|--------|
| **Business Owner** | Submit & validate problems |
| **Solver** | Propose practical solutions |
| **Builder** | Claim a problem and build a solution |
| **Observer** | Follow and participate |

## Example

**Problem**
> My technicians waste 30–45 minutes every morning figuring out which jobs have the right parts available.

**Validation**
- 43 businesses have this problem
- 12 would test a solution
- 7 would pay for a solution

**Proposed Solutions**
- QR-based truck inventory
- Better inventory software
- Automated parts tracking
- Outsourced inventory management

## Relationship to Mogul

| | Mogul | Business Solution Board |
|---|-------|-------------------------|
| Question | What boring business opportunity should I pursue? | What problems are businesses repeatedly experiencing, and who is willing to pay for a solution? |
| Use | Opportunity discovery | Validated demand data |

A future Mogul scout can pull high-signal problems from this board instead of only external research.

## Critical Risk: Empty Room

Nobody posts because nobody answers, and nobody answers because nobody posts.

**Mitigation:** Seed the board with real business problems *before* trying to grow a large community. **Done for HVAC.**

First validation question:
> Do people naturally confirm problems, propose solutions, and express willingness to test or pay?

## Research Strategy

Prefer **observed complaints** over survey answers.

Sources used so far:
- Reddit (r/HVAC, r/hvacpeople, r/hvacadvice)
- Industry reports & forums

Strong signal:
> "I spent my entire Saturday doing this manually."

Weak signal:
> "What business problems do you have?"

## Working Principle

**Don't build another place for businesses to talk.**

Build a place where business problems become:

**identified → validated → solved → tested → commercialized.**

---

## Repo Structure

```
├── README.md
├── docs/
│   ├── concept.md
│   ├── mvp-spec.md
│   ├── research/
│   └── outreach/          # Soft outreach templates & channels
├── data/
│   └── seed-problems/     # 45 real HVAC problems
└── research/              # (on research branch) original chat + source docs
```

See the `research` branch for the original chat history and concept source.
