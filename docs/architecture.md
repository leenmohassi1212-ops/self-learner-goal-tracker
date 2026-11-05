# Architecture

## The pieces, in words

    Browser  ->  Web app  ->  Database
                 Web app  ->  AI service (Gemini, then Groq)
    Scheduler  ->  Daily check (inside the web app)  ->  Database
                                                     ->  Email service  ->  Learner and chosen person
    Chosen person's email link  ->  Web app  ->  Database

## What each piece does and is not allowed to do

| Piece | Does | Not allowed to |
|---|---|---|
| Browser pages | Show the five screens, send the learner's actions | Talk to the database, email or AI directly; hold any secret key; calculate risk by itself |
| Web app | Log in, check ownership, save goals and tasks, calculate progress and risk | Show data to anyone but its owner (N2); send email except through the daily check or confirmation flow |
| Database | Keep the things in `data-model.md` | Be reachable without the web app's checks |
| Scheduler | Wake the daily check once an hour | Contain any logic of its own |
| Daily check | Find learners whose 8 AM has arrived, find no-task days, send emails, write email records | Email a pending or stopped chosen person (N1, N7); send twice for one day (N5) |
| Email service | Deliver what it is handed | Decide who gets what |
| AI service | Suggest a next step | Be required: the dashboard must work with it down (R12); receive names or emails (N9) |

## Why the check runs hourly

Learners live in different timezones, so "8 AM" arrives at different moments. `[ASSUMED A1]` The check runs every hour and only handles learners for whom it is now 8 AM. This is why N5 needs an email record: a repeated or late run must not send again.

## What will be hard

- **The daily check is the riskiest piece.** The consequence is the whole point of the app, and it runs with nobody watching. A silent failure means no warnings and the learner never finds out. It has to be tested by faking a missed day, not by waiting for one.
- **Day boundaries.** A tick at 11:59 PM and at 12:01 AM count for different days, and "day" means the learner's timezone, not the server's.
- **Emails landing in spam.** With no paid domain, warnings may never be seen. "Ignored" and "never arrived" look the same to the app. Test with Gmail and Outlook early.
- **Free-tier limits.** A free service can sleep or pause. If this happens on the final night, the demo fails. See `stack.md`.
- **Self-reporting.** The app can't tell if a task was really done or really fit in one day. A learner can tick everything to silence the emails. Version 1 accepts this.
