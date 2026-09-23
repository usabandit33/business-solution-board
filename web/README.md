# Web Prototypes

## Signup page

`signup.html` — role-based signup + email capture.

### How to use right now
1. Open the file in a browser, or
2. Serve it locally:
   ```bash
   npx serve web
   ```
3. Or push to any static host / import into Grok Build.

### What it captures
- Email (required)
- Display name (optional)
- Roles (one or more of: business_owner, solver, builder, observer)

Data is currently saved to `localStorage` under the key `bsb_signups` so you can inspect signups while prototyping.

See `docs/signup-and-email.md` for backend wiring options.
