# Patch to PowerUp

> Stop teaching AI to patch the leak. Teach it to find why the pipe keeps leaking.

`patch-to-powerup` is a Codex skill for the moment when "just fix this one thing" has clearly stopped working.

It is for teams and solo builders who keep seeing the same failure pattern:

- the user points at a bad output
- the AI adds a validator, repair step, fallback, blacklist, or UI filter
- the current artifact looks less embarrassing
- the next project fails in the same shape with different words

That is not iteration. That is patch stacking.

This skill forces Codex to translate product feedback into a producer-level system upgrade: find the first place the bad result became possible, change the official path there, and keep validators as guardrails instead of hidden brains.

## The Core Idea

Human-machine collaboration should not be:

```text
human points to one error -> AI fills one hole
```

It should be:

```text
human names the symptom and product standard
-> AI traces the first wrong decision
-> the system's producer capability is upgraded
-> the official path proves the new capability is consumed
```

The question is not only:

> How do we stop this bad output?

The better question is:

> Why did the system reliably generate this kind of bad output?

## When To Use It

Use this skill when you hear yourself saying things like:

- "This is becoming patch stacking."
- "It passed the schema but it is not usable."
- "The report reads like internal notes, not a client-facing product."
- "Do not fix this in the UI. Why is the packet wrong?"
- "The skill exists, but why is the main path not using it?"
- "The fallback is hiding that the producer cannot do the job."
- "This is not a style issue; the node is serving the wrong user."
- "The AI keeps fixing the visible symptom, not the system capability."

It is especially useful for LLM workflow systems: report generators, strategy pipelines, content tools, proposal builders, research agents, deck generators, and any product where the quality problem starts before the final writer.

## What The Skill Makes Codex Do

`patch-to-powerup` changes the repair posture.

Before editing, Codex must identify:

```text
symptom
-> judgement standard
-> feedback placement
-> first generation point
-> producer artifact
-> downstream consumer
-> guardrail
-> proof
```

That extra discipline matters because most bad fixes happen when the AI jumps straight from symptom to outlet:

- bad slogan -> blacklist words
- unreadable report -> polish the writer
- missing field -> fill a default
- confusing UI -> hide a few fields
- failed generation -> fallback to local template

Those can be useful emergency moves. They are not system capability.

## The First Generation Point

The skill asks:

> Where did the bad result first become possible?

Examples:

- It may not be a frontend display bug; the packet may already be wrong.
- It may not be an ugly writer problem; one model may be doing writing, extraction, strategy, mapping, and validation at once.
- It may not be bad naming; the system may not distinguish product, capability, play, case, touchpoint, and resource.
- It may not be a report polish issue; the writer may never have received a reader-facing argument plan.

If the first generation point does not change, the fix is probably still a patch.

## Feedback Is Not One Thing

The skill separates feedback into five placements:

| Placement | Meaning | Default handling |
| --- | --- | --- |
| `preference` | taste, tone, wording, density | prompt aesthetics, review guidance, human feedback memory |
| `quality` | product-poor but not structurally poisonous | producer method, input builder, scoring, candidate generation |
| `contract` | stable invariant | current contract, schema, tests |
| `capability` | skill/knowledge/method exists or should exist before the first decision | frontload into official entrypoint |
| `danger` | schema poison, cross-project contamination, leaked machine fields, legal/privacy/security risk, fake evidence | hard fail allowed |

The common mistake is making `quality` behave like `danger`.
That creates a fortress of validators around a producer that still starts wrong.

## Iteration Is Usually Not Rollback

Multi-round product feedback is often cumulative.

The user may not be saying:

> Undo what we just did.

They may be saying:

> Keep that, but add the missing boundary.

or:

> The direction is right, but the mechanism is still at the wrong layer.

So the skill adds an iteration delta check before implementation:

```text
new feedback:
current contract it touches:
relationship: union | evolution | constrain | replace | reversal | exception | experiment | deprecate
keep:
add:
change:
remove/deprecate:
official proof needed:
```

Default bias:

- no explicit "undo" -> start from `union`, `evolution`, or `constrain`
- "too much / too detailed / do not expose this" -> usually `constrain`, not reversal
- "better abstraction" -> usually `evolution`
- mutually exclusive old/new rules -> `replace`
- true rollback -> `reversal`, and it should close the old path intentionally

This prevents the AI from deleting useful capability just because the next feedback adds another boundary.

## Product Shape: Ask A Smaller Question

When the user has not fully defined who a node serves, the AI should not ask:

> What do you want this node to do?

That question is too large.

Instead, Codex should propose a small, refutable role contract:

```yaml
node_role_contract:
  user: "internal planner | sales | designer | operator | downstream model | final client"
  job: "what this user does with the output"
  default_visible:
    - "what the human should read, edit, choose, or approve"
  backstage_only:
    - "paths, prompts, IDs, asset plans, debug traces, raw fields"
  forbidden:
    - "what this node should not decide, expose, or regenerate"
  downstream_reads:
    - consumer: "next node"
      reads: "edited_visible_output | compiled_packet | runtime_artifact"
```

This turns vague dissatisfaction into a compact product contract.
The human can correct one slot instead of writing a product spec from scratch.

## Pattern Library

The bundled pattern library includes:

- `Compiler -> Writer`: separate judgement planning from final prose.
- `Reader Profile -> Argument Plan -> Final Output`: make the writer serve a real reader.
- `Domain Diagnosis -> Transfer`: diagnose the brand/user problem before channel transfer.
- `Severity Policy Helper`: one shared severity model instead of validator chaos.
- `Old Path Closure Test`: prove the old route is no longer authoritative.
- `Runtime Meta as Truth, Not Brain`: metadata records capability; it does not replace it.
- `Author -> Packet Compiler -> Renderer`: split writing, packet extraction, and rendering.
- `Ontology Before Controls`: stop UI filters from compensating for missing business types.
- `Rich Packet -> Minimal Decision Surface`: expose the smallest human decision object.
- `Fallback Shadow Audit`: find fallback that recreates missing meaning downstream.
- `Node Role Contract`: clarify who a node serves before implementation.
- `Iteration Delta Ledger`: keep, add, change, and deprecate explicitly across feedback rounds.

See [references/producer_pattern_library.md](references/producer_pattern_library.md).

## Repository Layout

```text
PatchtoPowerUp/
├── SKILL.md
├── INSTALL.md
├── README.md
├── examples/
│   └── capability_consumption_map.md
└── references/
    ├── producer_pattern_library.md
    ├── iteration_delta_checklist.md
    └── repo_contract_template.md
```

## Installation

Clone the repository and copy it into your Codex skills directory:

```bash
git clone https://github.com/banjopiiin1021/PatchtoPowerUp.git
mkdir -p ~/.codex/skills/patch-to-powerup
cp -R PatchtoPowerUp/* ~/.codex/skills/patch-to-powerup/
```

Then start a new Codex session. The skill is triggered by its metadata and by phrases like "patch stacking", "not system capability", "fallback is hiding the problem", or "find the first generation point".

## How It Works With Other Skills

This skill pairs naturally with:

- `capability-frontloading`: when a capability exists but the official path does not consume it.
- `single-contract-evolution`: when fixes have multiplied into duplicate paths, fallback sprawl, and validator stacks.
- `good-start-skill`: when starting a new project and you want this anti-patch logic installed into the project contract from day one.

## A Tiny Example

Bad repair:

```text
User: This Blueprint does not read like client PPT content.
AI: I will polish the reporter and hide the internal fields.
```

Power-up repair:

```text
User symptom:
  This Blueprint does not read like client PPT content.

Judgement standard:
  Blueprint should be an editable customer-proposal director draft for internal planners and sales.

First generation point:
  The model starts by paginating fields instead of diagnosing client persuasion.

Producer change:
  First required output becomes client_persuasion_diagnosis.

Runtime artifact:
  blueprint_packet.json contains source-bound persuasion cards and page jobs.

Downstream consumer:
  Deck generation reads the human-edited visible blueprint, not raw strategy fields.

Guardrail:
  Reporter refuses legacy packets instead of inventing readable pages.

Proof:
  Official entrypoint regression plus old-path closure test.
```

## Philosophy

The user is often better at judging "this is not the product" than at naming the exact system layer that failed.

The AI is often better at tracing the layer, changing the producer, updating contracts, and proving the official path.

Good collaboration is not:

```text
human writes requirements -> AI executes
```

It is:

```text
human calibrates product truth -> AI turns that truth into durable system capability
```

That is the power-up.
