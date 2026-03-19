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

## Methodology Overview

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
