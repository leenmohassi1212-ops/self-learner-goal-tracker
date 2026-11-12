# 02 Database tables

Why
Every later ticket writes to these tables, and the design was checked against `data-model.md` so no screen needs a field that isn't here. Getting the fields right now prevents the week-six schema change.

Done when
Tables exist for learner, goal, task, chosen person, email record and login session, with exactly the fields in `data-model.md` (task completion is a timestamp, not a date — R9 needs the time). A small script can insert and read back a row of each from the deployed app.

Touches
Supabase schema, a db module (pg), `data-model.md`.
