<div align="center">

# WeaveVision

### Reliable Visual Anomaly Detection for Textile Quality Control

![Python](https://img.shields.io/badge/Python-3.11-3776AB?style=flat-square&logo=python&logoColor=white)
![PyTorch](https://img.shields.io/badge/PyTorch-2.8-EE4C2C?style=flat-square&logo=pytorch&logoColor=white)
![Anomalib](https://img.shields.io/badge/Anomalib-2.5-009688?style=flat-square)
![OpenVINO](https://img.shields.io/badge/OpenVINO-Deployment-6F42C1?style=flat-square)
[![CI](https://github.com/seydivakkas/WeaveVision/actions/workflows/ci.yml/badge.svg)](https://github.com/seydivakkas/WeaveVision/actions/workflows/ci.yml)

**A local-first industrial vision system that learns from normal textile samples, localizes visual anomalies and turns model uncertainty into explicit quality-control decisions.**

`Industrial AI` · `Anomaly Detection` · `PatchCore` · `EfficientAD` · `Drift Monitoring` · `Selective Decisions`

</div>

---

## Why WeaveVision

In textile inspection, collecting every possible defect type is unrealistic. WeaveVision therefore focuses on **one-class / normal-only learning**: learn the visual structure of acceptable production and detect deviations from that reference distribution.

The system is designed around a production question that is broader than “is this image anomalous?”:

> **Can the model make a reliable quality decision under changing production conditions, and can it abstain when the evidence is not trustworthy?**

---

## Minimum reproducible run

```bash
git clone https://github.com/seydivakkas/WeaveVision.git
cd WeaveVision
uv sync --extra dev --frozen
uv run pytest -q
uv run weavevision doctor
uv run weavevision serve
```

The commands mirror the repository's CI/development contract. Model-backed inference additionally requires the corresponding validated model/threshold artifacts; the application is intentionally capable of degraded operation when those artifacts are unavailable.

---

## Decision model

WeaveVision does not force every sample into a binary pass/fail output.

```text
Input Image
    ↓
Domain / Capture Validation
    ↓
Anomaly Model
    ↓
Pixel + Image Anomaly Scores
    ↓
Calibration / Decision Gate
    ↓
PASS · REVIEW · FAIL · ABSTAIN
```

| Decision | Meaning |
|---|---|
| `PASS` | Evidence is consistent with the validated normal operating region |
| `REVIEW` | Borderline evidence requires human inspection |
| `FAIL` | Strong anomaly evidence exceeds the calibrated rejection threshold |
| `ABSTAIN` | Input/domain reliability is insufficient for a trustworthy automated decision |

---

## Core engineering capabilities

| Capability | Approach |
|---|---|
| Normal-only learning | PatchCore / EfficientAD style anomaly detection |
| Localization | Pixel-level anomaly heatmaps and overlays |
| High-resolution inspection | Tiled inference for textile imagery |
| Reliability-aware QA | Calibrated multi-state quality gate |
| Drift monitoring | EWMA, CUSUM and PSI signals |
| Model lifecycle | Registry, canary evaluation and rollback workflow |
| Active learning | Representative sample selection with coreset-style strategies |
| Local deployment | Offline-first architecture and OpenVINO-oriented export path |

---

## Engineering evidence

| Signal | Repository evidence |
|---|---|
| Automated tests | **262 / 262 passing** in the documented validation snapshot |
| Live repository health | GitHub Actions `CI` workflow badge above |
| Static quality | Ruff + mypy validation in the CI engineering workflow |
| ML framework | PyTorch + Anomalib |
| Deployment | OpenVINO-oriented inference/export path |
| Drift lifecycle | EWMA · CUSUM · PSI monitoring |
| Safety behavior | Explicit `REVIEW` and `ABSTAIN` states instead of forced automation |

[Evidence index](docs/evidence/README.md) · [Known limitations](KNOWN_LIMITATIONS.md)

---

## Reliability lifecycle

```text
Normal Reference Data
        ↓
Training / Feature Memory
        ↓
Threshold Calibration
        ↓
Model Registry
        ↓
Production Inference
        ↓
Drift Monitoring
   ┌────┴───────────┐
   ↓                ↓
Stable          Drift / Risk
   ↓                ↓
Continue      Review Samples
                    ↓
              Candidate Update
                    ↓
             Canary Validation
               ┌────┴────┐
               ↓         ↓
            Promote   Rollback
```

---

## Industrial design principles

1. **Normal-only learning when defect taxonomies are incomplete**
2. **Localization, not only anomaly scores**
3. **Calibration before automation**
4. **Abstention before unsafe confidence**
5. **Drift monitoring before silent degradation**
6. **Canary + rollback before model replacement**
7. **Local-first processing for industrial data control**

---

## Technology stack

**Machine Learning**  
`Python` · `PyTorch` · `Anomalib` · `PatchCore` · `EfficientAD`

**Vision & analytics**  
`OpenCV` · `Tiled Inference` · `Pixel-Level Heatmaps` · `Drift Statistics`

**Deployment & lifecycle**  
`Streamlit` · `OpenVINO` · `Model Registry` · `Canary / Rollback` · `pytest` · `Ruff` · `mypy`

---

## Documentation

- [Architecture index](docs/architecture/README.md)
- [Evidence index](docs/evidence/README.md)
- [Known limitations](KNOWN_LIMITATIONS.md)
- [Full technical documentation](docs/README_FULL.md)
- [Portable project knowledge base](SKILLS.md)

The full document covers architecture, phased acceptance gates, dataset governance, model lifecycle, UI flows, verified metrics, security boundaries, deployment and roadmap details.

---

## Scope boundary

WeaveVision is an engineering decision-support system. A model output is not equivalent to an unconditional manufacturing or commercial quality certificate. `REVIEW` and `ABSTAIN` are deliberate system states for cases where automation should not overclaim certainty.

---

<div align="center">

**Detect anomalies · quantify uncertainty · govern the model lifecycle**

[GitHub Profile](https://github.com/seydivakkas) · [Evidence](docs/evidence/README.md) · [Full Documentation](docs/README_FULL.md)

</div>
