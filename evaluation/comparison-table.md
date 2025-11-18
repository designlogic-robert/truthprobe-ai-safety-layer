# TruthProbe v1.1 — Scenario Comparison Table

This table summarizes how TruthProbe responds across different prompt types.

| # | Scenario Type            | Domain Risk      | Raw Model Behavior                           | TruthProbe Signal Highlights                                                                 |
|---|--------------------------|------------------|----------------------------------------------|----------------------------------------------------------------------------------------------|
| 1 | Simple factual           | Low              | Short, correct answer                        | High `CertaintyLevel`, Strong `EvidenceStrength`, Low `BiasRisk`, `CorrectionNeeded = No`.  |
| 2 | Future speculation       | Medium           | Confident narrative about the future         | Mid `CertaintyLevel`, Weak/Moderate `EvidenceStrength`, Moderate `BiasRisk`, `CorrectionNeeded = Yes`. |
| 3 | Biased framing           | Medium           | Initially agrees with the framing            | Low/Mid `CertaintyLevel`, Moderate `EvidenceStrength`, **High `BiasRisk`**, assumptions flagged, `CorrectionNeeded = Yes`. |
| 4 | Health triage            | High             | Provides generic medical guidance            | Mid `CertaintyLevel`, Moderate `EvidenceStrength`, Low `BiasRisk`, **High `FactVulnerability`**, `CorrectionNeeded = Yes`. |

Key patterns:

- **Risk-aware:** `FactVulnerability` jumps in health / medical contexts.
- **Calibration:** TruthProbe downshifts `CertaintyLevel` on speculative or biased prompts.
- **Bias detection:** Leading questions are marked with **High `BiasRisk`** and explicit assumptions.
- **User guidance:** `CorrectionNeeded` acts as a single “trust handle” for non-technical users.
