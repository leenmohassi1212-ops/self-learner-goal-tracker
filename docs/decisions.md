# Decisions

## 2026-11-05: how this folder was written

The interview was cut short. The task was due in 40 minutes, so the model asked two questions, then drafted from `brief.md`, `scope.md` and `promot-log.md` instead of interviewing for each file. Because of that, many lines below are the model's assumptions and are listed for review.

## 2026-11-05: assumed by the model, not yet confirmed

The model filled these gaps. For each one: confirm it, change it, then remove its tag from the file.

| ID | Assumption | Where | Why it matters |
|---|---|---|---|
| A1 | No-task email goes at 8 AM the next morning, learner's timezone | R9 | Asked in the interview, not answered. Alternatives: 10 PM the same day, or learner chooses |
| A2 | One active goal per learner | R2 | Keeps one dashboard screen and one simple no-task rule |
| A3 | Planned progress is a straight line from start to deadline; tasks have no planned dates | R5 | Ignores that some weeks are busier |
| A4 | Risk cut-offs: 0 behind, under 20%, 20% or more | R6 | The numbers have no evidence behind them |
| A5 | No backdating | N4 | Forgetting to tick yesterday still triggers the email |
| A6 | Chosen person sees only goal name, missed day and risk | N6 | Privacy vs. how embarrassing the consequence feels |
| A7 | Chosen person can stop emails with a link | N7 | Consent, but it removes the consequence if used |
| A8 | Goal can run before the chosen person confirms | R9 | A learner could avoid accountability by never getting a confirmation |
| A9 | Login with email and password | R1, N8 | Google login is the alternative |
| A10 | The whole tool list | `stack.md` | Written without knowing what you already know |
| A11 | Checks run from the day after creation through the deadline, and stop when all tasks are done | R9 | Emails on day one would be unfair |
| A12 | Code conventions | `rules.md` | Naming, structure, comments and errors |
| A13 | Chosen person can be replaced, and the new one must confirm | R8 | A learner could swap away someone who was holding them to it |
| A14 | Five screens | `screens.md` | Session Four designs exactly these |
| A15 | AI gets goal, tasks and career note only; suggestions aren't saved | N9 | Privacy vs. suggestion quality |
| A16 | A goal ends when all tasks are ticked or the learner ends it | R13 | A learner could end a goal to stop the emails |
| A17 | Start date is the day the goal is created | R2 | A later start date would change planned progress |
| A18 | Adding or deleting tasks recalculates the plan | R3 | A learner could delete tasks to hide their delay |
| A19 | Name asked at sign-up; timezone read from the browser | S1 | Travel would shift the 8 AM email |

## 2026-11-05: found by a rehearsal of the fresh-chat test

A model with no project context read the folder and caught these errors in the first drafts. All were fixed.

- Email retries contradicted "only at 8 AM". Now the check handles anyone whose 8 AM has passed and has no email record.
- The chosen person's email wasn't allowed to say who slipped. The learner's name is now allowed (N6).
- Duplicate checking ignored the goal, so someone chosen by two learners would miss an email. It now matches on goal too (N5).
- No requirement ended a goal, the start date was never collected, and neither were timezone or names. Added as A16, A17 and A19.
- Deleting tasks could erase delay. Recorded as A18, not solved.

Still open: `brief.md` says the app "turns a goal into daily tasks", then says the learner breaks it down. The requirements follow the second reading: the learner does it.

## Before 2026-11-05: chosen (from `brief.md` and `scope.md`)

- Web app for mobile and desktop browsers, not native.
- First audience is self-learners building a market skill; students come later.
- The consequence is the product: visible risk, and someone the learner chose finding out.
- Email both people on any no-task day, with no waiting and no rest days.
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
- Detecting whether a warning email was read: unreliable; "ignored" means no task that day.
- Waiting before escalating, behind-plan-only trigger, rest days.
- Full analytics dashboard: reduced to one screen.
