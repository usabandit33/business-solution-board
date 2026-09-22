# Account Structure & Roles

## Design Principles

1. **Keep identity light in MVP** — no complex profiles or social graphs.
2. **Roles are claims, not gates** — anyone can post a problem or solution; roles mainly affect credibility signals and future permissions.
3. **Business Owner is the highest-value signal** — we want to know when a real operator is speaking.
4. **One account can hold multiple roles** over time (e.g. an owner who also builds tools).
5. **Avoid heavy verification early** — self-declared + optional light proof is enough for the first 60–90 days.

---

## Core Roles

| Role | Primary Action | Credibility Weight | Notes |
|------|----------------|--------------------|-------|
| **Business Owner** | Post & validate problems, express "I'd test / I'd pay" | Highest | Can optionally link a business name / size / vertical |
| **Solver** | Propose practical solutions | Medium | Domain knowledge or prior experience |
| **Builder** | Claim a problem and work on a solution | Medium-High | Future: can update status, share results |
| **Observer** | Follow, comment lightly, validate | Low | Default for new accounts |

A single user account can declare one or more roles. The UI will surface the highest-relevant role for each action (e.g. when validating a problem, show as Business Owner if claimed).

---

## Account Fields (MVP)

```text
User
├── id
├── email (required for login)
├── display_name
├── roles[]                  # ["business_owner", "solver", "builder", "observer"]
├── business (optional)
│   ├── name
│   ├── verticals[]          # ["hvac", "plumbing", ...]
│   ├── size_range           # "1-5", "6-15", "16-50", "50+"
│   ├── location             # city / region (optional)
│   └── website / phone      # optional, private by default
├── created_at
└── last_active_at
```

### Self-Declaration Rules
- Roles are self-selected at signup or later in settings.
- No hard verification in MVP.
- Optional future: “Verified Owner” badge after simple proof (business card photo, domain email, LinkedIn, or supply-house reference).

---

## Permissions Matrix (MVP)

| Action                        | Observer | Solver | Builder | Business Owner |
|-------------------------------|----------|--------|---------|----------------|
| Post a problem                | ✓        | ✓      | ✓       | ✓              |
| "I have this problem too"     | ✓        | ✓      | ✓       | ✓ (higher weight) |
| Propose a solution            | ✓        | ✓      | ✓       | ✓              |
| Claim a problem (as Builder)  |          |        | ✓       | ✓              |
| "I'd test this"               | ✓        | ✓      | ✓       | ✓ (higher weight) |
| "I'd pay for this"            | ✓        | ✓      | ✓       | ✓ (highest weight) |
| Follow a problem              | ✓        | ✓      | ✓       | ✓              |
| Update solution status        |          |        | ✓ (own claims) | ✓ (own claims) |
| Edit / delete own content     | ✓        | ✓      | ✓       | ✓              |

Higher weight = the counter is shown more prominently or used in ranking (e.g. “7 Business Owners have this problem”).

---

## Why This Structure Works for the Empty-Room Problem

- Anyone can participate immediately (Observer / Solver).
- Real operators can self-identify and their signals carry more weight.
- Builders can claim work without needing a full company profile.
- We collect the three critical signals (have problem / would test / would pay) without forcing heavy profile completion.

---

## Future Extensions (Post-MVP)

- Verified Owner badge
- Team accounts (multiple people under one business)
- Builder reputation (completed claims, test results)
- Private messaging between Owner ↔ Builder (only after mutual interest)
- Stripe / payment intent signals for “I’d pay”
