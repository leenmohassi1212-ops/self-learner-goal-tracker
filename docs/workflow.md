# Workflow

How this project is built with an AI model.

## Starting a chat

1. Paste `progress.md` first, then `plan.md`.
2. Add only the files the job needs.
3. Paste `rules.md` before asking for any code.

The model has no memory of this project, so anything it wasn't given, it will guess.

## Writing or changing a document

1. **Feed it:** give it the files that already exist. Never start a file cold.
2. **Interview:** it asks one question at a time, before drafting anything.
3. **Draft, then attack:** for every line, it says whether I stated it, I implied it, or it invented it. Invented lines come first.
4. **Decide:** I settle each invented line and record it in `decisions.md`. Anything I can't defend out loud comes out.

## Checking the folder

Run the fresh-chat test after any big change, in a chat that has never seen the project. If the answer is wrong, the fix goes in the file that should have said it, not in the chat.

## Who decides what

- The model drafts, questions, and points out risks.
- I decide what the app does and what gets cut.
- When the model suggests something, I check `decisions.md` to see if it was already killed.

## Saving work

- Commit and push after each finished piece of work, so GitHub always has the latest version.
- Update `progress.md` before every session.
- Add good prompts to `promot-log.md`.

## If time runs out

Follow the cut order in `scope.md`, starting with the AI next step. If a document has to be drafted without the interview, tag every guess `[ASSUMED]` and list it in `decisions.md`, as happened on 2026-11-05.

## Known weak spot

Task 03's interview was cut short because time was short, so most of the folder began as the model's draft. Going through the open assumptions in `decisions.md` is how that gets repaired.
