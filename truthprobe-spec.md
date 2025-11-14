# TruthProbe v1.1 — Specification  
*A reasoning-layer utility for AI output evaluation.*

## Purpose  
Provide a portable method for evaluating AI answers by attaching a structured “TruthTail” to each response.  
This creates an interpretability layer usable across any large language model.

TruthProbe does not rely on internal model access.  
Its structure works entirely through instruction-driven reasoning.

---

## Reasoning Model

TruthProbe evaluates answers using six parallel checks:

### 1. CertaintyLevel (0–10)
A self-estimated heuristic score based on:
- internal coherence  
- commitment language (“definitely” vs “possibly”)  
- consistency between steps  

The model is asked to score its own output after generating it.

---

### 2. EvidenceStrength
Categories:
- **None** — Pure assertion  
- **Weak** — One source of reasoning  
- **Moderate** — Multiple supporting ideas  
- **Strong** — Clear, multi-stage justification  

Not factual correctness — just evidence structure.

---

### 3. BiasRisk
Evaluates whether the answer:
- frames the issue one-sidedly  
- omits major alternative paths  
- uses emotionally weighted or normative language  

Outputs: Low / Moderate / High.

---

### 4. AssumptionsDetected
TruthProbe asks the model to reveal:
- hidden premises  
- missing definitions  
- logical leaps  
- unstated constraints  

This gives the user insight into *why* the model answered the way it did.

---

### 5. FactVulnerability
Signals domains where hallucination rates are historically higher:
- medical  
- legal  
- statistics  
- finance  
- history  
- scientific claims without citations  

Outputs: Low / Moderate / High.

---

### 6. CorrectionNeeded
TruthProbe flags whether the user should double-check:
- reasoning gaps  
- overconfidence  
- weak assumptions  
- high-risk domains  

Outputs:
- **Yes: <reason>**  
- **No**  

---

## TruthTail Format (v1.1)
[TruthTail]
CertaintyLevel: X/10
EvidenceStrength: <None|Weak|Moderate|Strong>
BiasRisk: <Low|Moderate|High>
AssumptionsDetected: <list or "None">
FactVulnerability: <Low|Moderate|High>
CorrectionNeeded: <Yes|No> (+ reason if Yes)
[/TruthTail]

---

## Design Philosophy
TruthProbe follows three principles:

### 1. *Interpretability should be universal.*  
Any model, any skill level, any domain.

### 2. *Evaluation must be lightweight.*  
No complex code. No custom backend.

### 3. *Transparency should be user-readable.*  
Humans deserve to understand when AI is guessing.

---

## Integration Notes  
TruthProbe can be layered with:
- custom modes  
- memory anchoring  
- workflow agents  
- decision-assist systems  

It is intentionally small so that it can fit anywhere.
