# 12 Empty, loading and error states

Why
On demo night somebody opens the app with no data in it — that is the empty state, live, in front of people. And with Render's free tier, the loading state is the first thing every cold visit shows (`stack.md`, `design.md`).

Done when
Every screen shows the empty, loading and error states exactly as written in `design.md`: the dashboard with no goal points to S2; S3 with no tasks explains why one is needed; every whole-screen wait shows the shared loading state with the server-wake note; every whole-screen failure shows the v2 error screen (heading naming what failed, "nothing is lost" sentence, Try again, Back to log in), and every field-level failure shows the red input state with a sentence under the field — never a raw error (`rules.md`); the spinner holds still under prefers-reduced-motion.

Touches
All five screens, a shared loading partial, the shared error screen, the error helper.
