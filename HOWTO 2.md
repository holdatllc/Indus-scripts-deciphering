# HOWTO: Running the Indus Valley Analysis Pipeline

---

## Prerequisites

```bash
pip install pandas numpy matplotlib seaborn openpyxl scipy
```

Python 3.8+. The `scipy` package is required for Phase 9 (Fisher exact test).

---

## File Setup

```bash
cd code
cp ../data/*.csv .
```

Phase 7, 8, and 9 read output files from `results/` automatically. Either run in order, or copy the pre-generated files from `results/`.

---

## Run Order

### Step 1 — Phases 5 + 6 + Iconographic
```bash
python indus_analysis.py
```
Generates Phase 5/6 boundary validation, compound audit, motif heatmap, and the annotated Excel file needed by later phases.

### Step 2 — Phase 7: Master Lexicon
```bash
python phase7_master_lexicon.py
```
Builds the CORE symbol lexicon with positional variance and Fixed/Mobile classification.

### Step 3 — Phase 8: Access Keys (hand-picked)
```bash
python phase8_access_keys.py
```
Runs the original hand-picked matrix (M178/M270/M357/M153 × M024/M016/M044/M028) plus a top-15 full corpus matrix with HHI exclusivity scoring.

### Step 4 — Phase 9: Deep Statistical Analysis
```bash
python phase9_deep_access_keys.py
```
Runs Fisher exact test on all 580 title–core pairs, computes lift, exclusivity, vulnerability, and generates 3 statistical heatmaps.

---

## Output Files by Phase

### Phase 5+6 (`indus_analysis.py`)

| File | Content |
|---|---|
| `phase5_6_summary.csv` | Master headline stats |
| `m125_segment_validity.csv` | M125/M233 validity rates |
| `compound_subject_audit.csv` | 4 anomalous compound seals |
| `core_motif_correlation_matrix.csv` | CORE × motif counts |
| `exclusive_title_motif_matrix.csv` | START title × motif counts |
| `core_symbol_site_distribution.csv` | CORE by site |
| `indus_core_motif_heatmap.png` | Fig 1 |

### Phase 7 (`phase7_master_lexicon.py`)

| File | Content |
|---|---|
| `master_structural_lexicon.csv` | CORE symbol catalogue — position, motif, site, class |
| `core_title_substitution_matrix.csv` | 15×15 title × core co-occurrence |
| `functional_class_breakdown.csv` | Fixed vs Mobile counts |
| `motif_preference_heatmap.png` | Fig 2 |
| `core_title_substitution_heatmap.png` | Fig 3 |

### Phase 8 (`phase8_access_keys.py`)

| File | Content |
|---|---|
| `access_key_matrix.csv` | Top-15 raw co-occurrence |
| `access_key_matrix_normalised.csv` | Per-CORE probability |
| `deterministic_keys.csv` | All pairs ranked by strength |
| `access_key_heatmap.png` | Fig 4 |

### Phase 9 (`phase9_deep_access_keys.py`)

| File | Content |
|---|---|
| `deep_access_keys_full.csv` | All 580 pairs — lift, odds, Fisher p, significance |
| `deep_access_keys_significant.csv` | 497 pairs at p<0.05 |
| `title_exclusivity.csv` | HHI concentration per title + class |
| `core_vulnerability.csv` | LOCKED/RESTRICTED/OPEN/SINGLETON per core |
| `bidirectional_exclusive_pairs.csv` | Pairs where both title and core are exclusive |
| `access_lift_heatmap.png` | Fig 5: lift matrix |
| `access_fisher_heatmap.png` | Fig 6: −log10(p) significance |
| `title_exclusivity_chart.png` | Fig 7: HHI bar chart |
| `phase9_summary.csv` | Phase 9 headline stats |

---

## Understanding the Phase 9 Metrics

### Lift
```
lift = observed_cooccurrences / expected_under_independence
```
Lift > 1 means the pair co-occurs more than chance predicts. Lift = 10 means 10× more than expected. All 580 tested pairs have lift ≥ 3.

### Fisher Exact p-value
Tests whether the 2×2 contingency (has title vs doesn't × has core vs doesn't) is consistent with independence. p < 0.05 means the association is statistically significant given the corpus size.

### HHI Concentration (Title Exclusivity)
```
HHI = sum(share_i^2)  for each core i that this title appears with
```
HHI = 1.0 → title appears with only one core. HHI = 0.1 → title spread evenly across 10 cores.
- EXCLUSIVE: HHI > 0.80
- PREFERENTIAL: HHI 0.40–0.80
- GENERALIST: HHI < 0.40

### Core Vulnerability Classes
- **LOCKED**: n≥2, HHI>0.80 — single title controls almost all access
- **RESTRICTED**: n≥2, HHI>0.40 — top title dominates but not exclusive
- **OPEN**: n≥2, spread across multiple titles
- **SINGLETON**: only 1 co-occurrence event (statistically indeterminate)

---

## Adjusting Thresholds

### Phase 9 — Change Fisher significance level
```python
# In phase9_deep_access_keys.py:
"sig_05": p_fisher < 0.05,   # change to 0.01 for stricter
"sig_10": p_fisher < 0.10,   # change to 0.05 to remove this column
```

### Phase 9 — Change exclusivity thresholds
```python
"exclusivity_class": (
    "EXCLUSIVE"    if hhi > 0.80 else   # raise to 0.90 for stricter
    "PREFERENTIAL" if hhi > 0.40 else   # raise to 0.60 for stricter
    "GENERALIST"
),
```

### Phase 9 — Change minimum support
```python
# core_vulnerability classification:
"access_class": (
    "LOCKED"     if hhi > 0.80 and n_events >= 2 else   # raise to 3
    "RESTRICTED" if hhi > 0.40 and n_events >= 2 else   # raise to 3
```

---

## Troubleshooting

| Error | Fix |
|---|---|
| `FileNotFoundError: semantic_interpretations_2.csv` | `cp ../data/*.csv .` |
| `FileNotFoundError: phase6_compound_audit.xlsx` | Run Phase 5+6 first |
| `ModuleNotFoundError: scipy` | `pip install scipy` |
| All pairs show p=1.0 | n=1 data only — this is correct; use lift instead |
| 497 significant pairs seems high | Correct — Fisher exact is sensitive to marginal frequencies; use lift ≥ 3 as a secondary filter |

---

## Citation

```
Holdat LLC / WILL DA BEATZ HOLDAT (2025).
Indus Valley Script: Computational Evidence for the Minimal Grammar Hypothesis.
GitHub: [repository URL]
```
