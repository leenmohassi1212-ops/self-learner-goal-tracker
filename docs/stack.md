# Stack

`[ASSUMED A10]` The whole table except the AI row is the model's recommendation, not yet confirmed. Replace it with what you already know if that differs. "It is what I already know" beats everything below.

| Piece | Tool | Honest reason |
|---|---|---|
| Language | JavaScript | This is a JS mentorship track |
| Web app and pages | Next.js (React) | One project holds both pages and server logic, so one person has fewer pieces to run |
| Hosting | Vercel, free tier | Free, deploys from GitHub, works with Next.js |
| Database and login | Supabase, free tier | One service covers both, including protected passwords (N8) |
| Email | Brevo, free tier | Can send from a verified single address with no purchased domain |
| Scheduler | GitHub Actions, hourly | Free, and can run hourly |
| AI next step | Gemini, Groq as backup | Decided in `scope.md`; both have free tiers |

## Rejected

| Rejected | Why |
|---|---|
| Native mobile app | Scope: web app chosen; phone tracking mostly blocked on iOS anyway |
| Calling Claude from the app | Scope: the Pro subscription has no API access and paid services aren't possible |
| Browser push notifications | Scope: iPhone requires home-screen install |
| Resend for email | Sending to other people's addresses needs a verified domain, which costs money (N10) |
| Vercel's built-in scheduler | The free tier is too limited for hourly runs |
| Separate frontend and backend | Two things to deploy, with about eight hours a week |

## Check in the first week

Free limits change, and these were written from the model's memory, not checked against the current pricing pages. Before relying on them:

- Does Supabase's free tier pause after inactivity? If so, open it before the final night.
- Does Brevo really deliver to Gmail from a single verified address, without landing in spam?
- Does GitHub Actions run close enough to on time? Scheduled runs can start late.
- Are the Gemini and Groq free tiers still available?
