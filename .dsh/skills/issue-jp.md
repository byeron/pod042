---
name: issue-jp
description: "Write a Japanese reading copy of issues/ under issues/jp/ for the user."
whenToUse: "Only when the user invokes /issue-jp. Never on the agent's own judgment."
disable-model-invocation: true
user-invocable: true
---

# /issue-jp

`issues/` is the task source. `issues/jp/` is for the user's eyes only and is never a task source.

## Scope

- The issues named in the user's message. A named issue is translated whatever its `status`. Anything the user says they will not read is skipped, even when named.
- If none is named: every issue with `status: open` or `status: needs-human`. Skip `closed` and `done`.

## Output

One file per issue: `issues/jp/<number>-<slug>.md`, same name as the English file. Five fields, no other content. Frontmatter: `status` (the current value, unchanged) and `検証` (the English frontmatter `verify` command, copied verbatim, not translated). Sections:

- `## 完成条件`: the acceptance criteria, translated. 1-3 lines.
- `## 現状`: the first line of `## Handoff`, translated. Empty `## Handoff`: `未着手`.
- `## 私への質問`: each question waiting for the user, translated. None: `なし`.

## Rules

- Don't edit the English issue. Don't change any `status`. Don't run any `verify` command.
- Don't copy the English body or the `## Handoff` history. Summarize.
- Update an existing jp file in place, same length or shorter.
- Never add Japanese text to `issues/`, `PLAN.md`, or `drafts/`.
- Report one line per file written: `<path>: <status>`. One line per issue skipped: `<path>: skipped`.
