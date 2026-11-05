# Architecture

## The pieces, in words

    Browser  ->  Web app  ->  Database
                 Web app  ->  AI service (Gemini, then Groq)
    Scheduler  ->  Hourly check (inside the web app)  ->  Database
                                                      ->  Email service  ->  Learner and chosen person
    Chosen person's email link  ->  Web app  ->  Database

## What each piece does and is not allowed to do

| Piece | Does | Not allowed to |
|---|---|---|
| Browser pages | Show the five screens, send the learner's actions | Talk to the database, email or AI directly; hold any secret key; calculate risk by itself |
| Web app | Log in, check ownership, save goals and tasks, calculate progress and risk | Show data to anyone but its owner (N2); send email except through the hourly check or confirmation flow |
| Database | Keep the things in `data-model.md` | Be reachable without the web app's checks |
| Scheduler | Wake the hourly check once an hour | Contain any logic of its own |
| Hourly check | Find learners past 48 hours with no completed task and no email record for that period, send emails, write email records | Email a pending or stopped chosen person (N1, N7); send twice for one day (N5) |
| Email service | Deliver what it is handed | Decide who gets what |
| AI service | Suggest a next step | Be required: the dashboard must work with it down (R12); receive names or emails (N9) |

## Why the check runs hourly

Each learner's 48 hours run out at a different moment, depending on when they last ticked a task. The check runs every hour and handles every learner past 48 hours with no email record for that period. So an email can arrive up to an hour late, at any time of day or night. A late run still sends, a failed email is retried on the next run, and the record stops anything going out twice (N5).

## What will be hard

- **The hourly check is the riskiest piece.** The consequence is the whole point of the app, and it runs with nobody watching. A silent failure means no warnings and the learner never finds out. It has to be tested by faking 48 quiet hours, not by waiting for them.
- **The 48-hour loophole.** A learner who ticks one task every 47 hours never triggers an email, so they can work every other day and nobody finds out. The risk level on the dashboard still shows the delay, but no email does. This is an accepted cost of the 48-hour rule.
- **Emails at odd hours.** Because the clock starts at the last tick, a warning can reach the chosen person at 3 AM.
- **Emails landing in spam.** With no paid domain, warnings may never be seen. "Ignored" and "never arrived" look the same to the app. Test with Gmail and Outlook early.
- **Free-tier limits.** A free service can sleep or pause. If this happens on the final night, the demo fails. See `stack.md`.
- **Login built by hand.** With no login service, password protection, sessions and the N2 ownership check are all on us. A mistake here exposes people's data.
- **A chosen person who never confirms.** The goal can't start until they do, so a busy friend blocks the learner completely. The only way out is naming someone else.
- **No undo after the start.** Tasks can't be deleted and the goal can't be ended early, so a learner whose plans really change is stuck until the deadline. This is deliberate, and it may feel harsh.
- **Self-reporting.** The app can't tell if a task was really done or really fit in one day. A learner can tick everything to silence the emails. Version 1 accepts this.
