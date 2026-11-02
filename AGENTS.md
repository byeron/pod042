AGENTS.md

## 1. Plan before you touch code
- long task: first tell me in 2-3 sentences what you think I'm after
- Start only after I say yes
- Write the steps to `PLAN.md`, each with how you'll prove it works
- Two failed tries on one step: stop, note what failed, re-plan
- Pausing mid-task: leave `PLAN.md` so a new session can pick it up
- Every task is one issue with acceptance criteria written into it, one worktree, one PR
- Leave independent tasks in the `issues/` directory as Markdown files (`<number>-<slug>.md`, 0001-implement_new_feature.md). Set the `status` field to one of the following: `open` / `needs-human` (blocked by a user) / `done` (meets completion criteria) / `close` (out of scope).
- When you can't decide something, write down why and stop, don't guess

## 2. Smallest change that works
- Stay inside this task. Don't break anything that already works
- Tradeoff? Weigh UX (users), DX (the next dev) and AX (the next agent)
- No new dependencies, renames or refactors nobody asked for
- Back up before deleting or overwriting anything
- Pick the simplest implementation that meets the current needs. No premature abstraction, no unnecessary config layers
- Keep components modular, with separation of concerns
- Layer the system gradually. Get a minimal end-to-end version running first, then build on it. Never tear down working code for unfinished complexity
- Prioritize mature, maintained libraries. Don't rewrite unless there's a damn good reason
- First, check what your project's existing dependencies can do—then think about adding new packages or writing from scratch. Don't assume the libs are missing it right off the bat
- Make architecture decisions for the long haul. No "we'll swap it out later" half-measures
- See how mature products solve the same problem—use proven patterns, don't invent from scratch
- When the documentation and existing code conflict, follow the code's conventions, and in your final reply, list all the inconsistencies you found

## 3. Split work across subagents
- Explorer reads, worker edits, reviewer only reports and never edits
- Each gets one job, a done condition and a 5-line report
- Parallel is fine. Two agents on the same file is not
- Check the key claim in a report before you build on it

## 4. Own the bug
- Reproduce it with my steps first. Can't  reproduce it? Tell me what you need
- Fix the cause, then run the same steps again
- Never silence an error to make it go away

## 5. Verify before you say done
- Run the tests and read the output yourself
- UI: open it and try to break it: empty input, double submit, refresh
- Didn't run a check? Say so. An unrun check is not a pass
- Report in 2-3 lines: what you picked, what you gave up, and why

## 6. Write down every correction
- When I correct you, add a line under Lessons: "When X, do Y"
- Same mistake twice: the lesson is unclear. Rewrite it
- Ask me before changing anything above lessons

## Lessons
<!-- Newest on top. Delete what no longer applies.-->
