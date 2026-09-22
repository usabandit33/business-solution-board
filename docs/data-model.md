# Data Model (MVP)

Simple relational model that supports the core loop without over-engineering.

## Entities

### User
See `docs/account-structure.md`.

### Problem
```text
Problem
├── id
├── author_id → User
├── title
├── description
├── verticals[]              # ["hvac", "plumbing", ...]
├── workflow_stages[]        # ["lead_response", "scheduling", "parts", ...]
├── location (optional)
├── company_size_range (optional)
├── status                   # "open" | "claimed" | "solved" | "archived"
├── validation_count         # denormalized for speed
├── solution_count
├── created_at
└── updated_at
```

### Validation ("I have this problem too")
```text
Validation
├── id
├── problem_id → Problem
├── user_id → User
├── role_at_time             # snapshot of highest role when validated
├── comment (optional, short)
├── intensity (optional)     # 1–5 "how bad is it"
└── created_at
```
Unique constraint: (problem_id, user_id)

### Solution
```text
Solution
├── id
├── problem_id → Problem
├── author_id → User
├── description
├── link (optional)
├── estimated_cost (optional)
├── effort (optional)        # "weekend" | "1-2 weeks" | "month+"
├── status                   # "proposed" | "claimed" | "in_progress" | "tested" | "launched"
├── claimed_by → User (nullable)
├── test_count               # denormalized
├── pay_interest_count       # denormalized
├── created_at
└── updated_at
```

### TestInterest ("I'd test this")
```text
TestInterest
├── id
├── solution_id → Solution
├── user_id → User
├── role_at_time
├── contact_preference (optional)
└── created_at
```
Unique: (solution_id, user_id)

### PayInterest ("I'd pay for this")
```text
PayInterest
├── id
├── solution_id → Solution
├── user_id → User
├── role_at_time
├── price_range (optional)   # "<$50/mo" | "$50-200" | "$200-500" | "$500+"
└── created_at
```
Unique: (solution_id, user_id)

### Follow
```text
Follow
├── user_id → User
├── problem_id → Problem
└── created_at
```

---

## Key Derived Metrics (shown on problem/solution cards)

- **Business Owners who have this problem** (count of Validations where role_at_time includes business_owner)
- **Total "I have this too"**
- **Solutions proposed**
- **I'd test** count
- **I'd pay** count + price-range distribution

These numbers are the primary ranking and trust signals.

---

## Indexing Priorities

- Problems by vertical + workflow_stage
- Problems ordered by validation_count (especially Business Owner validations)
- Solutions ordered by pay_interest_count + test_count
- Full-text search on title + description

---

## What We Explicitly Avoid in MVP

- Social graph / following users
- Private messages
- Complex reputation scores
- Multi-tenant organizations
- Payment processing (only interest signals)
