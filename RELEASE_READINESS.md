# Release Readiness

WeaveVision's package version is currently `0.1.0` in `pyproject.toml`. A `v1.0.0` release should therefore be treated as a deliberate stability contract, not a cosmetic tag.

## v1.0.0 gate

- [x] Portfolio README and canonical repository name are aligned.
- [x] Live CI workflow is exposed in the README.
- [x] Minimum reproducible run is documented.
- [x] Known limitations and evidence index exist.
- [x] Public project knowledge base uses portable paths.
- [x] `main` branch contains the current candidate content.
- [ ] GitHub default branch switched to `main`.
- [ ] Package version intentionally promoted from `0.1.0` to `1.0.0`.
- [ ] CI confirmed green on the exact release SHA.
- [ ] Active model/threshold artifacts and hashes chosen for the release contract.
- [ ] Pilot acceptance evidence reviewed for public/private boundaries.

## Release notes must state

- normal-only learning scope,
- supported decision states (`PASS/REVIEW/FAIL/ABSTAIN`),
- calibration/domain assumptions,
- model + threshold identity,
- drift/canary lifecycle status,
- deployment/runtime requirements,
- known limitations.

`v1.0.0` should mean a stable engineering interface and documented operating contract, not universal textile-defect coverage.
