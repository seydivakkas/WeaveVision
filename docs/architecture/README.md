# Architecture Index

The detailed WeaveVision architecture is maintained in [`../ARCHITECTURE.md`](../ARCHITECTURE.md).

## High-level flow

```text
Input / Capture Validation
        ↓
Normal-Only Anomaly Model
        ↓
Image + Pixel Anomaly Evidence
        ↓
Threshold / Calibration Layer
        ↓
PASS · REVIEW · FAIL · ABSTAIN
        ↓
Persistence / Reports / Feedback
        ↓
Drift Monitoring → Triage → Canary / Rollback
```

## Main code boundaries

- `../../src/weavevision/domain/` — contracts and typed errors
- `../../src/weavevision/data/` — adapters, manifests, leakage controls and tiling
- `../../src/weavevision/models/` — model adapters, registry and artifact integrity
- `../../src/weavevision/inference/` — quality gate, prediction and localization
- `../../src/weavevision/evaluation/` — calibration, metrics, drift and robustness
- `../../src/weavevision/services/` — application/lifecycle orchestration
- `../../src/weavevision/ui/` — Streamlit product surface

For claim evidence, see [`../evidence/README.md`](../evidence/README.md).
