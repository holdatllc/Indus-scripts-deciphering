# Indus Valley Script — Constraint-Based Structural Analysis
### Corrected Co-occurrence Metrics · 1,670 Seal Sequences

[![Python](https://img.shields.io/badge/Python-3.8+-blue.svg)](https://python.org)
[![License](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)
[![Status](https://img.shields.io/badge/Status-Preprint%20%2F%20Not%20Peer%20Reviewed-orange.svg)]()

---

## What This Is

A four-phase computational grammar analysis of 1,670 Indus Valley seal sequences. The pipeline tests the combinatorial structure between identity signs (CORE) and title/classifier signs (START), corrects a systematic denominator error discovered during review, and produces a statistically honest model of the script's constraint structure.

---

## One-Sentence Result

> **The Indus inscriptions exhibit a sparse, constraint-based co-occurrence structure with rare statistically significant identity–title pairings embedded within a largely open combinatorial system.**

---

## The Five Publishable Claims

| # | Claim | Evidence |
|---|---|---|
| 1 | **Minimal Grammar is real** | 99.76% isolation rate — one clause, one identity |
| 2 | **M125 is a syntactic boundary operator** | 75% clause-split validity, above chance |
| 3 | **CORE signs occupy a fixed grammatical slot** | 90% Fixed-Pattern (positional variance < 0.05) |
| 4 | **Title–core system is sparse and open, not locked** | 0 LOCKED cores after correction; 4 robust pairs at p < 0.001 |
| 5 | **CORE symbols associate non-randomly with iconography** | Motif co-occurrence is the strongest structural signal |

---

## What This Does NOT Claim

- ~~The Indus script is an MFA / access-key system~~ — not supported
- ~~Titles are locked to identities globally~~ — contradicted by corrected HHI data
- ~~Deterministic credential pairs exist~~ — eliminated by denominator correction
- ~~The script encodes spoken language~~ — out of scope

---

## Methodological Correction (Important)

A systematic error was identified and corrected between analysis versions:

**v1 (incorrect):**
```
strength = n_both / seals_where_core_appears_with_any_title
```

**v2 (correct):**
```
strength = n_both / ALL_seals_where_core_appears
```

The v1 method excluded title-free seals from the denominator, inflating every pairing strength. 52 pairs were inflated by more than 20 percentage points. The worst case (M222←M001) went from 100% → 20%.

| Metric | v1 (wrong) | v2 (correct) |
|---|---|---|
| LOCKED cores | 1 | **0** |
| RESTRICTED cores | 81 | **59** |
| OPEN cores | 99 | **155** |
| Robust pairs | 5 | **4** |

> *"The disappearance of all fully deterministic pairings after correction indicates that previously observed rigidity was an artefact of conditional sampling rather than an intrinsic property of the system."*

---

## Key Numbers (Corrected)

| Metric | Value |
|---|---|
| Seals analysed | 1,670 |
| Isolation rate (Minimal Grammar) | **99.76%** |
| Fixed-Pattern CORE symbols | **90%** (18/20) |
| Exclusive titles (HHI > 0.80) | **0** |
| LOCKED cores (correct denominator) | **0** |
| Restricted cores (preferred pairing, n ≥ 2) | **59** |
| Robust pairs (all 4 gates simultaneously) | **4** |

**The 4 robust pairs:**

| Pair | True Strength | Lift | Fisher p |
|---|---|---|---|
| M396 ← M014 | 66.7% | 65× | 0.0003 |
| M164 ← M060 | 66.7% | 56× | 0.0004 |
| M224 ← M008 | 66.7% | 51× | 0.0005 |
| M280 ← M080 | 50.0% | 44× | 0.0007 |

No pairing reaches 100% under the corrected denominator.

---

## Pipeline

| Phase | Script | Method |
|---|---|---|
| **5+6** | `indus_analysis.py` | M125 boundary test + compound subject audit |
| **7** | `phase7_master_lexicon.py` | Positional variance → Fixed/Mobile lexicon |
| **8** | `phase8_access_keys.py` | Hand-picked matrix + HHI exclusivity |
| **9** | `phase9_deep_access_keys.py` | Fisher exact + lift + corrected strength |

---

## Quick Start

```bash
pip install pandas numpy matplotlib seaborn openpyxl scipy

cd code
cp ../data/*.csv .

python indus_analysis.py           # Phase 5+6
python phase7_master_lexicon.py    # Phase 7
python phase8_access_keys.py       # Phase 8
python phase9_deep_access_keys.py  # Phase 9 (corrected)
```

---

## Repository Structure

```
indus_valley_repo/
├── README.md
├── HOWTO.md
├── code/
│   ├── indus_analysis.py
│   ├── phase7_master_lexicon.py
│   ├── phase8_access_keys.py
│   └── phase9_deep_access_keys.py       ← v2, corrected denominator
├── data/
│   ├── semantic_interpretations_2.csv
│   └── seal_catalog.csv
├── results/
│   ├── phase5_6_summary.csv
│   ├── m125_segment_validity.csv
│   ├── compound_subject_audit.csv
│   ├── core_motif_correlation_matrix.csv
│   ├── exclusive_title_motif_matrix.csv
│   ├── core_symbol_site_distribution.csv
│   ├── master_structural_lexicon.csv
│   ├── core_title_substitution_matrix.csv
│   ├── functional_class_breakdown.csv
│   ├── access_key_matrix.csv
│   ├── access_key_matrix_normalised.csv
│   ├── deterministic_keys.csv
│   ├── corrected_pairing_strength.csv   ← v2, all 580 pairs
│   ├── robust_constrained_pairs.csv     ← v2, 4 pairs passing all gates
│   ├── title_exclusivity.csv
│   ├── core_vulnerability.csv
│   ├── phase8_summary.csv
│   ├── phase9_summary.csv
│   ├── indus_core_motif_heatmap.png     ← Fig 1
│   ├── motif_preference_heatmap.png     ← Fig 2
│   ├── core_title_substitution_heatmap.png ← Fig 3
│   ├── access_key_heatmap.png           ← Fig 4
│   ├── access_lift_heatmap.png          ← Fig 5
│   ├── access_fisher_heatmap.png        ← Fig 6
│   ├── true_strength_heatmap.png        ← Fig 7
│   ├── title_exclusivity_chart.png      ← Fig 8
│   ├── before_after_correction.png      ← Fig 9 (before/after bar chart)
│   └── phase6_compound_audit.xlsx
└── paper/
    └── indus_minimal_grammar.md         ← Full paper, corrected framing
```

---

## Citation

```
Holdat LLC / WILL DA BEATZ HOLDAT (2025).
A Constraint-Based Structural Analysis of Indus Inscriptions
Using Corrected Co-occurrence Metrics.
GitHub: [repository URL]
```

---

## License

MIT License. Analysis code © 2025 Holdat LLC.  
Data derived from publicly available Indus corpus (Mahadevan 1977).
