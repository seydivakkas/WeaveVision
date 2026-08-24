# Known Limitations

WeaveVision is an industrial visual anomaly detection and decision-support system. The following boundaries are part of the engineering contract.

## 1. Normal-reference dependency

The anomaly model learns from normal/reference production imagery. If the reference set does not represent the intended operating conditions, anomaly scores and thresholds may not remain valid.

## 2. Capture and domain shift

Camera position, illumination, focus, scale, textile family, production process and other capture/domain changes can alter the feature distribution. The system therefore includes quality gates and drift monitoring, but these mechanisms do not make domain shift disappear.

## 3. Threshold scope

Decision thresholds are calibration artifacts tied to a specific model, dataset and validation contract. They must not be selected on the test set and should be revalidated after material model/domain changes.

## 4. Incomplete defect taxonomy

WeaveVision is intentionally anomaly-oriented rather than dependent on a complete catalog of defect labels. This helps detect deviations, but an anomaly score does not automatically provide a correct semantic defect name or root cause.

## 5. Human-review states are deliberate

`REVIEW` and `ABSTAIN` are valid outcomes. They indicate that automated pass/fail is not sufficiently supported by the available evidence. Removing these states would weaken the reliability model.

## 6. Drift signals are indicators

EWMA, CUSUM and PSI can surface distribution changes, but a drift alert does not by itself prove model failure or identify the physical cause. Triage and representative sample review remain necessary.

## 7. Pilot / deployment boundary

Repository tests and local deployment evidence do not constitute an unconditional manufacturing quality certificate, ERP/SaaS production approval or a guarantee of performance on every textile/camera configuration.

## Evidence policy

Claims should be supported by repository evidence such as CI results, dataset/license records, experiment protocols, calibration artifacts and lifecycle documentation. See `docs/evidence/README.md`.
