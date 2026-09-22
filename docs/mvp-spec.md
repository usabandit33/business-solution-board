# MVP Specification

## Goal of MVP

Validate that people will:
1. Confirm real problems ("I have this too")
2. Propose solutions
3. Express willingness to test
4. Express willingness to pay

Without building a full social platform.

## Core Features

### 1. Post a Problem
- Title (required)
- Description (required)
- Category (home-service vertical or workflow stage)
- Optional: industry tags, company size range, location (city/region)
- Author type: Business Owner / Solver / Builder / Observer

### 2. I Have This Problem Too
- One-click validation counter
- Optional short comment ("How bad is it for you?")

### 3. Propose a Solution
- Text description
- Optional: link, rough cost estimate, build effort
- Can be claimed later by a Builder

### 4. Follow a Problem
- Notification when new solutions or validation activity happens

### 5. I'd Test This
- Button on a proposed solution
- Counter + optional contact preference

### 6. I'd Pay for This
- Button on a proposed solution
- Optional price range indication

### 7. Categories
- By vertical (HVAC, Plumbing, …)
- By workflow stage (Lead response, Scheduling, Parts, Invoicing, …)

### 8. Search
- Full-text search across problems and solutions
- Filters: category, validation count, "has paid interest"

## Non-Goals (MVP)

- Private messaging
- User profiles beyond basic type + optional business name
- Feed / infinite scroll social experience
- Ads or paid promotion
- Complex recommendation AI
- Mobile apps (responsive web is enough)

## Seeding Requirement

Before launch, populate with 30–100 real observed problems from public sources (Reddit, forums, reviews). This is non-negotiable to avoid the empty-room problem.

## Success Metrics (first 30–60 days)

- % of problems that receive ≥3 "I have this too"
- % of problems that receive ≥1 proposed solution
- Number of "I'd test" / "I'd pay" signals
- Qualitative feedback from early home-service owners
