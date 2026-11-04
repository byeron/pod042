# AGENTS.md

## 1. Plan before you touch code
- Long task: first tell me in 2-3 sentences what you think I'm after
- Start only after I say yes
- Write the steps to `PLAN.md`, each with how you'll prove it works
- Two failed tries on one step: stop, note what failed, re-plan
- Pausing mid-task: `PLAN.md` points to the live issue. Everything the next agent needs is in that issue's `## Handoff`.
- Every task is one issue with acceptance criteria written into it, one worktree, one PR
- Leave independent tasks in the `issues/` directory as Markdown files (`<number>-<slug>.md`, `0001-implement-new-feature.md`). Set the `status` field to one of the following: `open` / `needs-human` (blocked by a user) / `done` (meets completion criteria) / `closed` (out of scope). English issues live directly in `issues/`; `issues/jp/` holds translations only and is never a task source.
- Each issue file: frontmatter `status`, plus one `## Handoff` section, append-only, newest entry on top. No other section is required.
- Split every task into its smallest units. Each unit is one issue.
- `PLAN.md` is a pointer to issues, not a copy of them: one line per issue that links the `issues/` file. Never restate the issue body.
- `PLAN.md` and the `issues/` files are documents for information exchange between agents. Write them for the next agent, minimize token use; human readability is not a goal.
- Keep a Japanese translation for me to read in `issues/jp/` (`<number>-<slug>.md`). Update it when the English issue changes.
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
- Reproduce it with my steps first. Can't reproduce it? Tell me what you need
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
- Ask me before changing anything above Lessons

## 7. Hand off to the next agent
- Your job is a correct handoff, not a finish. It is fine to leave work unfinished in your own session if the next agent can resume cleanly.
- Before you stop, append to the issue's `## Handoff`: what you changed, the exact next step, the command to run, known blockers and dead ends.
- On resume: read `PLAN.md`, open the first issue with status `open`, read its `## Handoff`, run its verify command, then continue.
- A `## Handoff` note is already a `yes`. Don't ask me to continue an `open` issue.
- A subagent's 5-line report goes into the same `## Handoff`, tagged with its job (explorer / worker / reviewer).
- Dump rough thinking into `drafts/`. Don't polish it. Human readability is not a goal.
- Use compaction aggressively: a long transcript is a cost, not an asset. A step is not verified until its failure notes are in the issue's `## Handoff`. Compact only after that write.

## Lessons
<!-- Newest on top. Delete what no longer applies.-->
