# Decisions

## 2026-11-05: how this folder was written

The interview was cut short. The task was due in 40 minutes, so the model asked two questions, then drafted from `brief.md`, `scope.md` and `promot-log.md` instead of interviewing for each file. Because of that, many lines below are the model's assumptions and are listed for review.

## 2026-11-05: decided in review

- **Stack: plain JavaScript and Node.** Killed the model's Next.js and Vercel recommendation, because it meant learning more new things.
- **The goal can't start until the chosen person confirms (was A8).** The model's draft let the goal run without them. Rejected, because a learner could avoid accountability by never getting a confirmation. The accepted cost is that a busy friend can delay the start.
- **Block dodging (was A16, A18).** No deleting tasks and no ending a goal early once it has started. The draft allowed both, and the model recommended telling the chosen person instead. Chosen the stricter way. The accepted cost is that a learner whose plans change is stuck until the deadline.
- **Warning emails go out after 48 hours with no task completed (was A1).** This reverses the earlier decision to email on any no-task day. The model's draft was 8 AM the next morning. The accepted cost is that a learner who ticks one task every 47 hours never triggers an email.

## 2026-11-05: assumed by the model, not yet confirmed

The model filled these gaps. For each one: confirm it, change it, then remove its tag from the file. A1, A8 and A18 are decided above and no longer appear in the files.

| ID | Assumption | Where | Why it matters |
|---|---|---|---|
| A2 | One active goal per learner | R2 | Keeps one dashboard screen and one simple no-task rule |
| A3 | Planned progress is a straight line from start to deadline; tasks have no planned dates | R5 | Ignores that some weeks are busier |
| A4 | Risk cut-offs: 0 behind, under 20%, 20% or more | R6 | The numbers have no evidence behind them |
| A5 | No backdating | N4 | Forgetting to tick yesterday still triggers the email |
| A6 | Chosen person sees only learner's name, goal name, time since the last task and risk | N6 | Privacy vs. how embarrassing the consequence feels |
| A7 | Chosen person can stop emails with a link | N7 | Consent, but it removes the consequence if used |
| A9 | Login with email and password | R1, N8 | Google login is the alternative |
| A10 | Express, Render, Supabase, Brevo and GitHub Actions, to fit plain JS and Node | `stack.md` | Picked from memory; free limits not checked |
| A11 | The 48-hour clock runs until the deadline, and stops when all tasks are done | R9 | Decides when the emails finally stop |
| A12 | Code conventions | `rules.md` | Naming, structure, comments and errors |
| A13 | Chosen person can be replaced, and the new one must confirm | R8 | A learner could swap away someone who was holding them to it |
| A14 | Five screens | `screens.md` | Session Four designs exactly these |
| A15 | AI gets goal, tasks and career note only; suggestions aren't saved | N9 | Privacy vs. suggestion quality |
| A16 | If the deadline passes with tasks left, the goal ends by itself | R13 | Without this, a learner who misses a deadline could never start a new goal |
| A17 | Start date is the day the chosen person confirms | R2 | A slow confirmation shortens the time until the deadline |
| A19 | Name asked at sign-up; timezone read from the browser | S1 | Used for the deadline and completion dates, no longer for email timing |
| A20 | Learner can write tasks while waiting, but not tick them | R8 | Work done before the confirmation isn't counted |
| A21 | Deadline can't be moved after the goal starts | N11 | Same dodge as deleting tasks; not covered by the review decision |
| A22 | Another email goes out every further 48 hours with no task completed | R9 | The alternative is one email only, which a learner could then ignore |
| A23 | The working routine | `workflow.md` | Written by the model during Task 03, not recorded from what you actually do |

## 2026-11-05: research.md and workflow.md written late

Neither Task 02 file was in the repo or found on the computer, so the model wrote both during Task 03. `research.md` found that evidence for social accountability is mixed, and one study found worse results. The idea stays, but the app can't promise that the consequence works. No learners have been interviewed yet.

## 2026-11-05: found by a rehearsal of the fresh-chat test

A model with no project context read the folder and caught these errors in the first drafts. All were fixed.

- Email retries contradicted "only at 8 AM". The check now handles anyone with no email record for the period, which still applies under the later 48-hour rule.
- The chosen person's email wasn't allowed to say who slipped. The learner's name is now allowed (N6).
- Duplicate checking ignored the goal, so someone chosen by two learners would miss an email. It now matches on goal too (N5).
- No requirement ended a goal, the start date was never collected, and neither were timezone or names. Now covered by R13, A17 and A19.
- Deleting tasks could erase delay. Solved by the decision to block deleting after the start.

Still open: `brief.md` says the app "turns a goal into daily tasks", then says the learner breaks it down. The requirements follow the second reading: the learner does it.

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
