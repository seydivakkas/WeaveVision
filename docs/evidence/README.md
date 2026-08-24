# Evidence Index

This index maps WeaveVision portfolio claims to repository-level engineering evidence.

## Quality and CI

- `../../.github/workflows/ci.yml` — Ruff, formatting, mypy, pytest/coverage and package build contract.
- `../../.github/workflows/security.yml` — repository security checks.

## Dataset and claim governance

- `../DATASET_AND_LICENSE_REGISTER.md` — dataset/license register.
- `../CLAIM_CONTRACT.md` — rules for what the project may and may not claim.
- `../EXPERIMENT_PROTOCOL.md` — experiment protocol.
- `../MODEL_SELECTION_VERDICT.md` — model-selection record.
- `../FINAL_VERDICT.md` — current engineering verdict.

## Reliability lifecycle

- `../DRIFT_LIFECYCLE_IMPLEMENTATION.md` — drift monitoring/lifecycle implementation.
- `../COMPANY_PILOT_RUNBOOK.md` — pilot runbook.
- `../EXECUTION_LOG.md` — execution evidence and engineering history.

## Interpretation rules

1. CI status is live; historical test counts are snapshots.
2. Model thresholds are valid only for their documented calibration contract.
3. `REVIEW` and `ABSTAIN` are reliability outcomes, not software failures.
4. Drift signals require triage; they are not root-cause proofs.
5. Company/pilot evidence must remain separated from confidential raw data and credentials.

See `../../KNOWN_LIMITATIONS.md` for explicit scope boundaries.
