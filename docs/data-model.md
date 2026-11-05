# Data model

No schema here, only what the app knows about.

## Learner
Email, protected password, name, timezone, career note (optional, only used for the AI suggestion).

## Goal
Target, type (exam or self-set), start date (empty until the chosen person confirms), deadline, status (waiting, active, completed, or ended), picked next step (optional, points to one Task).

## Task
Title, position in the order, date completed (empty until ticked).

## Chosen person
Name, email, status (pending, confirmed, or stopped), private link value for the confirm and stop links.

## Email record
Recipient (learner or chosen person), goal, the day it is about, the time it was sent.

This exists to enforce N5. Before sending, the daily check looks for a record with the same recipient, goal and day. Someone chosen by two learners still gets both emails.

## How they relate

- A learner has many goals over time, but only one active goal. `[ASSUMED A2]`
- A goal belongs to one learner and has many tasks.
- A goal has at most one current chosen person. Replacing them starts a new pending one. `[ASSUMED A13]`
- A goal has many email records.

## Deliberately not stored

- Risk level, delay, and planned progress. They are calculated from the deadline, start date and tasks each time, so they can't go out of date. `[ASSUMED A3]`
- Whether an email was read. Scope ruled this out as unreliable.
- AI suggestions. Generated when asked for, then thrown away. `[ASSUMED A15]`
