# HOWTO: Running the Indus Valley Analysis Pipeline
## Step-by-step guide for reproducibility

---

## Prerequisites

- Python 3.8 or higher
- pip

Install all required packages in one command:

```bash
pip install pandas numpy matplotlib seaborn openpyxl
```

---

## Step 1: Get the Data Files

Two CSV files must be present in the same directory as the script when you run it:

| File | What it is |
|---|---|
| `semantic_interpretations_2.csv` | 1,670 Indus seal sequences with role annotations (provided in `data/`) |
| `seal_catalog.csv` | Iconography and site metadata per seal (provided in `data/`) |

---

## Step 2: Set Up Your Working Directory

```bash
# From the repo root:
cd code
cp ../data/semantic_interpretations_2.csv .
cp ../data/seal_catalog.csv .
```

Or simply run from the repo root and make sure the data files are alongside the script.

---

## Step 3: Run the Pipeline

```bash
python indus_analysis.py
```

The script will print progress to the console and write all outputs to a `results/` folder.

**Expected runtime:** ~15–30 seconds on a standard laptop.

---

## Step 4: Find Your Outputs

After running, `results/` will contain:

| File | What it tells you |
|---|---|
| `phase5_6_summary.csv` | Master summary — one-stop view of all findings |
| `m125_segment_validity.csv` | Phase 5: How often M125/M233 produce valid clause splits |
| `compound_subject_audit.csv` | Phase 6: The 4 anomalous compound-grammar seals |
| `core_motif_correlation_matrix.csv` | CORE symbol × animal motif co-occurrence counts |
| `exclusive_title_motif_matrix.csv` | START title × animal motif co-occurrence counts |
| `core_symbol_site_distribution.csv` | CORE symbols by excavation site |
| `indus_core_motif_heatmap.png` | Heatmap visualization (Figure 1 of the paper) |
| `phase6_compound_audit.xlsx` | Full annotated dataset with 3 sheets (pre-generated) |

---

## What Each Phase Does

### Phase 5 — Syntactic Wall Test
Tests whether M125 behaves as a true clause boundary by checking that both sides of an M125 split form valid minimal clauses. A validity rate well above chance (~75%) confirms M125 as a boundary operator.

### Phase 6 — Compound Subject Audit
Splits every sequence at M125 walls, then checks each isolated clause for `[CORE REL CORE]` — the signature of lineage or compound grammar. 4 matches out of 1,670 seals (0.24%) → Minimal Grammar confirmed.

### Iconographic Anchoring
Joins role sequences to the seal catalog and builds a matrix of which CORE identity symbols appear on which animal-motif seals. Reveals administrative departmental structure.

### Exclusive Title Audit
Same as above but for START (classifier/title) symbols — shows which titles are siloed to which animal departments.

### Site Distribution
Shows how CORE symbols are distributed across Mohenjo-daro, Harappa, Chanhu-daro, Lothal, and Kalibangan.

---

## Modifying the Analysis

### Change the boundary symbol
In `indus_analysis.py`, the `build_role_string()` function maps M125 → BOUNDARY. To test M233 as the primary boundary:

```python
# Around line 45 in indus_analysis.py:
if sign == "M233":          # change from M125
    out.append("BOUNDARY")
```

### Change the compound pattern
The strict compound regex is defined on line ~85:

```python
STRICT_COMPOUND = re.compile(r"CORE (REL )+CORE")
```

To allow CORE-CORE adjacency without a REL bridge:

```python
STRICT_COMPOUND = re.compile(r"CORE CORE")
```

### Use your own corpus
Replace `semantic_interpretations_2.csv` with any CSV that has:
- `form` — seal identifier
- `raw_sequence` — space-separated sign codes
- `role_sequence` — space-separated role tags (START/CORE/LINK/END)
- `interpretation` — sequence class label

---

## Troubleshooting

**`FileNotFoundError: semantic_interpretations_2.csv`**  
→ Make sure both CSV files are in the same directory you run the script from.

**`ModuleNotFoundError: No module named 'seaborn'`**  
→ Run `pip install seaborn matplotlib pandas numpy openpyxl`

**Heatmap not rendering / blank PNG**  
→ The script uses `matplotlib.use("Agg")` (non-interactive backend). The PNG file is always written to `results/` regardless of display settings. Open it with any image viewer.

---

## Citing This Work

```
Holdat LLC / WILL DA BEATZ HOLDAT (2025).
Indus Valley Script: Computational Evidence for the Minimal Grammar Hypothesis.
GitHub: [repository URL]
```
