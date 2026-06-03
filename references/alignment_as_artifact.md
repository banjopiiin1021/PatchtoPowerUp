# Alignment As Artifact

Use this when a conversation resolves an important judgement.

The principle:

> If an alignment matters to future behavior, it must become an artifact.

Chat memory is useful for recall.
It is not enough for runtime.

## Minimum Record

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

## Placement Rules

- Stable runtime invariant -> active `current` contract.
- Business ontology boundary -> current knowledge source plus prompt/input consumer.
- Product shape decision -> node contract and UI/producer tests.
- New but unproven method -> proposed change or dated alignment note with promotion criteria.
- One-off preference -> feedback memory or local note, not hard contract.

## Example

```yaml
alignment_record:
  aligned_at: "2026-06-03"
  alignment: "Voice stream ads are execution touchpoints; scenario marketing is the strategy method and solution package."
  trigger_context: "Strategy recommended voice stream ads directly as the main strategy."
  correct_judgement: "Strategy must first define the scenario strategy: moment, audience, need, and touchpoint combination. Voice stream can only be selected as one execution touchpoint inside that strategy."
  enters: "current_contract"
  owner_contract_or_doc: "contracts/workflows/brief_to_creative_collab/current.yaml"
  runtime_consumer:
    - "strategy_development prompt"
    - "resource_cost_profile"
    - "Blueprint handoff"
  proof_or_test:
    - "tests/test_ximalaya_resource_cost_profile.py::test_scenario_marketing_is_not_scene_audio_stream"
```
