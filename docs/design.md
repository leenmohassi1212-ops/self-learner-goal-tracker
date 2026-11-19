# Design

The look and behaviour of every screen. Source of truth for layout is the v2 design canvas; this file carries everything the build needs in words, because next week the model reads this file, not a screenshot.

**Design canvas (v2, current):** https://claude.ai/artifact/Vj2nqRSmvp1WXS5uaJJZcP
**Figma file (v1, superseded):** https://www.figma.com/design/laIOka4SleP4JulAHQnG8N

v1 designed 2026-11-12; v2 redesigned 2026-11-19, both before the Brevo test and the interviews — see `decisions.md`. Treat the visuals as a draft until both happen; the states and rules below stand either way. Where v1 images below differ from this text, the text and the v2 canvas win.

## What changed in v2 (2026-11-19)

- **New colors:** deep navy ink (`#0B1324`) plus one blue accent (`#2F54EB`), replacing violet. The next-step card is the one dark (ink) card on the dashboard, so the next step is the first thing the eye finds.
- **New font:** Plus Jakarta Sans (Google Fonts), weights 400/500/600/700, replacing the system stack / Inter.
- **A dedicated error screen** ("We couldn't load your goal") with Try again and Back to log in — see Shared states.
- **Completed tasks move to the bottom.** On S3 (and the desktop task list) to-do tasks come first, in the learner's order; ticked tasks drop into a "Completed" group under them.
- **Minor notes removed from the screens:** the timezone footnote (S1), the "Only used for AI suggestions" footnote (S2), the "Tasks can be deleted only before the goal starts" footnote (S3, the rule is still enforced by the server), the "While you wait" card (S4 waiting), the "Risk is an estimate…" sentence on desktop (the ESTIMATE label beside the badge already covers N3), and the "every email has a stop link" footnote (S5; the stop link stays in every email, N7). Explainers were cut to one line each.

## The idea

Calm and quiet, so the one thing that matters — the risk and the next step — stands out.

- White cards on a soft cool-gray background. Navy ink for type and the next-step card; blue is the only accent, used mainly for the one primary button per screen.
- Green, amber and red appear only when they mean something: on track, at risk / the 48-hour clock, high risk / stopped.
- Rounded cards with thin 1px borders instead of shadows.
- One screen, one message, one primary action.
- Every risk mention carries the word "estimate" (N3).
- The design uses only fields in `data-model.md` or values computed from them. It forced no new fields.

## Tokens

Copy this into the stylesheet as-is. All text/background pairs pass WCAG AA (4.5:1).

```css
/* in <head>: <link rel="stylesheet" href="https://fonts.googleapis.com/css2?family=Plus+Jakarta+Sans:wght@400;500;600;700&display=swap"> */
:root {
  /* color */
  --bg-base: #F4F6FA;
  --bg-surface: #FFFFFF;
  --bg-subtle: #EEF1F6;
  --bg-pressed: #E3E7EF;
  --bg-ink: #0B1324;            /* the next-step card, logo tile, avatar */
  --text-primary: #0B1324;
  --text-secondary: #5A6478;
  --text-on-ink-label: #A9B8FF; /* small caps label on the ink card */
  --text-disabled: #98A1B3;     /* decorative only, never for real text */
  --accent: #2F54EB;
  --accent-hover: #2445D0;
  --accent-pressed: #1A36AE;
  --accent-text: #2446D8;
  --accent-soft: #EAEFFF;
  --on-accent: #FFFFFF;
  --success: #12804A;
  --success-soft: #E4F5EC;
  --warning: #A65B06;
  --warning-bar: #E08A1E;       /* the 48-hour bar fill only, never text */
  --warning-soft: #FDF2E2;
  --danger: #C8291D;
  --danger-soft: #FDECEA;
  --border: #E3E7EF;

  /* spacing — 8pt grid only */
  --space-4: 4px;  --space-8: 8px;   --space-12: 12px; --space-16: 16px;
  --space-24: 24px; --space-32: 32px; --space-48: 48px; --space-64: 64px;

  /* radius */
  --radius-card: 20px;
  --radius-control: 12px;     /* inputs; buttons use 14px */
  --radius-pill: 999px;

  /* type */
  --font: "Plus Jakarta Sans", system-ui, -apple-system, "Segoe UI", sans-serif;
}

@media (prefers-color-scheme: dark) {
  :root {
    --bg-base: #0B1020;
    --bg-surface: #151B2E;
    --bg-subtle: #1F2740;
    --bg-pressed: #29324D;
    --bg-ink: #1F2A4D;
    --text-primary: #F2F4F8;
    --text-secondary: #A3ACBF;
    --text-on-ink-label: #B9C6FF;
    --text-disabled: #5A6478;
    --accent: #4D6FFF;
    --accent-hover: #6683FF;
    --accent-pressed: #7F97FF;
    --accent-text: #9DB0FF;
    --accent-soft: #1E2A55;
    --success: #4ADE80;
    --success-soft: #12301F;
    --warning: #FBBF24;
    --warning-bar: #F59E0B;
    --warning-soft: #33260F;
    --danger: #F87171;
    --danger-soft: #3A1717;
    --border: #2A3350;
  }
}
```

## Type scale

Plus Jakarta Sans. Four weights: Regular 400, Medium 500, Semi Bold 600, Bold 700. Headings use letter-spacing -0.02em.

| Style | Size / line | Weight | Used for |
|---|---|---|---|
| Display number | 44 / 48 (56 desktop) | Bold | "N tasks behind plan" — the N |
| Title | 28 / 34 | Bold | Screen headings |
| Title 2 | 22 / 28 | Bold | Card headlines, next step, dashboard header |
| Headline | 16–17 / 24 | Semi Bold–Bold | Buttons, emphasized rows |
| Body | 15–16 / 23–24 | Regular | Default reading text, inputs |
| Footnote | 13 / 19 | Regular–Medium | Helper text, field errors |
| Label | 12 / 16 | Bold, +0.06em, caps | "NEXT STEP", "ESTIMATE", "AI SUGGESTION", pills |

## Rules

- Elevation: 1px `--border` line; at most `0 1px 2px rgba(0,0,0,0.04)`. No colored shadows.
- Motion: 150–250ms ease on hover/press/expand; none under `prefers-reduced-motion`.
- Focus: 2px `--accent` ring, offset 2px, on every interactive element.
- Touch targets at least 44px. Text measure at most 65ch.
- Icons are inline stroke SVG (2px, round caps), never emoji.
- Error messages: a plain sentence under the field or in place of the content, in `--danger`, saying what failed and what to do next — never a raw error (`rules.md`).

## Components (v1 images below; v2 canvas restyles them)

Button (Primary / Secondary / Tertiary × Default / Hover / Pressed / Disabled / Focus), Input (Default / Focus / Filled / Error / Disabled), Task Row (To do / Done), Badge (Neutral / Accent / Success / Warning / Danger), and 14 stroke icons.

![Components](design/components.png)

## Shared states

Two patterns every screen reuses, instead of inventing its own:

- **Loading.** Centered ink logo tile inside a spinning arc in `--accent` (still under `prefers-reduced-motion`), "Loading your goal…", and the one-line note "The first visit can take up to a minute." — because Render's free tier sleeps (`stack.md`). Used whenever a whole screen waits; a single action that waits (a save, a send) instead disables its button and swaps its label to "…ing" with the spinner.
- **Error screen (v2, its own artboard).** Small logo + "Goal Tracker" at the top; centered cloud-off icon in a white tile inside two `--danger-soft` rings; a heading naming what failed ("We couldn't load your goal"); one sentence saying nothing is lost ("your tasks and the 48-hour clock are safe on the server"); a small bordered hint "If the app was idle, the first try can take up to a minute"; "Try again" primary (refresh icon) pinned to the bottom, with "Back to log in" as a tertiary link under it. The container has `role="alert"`. Every whole-screen failure uses it, swapping only the heading and sentence (S5 uses "That didn't go through. Your answer wasn't recorded — try the link again."). A failed field-level action shows the Input error state instead: red 1.5px border, a soft red focus ring, and an icon + sentence under the field.

## Screens — all four states, every screen

Five screens (`screens.md`, A14). The extra dashboard frames on the canvas are states of S4, not new screens.

### S1 · Sign up / Log in — serves R1, N8

**On it:** logo, app name, tagline; a Sign up / Log in segmented control; Name (sign-up only), Email, Password inputs (the timezone is still read from the browser, A19, but no longer mentioned on screen); primary button; "Forgot your password?" tertiary link, which swaps the card to an email field + "Send reset link", and from the emailed link to a new-password field.

- **Empty:** the form itself is the empty state — blank fields with placeholder text, Sign up tab active. This is the first thing every new user sees.
- **Loading:** on submit, the button disables and reads "Creating account…" / "Logging in…" with the small spinner; fields lock.
- **Error:** a plain sentence under the failing field: "That email and password didn't match. Try again or reset your password." The reset request always answers "If that account exists, the email is on its way" — it never reveals whether an account exists (R1).
- **Full:** valid session → straight to S4. A logged-in learner who opens S1 is redirected to S4.

### S2 · Goal — serves R2, R8, R13, N11

**On it:** "Set your goal" heading; Goal input; Exam date / Self-set selector; Deadline input; optional career note (N9 still holds; the footnote is gone); a chosen-person card — one-line explainer ("They're emailed only after 48 hours with no task done. Your goal starts when they confirm."), their name + email inputs, and the screen's primary button, "Send confirmation request".

- **Empty:** blank form, Exam date preselected. Reached on day one from the dashboard's empty state, or via "Start a new goal" after an outcome.
- **Loading:** "Send confirmation request" disables to "Sending…". Saving edits to a waiting goal shows "Saving…".
- **Error:** naming your own account address → "Your chosen person can't be you — pick someone who'll notice" (R8). Request with zero tasks → the button stays disabled with the footnote "Add at least one task first" linking to S3 (R8). A failed send → "The email didn't go out. Nothing was lost — try again."
- **Full:** a waiting goal shows the saved values, editable, with Abandon as a tertiary action (R13). After the goal starts: deadline and target read-only (N11); the chosen person is replaceable only if they stopped (R8).

### S3 · Tasks — serves R3, R8

**On it:** "Break it into daily tasks" heading; the goal + deadline chip; an add-task field with a 48px "+" button; the ordered to-do list (checkbox, title, drag handle), then a "Completed" group below it; "Continue" primary.

- **Empty:** a dashed card with a list icon, "No tasks yet", and "Add the first small step — something you can finish today." Continue disabled, with "Add at least one task to continue." under it (R8).
- **Loading:** list area shows three gray skeleton rows on first load; adding a task disables the "+" while saving.
- **Error:** a failed add keeps the typed text in the field and shows "That didn't save. Try again." Deleting after the start, or the last task while a request is out, is refused with "Tasks are locked once the goal starts — that's the deal" / "The request Sara got promised at least one task" (R3, R8).
- **Full:** to-do rows first, in the learner's order, reorderable by drag; done rows (green check, struck-through, gray, no drag handle) move down into the "Completed" group on a subtle background. The stored order doesn't change — unticking puts a task back in its old place. Ticking happens on S4, not here.

### S4 · Dashboard — serves R4, R5, R6, R7, R8, R10, R12, R13, N3, N7

**On it (full/active):** greeting + goal + days-left header; status card — risk badge (On track `--success` / At risk `--warning` / High risk `--danger`) always next to the label "ESTIMATE" (N3), the N of "N tasks behind plan" as a large display number, one progress track — Done filled in `--accent`, a navy tick marking Planned by today — with counts (R5, R6); next-step card in `--bg-ink`, placed right under the status card — the next unticked task or the learner's pick (R7), with the screen's one primary button "Mark as done" (R4; the last task asks "This completes your goal — sure?" per R13); 48-hour clock card — "Last task done N h ago", hours left, amber bar toward 48h, "At 48 h, you and Sara get an email." (R9); AI suggestion card with "Add as a task" tertiary (R12 — if AI fails, the card simply shows the next unticked task and nothing breaks); chosen-person row with status badge (Confirmed / Pending / Stopped).

- **Empty:** no goal at all (new account, or the old goal is finished and replaced) → a single card: "No goal yet. One goal, a real deadline, someone who'll notice." with "Set your goal" primary leading to S2.
- **Loading:** skeleton: gray header bar plus three gray card outlines, with the shared loading note if it's the first hit of the day (server wake-up).
- **Error:** the shared error state — "We couldn't load your goal. Nothing is lost — your tasks and the 48-hour clock are safe on the server." + Try again.
- **Full** — five sub-states, all designed on the canvas:
  - **Waiting** (R8, A20): "Waiting for Sara to confirm" with a Pending badge, one sentence that the goal and clock start when Sara confirms, a "Choose someone else" link, a small summary (deadline, tasks written), and "Add more tasks" secondary.
  - **Active:** as described above.
  - **Person stopped** (N7, R9): a danger banner "Sara stopped emails — until someone else confirms, warnings go only to you", with "Choose someone else"; the chosen-person row shows a Stopped badge.
  - **Completed** (R10, R13): green check, "Goal completed", final count "30 of 30 tasks", "Start a new goal" primary. No email is sent (decision).
  - **Ended** (R10, R13): flag icon, "Deadline passed", the date, final count, note that both people got one final email, "Start a new goal" primary.

### S5 · Chosen person page — serves R8, N1, N6, N7

Opened from an email link, no login. **On it:** "Leen picked you" heading; what this is, in two sentences; the goal card (name + deadline — the request states the deadline so they agree knowing it, R8); a "What you'll get" list (an email only after 48 quiet hours; the goal name, delay and risk estimate, never task details — N6; one final email if the deadline is missed); "Confirm — I'm in" primary; "Stop all emails about this goal" in `--danger` (every email still carries a stop link, N7; the page no longer says so).

- **Empty (invalid link):** an ended or abandoned goal, or a replaced pending person → "This link isn't active anymore. Nothing more will be sent to you." No buttons (R13: a confirm link on an ended goal is refused).
- **Loading:** the shared loading state while the link is checked.
- **Error:** "That didn't go through. Your answer wasn't recorded — try the link again."
- **Full:** the request as above; after confirming → "You're in" (green check) with when they'll hear from us; after stopping → "Emails stopped" with "Leen can see that you stopped and may choose someone else."

## Emails (not screens, for completeness)

Five, wording in one place (`rules.md`): confirmation request (deadline included, R8), no-task warning to the learner, no-task warning to the chosen person (N6 fields only, stop link, "estimate", N3/N7), missed-deadline email (R13), password reset (R1). Email layout: plain, the app's name, one sentence of fact, one link.

![Screens](design/screens.png)

![Tokens sheet](design/tokens.png)
