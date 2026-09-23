# Signup + Email Capture

## Goal

Let users sign up with:
1. **Email** (required)
2. **One or more roles** (Business Owner / Solver / Builder / Observer)
3. Optional display name

This feeds the account structure defined in `docs/account-structure.md` and gives us a clean list for outreach and future notifications.

## Prototype

A ready-to-use page lives at:

```
web/signup.html
```

Open it in any browser. It:
- Validates email + at least one role
- Stores the signup in `localStorage` (so you can inspect it)
- Logs the payload to the console
- Shows a success state

### Payload shape

```json
{
  "email": "owner@example.com",
  "display_name": "Alex’s HVAC",
  "roles": ["business_owner", "builder"],
  "source": "signup-page",
  "created_at": "2026-09-22T...
}
```

## Wiring a real backend (next steps)

Replace the `localStorage` block in `web/signup.html` with one of:

### Option A – Simple form service (fastest)
- [Formspree](https://formspree.io) or [Getform](https://getform.io)
- Point the form `action` or a `fetch` to their endpoint
- Emails land in your inbox immediately

### Option B – Your own API
```js
await fetch('/api/signup', {
  method: 'POST',
  headers: { 'Content-Type': 'application/json' },
  body: JSON.stringify(payload)
});
```

Suggested endpoint stores:
- email (unique)
- roles[]
- display_name
- created_at
- optional confirmation token for magic-link later

### Option C – Grok Build / hosted
Drop `web/signup.html` into any static host (Vercel, Netlify, GitHub Pages) or import the form into a Grok Build project. The payload is already structured for any backend.

## Email capture principles

- Email is the only required field.
- We ask for roles up front so every signup is already segmented.
- We only promise relevant emails (problems they follow, test invitations, solution updates).
- Always include an unsubscribe path when you send real mail.

## Suggested next build steps

1. Deploy `web/signup.html` (or convert to React/Next component).
2. Connect a real email capture endpoint.
3. Add a simple confirmation email (“You’re in – here’s how the board works”).
4. Later: magic-link login that re-uses the same email + roles.
