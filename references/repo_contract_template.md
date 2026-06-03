# Repo Contract Template: Patch To Powerup

Use this template when a repo needs to prevent product-quality fixes from becoming patch stacks.

The contract belongs in the repo's active truth surface, usually:

```text
contracts/system/current.yaml
```

or the equivalent current system contract for that project.

## YAML Section

```yaml
system_capability_iteration:
  version: "1.0"
  principle: "Human product judgement must be converted into producer-level system capability before downstream guardrails are treated as the fix."
  official_entrypoint_required: true
  first_draft_test_required: true
  consumption_map_required: true
  judgement_standard_required: true
  problem_classes:
    - single_bug
    - path_fork
    - producer_quality_gap
    - contract_conflict
    - input_layer_error
    - reader_task_error
    - product_shape_shift
  intervention_order:
    - identify_user_symptom_and_real_target
    - extract_human_judgement_standard
    - classify_problem
    - classify_feedback_placement
    - locate_first_decision_entrypoint
    - locate_first_generation_point
    - change_producer_or_input_compiler
    - remove_or_bound_masking_fallback
    - preserve_guardrail_for_hard_boundary
    - write_runtime_artifact
    - verify_downstream_consumption
    - test_official_entrypoint
    - close_or_demote_old_path
  producer_before_validator: true
  feedback_placement:
    preference:
      default_handling: prompt_aesthetic_or_human_feedback
      hard_fail_by_default: false
    quality:
      default_handling: producer_method_or_input_builder
      hard_fail_by_default: false
    contract:
      default_handling: current_contract_schema_and_tests
    capability:
      default_handling: frontload_into_official_entrypoint
    danger:
      default_handling: hard_fail_allowed
  allowed_guardrails:
    hard_fail:
      - wrong_project_or_source
      - schema_or_interface_poison
      - irreversible_external_delivery
      - data_loss_or_state_corruption
      - security_privacy_legal_compliance_risk
      - zero_evidence_presented_as_full_evidence
    repair_required:
      - locally_repairable_output_defect
    warn_and_continue:
      - readability_or_taste_risk
      - preference_alignment_risk
      - non_poisoning_structure_risk
    ledger_only:
      - learning_or_monitoring_observation
  forbidden_completion_claims:
    - "validator_only_fix"
    - "repair_only_fix"
    - "fallback_only_fix"
    - "ui_or_report_polish_only_fix"
    - "sidecar_only_fix"
    - "meta_only_fix"
  runtime_manifest_fields:
    - run_id
    - official_entrypoint
    - contract_id
    - contract_hash
    - first_decision_entrypoint
    - first_generation_point
    - producer_artifact
    - downstream_consumer
    - guardrail_policy_version
    - masking_fallback_policy
    - git_commit
    - run_mode
  proof_required:
    - contract_integrity_check
    - official_entrypoint_regression
    - old_path_closure_or_demote_check
```

## Contract Meaning

- `producer_before_validator` means the first draft or first decision must change before downstream checks can be called a fix.
- `judgement_standard_required` means the system captures what the human taught as "good" before translating it into code.
- `consumption_map_required` means every meaningful capability change must name source, official entrypoint, first forced act, runtime artifact, downstream consumer, guardrail, and proof.
- `feedback_placement` prevents preference and quality issues from becoming hard blockers by default.
- `forbidden_completion_claims` prevents fake closure from validation, repair, fallback, UI hiding, or metadata alone.
- `masking_fallback_policy` records whether fallback was removed or explicitly bounded so it cannot recreate missing producer meaning.
- `proof_required` keeps the repo from saying a debug path succeeded when the production path did not run.
