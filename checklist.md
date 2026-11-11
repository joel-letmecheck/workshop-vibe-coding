# Launch checklist — 10 boxes before you hit publish
Print this. Tick every box before real customers use your app.

- [ ] **Secret keys only on the server** — if not: strangers spend your money
- [ ] **RLS (Row Level Security) on for every table** — if not: customers see each other's data
- [ ] **Every action checks who's logged in, on the server** — if not: paywall and admin pages open
- [ ] **Rate limits on login, signup and AI calls** — if not: bots, guessed passwords, giant bills
- [ ] **Spending caps on every paid service** — if not: a surprise invoice
- [ ] **Backups on, and one restore tested** — if not: one bad command ends the company
- [ ] **Separate test and live databases** — if not: testing deletes real customers
- [ ] **You tested signup, login and payment yourself** — if not: customers find the bugs
- [ ] **Security scan run and every critical issue fixed** (e.g. free quick check at https://letmecheck.ai) — if not: attackers run it for you
- [ ] **Privacy page says what you collect and why** — if not: users can't trust you with data (ask a professional for the legal side)

Paste-ready prompts for each box: [cheatsheet.md](cheatsheet.md)
