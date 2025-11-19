# TruthProbe Specification (v1.2)

TruthProbe is the public-stable reasoning transparency module for SynCE.  
It evaluates model-generated answers and emits a structured TruthTail with  
interpretable confidence, evidence, risk, and integrity signals.

---

## 1. Purpose

TruthProbe provides:
- predictable, structured reasoning transparency  
- machine-readable audit signals  
- lightweight evaluation without rewriting answers  
- safety signals that integrate into SynCE Runtime  

TruthProbe is designed to be model-agnostic and can run on any LLM.

---

## 2. TruthTail Design

The TruthTail captures seven key evaluation signals:

- **CertaintyLevel (0–10)** — stability of the model's answer  
- **EvidenceStrength** — None → Strong  
- **BiasRisk** — likelihood of biased framing  
- **AssumptionsDetected** — implicit statements not grounded in the answer  
- **TopicRisk** — sensitivity or domain hazard level  
- **FactVulnerability** — how often models hallucinate on this topic  
- **CorrectionNeeded** — whether the answer materially fails  

All values are deterministic text enums to support downstream tooling.

---

## 3. Operating Principles

TruthProbe must:
- evaluate only the existing answer  
- avoid adding facts or corrections unless required  
- remain emotionally neutral  
- avoid assuming user intent  
- follow SynCE governance (GR-007, GR-008, CAP)  

---

## 4. Mode Behavior Requirements

TruthProbe operates as a two-step program:

1. Generate the assistant’s normal answer.  
2. Evaluate that answer using the v1.2 TruthTail schema.  

TruthProbe may not:
- rewrite the answer  
- fill in missing information  
- assume correctness  
- persuade or moralize  

---

## 5. TruthTail Specification
```
[TruthTail]
CertaintyLevel: X/10
EvidenceStrength: None | Weak | Moderate | Strong
BiasRisk: Low | Moderate | High
AssumptionsDetected: <list or "None">
TopicRisk: Low | Moderate | High
FactVulnerability: Low | Moderate | High
CorrectionNeeded: Yes | No (+ reason if Yes)
[/TruthTail]
```

---

## 6. Integration Points

TruthProbe integrates with:
- SynCE Runtime (L5)
- Audit systems
- Evaluation harnesses
- Tooling pipelines
- LLM interfaces

TruthProbe emits purely analytical metadata and is safe for all contexts.

---

## 7. Versioning

v1.2 — Public stable  
All experimental versions appear only in EDEN.

End of spec.
