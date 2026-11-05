# Data model

No schema here, only what the app knows about.

## Learner
Email, protected password, name, timezone, career note (optional, entered on the Goal screen, only used for the AI suggestion), protected password-reset value and its expiry (empty unless a reset was asked for).

## Goal
Target, type (exam or self-set), start time (empty until the chosen person confirms), deadline, status (waiting, active, completed, or ended), picked next step (optional, points to one Task).

## Task
Title, position in the order, exact time completed (empty until ticked). The 48-hour clock needs the time, not only the date.

## Chosen person
Name, email, status (pending, confirmed, or stopped), private link value for the confirm and stop links.

## Email record
Recipient (learner or chosen person), goal, the 48-hour period it is about (counted in 48-hour blocks from the last tick or the goal's start, or that it is the missed-deadline email), the time it was sent.

This exists to enforce N5. Before sending, the hourly check looks for a record with the same recipient, goal and period. Someone chosen by two learners still gets both emails.

## Login session
Kept in the database by the session library (`stack.md`), so a learner stays logged in when the server restarts or sleeps.

## How they relate

- A learner has many goals over time, but only one active goal.
- A goal belongs to one learner and has many tasks.
- A goal has at most one current chosen person. Replacing them starts a new pending one. After the goal starts, only someone who stopped can be replaced.
- A goal has many email records.

## Deliberately not stored

- Risk level, delay, and planned progress. They are calculated from the deadline, start time and tasks each time, so they can't go out of date.
- Whether an email was read. Scope ruled this out as unreliable.
- AI suggestions. Generated when asked for, then thrown away.
