# PACIS — Patient AI Care & Intelligence System
## Project Specification Document v1.0

---

## 1. Project Overview

PACIS is a patient-level AI medical system that takes symptom inputs, cross-references a disease database, calculates estimated diagnosis probabilities, and maintains a longitudinal patient record with outcome tracking. It is designed with a privacy-first architecture — patient identity is protected by default, with emergency flagging built in.

This is a research/portfolio project. No private or HIPAA-protected data is used. All disease/symptom data sourced from WHO and CDC public datasets.

---

## 2. Core Features to Build

### 2.1 Symptom Input Engine
- Accepts structured patient symptom data
- Supports multiple symptoms per input
- Normalizes symptom names against WHO ICD-11 classification

### 2.2 Disease Database
- Built from WHO and CDC public datasets
- Maps symptoms → possible diseases
- Stores disease metadata (severity, common treatments, progression patterns)
- Data sources:
  - WHO ICD-11: https://icd.who.int/en
  - WHO Global Health Observatory: https://www.who.int/data/gho
  - CDC Wonder: https://wonder.cdc.gov
  - CDC NCHS: https://www.cdc.gov/nchs/index.htm

### 2.3 Diagnosis Probability Calculator
- Takes symptom input
- Cross-references disease database
- Returns ranked list of possible diagnoses with probability scores
- Example output:
```
Input symptoms: fever, fatigue, dry cough
Output:
  1. Influenza — 74%
  2. COVID-19 — 61%
  3. Pneumonia — 43%
  4. Tuberculosis — 12%
```

### 2.4 Patient Record Store
- Each patient gets a unique anonymized ID
- Stores:
  - Symptom history per visit
  - Diagnosis estimates per visit
  - Treatments recorded
  - Outcomes recorded
- No real name or personal identity stored by default

### 2.5 Outcome Tracker
- Tracks what treatment was given after each diagnosis
- Records whether treatment was effective
- Over time builds a record of:
  - What symptoms led to what diagnoses
  - What treatments worked
  - How conditions progressed

### 2.6 Emergency Detection
- Automatically flags combinations of symptoms that indicate critical conditions
- Examples: chest pain + shortness of breath, loss of consciousness, sepsis indicators
- Triggers an alert when emergency threshold is met
- Emergency flag output includes:
  - Condition suspected
  - Urgency level (1-3)
  - Recommended immediate action

---

## 3. System Architecture

```
Patient Symptom Input
        ↓
Symptom Normalization Layer
        ↓
Disease Database (WHO/CDC)
        ↓
Diagnosis Probability Engine
        ↓
Emergency Detection Check
        ↓
Patient Record Store
        ↓
Outcome Tracker
```

---

## 4. Tech Stack (Suggested)

| Component | Suggested Tool |
|---|---|
| Language | Python 3.10+ |
| Database | SQLite (local) or PostgreSQL |
| ML/Probability | scikit-learn or custom Bayesian model |
| Data Processing | pandas, numpy |
| API Layer (optional) | FastAPI |
| Frontend (optional, later) | React or simple HTML/CSS |

---

## 5. Privacy Rules (Non-Negotiable)

- No real patient names stored anywhere in the system
- Patient IDs are anonymized hashes only
- Emergency flag does not expose identity — only condition + urgency
- All data stays local — no external transmission

---

## 6. What We Are NOT Building (Yet)

- No international/global infrastructure
- No cross-hospital networking
- No real-time live hospital integration
- No actual medical deployment (this is a research simulation)

---

## 7. Contributor Areas Needed

| Role | What You'd Work On |
|---|---|
| Backend Dev | Core Python system, database, symptom engine |
| ML Engineer | Diagnosis probability model |
| Data Engineer | WHO/CDC dataset integration and cleaning |
| Frontend Dev | Simple UI for symptom input and record display (later phase) |

---

## 8. Project Lead

**Srihith** — System architecture, research design, project direction

All contributors credited. Contributor agreement required before merge.

---

## 9. Current Status

- [x] System architecture complete
- [x] Research framework complete
- [ ] Disease database build
- [ ] Symptom input engine
- [ ] Diagnosis probability model
- [ ] Patient record store
- [ ] Outcome tracker
- [ ] Emergency detection module
- [ ] Frontend (later phase)
