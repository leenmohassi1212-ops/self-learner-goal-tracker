# 04 Password reset

Why
A locked-out learner is the worst dead end in this app, because a started goal cannot be ended early (R1, `decisions.md`). Reset survives every cut (`scope.md`).

Done when
Asking for a reset sends an email with a link that works once and then expires; the answer on screen is the same whether or not the account exists (R1). The new password logs in. This is also the first real Brevo send through the app.

Touches
S1 screen (reset request + new password views), reset routes, learner table (reset value and expiry), email module.
