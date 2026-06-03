# Example: Capability Consumption Map

```text
problem symptom:
  The report reads like an internal review and not a marketing insight product.

root-cause layer:
  reader_task_error + producer_quality_gap

first decision entrypoint:
  report input compiler decides the argument before the writer sees the task.

producer to change:
  add ReportArgumentPlan generated from customer-facing reader profile and evidence requirements.

runtime artifact:
  runs/{run_id}/report_argument_plan.json is referenced by writer_brief.json and runtime_manifest.json.

guardrail that remains:
  validator checks schema, evidence refs, forbidden machine fields, and zero-evidence hard fail.

official-path proof:
  official runner test asserts writer input includes report_argument_plan_id and stale direct-writer path is not used.
```
