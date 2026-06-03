---
name: patch-to-powerup
description: Turn patch-stacking feedback into producer-level system upgrades. Use when the user says a fix is becoming patch stacking, when product-shape feedback should upgrade system capability, or when requirements, taste, strategy, or output quality need to be iterated into a real capability instead of another validator, repair, fallback, or surface tweak.
---

# Patch To Powerup

This is the system capability iteration skill with a less boring name.

Use this skill when the user is not merely asking for one visible mistake to be fixed.
They are using a bad example, product feeling, reader reaction, or requirement shift to expose that the system's judgement path is wrong.

The goal is to convert human product judgement into a frontloaded, reusable, verifiable system capability.

## Core Thesis

Human-machine collaboration must not become:

> Human points to one error; AI fills one hole.

That creates a patch system.

The correct loop is:

> Human names the symptom and real product target; AI traces it to the capability entrypoint; both upgrade the system's judgement method.

The fix is not complete until the official producer path can make a better first draft or first decision.

## Trigger Phrases

Use this skill immediately when the user says or implies:

- "又在打补丁"
- "不是系统能力"
- "不是产品形态"
- "读不懂"
- "像内部复盘"
- "不是营销洞察"
- "后验拦截"
- "不要只删这句话"
- "需求变了"
- "拟合产品形态"
- "以后所有项目都不要再这样"
- "人机应该怎么配合"
- "AI 不要哪里炸修哪里"
- "先定位第一生成点"
- "这不是策略，是解释"
- "报告不像人看的"
- "schema 合法不等于产品可用"
- "这个节点服务谁"
- "客户看得懂吗"
- "这不是给客户看的"
- "我没有说清它是谁用的"

If the issue also involves installed capability not entering the main path, use `capability-frontloading`.
If the issue also involves duplicate paths or one evolving contract, use `single-contract-evolution`.

## Collaboration Contract

### Human's highest-value input

Prefer product judgement over micro-edits:

- what good means in this product
- what feels wrong
- why the output does not resemble the intended product
- what a real reader or client would not understand
- where the work sounds fake, internal, generic, or over-constrained
- what the product should do instead

Do not reduce the user's feedback to a literal string replacement if it reveals a deeper capability issue.

Human feedback is most valuable when it states a judgement standard, not only a bad sentence:

- "A good Big Idea makes the target audience feel 'this is about me'."
- "This is a campaign slogan, not a tagline."
- "Schema-valid is not the same as product-usable."
- "Do not use fallback to hide that the producer lacks the capability."
- "The user should only need to choose a direction, write one revision note, and continue or ask for changes."

### AI's responsibility

Before editing, classify the problem:

- `single_bug`: one local code or data defect
- `path_fork`: multiple active routes or stale entrypoints
- `producer_quality_gap`: first draft/decision is framed wrong
- `contract_conflict`: current truth, prompt, validator, or workflow disagree
- `input_layer_error`: data is compiled into the wrong layer or entity
- `reader_task_error`: writer has the wrong audience, job, or output task
- `product_shape_shift`: the desired product form changed and needs new contracts

If the answer is not clear, inspect the official path before guessing.

## Role Hypothesis Before Implementation

Do not wait for the human to fully define the product role from scratch.
When the node's user, job, or visible surface is unclear, propose a small, refutable node-role contract before editing.

Do not ask a huge question such as:

> What do you want this node to do?

Instead, infer from context and ask for correction on a narrow draft:

```text
My current node-role hypothesis:

user:
  internal planner / sales / designer / operator / downstream model / final client
job:
  what this user does with the output
default visible:
  what the human should read, edit, choose, or approve
backstage only:
  paths, prompts, IDs, raw fields, asset plans, debug traces, or machine metadata
forbidden:
  what this node should no longer decide, expose, or regenerate
downstream reads:
  which later node consumes this output, and whether it reads edited visible content or raw packet data
```

Then ask the user to correct only the wrong slots.
This turns vague dissatisfaction into a compact product contract.

Example:

```text
I will treat Blueprint as an editable customer-proposal director draft for internal planners and sales, not as a final-client backend or a field table.
Visible: page order, page claim, client-facing copy, proof object, visual direction.
Backstage: source paths, search prompts, image prompts, asset plan.
Forbidden: strategy re-selection, reserve options, internal IDs, risk boundaries, raw material paths.
Downstream: Deck reads the human-edited visible blueprint first.
```

If the user confirms, implement against this contract.
If they correct one or two slots, update the contract before code.

## Translate Complaints Into Product Shape

The user may describe product shape through dissatisfaction instead of product language.
Translate signals like these into a node-role or boundary hypothesis:

- "Can a client understand this?" -> visible layer should be client-facing proposal copy, not backend fields.
- "This is not PPT content" -> the node is producing internal structure instead of delivery-ready page text.
- "Strategy already selected this" -> this node should translate and paginate, not reopen strategy choices.
- "I want every word that will appear in the deck" -> visible output must include final editable page text, while prompts and asset paths stay backstage.
- "I need to edit text, delete paragraphs, and add pages" -> the UI is an editor, not a report viewer.

This is still implementation guidance only after it is converted into a concrete node-role contract.

## Find The First Generation Point

Do not translate the user's stated problem directly into the nearest surface patch.
First ask:

> Where did the bad result first become possible?

Use this diagnostic shape:

- It may not be a frontend display bug; the packet may already be wrong.
- It may not be an ugly writer problem; one model may have been asked to write, extract structure, map resources, and judge strategy at once.
- It may not be bad naming; the system may have failed to distinguish capability, product, play, project, touchpoint, and case.
- It may not be a report polish issue; the writer may have never received a reader-facing argument plan.

The target is the first generation point:

- first model instruction
- first required output field
- first input compiler decision
- first packet or handoff shape
- first ontology or classification boundary
- first UI control data model

If the first generation point does not change, the fix is probably still a patch.

## First-Draft Test

Every capability iteration must ask:

> Would this change alter the system's first draft or first meaningful decision?

If no, the change is probably a guardrail, repair, display tweak, or outlet blocker.
Those may remain useful, but they are not the capability upgrade.

## Required Consumption Map

Before implementation, produce this map:

```text
problem symptom
-> judgement standard
-> root-cause layer
-> capability source
-> official entrypoint
-> first forced act / first generation point
-> producer to change
-> runtime artifact that proves consumption
-> downstream consumer
-> guardrail that remains
-> official-path proof
```

If the map can only name a validator, repair, fallback, report polish, UI display, audit meta, or sidecar runner, the plan is not ready.

## Case Or Method

Every correction must be classified before implementation:

- `case_fix`: the failure is a one-off contamination or artifact-specific defect; repair the current artifact and record the boundary.
- `method_upgrade`: the failure reveals a reusable business, product, ontology, producer, or workflow rule; move it into the official path.

Examples:

- "Do not use an irrelevant audience for this one project" can be a case fix.
- "Strategy audiences must flow from insight judgement -> strategy working audience -> platform-recognizable proxy audience" is a method upgrade.
- "This card looks messy" can be a case fix.
- "The system cannot distinguish ability, product, play, project, touchpoint, and case" is a method upgrade.

When in doubt, prefer a narrow method upgrade at the first generation point over adding a broad downstream blocker.

## Feedback Placement Taxonomy

Do not turn every user correction into a hard rule.
Place it first:

- `preference`: taste, tone, wording, density, or style. Put it into prompt aesthetics, review guidance, or human feedback memory. Do not hard fail by default.
- `quality`: the output is product-poor but not structurally poisonous. Move the method into the producer, input builder, skill cards, candidate generation, or scoring.
- `contract`: a stable invariant such as required routes, schema fields, handoff structure, or source-of-truth boundary. Put it into current contracts and tests.
- `capability`: a skill, knowledge layer, method, or ontology exists or should exist but is not consumed before the first decision. Frontload it into the official entrypoint.
- `danger`: schema poison, cross-project contamination, machine fields leaking, security/privacy/legal/compliance risk, irreversible delivery, or fake evidence. This can hard fail.

The common failure is making `quality` behave like `danger`.
That creates a heavy wall of validators while the producer still starts wrong.

## Intervention Rules

### Producer before validator

Capability must enter the producer path first:

- intake classifier
- routing or lens selector
- research planner
- input compiler
- candidate generator
- scorer or judge
- argument planner
- writer brief
- formal handoff builder

Validators only guard hard boundaries or prove the improved producer did not regress.

### Change what the system does first

Do not start with:

- "ban this phrase"
- "add a hard stop"
- "repair after generation"
- "polish the report"
- "hide it in UI"
- "write a meta note"

Start by changing the earliest artifact that frames judgement.
Common patterns:

- `raw assets -> judgement plan -> writer writes`
- `reader_profile -> argument_plan -> final_output`
- `brand_pain_mining -> communication_insight_probe -> channel_transfer`
- `source truth -> route/lens selection -> evidence requirements -> candidate scoring`

### Repartition capability, not just rules

Many durable fixes are responsibility splits, not extra instructions.

Before adding another prompt rule, ask whether one producer is doing too many jobs.
Common upgrades:

- report author writes the human-readable strategy; packet compiler extracts controls, DataClaw requests, resource mapping, and handoff structure
- writer writes for the real reader; argument planner decides what must be argued
- local renderer assembles structure; it does not invent strategy copy
- validator guards business and schema boundaries; it does not act as the hidden generator
- UI renders decision controls from a typed packet; it does not filter random generated language into product shape

If a single LLM is being asked to write the report, extract a packet, map resources, create controls, and police business rules in one pass, look for a capability repartition before tightening validators.

### Remove masking fallback

Fallback is not neutral when it hides that the producer failed.

Audit all places that can silently recreate missing capability:

- writer fallback
- runner repair
- normalizer fill-ins
- local default fields
- frontend confirmation or handoff builders
- cached artifact reuse
- UI display filters that make broken packets look intentional

If fallback remains, it must be explicit, bounded, and visible in runtime metadata.
It must not create slogans, strategy, arguments, routes, controls, or business meaning that the official producer failed to produce.

### Simplify the user's decision object

Product-shape iteration should observe how the human decides.
Do not expose every system field just because the backend has it.

Ask:

- What is the smallest object the user needs to choose?
- What single note or correction should they be able to add?
- What previous version or comparison is needed to decide?
- Which machine fields should stay hidden or summarized?

The UI can be backed by a rich packet, but the decision surface should expose only the user's real decision object.

### Converge requirement changes into contracts

Requirement changes are not necessarily resets.
Treat repeated corrections as a contract convergence process:

- node responsibility: what this node now does
- non-responsibility: what this node must stop doing
- upstream boundary: what is already decided before this node
- downstream boundary: what this node hands off and to whom
- visible/backstage boundary: what the human sees versus what machines keep
- main-chain capability: what must enter the official path

Do not treat comments like "too detailed", "no alternatives", "can the client read this", or "use my previous deck as reference" as isolated copy edits when they define the product form.

### Human-in-the-loop belongs in artifacts

Do not write AI pause instructions such as "wait for approval" as the system fix.
Produce reviewable artifacts:

- classification result
- consumption map
- proposed contract patch
- changed producer entrypoint
- node-role hypothesis or product contract when product shape is unclear
- runtime manifest or trace
- regression proof
- case-or-method classification

The human decides from those artifacts.

## Three-Layer Deliverable

When the user asks to make this pain disappear across projects, produce all three layers when applicable:

1. **Skill layer**: update or create a global skill that teaches Codex the collaboration method.
2. **Contract layer**: add a repo contract template that enforces producer-before-validator, single entrypoint, severity levels, manifest truth, and old-path closure.
3. **Pattern layer**: add reusable implementation patterns for compiler-writer separation, reader/profile planning, severity policy, report meta, and official-entrypoint tests.

One layer alone is incomplete:

- Skill without contract becomes good intentions.
- Contract without pattern becomes slogans.
- Pattern without skill gets applied only after the user complains.

## Severity Model

Use one shared severity model:

- `hard_fail`: schema poison, wrong source/project, irreversible delivery, public/money/security/privacy/legal/compliance risk, or zero evidence pretending to be full evidence.
- `repair_required`: locally fixable output defect; repair and continue.
- `warn_and_continue`: quality, taste, readability, preference, or non-poisoning structure risk.
- `ledger_only`: record for learning, monitoring, or future tuning.

Repeated quality failures should usually upgrade producer capability, not become wider hard stops.

## Completion Gate

Do not claim completion unless you can name:

- the user's symptom and real target
- the judgement standard learned from the human
- the node-role hypothesis or product contract, if product shape was unclear
- the problem class
- the feedback placement: preference, quality, contract, capability, or danger
- whether the correction is a case fix or method upgrade
- the first decision entrypoint changed
- the first generation point changed
- the producer artifact now consumed by the official path
- the downstream consumer that receives the capability
- the guardrail that remains and why it is not the main brain
- any masking fallback removed or explicitly bounded
- the official-path proof
- the write-back surface that prevents future drift

## Output Standard

Keep final reports short, but include:

```text
symptom -> judgement standard -> placement -> first generation point -> producer artifact -> downstream consumer -> proof
```

If no code or contract was changed, explicitly say the result is only a planning or diagnosis pass.
