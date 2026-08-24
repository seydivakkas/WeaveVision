# WeaveVision — Project Knowledge Base

This file is the portable, public project context for engineering assistants and contributors.

## Project identity

- **Product:** WeaveVision
- **Repository:** `seydivakkas/WeaveVision`
- **Repository root:** `<repo-root>` — never assume a user-specific absolute filesystem path
- **Python package:** `weavevision`
- **Architecture:** modular monolith
- **Primary interface:** Streamlit + Typer CLI
- **Persistence:** SQLite
- **Core ML:** PyTorch + Anomalib
- **Deployment direction:** local-first / OpenVINO-oriented

## Product boundary

WeaveVision is a normal-only / one-class visual anomaly detection and textile quality analytics system. It produces anomaly scores, pixel-level localization and explicit quality-control states including `PASS`, `REVIEW`, `FAIL` and `ABSTAIN`.

It does **not** generate carpet designs, certify manufacturing quality unconditionally, or replace expert review.

## Engineering rules

1. Do not calibrate thresholds on the test set.
2. Do not write performance claims without repository evidence.
3. Keep domain/capture validation before automated QA decisions.
4. Preserve `REVIEW` and `ABSTAIN` instead of forcing every input into pass/fail.
5. Use repository-relative paths or configuration; never hard-code developer-specific paths.
6. Keep model/data provenance and hash checks in lifecycle operations.
7. Run CI-equivalent checks before material changes:

```bash
uv sync --extra dev --frozen
uv run ruff check .
uv run ruff format --check .
uv run mypy src
uv run pytest -q
uv build
```

## Key code areas

- `src/weavevision/domain/` — schemas, enums, protocols and typed errors
- `src/weavevision/data/` — dataset adapters, manifests, split/leakage controls and tiling
- `src/weavevision/models/` — Anomalib adapters, registry and export/hash logic
- `src/weavevision/inference/` — quality gate, predictor, post-processing and regions
- `src/weavevision/evaluation/` — metrics, calibration, drift/PSI and robustness
- `src/weavevision/services/` — orchestration and lifecycle services
- `src/weavevision/ui/` — Streamlit product surface

## Documentation

- `README.md` — portfolio-first overview
- `docs/README_FULL.md` — full technical system documentation
- `docs/SKILLS_FULL.md` — archived original assistant-oriented knowledge base
- `.github/workflows/ci.yml` — current CI contract

When documentation and executable code disagree, inspect the current code/configuration and machine-readable evidence before making a claim.
