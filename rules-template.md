# Rules note for my AI coding tool
Save this as `rules.md` in your project (or paste it into your tool's rules / knowledge / custom-instructions setting). Ask the AI to read it before every task.

## What the app is
- App: <one sentence, e.g. "booking tool for yoga studios">
- Who uses it: <e.g. studio owners, students, me as admin>
- What each user may see and do:
  - <role 1>: <can see / can do>
  - <role 2>: <can see / can do>

## Never do this
- Never put secret keys or passwords in code that runs in the browser. Keep them on the server / in environment settings.
- Never turn off or loosen database access rules (RLS) to make an error go away. Tell me instead.
- Never change or delete the live database without asking me first. Use the test database.
- Never trust prices, roles or user IDs sent from the browser. Check them on the server.

## Always do this
- Check on the server, for every action, who is logged in and whether they're allowed.
- Add rate limits to login, signup and anything that calls a paid AI service.
- Before changing code, list the files you'll touch and why. Wait for my OK on big changes.
- After every change that works, commit to GitHub with a short message.
- Keep a plain notes file explaining how the app fits together, and update it after each change.
- Explain what you did in plain English. I am not a developer.

## Data we store
- <e.g. names, emails, booking history; NO card numbers (Stripe handles payments)>
