# Vibe Coding Without Getting Burned — Cheat Sheet
Workshop by Joel, founder of [LetMeCheck](https://letmecheck.ai) · demo app: https://letmecheckdemo.netlify.app/

Every risk: **what breaks → what it costs you → what to tell the AI.**

## 3 review prompts (paste after every big feature)
1. "What could a stranger do with this app that they shouldn't be able to? Rank each by how bad it is, and fix the worst first."
2. "List every place this app stores or shows customer data, and who can see it. Flag anything visible without logging in."
3. "What would break if 1,000 people used this at once, or one person hit it 10,000 times? What would it cost us?"

## Before you build
- Write a rules note the AI reads every time → [rules-template.md](rules-template.md)
- Describe who the users are and what each may see and do
- "Commit to GitHub after every change that works." (save points)
- One feature per request. First ask: "List the files you'll touch and why." Click through it before the next.
- Before bigger changes: "Before you change anything, list the files you'll touch and why. Keep a plain notes file that explains how the app fits together."

## Fix prompts by area
| Area | What breaks | Tell the AI |
|---|---|---|
| Browser (frontend) | Secret keys in the page can be copied by anyone | "Find every secret key or password in code that runs in the browser. Move each to the server, and tell me which keys I must replace." |
| Server (backend) | Paywall skipped, users act as others | "Make every action check on the server who is logged in and whether they're allowed." |
| Server | Users edit prices or roles and pay nothing | "Recalculate prices and roles on the server. Ignore them from the browser." |
| Server | One script runs up your AI bill | "Add rate limits to login, signup and every AI call." |
| Bills | No ceiling when it goes wrong | "List every paid service we call and where I set a monthly limit." |
| Database | Customers see each other's data | "Turn on Row Level Security (RLS) for every table. Users only see their own rows." |
| Files/storage | Uploaded IDs or photos open to anyone | "List every place we store files or data. Can anyone open them without logging in? Lock each one to its owner." |
| Growing app | Fix one thing, break three | "Before you change anything, list the files you'll touch and why. Keep a plain notes file that explains how the app fits together." |

## 3 publish prompts
1. Test: "Write tests for signup, login, payment and our main feature. Run them and tell me in plain English what failed."
2. Review: "Act as a security reviewer. Go through every page and API route and list what a logged-out user, or a different user, could reach."
3. Scan & fix: "Here is my security report. Fix one issue at a time, explain each fix simply, and tell me how to check it worked."

Free quick check (about a minute, no account): https://letmecheck.ai

## Launch checklist
See [checklist.md](checklist.md).

## Secret keys by tool
- Put secret keys in your tool's server-side secrets. Any setting whose name starts with `VITE_` or `NEXT_PUBLIC_` is visible to everyone.

## Call a developer when…
- you take payments or store IDs or health data
- customers depend on it every day
- the AI goes in circles on the same bug
- an investor or client asks "is it secure?"

## Real incidents mentioned
- Tea app, July 2025: ~72,000 images exposed incl. ~13,000 selfies and photo IDs (Reuters, 26 Jul 2025: https://www.reuters.com/sustainability/boards-policy-regulation/womens-dating-app-tea-reports-72000-images-stolen-security-breach-2025-07-26/); second leak of ~1.1 million private messages (BleepingComputer, 28 Jul 2025: https://www.bleepingcomputer.com/news/security/tea-app-leak-worsens-with-second-database-exposing-user-chats/)
- Replit agent deleted SaaStr's production database during a code freeze, July 2025 (The Register, 21 Jul 2025: https://www.theregister.com/2025/07/21/replit_saastr_vibe_coding_incident/)
- CVE-2025-48757: weak RLS policies in Lovable-generated sites (disputed by Lovable): https://www.cve.org/CVERecord?id=CVE-2025-48757
