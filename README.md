# Computational Structural Analysis of the Indus Script

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Python 3.8+](https://img.shields.io/badge/python-3.8+-blue.svg)](https://www.python.org/downloads/)

A rigorous computational structural analysis of the undeciphered Indus Valley script, extracting symbol roles, positional constraints, substitution systems, and emergent semantic behavior from 1,670 inscriptions.

---

## Abstract

This repository presents a full computational pipeline for analyzing the Indus script using transition graph modeling, clustering, substitution analysis, slot structure extraction, and semantic fingerprinting.

The results demonstrate that the Indus script exhibits **non-random, rule-governed structural organization** consistent with a constrained symbolic system, potentially compatible with linguistic encoding, though no phonetic decipherment is claimed.

---

## Key Findings

- 390 unique symbols analyzed
- 77 strict prefix/classifier symbols (100% initial position)
- 3â7 strong suffix/terminal markers (>95% final position)
- Stable slot structure: `[CLASSIFIER] -> [CONTENT] -> [MARKER]`
- 94.9% agreement between clustering and rule-based roles
- 6/6 structural validation tests passed
- 100% consistency on held-out structural validation
- 52 identity-like cores detected
- Strong centralization pattern with hub symbol (M059)
- Emergent hierarchy-like behavior from distribution

---

## 📈 Role Transition Heatmap

![Role Transition Heatmap](figures/role_transition_heatmap.png)

This heatmap shows transition frequencies between symbol roles.

Key observations:
- RELATIONAL_MARKER → RELATIONAL_MARKER dominates (2145 transitions)
- CLASSIFIER → RELATIONAL is the primary entry path
- HUB (M059) feeds into the relational layer
- CASE_MARKERs act as terminal endpoints

This supports a relational, interaction-driven grammar rather than a simple label system.

## Methodology Overview

# Indus Script Structural Analysis — Anchor Engine v5

A data-driven, distributional analysis of the Indus script using role classification, identity modeling, and interaction-based grammar reconstruction.

This repository presents a fully structural approach to analyzing the Indus script, avoiding unsupported semantic claims while identifying consistent symbolic roles, hierarchical organization, and interaction patterns.

---

## 🧠 Overview

This project models the Indus script as a **layered symbolic system** with:

- Prefix classifiers
- Identity-like cores (agents/entities)
- A dominant relational layer
- Suffix/case markers
- A unique global hub symbol (M059)

The system is analyzed using:
- positional statistics
- entropy-based role detection
- identity clustering
- stability testing
- interaction modeling

---

## 🔥 Key Findings

### 1. Hierarchical Role System

The script organizes into consistent functional layers:

- **77 classifier symbols** (prefix, position = 0.0)
- **52 identity cores**
- **17 relational markers** (mid-sequence connectors)
- **22 case markers** (suffix endings)

---

### 2. M059 — Global Hub Authority

M059 is uniquely identified as a **system-level hub**:

- 210+ occurrences
- Appears with **74 different classifiers**
- Connects to **23 identity-like agents**
- Positionally flexible (avg ≈ 0.58)
- Highest entropy and connectivity

Critically:

> M059 fails the identity stability test → confirming it is **not a personal name**, but a structural or institutional marker.

---

### 3. Identity Stability

Identity candidates were evaluated using:
- prefix diversity
- suffix diversity
- entropy
- positional consistency
- neighbor consistency

Results:

| Class | Count | Description |
|------|------|------------|
| HIGH_STABILITY | 5 | Strong recurring identities |
| MODERATE_STABILITY | 43 | Probable identities |
| LOW_STABILITY / HUB | 4 | Includes M059 |

No structural artifacts detected.

---

### 4. Relational Dominance

The system is **not identity-heavy**.

Instead:

- RELATIONAL_MARKER → RELATIONAL_MARKER is the most common transition
- CLASSIFIER → RELATIONAL dominates over CLASSIFIER → IDENTITY

This suggests:

> The script is structurally relational, likely encoding associations, transactions, or classifications rather than simple labels.

---

### 5. Anchor Engine v5 Improvements

- Removed artificial confidence uniformity
- Classifier confidence now varies (0.66–0.96)
- Identity stability test added
- Role interaction modeling introduced
- Clean separation of HUB vs IDENTITY

---

## 📊 Core Files

### Anchor Mapping
- `unified_anchor_map.csv` — All symbols with roles and confidence
- `key_symbol_anchors.csv` — Key structural symbols

### Identity Modeling
- `identity_stability_test.csv` — Stability scores and classifications

### Interaction Analysis
- `role_transitions.csv` — Role-to-role transitions
- `role_patterns.csv` — All sequence patterns
- `classifier_agent_pairings.csv` — Prefix–identity relationships
- `m059_interaction_analysis.csv` — Full hub behavior

---

## 🧪 Methodology

This project uses a **purely distributional approach**:

- No assumed language
- No forced phonetic mapping
- No external semantic injection

Techniques include:
- entropy analysis
- positional modeling
- clustering
- graph connectivity
- interaction analysis

---

## ⚠️ Important Note

This is **not a decipherment**.

Instead, this work establishes:

- structural roles
- interaction grammar
- identity-like units
- system hierarchy

True decipherment requires:
- bilingual inscriptions
- known proper names
- external archaeological correlation

---

## 🧠 Interpretation

The results support the interpretation of the Indus script as:

> A structured symbolic system with a strong relational backbone, potentially used for administrative, economic, or institutional recording.

---

## 🚀 How to Use

Run full analysis:

```bash
python run_analysis.py --all

### 1. Transition Graph Analysis
- Chi-square and co-occurrence modeling
- Directed symbol transitions
- Positional frequency extraction

### 2. Role Classification
Symbols classified by:
- Start ratio
- End ratio
- Entropy
- Flow (in/out degree)

Roles:
- STARTER
- CORE
- ENDING
- CONNECTOR

---

### 3. Clustering

K-means clustering on structural features:
- Position ratios
- Transition density
- Entropy

Result:
- 94.9% alignment with rule classification

---

### 4. Substitution System

Detected via:
- Context similarity (cosine)
- Position equivalence
- Neighbor matching

Findings:
- Large interchangeable prefix families
- Stable suffix equivalence classes
- Core substitution groups

---

### 5. Slot Structure Extraction

Dominant pattern:

```
[CLASSIFIER] -> [CONTENT] -> [MARKER]
```

Top templates cover 55.9% of corpus.

---

### 6. Identity Detection

52 symbols show:
- High context diversity
- Multi-frame occurrence
- Stable positional behavior

These act as **identity-like structural elements**.

---

### 7. Dominance & Hierarchy Analysis

Findings:
- 96% of identities are highly distributed
- One dominant hub (M059)

Interpretation:
- Strong centralization
- Possible institutional or system-level role

---

### 8. Semantic Fingerprinting

Each identity analyzed by:
- Prefix distribution
- Suffix distribution
- Sequence position
- Co-occurrence network

Resulting categories:
- CORE_ENTITY
- FLEXIBLE_AGENT
- HUB_AUTHORITY

---

## Semantic Interpretation (Constrained)

Observed structure:

```
[CLASSIFIER] + [ENTITY] + [MARKER]
```

Possible functional roles:

| Component | Interpretation |
|----------|---------------|
| Prefix | category / classifier |
| Core | entity / identifier |
| Suffix | relational marker |

---

## Central Observation

M059:
- 210 occurrences
- Appears across many contexts
- High connectivity

Interpretation:
- Hub-like symbolic function
- Likely high-level or general role

---

## What This Analysis Does NOT Claim

- No phonetic decipherment
- No direct translation
- No confirmed language family
- No validated semantic meanings

All interpretations are **distributional hypotheses only**.

---

## Conclusions

1. The Indus script is structurally non-random  
2. It follows consistent positional rules  
3. It exhibits substitution and clustering behavior  
4. It supports a slot-based symbolic system  
5. Identity-like elements and centralization exist  
6. Structural modeling is complete at the statistical level  

---

## Requirements for True Decipherment

- Bilingual inscription
- Known proper names
- Archaeological correlation
- External phonetic anchor

---

## Repository Structure

```
indus-script-analysis/
âââ code/
âââ data/
âââ results/
âââ figures/
âââ docs/
```

---

## Citation

@misc{indus_structural_analysis_2026,
  title = {Computational Structural Analysis of the Indus Script},
  year = {2026}
}

---

## License

MIT
