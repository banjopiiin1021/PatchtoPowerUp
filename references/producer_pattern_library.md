# Producer Pattern Library

These implementation patterns turn product judgement into reusable system capability.

They are intentionally small.
Use them as starting contracts, not as heavy architecture.

## Pattern 1: Compiler -> Writer

Use when a report, proposal, deck, or narrative output is unreadable because the writer is also doing strategy judgement.

```text
source materials
-> input compiler
-> judgement / argument plan
-> writer brief
-> final writer
-> validator as guardrail
```

Rules:

- The compiler decides what should be argued.
- The writer decides how to say it to the intended reader.
- The validator guards schema, evidence, and hard boundaries.
- Report polish cannot invent the missing argument plan.

Minimum artifacts:

- `compiled_input.json`
- `argument_plan.json`
- `writer_brief.json`
- `final_output.md`
- `runtime_manifest.json`

## Pattern 2: Reader Profile -> Argument Plan -> Final Output

Use when output sounds like internal notes instead of a product a customer can read.

```text
target_reader
-> reader_job_to_be_done
-> reader_confusion_risks
-> argument_plan
-> final_output
```

The writer must consume the reader profile before producing the first section.

## Pattern 3: Domain Diagnosis -> Transfer

Use when the system jumps directly from platform assets to a recommendation without understanding the brand or user's real problem.

```text
brand_pain_mining
-> communication_insight_probe
-> counter_evidence_check
-> platform_or_channel_transfer
-> selected_solution
```

Do not let channel transfer run before pain mining.

## Pattern 4: Severity Policy Helper

Use one helper or shared policy for severity.

```text
hard_fail: corrupts state, source, schema, irreversible delivery, or high-risk domain
repair_required: local output defect can be repaired
warn_and_continue: quality or preference risk
ledger_only: learning or monitoring note
```

Avoid separate validators inventing different severity meanings.

## Pattern 5: Old Path Closure Test

Whenever a producer path is replaced or upgraded, add a regression that proves the old path is not still authoritative.

Test shape:

```text
given old artifact or stale checkpoint exists
when official entrypoint runs
then new producer artifact is generated or consumed
and old path is ignored, demoted, or read-only
```

## Pattern 6: Runtime Meta as Truth, Not Brain

Meta should record:

- what was consumed
- which entrypoint ran
- which producer artifact framed the first decision
- which guardrail policy applied
- which fallback or repair happened

Meta must not be the only place where the capability exists.

## Pattern 7: Author -> Packet Compiler -> Renderer

Use when one model is overloaded with writing, extracting, mapping, judging, and formatting.

```text
author
-> packet_compiler
-> renderer
-> validator as boundary guard
```

Rules:

- The author writes the human-facing argument or strategy.
- The packet compiler turns the author output and domain ontology into controls, mappings, requests, and handoffs.
- The renderer assembles the approved structure and must not invent missing strategy.
- The validator guards schema, business boundaries, and source truth.

This pattern is useful when a system produces confusing controls, messy resource mapping, or reports that explain how to do strategy instead of doing strategy.

Minimum artifacts:

- `author_report.md`
- `core_judgements.json`
- `compiled_packet.json`
- `rendered_output.md`
- `validation_report.json`
- `runtime_manifest.json`

## Pattern 8: Ontology Before Controls

Use when product controls are messy because the system has not separated business entities.

```text
source terms
-> ontology classification
-> typed packet fields
-> UI controls
```

Do not let UI filtering compensate for missing ontology.
Define boundaries such as:

- capability
- product
- play
- project
- touchpoint
- case
- resource slot
- resource package

If these are mixed upstream, the UI will keep needing local patches.

## Pattern 9: Rich Packet -> Minimal Decision Surface

Use when product screens expose too many backend fields, buttons, routes, or machine options.

```text
rich typed packet
-> user decision object
-> one revision note
-> confirm / request changes
-> version comparison when needed
```

Rules:

- The backend may preserve full structure for downstream execution.
- The UI should expose only the smallest object the human must decide on.
- Machine fields, route internals, schema scaffolding, and repair metadata stay hidden unless they affect the user's decision.
- If the UI needs local filtering to look usable, the packet is probably not typed correctly upstream.

Example decision objects:

- choose one slogan and direction
- choose primary strategy vs reserve option
- approve a report argument plan
- select a resource package with clear business meaning

## Pattern 10: Fallback Shadow Audit

Use when a producer-level repair appears complete but old behavior keeps returning through another layer.

Audit:

- writer fallback
- runner repair
- normalizer defaults
- local fill-ins
- frontend handoff builders
- cached stale artifacts
- display filters

Test shape:

```text
given producer omits a required capability artifact
when official entrypoint and UI handoff run
then no downstream layer silently recreates the missing meaning
and the runtime reports the real producer failure or bounded degradation
```

Fallback may preserve delivery format.
Fallback must not create the missing strategy, slogan, route, resource mapping, or product judgement.

## Pattern 11: Node Role Contract

Use when the user is reacting to product shape but has not explicitly defined who the node serves.

Draft this before implementation:

```yaml
node_role_contract:
  node_id: ""
  user: "internal planner | sales | designer | operator | downstream model | final client"
  job: ""
  default_visible:
    - ""
  backstage_only:
    - ""
  forbidden:
    - ""
  upstream_boundary:
    - ""
  downstream_reads:
    - consumer: ""
      reads: "edited_visible_output | compiled_packet | runtime_artifact"
```

Rules:

- Make the hypothesis specific enough that the user can reject one slot.
- Do not ask the user to write the whole product definition from scratch.
- After confirmation, bind producer prompt, packet schema, UI surface, and tests to this contract.
- If the UI and producer disagree about this contract, the producer contract wins and the UI must be repaired to match it.

## Pattern 12: Iteration Delta Ledger

Use when feedback arrives across several rounds and the team risks treating every new correction as rollback.

```yaml
iteration_delta:
  new_feedback: ""
  current_contract_touched: ""
  relationship: "union | evolution | constrain | replace | reversal | exception | experiment | deprecate"
  keep:
    - ""
  add:
    - ""
  change:
    - ""
  remove_or_deprecate:
    - ""
  official_proof_needed:
    - ""
```

Rules:

- Default to `union`, `evolution`, or `constrain` unless the user explicitly asks to undo.
- Never delete a working capability just because the next feedback adds a new boundary.
- If a rule is replaced, name the old rule and add a no-read/no-use check for the old path.
- If something is only an experiment, label it non-authoritative and define promotion criteria.

## Pattern 13: Alignment Record

Use when a conversation resolves an important judgement that future runs must not rediscover from scratch.

```yaml
alignment_record:
  aligned_at: ""
  alignment: ""
  trigger_context: ""
  correct_judgement: ""
  enters: "current_contract | proposed_change | knowledge_current | prompt_compiler | schema | pattern_library | memory_note"
  owner_contract_or_doc: ""
  runtime_consumer:
    - ""
  proof_or_test:
    - ""
```

Rules:

- If it affects runtime, memory alone is not enough.
- If it is stable, enter `current` or the active knowledge source.
- If it is not stable, record as proposed with promotion criteria.
- Name the runtime consumer so the record is not just documentation.
- Add at least one proof path when the alignment prevents a known regression.
