# 11 Goal end

Why
The finish line in both directions, and the one email on the biggest failure (R13). Without this, goals run forever and the dashboard has no outcome to show (R10).

Done when
R13's done-when passes: the last tick asks for confirmation and a completed goal can't be unticked; ending a started goal early is refused; when the deadline passes with tasks left (midnight, learner's timezone) the hourly check ends the goal and sends each person the missed-deadline email once, even if it runs twice; a completed goal sends none. The dashboard then shows the outcome, the final count, and "Start a new goal"; the old goal disappears once a new one exists and gets no more warnings (R10).

Touches
Check endpoint, goal status, S4 completed and ended states, email module.
