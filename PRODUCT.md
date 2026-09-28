# DataBridge — Product brief

## Problem and evidence

In SCM-focused ERP implementations, data migration and cutover teams commonly receive vendor and legacy master data as differently structured CSV and spreadsheet files. Analysts normalize headers, copy data into a target template, and check required fields through one-off spreadsheet formulas. The workaround can consume repeated analyst time, is difficult to reproduce consistently across suppliers, and leaves a weak audit trail for unresolved rows.

This is a practitioner problem hypothesis grounded in common ERP data-readiness workflows. This repository has no documented participant interview, usage telemetry, or pilot result yet. No time-savings or defect-reduction claim is made.

## Product choice and prioritization

Prioritized one narrow, recurring task: map source columns to a target schema, apply explicit checks, and make rejected rows visible in an export. CSV/XLS/XLSX support and deterministic validations come first because teams need a useful workflow even when they cannot send data to an AI service. AI mapping is optional and limited to a few sample rows per file.

## Success criteria

Run a timed comparison with one implementation analyst on a representative, approved sample dataset. Record a manual baseline and DataBridge result for:

- elapsed time from raw file to reviewed, target-shaped output;
- mapping corrections required before approval;
- invalid rows detected and missed against a manually verified reference;
- participant confidence in explaining each flagged row and its source.

Proposed pilot acceptance: complete the task with lower elapsed time than the participant’s normal workflow, detect every seeded validation issue, and require no more mapping corrections than the current manual process. Report the raw counts, dataset characteristics, and limitations; do not generalize one pilot into a broad ROI claim.

## Deferred

- direct ERP connectors, write-back, migration orchestration, and audit history;
- shared schemas, team accounts, role-based approvals, and managed provider keys;
- large-file streaming, multi-sheet policy, and value transformation/catalog matching;
- claims of compliance, production readiness, or automatic acceptance of source data.

## Learning to capture

After the pilot, document where the analyst spent time, which rules were missing, how often AI mapping was corrected, what data could not be sent to a provider, and whether the error export fits the team’s cutover controls. Update this brief with the participant role, date, sample size, observed results, and decisions. Keep confidential source files out of Git.
