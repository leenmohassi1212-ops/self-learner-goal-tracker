# 03 Sign up and log in

Why
Everything else needs to know who is logged in, and login is hand-built — the riskiest security piece in the app (R1, N2, N8, `architecture.md`).

Done when
A learner signs up with name, email and password (timezone read from the browser once, A19), logs out, logs back in, and lands on the same account. A wrong password is refused with a plain sentence. The database holds no readable password (N8). Opening another learner's goal by its address is refused (N2). The session survives a server restart (connect-pg-simple).

Touches
S1 screen, auth routes, session store, learner table.
