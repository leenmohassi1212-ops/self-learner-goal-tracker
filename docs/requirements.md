# Requirements

Anything tagged `[ASSUMED An]` was drafted by the model and has not been confirmed. See the list in `decisions.md`.

## Must do

R1 A learner can sign up and log in with an email and password. `[ASSUMED A9]`
   Done when: a new learner can sign up, log out, and log back in to the same goal; a wrong password is refused.

R2 A learner can set one active goal: a target, a type (exam or self-set), and a deadline. `[ASSUMED A2]`
   The goal starts on the day the chosen person confirms (R8). That day is its start date. `[ASSUMED A17]`
   Done when: "AWS exam on a set date" and "finish a React course in four weeks" can both be saved; a second active goal is refused.

R3 A learner can break the goal into small ordered tasks, such as a lesson or a chapter.
   Tasks can be deleted only before the goal starts, so deleting can't hide a delay. Adding a task later recalculates the plan from the new total.
   Done when: tasks can be added, edited and reordered, and the order is still there after logging back in; deleting a task after the goal starts is refused.

R4 A learner can mark a task done, self-reported.
   Done when: ticking a task records today's date and progress changes at once; unticking clears it.

R5 The app compares planned progress with actual progress against the deadline. Planned progress is a straight line from the goal's start date to its deadline. `[ASSUMED A3]`
   Done when: for 10 tasks over 20 days, on day 10 with 3 done, it shows planned 5, actual 3, behind by 2.

R6 The app shows the delay and a risk level, labelled as an estimate. `[ASSUMED A4]`
   On track: not behind. At risk: behind by under 20% of all tasks. High risk: behind by 20% or more, or the deadline has passed with tasks left.
   Done when: with 10 tasks, being behind by 0, 1 and 2 shows On track, At risk and High risk.

R7 The app always shows a next step: the next unticked task, unless the learner picks a different one.
   Done when: ticking the current next step moves it to the next unticked task; a task the learner picked stays until it is ticked or changed.

R8 A learner names a chosen person by email, who must confirm by email before receiving anything. The goal cannot start until they confirm. While waiting, the learner can write tasks but not tick them, and no warning emails go out. `[ASSUMED A20 for writing tasks]`
   Done when: the chosen person's status stays "pending" until they click the confirm link; ticking is refused until then; if nobody confirms, the learner can name someone else; a new chosen person starts at "pending" again. `[ASSUMED A13]`

R9 After 48 hours with no task completed, the learner and their confirmed chosen person each get an email. The clock starts at the last tick, or at the goal's start if nothing has been ticked. There are no rest days. Each further 48 hours with no task completed sends another email. `[ASSUMED A22 for repeats]`
   Done when: 47 hours without a tick sends nothing; 48 hours sends both emails; 96 hours sends both again; a tick restarts the clock.
   The clock runs until the deadline, and stops once every task is done. `[ASSUMED A11]`
   If a chosen person stops emails or is replaced after the goal starts, only the learner gets the email until a new one confirms. `[ASSUMED A7, A13]`

R10 Goal, progress, risk and next step all appear on one dashboard screen.
    Done when: all four are visible on a phone browser and a desktop browser without opening another screen.

R11 The app is hosted live for the final night.
    Done when: it works at a public address from a phone that has never opened it before.

R12 (Built last, cut first.) The dashboard can show an AI next-step suggestion based on the learner's goal and career plans, using Gemini with Groq as backup.
    Done when: a suggestion appears; if Gemini fails Groq is tried; if both fail, the next unticked task still shows and nothing breaks.

R13 A goal is completed when every task is ticked. The learner cannot end a started goal early. If the deadline passes with tasks left, the goal ends by itself. `[ASSUMED for the deadline rule: A16]`
    Done when: ending a started goal early is refused; after a goal is completed or ended, a new goal can be created and no more emails are sent about the old one.

## Must never do

N1 Never email a chosen person about a learner before they have confirmed.
   Done when: a pending chosen person receives only the confirmation email, whatever the learner does.

N2 Never show one learner's goals or tasks to another learner.
   Done when: logged in as learner A, opening learner B's goal by its address is refused.

N3 Never present the risk level as a true prediction of passing or failing.
   Done when: the word "estimate" appears next to the risk level everywhere it is shown, including emails.

N4 Never let a learner backdate a completed task to avoid an email. `[ASSUMED A5]`
   Done when: the app has no way to enter a completion date; it is always the day of the tick.

N5 Never send the same person two warning emails about the same goal and the same 48-hour period.
   Done when: running the hourly check twice in a row sends each email once.

N6 Never tell the chosen person more than the learner's name, the goal's name, the time since the last completed task and the risk level. `[ASSUMED A6]`
   Done when: the email contains no task names and no other account details.

N7 Never keep emailing a chosen person who has opted out. Every email to them has a stop link. `[ASSUMED A7]`
   Done when: after clicking stop, that person receives nothing more for that goal, and the learner can see they stopped.

N8 Never store a password in readable form. `[ASSUMED A9]`
   Done when: the database holds no readable passwords.

N9 Never send anyone's name or email address to the AI service. `[ASSUMED A15]`
   Done when: the request contains only the goal, the remaining tasks and the career note.

N10 Never depend on a paid service.
    Done when: the live app runs a full week at a cost of zero.

N11 Never let a learner move the deadline after the goal starts. `[ASSUMED A21]`
    Done when: changing the deadline of a started goal is refused.
