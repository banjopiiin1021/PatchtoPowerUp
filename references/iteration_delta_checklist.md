# Iteration Delta Checklist

Use this checklist when human feedback arrives across multiple rounds.

The key assumption:

> New feedback is not automatically a rollback.

Many product-shape conversations evolve by taking the union of several partial truths.
The AI must preserve what remains valid, add what was missing, and explicitly close only what is truly obsolete.

## Relationship Types

| Type | Meaning | Default action |
| --- | --- | --- |
| `union` | New feedback adds a missing dimension while previous rule still holds. | Keep old rule, add new rule, test both. |
| `evolution` | Same product intent, better mechanism or abstraction. | Upgrade producer/contract; migrate old wording. |
| `constrain` | Prior rule was too broad. | Narrow scope, add conditions, keep core. |
| `replace` | New rule supersedes an old rule. | Name old rule, replace it, close old path. |
| `reversal` | User truly wants to undo a prior decision. | Require explicit confirmation or strong evidence; remove old proof paths. |
| `exception` | One-off case does not change general method. | Patch artifact and record boundary. |
| `experiment` | Trial path, not official truth yet. | Label non-authoritative; define promotion criteria. |
| `deprecate` | Old path/rule/fallback should stop influencing runtime. | Close path, test no-read/no-use. |

## Checklist

```text
new feedback:
current contract it touches:
relationship:
why this is not simply rollback:
keep:
add:
change:
remove/deprecate:
open question:
official proof needed:
```

## Decision Heuristics

- If the user says "also", "and", "not only", "还要", or adds a missing use case, start from `union`.
- If the user says "其实应该", "更准确地说", or gives a better abstraction, start from `evolution`.
- If the user says "太多", "太细", "不要展示", or "不是给这个人看的", start from `constrain`.
- If the user says "不要 X，要 Y" and X/Y are mutually exclusive, start from `replace`.
- If the user says "回到之前", "撤掉", or explicitly rejects the prior decision, start from `reversal`.
- If the issue is tied to one artifact, one account, one dataset, or one campaign, consider `exception`.
- If the idea is promising but unproven, use `experiment`.
- If an old fallback or route can still influence runtime, use `deprecate`.

## Completion Rule

Before claiming a multi-round iteration is complete, name:

- what stayed true
- what was added
- what was narrowed
- what was replaced or deprecated
- what is still experimental
- which official-path proof prevents accidental rollback
