# Self-Learner Goal Tracker

A web app for mobile and desktop browsers. It turns a learning goal into daily tasks and warns the learner, and a person they chose, when they fall behind.

> **Status:** Planning stage. The problem, scope, and first version are defined in [`docs/`](docs/). Development hasn't started yet.

## The Problem

Self-learners working toward a skill the market values, such as an AWS certification or React, often put off today's work across the week and never finish a goal. They get bored quickly even when they have the energy, lose hours to their phones, and don't know what to do next.

Current tools don't fix this because skipping them costs the learner nothing:

- **To-do lists, focus timers, and phone blockers:** learners ignore the reminders or turn the blockers off.
- **Studying with friends:** friends are too busy to meet regularly, and nobody holds anyone accountable.

The consequences that do work are seeing the real risk of missing the deadline, and knowing that someone the learner chose will find out when they slack off.

## How It Works

1. **Set a goal:** an exam date (e.g. AWS) or a self-set target and deadline (e.g. finish a React course in four weeks).
2. **Break it down:** split the goal into small tasks that each fit in one day, such as a lesson or a chapter.
3. **Mark tasks done:** completion is self-reported in version 1.
4. **Compare plan vs. actual:** the app tracks planned progress against actual progress toward the deadline.
5. **See the risk:** it shows where the delay is and the risk of missing the goal.
6. **Know the next step:** the next unticked task, the learner's own choice, or an AI suggestion based on their career plans.
7. **Accountability emails:** on any day with no task completed, the app emails both the learner and their chosen person. That person must confirm by email before they receive anything.

> The risk figure is an estimate based on progress against the plan. It doesn't predict whether the learner will pass.

## Who It's For

Version 1 is for **self-learners building a market-valued skill**, some with a fixed exam date and others with their own target and deadline. School and university students are planned as a later audience.

## Success

A learner succeeds when they reach the goal they set at the start, by its deadline, and always know their next step.

## Version 1 Scope

| # | Feature | Status |
|---|---|---|
| 1 | Accounts (sign-up and login) | In scope |
| 2 | Goals with a target and deadline (exam date or self-set) | In scope |
| 3 | Small daily tasks, marked done (self-reported) | In scope |
| 4 | Plan vs. actual progress against the deadline | In scope |
| 5 | Risk warning and delay display | In scope |
| 6 | Daily email on no-task days, to the learner and their chosen person | In scope |
| 7 | Chosen person confirms by email first | In scope |
| 8 | One-screen dashboard | In scope |
| 9 | Live hosting for the final demo | In scope |
| 10 | AI next-step suggestion (Gemini, with Groq as backup) | Built last, cut first |

### Out of Scope

| What | Why |
|---|---|
| Automatic phone and app usage tracking | Needs a native app; iOS mostly blocks it |
| Native mobile app | Web app chosen instead |
| Browser push notifications | iPhone requires home-screen install; email only |
| Automatic course-progress tracking | Planned for a future version |
| True "probability of failing" | Needs data from many learners; estimate only |
| Detecting whether warning emails were read | Unreliable; "ignored" means no task completed that day |
| Full analytics dashboard | Reduced to one screen |

## Constraints

- Eight-week timeline, solo developer, about eight hours per week
- Must be shown working live at the end
- No paid services beyond one AI subscription (free tiers of Gemini or Groq for in-app AI)

## Documentation

| File | Contents |
|---|---|
| [`docs/brief.md`](docs/brief.md) | Project brief: problem, audience, and how the app works |
| [`docs/scope.md`](docs/scope.md) | What's in and out of version 1 |
| [`docs/proplems.md`](docs/proplems.md) | Candidate problems the project addresses |
| [`docs/promot-log.md`](docs/promot-log.md) | Prompt log from the planning process |
