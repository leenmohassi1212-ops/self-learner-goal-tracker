# Stack

Decided: plain JavaScript and a small Node server, because it means fewer new things to learn. `[ASSUMED A10]` The specific services and libraries below are the model's picks to fit that decision and are not yet confirmed.

| Piece | Tool | Honest reason |
|---|---|---|
| Language | JavaScript | This is a JS mentorship track |
| Pages | Plain HTML, CSS and JavaScript | Decided: nothing new to learn before building |
| Server | Node with Express | Express is the small, common way to run a Node server, and it serves the pages too |
| Login | Built by hand, with a standard password-hashing library | Decided: no framework or login service. See the risk in `architecture.md` |
| Hosting | Render, free tier | Free, runs a Node server, deploys from GitHub |
| Database | Supabase, free tier, as a database only | Free hosted database |
| Email | Brevo, free tier | Can send from a verified single address with no purchased domain |
| Scheduler | GitHub Actions, hourly | Free, and can run hourly |
| AI next step | Gemini, Groq as backup | Decided in `scope.md`; both have free tiers |

## Rejected

| Rejected | Why |
|---|---|
| Next.js with Vercel | Considered first, but it means learning a framework; plain JS and Node chosen instead |
| Native mobile app | Scope: web app chosen; phone tracking mostly blocked on iOS anyway |
| Calling Claude from the app | Scope: the Pro subscription has no API access and paid services aren't possible |
| Browser push notifications | Scope: iPhone requires home-screen install |
| Resend for email | Sending to other people's addresses needs a verified domain, which costs money (N10) |
| Separate frontend and backend | Two things to deploy, with about eight hours a week |

## Check in the first week

Free limits change, and these were written from the model's memory, not checked against the current pricing pages. Before relying on them:

- Does Render's free tier sleep when idle? If so, the first visit is slow, so open it before the final night.
- Does Supabase's free tier pause after inactivity? If so, the same applies.
- Does Brevo really deliver to Gmail from a single verified address, without landing in spam?
- Does GitHub Actions run close enough to on time? Scheduled runs can start late.
- Are the Gemini and Groq free tiers still available?
