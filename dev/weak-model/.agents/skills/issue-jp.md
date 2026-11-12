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

One file per issue: `issues/jp/<number>-<slug>.md`, same name as the English file. Frontmatter: `status` (the current value, unchanged) and `検証` (the English frontmatter `verify` command, copied verbatim, not translated). Then the title line: `# ` plus the English issue's first `# ` heading, translated; the English issue has no heading: a short Japanese title translated from `<number>-<slug>`. Never invent one. Then sections, in this order, each filled as shown when empty:

- `## 背景`: the issue's `## Background`, translated. No such section: summarize the body or title in 1-2 lines. No information at all: `記載なし`. Never invent one.
- `## 問題点`: the issue's `## Problem`, translated. No such section but the body describes what is wrong: summarize it in 1-2 lines. No information at all: `記載なし`. Never invent one.
- `## 終了条件`: the acceptance criteria, translated, one `- ` bullet per criterion. Keep every criterion; compress the wording, never drop an item.
- `## 進行中`: from the newest (top) `## Handoff` entry: a `- ` bullet for what was changed, a `- ` bullet for the exact next step. Empty `## Handoff`: `未着手`.
- `## ブロック`: blockers and dead ends named in any `## Handoff` entry that still hold, one `- ` bullet each, each question waiting for the user included. None: `なし`.
- `## ユーザーのコメント`: instructions or decisions from the user recorded in `## Handoff`, one `- ` bullet each, newest first. Do not mix in agent notes. None: `なし`.

## Rules

- Don't edit the English issue. Don't change any `status`. Don't run any `verify` command.
- Don't copy the English body or the `## Handoff` history. Extract and summarize; one section may cite at most one short quote.
- `背景` and `問題点` stay prose, 1-2 lines. The four bullet sections (`終了条件`, `進行中`, `ブロック`, `ユーザーのコメント`) use `- ` items, at most 3 each, except `終了条件` which gets one bullet per criterion. Update an existing jp file in place.
- Never add Japanese text to `issues/`, `PLAN.md`, or `drafts/`.
- Report one line per file written: `<path>: <status>`. One line per issue skipped: `<path>: skipped`.
