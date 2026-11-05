# Rules

For any model writing code in this repo. `[ASSUMED A12: naming, structure, comments and errors are the model's draft]`

**If something is unclear, ask me instead of making assumptions.** (Session One line, from `promot-log.md` V1.)

## Naming

- Use the words from `data-model.md` in code: learner, goal, task, chosen person. Not user, friend, or buddy.
- Variables and functions in camelCase; files in kebab-case.
- Names say what something is. No `data`, `temp`, or `helper`.

## File structure

- One HTML page for each screen in `screens.md`. No extra screens.
- Plain JavaScript in the browser and Node on the server. No front-end framework.
- Calculation of progress and risk lives in one place, used by both the dashboard and the emails.
- Email wording lives in one place.
- Secret keys live in environment settings, never in the repo.

## Comments

- Explain why, not what.
- When code enforces a requirement, name it: R9, N5.

## Error handling

- Show the learner a plain sentence saying what failed and what to do next. Never a raw error.
- If AI fails, fall back to the next unticked task (R12).
- If an email fails, log it, write no email record, and let the next hourly run retry.
- A failure for one learner must not stop the hourly check for the others.

## Testing

- Every "Done when" in `requirements.md` is what gets tested.
- Risk, the 48-hour clock and the hourly check get tests first, because mistakes there are invisible.

## Never

- Never build anything in `screens.md`'s Not building line or `scope.md`'s out list.
- Never add a paid service or a new library without asking.
- Never bring back an idea killed in `decisions.md` without asking.
- Never email a real person from a test or the demo. Only addresses the project owner owns are allowed.
- Never change a requirement silently. Propose it, and record the decision in `decisions.md`.
- Never put a secret, password or real email address in the repo.
