# 01 Project skeleton

Why
Nothing can be tested or demoed until a server runs at a public address with a database behind it, and the two known free-tier risks — Render sleeping, Supabase pausing — have to be seen early, not on demo night (`stack.md`, R11, N10).

Done when
Pushing to GitHub main deploys to Render by itself. Opening the public URL on a phone shows a page served by Express that reads one value out of Supabase and prints it. All keys live in environment settings; the repo contains none (`rules.md`).

Touches
Repo layout, Express server, Render service, Supabase project, environment settings.
