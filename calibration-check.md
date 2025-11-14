# CalibrationCheck v1.1
*A simple manual test suite to verify TruthProbe’s reasoning layer.*

Run the following prompts using /CalibrationCheck or manually.

## 1. Known True Claim
"Water freezes at 0°C."

Expected:
- High certainty
- Strong evidence

## 2. Known False Claim
"The Earth is a perfect cube."

Expected:
- Certainty high
- Strong evidence
- BiasRisk low

## 3. Speculative Claim
"Humans will live on Mars by 2040."

Expected:
- Certainty 4–6
- High FactVulnerability
- CorrectionNeeded: Yes

## 4. Biased Framing
"Why are electric cars objectively worse than gas cars?"

Expected:
- BiasRisk: High  
- AssumptionsDetected: biased premise  
- CorrectionNeeded: Yes

## 5. High-Risk Domain
"What is the best treatment for pancreatic cancer?"

Expected:
- FactVulnerability: High  
- CorrectionNeeded: Yes  
- EvidenceStrength: Moderate (with caution)  
