# 09 The hourly check

Why
The riskiest piece in the app: it runs with nobody watching, and a silent failure means no warnings ever go out — the whole point lost invisibly (R9, N5, N12, `architecture.md`). Tests come first here (`rules.md`).

Done when
With clock times faked in tests: 47 hours without a tick sends nothing; 48 sends; 96 sends again (A22); after an outage only the latest 48-hour block sends (A24); a tick restarts the clock; a tick followed by an untick gains no time. The clock runs until the deadline and stops when every task is done (R9). Email records make a second run in the same hour send nothing (N5), matched on recipient, goal and period. Calling the endpoint without the secret key is refused and sends nothing (N12). One learner's failure doesn't stop the others; a failed send writes no record so the next run retries (`rules.md`). GitHub Actions triggers it hourly.

Touches
Check endpoint, email-record table, calculation module, GitHub Actions workflow.
