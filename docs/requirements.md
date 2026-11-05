# Requirements

Anything tagged `[ASSUMED An]` was drafted by the model and has not been confirmed. See the list in `decisions.md`.

## Must do

R1 A learner can sign up and log in with an email and password. `[ASSUMED A9]`
   Done when: a new learner can sign up, log out, and log back in to the same goal; a wrong password is refused.

R2 A learner can set one active goal: a target, a type (exam or self-set), and a deadline. `[ASSUMED A2]`
   The start date is the day the goal is created. `[ASSUMED A17]`
   Done when: "AWS exam on a set date" and "finish a React course in four weeks" can both be saved; a second active goal is refused.

R3 A learner can break the goal into small ordered tasks, such as a lesson or a chapter.
   Adding or deleting a task recalculates the plan from the new total, so deleting tasks can shrink the delay. `[ASSUMED A18]`
   Done when: tasks can be added, edited, deleted and reordered, and the order is still there after logging back in.

R4 A learner can mark a task done, self-reported.
   Done when: ticking a task records today's date and progress changes at once; unticking clears it.

R5 The app compares planned progress with actual progress against the deadline. Planned progress is a straight line from the goal's start date to its deadline. `[ASSUMED A3]`
   Done when: for 10 tasks over 20 days, on day 10 with 3 done, it shows planned 5, actual 3, behind by 2.

R6 The app shows the delay and a risk level, labelled as an estimate. `[ASSUMED A4]`
   On track: not behind. At risk: behind by under 20% of all tasks. High risk: behind by 20% or more, or the deadline has passed with tasks left.
   Done when: with 10 tasks, being behind by 0, 1 and 2 shows On track, At risk and High risk.

R7 The app always shows a next step: the next unticked task, unless the learner picks a different one.
   Done when: ticking the current next step moves it to the next unticked task; a task the learner picked stays until it is ticked or changed.

R8 A learner names a chosen person by email, who must confirm by email before receiving anything.
   Done when: the chosen person's status stays "pending" until they click the confirm link; a new chosen person starts at "pending" again. `[ASSUMED A13]`

R9 After any day with no task completed, the learner and their confirmed chosen person each get an email, sent at 8 AM the next morning in the learner's timezone. There are no rest days and no waiting period. `[ASSUMED A1 for the time]`
   Done when: a day with no tick produces both emails the next morning; a day with one tick produces none.
   Days checked run from the day after the goal is created through the deadline, and stop once every task is done. `[ASSUMED A11]`
   If the chosen person has not confirmed, only the learner gets the email. `[ASSUMED A8]`

R10 Goal, progress, risk and next step all appear on one dashboard screen.
    Done when: all four are visible on a phone browser and a desktop browser without opening another screen.

R11 The app is hosted live for the final night.
    Done when: it works at a public address from a phone that has never opened it before.

R12 (Built last, cut first.) The dashboard can show an AI next-step suggestion based on the learner's goal and career plans, using Gemini with Groq as backup.
    Done when: a suggestion appears; if Gemini fails Groq is tried; if both fail, the next unticked task still shows and nothing breaks.

R13 A goal is completed when every task is ticked, and the learner can end it at any time. A passed deadline alone does not end it. `[ASSUMED A16]`
    Done when: after a goal is completed or ended, a new goal can be created and no more emails are sent about the old one.

## Must never do

N1 Never email a chosen person about a learner before they have confirmed.
   Done when: a pending chosen person receives only the confirmation email, even on a no-task day.

N2 Never show one learner's goals or tasks to another learner.
   Done when: logged in as learner A, opening learner B's goal by its address is refused.

N3 Never present the risk level as a true prediction of passing or failing.
   Done when: the word "estimate" appears next to the risk level everywhere it is shown, including emails.

N4 Never let a learner backdate a completed task to avoid an email. `[ASSUMED A5]`
   Done when: the app has no way to enter a completion date; it is always the day of the tick.

N5 Never send the same person two no-task emails about the same goal and day.
   Done when: running the daily check twice in a row sends each email once.

N6 Never tell the chosen person more than the learner's name, the goal's name, the missed day and the risk level. `[ASSUMED A6]`
   Done when: the email contains no task names and no other account details.

N7 Never keep emailing a chosen person who has opted out. Every email to them has a stop link. `[ASSUMED A7]`
   Done when: after clicking stop, that person receives nothing more for that goal, and the learner can see they stopped.

N8 Never store a password in readable form. `[ASSUMED A9]`
   Done when: the database holds no readable passwords.

N9 Never send anyone's name or email address to the AI service. `[ASSUMED A15]`
   Done when: the request contains only the goal, the remaining tasks and the career note.

N10 Never depend on a paid service.
    Done when: the live app runs a full week at a cost of zero.
