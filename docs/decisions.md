# Decisions

## 2026-11-05: how this folder was written

The interview was cut short. The task was due in 40 minutes, so the model asked two questions, then drafted from `brief.md`, `scope.md` and `promot-log.md` instead of interviewing for each file. Because of that, many lines below are the model's assumptions and are listed for review.

## 2026-11-05: decided in review

- **Stack: plain JavaScript and Node.** Killed the model's Next.js and Vercel recommendation, because it meant learning more new things.
- **The goal can't start until the chosen person confirms (was A8).** The model's draft let the goal run without them. Rejected, because a learner could avoid accountability by never getting a confirmation. The accepted cost is that a busy friend can delay the start.
- **Block dodging (was A18, and an earlier version of A16 that let learners end a goal).** No deleting tasks and no ending a goal early once it has started. The draft allowed both, and the model recommended telling the chosen person instead. Chosen the stricter way. The accepted cost is that a learner whose plans change is stuck until the deadline.
- **Warning emails go out after 48 hours with no task completed (was A1).** This reverses the earlier decision to email on any no-task day. The model's draft was 8 AM the next morning. The accepted cost is that a learner who ticks one task every 47 hours never triggers an email.
- **Unticking takes the 48-hour clock back.** The clock counts from the most recent task still ticked, or from the goal's start if none are. Otherwise a tick and untick would silence the emails for free. The accepted cost is that a warning can go out straight after an untick if 48 hours have already passed.
- **A completed goal is final.** The learner confirms before the last tick, and it can't be unticked afterwards. This stops a finished goal being reopened. The accepted cost is that a learner who confirms by mistake can't undo it.
- **A goal needs at least one task before the confirmation request goes out.** So a goal can never start empty, and the last task can't be deleted while a request is out. The accepted cost is that a learner can write one task to get started and leave the plan thin until they add more.
- **Planned progress starts at day 0 and rounds down to a whole task.** A learner shows as behind only after missing a whole task, and the dashboard shows whole numbers. The accepted cost is that a learner can be slightly behind the exact line and still show On track.
- **The deadline passes at the end of the deadline date, in the learner's timezone.** The whole day counts. The accepted cost is that a learner can tick tasks after sitting an exam that same day.
- **A waiting goal can be edited or abandoned.** Nothing is at stake until it starts, so this doesn't weaken the no-dodging rule. A waiting goal counts as the learner's one goal, so a second is refused until it ends. If the deadline passes while waiting, it ends by itself and the confirm link stops working. The accepted cost is that a learner can abandon a goal rather than face a chosen person who is slow to reply.
- **A missed deadline sends one final email to both people; a completed goal sends none.** The model recommended telling them either way. Chosen the narrower way, to keep the consequence for the biggest failure with less to build. N6 now allows saying the deadline passed. The accepted cost is that a chosen person never hears when the learner succeeds, so the emails simply stopping could mean success or a stop.
- **After a goal finishes, the dashboard shows the outcome, the final count and a way to start a new goal.** The old goal stops being shown once a new one exists, so no history page is needed. The accepted cost is that a learner can't look back at past goals.
- **A learner can't name their own account address as the chosen person.** The accepted cost is that a second address of their own can't be detected, so a learner determined to dodge still can. Version 1 accepts this, as it does self-reporting.
- **After the start, a chosen person can be replaced only if they stopped (was A13).** The draft allowed any replacement, which let a learner switch off the consequence by naming someone who never confirms. Before the start, they can still be replaced freely. The accepted cost is that a friend who goes quiet without clicking stop stays in place until the deadline.
- **The confirmation request shows the deadline; there is no limit on how far away it can be.** The chosen person agrees knowing it and can push back on a silly date, and no invented cap is needed. N6 now allows the deadline. The accepted cost is that a distant deadline still weakens the risk level if the chosen person doesn't object, though the 48-hour emails still go out.
- **Password reset by email, but no check on the learner's own address.** A goal can't be ended early, so a lockout would be the worst dead end. Sign-up doesn't depend on email delivery, which is still untested. The accepted cost is that a mistyped address sends the learner's warnings, including their name and goal, to a stranger, and the learner gets no warnings themselves.
- **The demo uses a prepared goal and triggers the real hourly check live.** The goal's last tick is set over 48 hours back in the database, and emails go only to addresses the project owner owns. The app needs no fake-time feature. The accepted cost is that the demo still depends on the emails arriving promptly and outside spam.
- **An AI suggestion is text only.** A learner who likes it adds the task themselves, so no plan changes without a deliberate choice. The accepted cost is one extra step for the learner.
- **Warnings go out at any hour.** 48 hours means 48 hours, with no overnight hold, because a hold would give the learner a grace period to exploit. The accepted cost is that an annoyed friend woken at night might click stop.
- **Libraries: Express, pg, bcryptjs, express-session and connect-pg-simple; Node's own test runner and fetch.** Sessions come from widely used code because a mistake there could expose people's data (N2). Brevo is called through its web API. The accepted cost is two more libraries to learn. Anything further still needs asking (`rules.md`).
- **Before any code: test real Brevo sends to Gmail and Outlook, then talk to at least three self-learners, then design the screens.** Either result could change the plan, so both come before building on it. The accepted cost is that some of the eight hours a week go to checks instead of code.
- **The hourly check needs a secret key (N12).** The key lives in environment settings on Render and GitHub, and the demo uses it too. The accepted cost is one more secret to keep in step in two places.
- **Cut order: AI next step, the learner's own next-step pick, task reordering, the missed-deadline email.** These are furthest from the 48-hour warning. Password reset stays, because a lockout is the worst dead end. The accepted cost is that a tight finish loses the final email on the biggest failure.
- **Working date for the final night: about 2026-12-31.** This counts eight weeks from today. Check it against the real course date, because the first docs are from mid-October.

## 2026-11-05: assumptions confirmed in review

Every remaining assumption was confirmed as drafted, so no `[ASSUMED]` tags are left in the files.

- **A4:** risk cut-offs are 0 behind, under 20%, and 20% or more. The number still has no evidence, so revisit it after the interviews.
- **A6:** the chosen person sees only what N6 lists, with no task names.
- **A7:** the chosen person can stop emails with a link, and the learner sees that on the dashboard. The accepted cost is that using it removes the consequence until a replacement confirms.
- **A22:** another email goes out every further 48 hours with no task completed. The accepted cost is that a tired friend may click stop.
- **A2:** one active or waiting goal per learner. Several goals could come in a later version.
- **A3:** planned progress is a straight line, and tasks have no planned dates. The accepted cost is that a planned busy week shows as falling behind.
- **A5:** no backdating. The accepted cost is an occasional unfair email when a learner forgets to tick.
- **A21:** the deadline never moves after the start. The accepted cost is that a real exam reschedule leaves the risk level wrong until the old date.
- **A11:** the 48-hour clock runs until the deadline, and stops when all tasks are done.
- **A16:** if the deadline passes with tasks left, the goal ends by itself. The accepted cost is that unfinished tasks do not carry over to a new goal.
- **A17:** the goal starts when the chosen person confirms. The accepted cost is that a slow confirmation shortens the time until the deadline.
- **A20:** the learner can write tasks while waiting, but not tick them. The accepted cost is that work done before the confirmation is not counted.
- **A9:** login is by email and password. The accepted cost is that protecting passwords is on us (N8).
- **A10:** Express, Render, Supabase, Brevo and GitHub Actions, subject to the checks in `stack.md`.
- **A15:** the AI gets the goal, remaining tasks and career note only, and suggestions are not saved. The accepted cost is that it can repeat itself.
- **A19:** sign-up asks for the name, and the timezone is read from the browser once. The accepted cost is that a move abroad shifts when the deadline passes.
- **A12:** the code conventions in `rules.md`.
- **A14:** five screens, and Session Four designs exactly these.
- **A23:** the working routine in `workflow.md` matches how the project owner works.
- **A24:** a 48-hour period is a block counted from the last tick or the goal's start. After an outage, only the latest block gets an email, so nobody gets a run of old warnings. The email states the real time since the last task.

## 2026-11-05: research.md and workflow.md written late

Neither Task 02 file was in the repo or found on the computer, so the model wrote both during Task 03. `research.md` found that evidence for social accountability is mixed, and one study found worse results. The idea stays, but the app can't promise that the consequence works. No learners have been interviewed yet.

## 2026-11-05: found by a rehearsal of the fresh-chat test

A model with no project context read the folder and caught these errors in the first drafts. All were fixed.

- Email retries contradicted "only at 8 AM". The check now handles anyone with no email record for the period, which still applies under the later 48-hour rule.
- The chosen person's email wasn't allowed to say who slipped. The learner's name is now allowed (N6).
- Duplicate checking ignored the goal, so someone chosen by two learners would miss an email. It now matches on goal too (N5).
- No requirement ended a goal, the start date was never collected, and neither were timezone or names. Now covered by R13, A17 and A19.
- Deleting tasks could erase delay. Solved by the decision to block deleting after the start.

`brief.md` said the app "turns a goal into daily tasks", then said the learner breaks it down. It now says the app helps the learner do it, which matches the requirements.

## 2026-11-05: questions from the fresh-chat test

The test understood what we're building, for whom, and what we're not building. These are the questions it would still ask. All were settled in review on 2026-11-05.

1. **Unticking:** decided above, for both the clock and a completed goal.
2. **Zero tasks:** decided above. A goal needs at least one task before the request goes out.
3. **Planned progress:** decided above. Day 0 start, rounded down.
4. **Goal ends:** decided above: the deadline's exact moment, waiting goals, the final email and the dashboard afterwards.
5. **More dodges:** decided above: naming their own address, replacing mid-goal, and a distant deadline.
6. **Accounts:** decided above. Password reset, no address check.
7. **Live demo:** decided above. Prepared goal, real check, owned addresses only.
8. **AI next step:** decided above. Text only.
9. **3 AM emails:** decided above. Warnings go out at any hour.
10. **Libraries:** decided above.
11. **Order of work:** decided above. Email test, interviews, then screens.

## Before 2026-11-05: chosen (from `brief.md` and `scope.md`)

- Web app for mobile and desktop browsers, not native.
- First audience is self-learners building a market skill; students come later.
- The consequence is the product: visible risk, and someone the learner chose finding out.
- Email both people on any no-task day, with no waiting and no rest days. (The timing was replaced by the 48-hour rule above; no rest days still stands.)
- Chosen person must confirm by email first.
- Task completion is self-reported in version 1.
- Risk is an estimate only.
- AI next step uses Gemini with Groq as backup, built last and cut first.
- Constraints: eight weeks, alone, about eight hours a week, no paid services.

## Before 2026-11-05: killed (from `scope.md`)

Do not suggest these again without a new reason.

- Automatic phone and app usage tracking: needs a native app; iOS mostly blocks it.
- "Simulation of the user's brain" and all parts of life: too broad.
- Browser push notifications: iPhone needs home-screen install.
- Calling Claude from the app: Pro has no API access.
- Automatic course-progress tracking: future version.
- True "probability of failing": needs many learners' data.
- Detecting whether a warning email was read: unreliable; "ignored" means still no task 48 hours later.
- Behind-plan-only trigger, rest days. (Waiting before escalating was also killed here, then brought back as the 48-hour rule.)
- Full analytics dashboard: reduced to one screen.
