# Indus Valley Script — Five-Type Structural Taxonomy
### Computational Evidence from 1,670 Seal Sequences

[![Python](https://img.shields.io/badge/Python-3.8+-blue.svg)](https://python.org)
[![License](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)
[![Status](https://img.shields.io/badge/Status-Preprint%20%2F%20Not%20Peer%20Reviewed-orange.svg)]()

---

## The Model

Five structurally distinct inscription classes — each with its own template,
sign vocabulary, and administrative function:

| Type | Name | Template | N seals | % |
|---|---|---|---|---|
| **0** | Standard | `(START?) (END*) CORE (END+)` | ~1,516 | ~90.8% |
| **1** | Title-free | `(END*) CORE (END+)` | ~134 | ~8.0% |
| **2** | Juxtaposition compound | `END CORE CORE END` | ~12 | ~0.7% |
| **3** | Bridged compound | `CORE M235 CORE` | ~4 | ~0.24% |
| **4** | Multi-identity | `END [CORE×n] END` | ~1 | ~0.06% |

---

## Three Structural Findings

### 1. M235 — Specialised Compound Operator
Appears in 7 seals. **100% REL** in every appearance. Concentrated on geometric
seals at **7.5× baseline** (p=0.005). The bridge sign in **3 of 4** bridged
compounds. First sign-level evidence for a grammatical distinction between
single-identity and compound-identity inscription types.

### 2. END CORE CORE END — Canonical Juxtaposition Class
**91.7% template uniformity** across 12 probable compound seals. Consistent
flanking vocabulary (M342, M233, M391, M089). A recognised inscription class
with a canonical form — not annotation noise.

### 3. Geometric Register — Differentiated Vocabulary
Five signs significantly concentrated on geometric seals:
M349 (**17.6×**, p=0.0002) · M235 (7.5×) · M177 (7.0×) · M345 (7.0×) · M305 (2.1×).
Geometric seals host compound grammar at **15× the non-geometric rate** (p=0.021).

---

## Three Groundbreaking Experiments

### Experiment 1: CORE Co-occurrence Social Network
**Result: Win** — but communities align with **sites**, not motifs.
- Network modularity: **0.859** (exceptional — anything >0.7 is very strong)
- 34 communities detected, each dominated by Harappa or Mohenjo-daro
- **Interpretation:** The corpus is multiple geographically-local administrative
  registries, not a single centralised system. Each city had its own identity
  vocabulary.

### Experiment 2: Dravidian Suffix Alignment Test
**Result: Productive failure** — found a new grammatical class instead.
- 18 flexible END markers found — no alignment with Dravidian case slots
- **BUT:** M305, M249, M220 are sequence-final **97–98%** of the time
- These are **sentence-final particles** — a fourth grammatical class beyond
  START/CORE/LINK/END. First distributional evidence for this class.

### Experiment 3: Compound Pair Uniqueness
**Result: Decisive negative** — every pair is unique.
- **Zero** repeated CORE pairs across all 16 compound seals or 210 total pairs
- Compound inscriptions record **one-time extraordinary transactions**,
  not ongoing bilateral relationships
- Combined with Experiment 1: rare compound seals document inter-community
  events between identities normally embedded in separate site registries

---

## Ten Claims

| # | Claim | Evidence |
|---|---|---|
| 1 | Five-type inscription taxonomy | Role-tag template analysis across corpus |
| 2 | M235 is a specialised compound operator | 100% REL, 7.5× geometric, 3/4 bridges |
| 3 | Juxtaposition compound is a canonical class | 91.7% template uniformity |
| 4 | Geometric seals are a differentiated register | M349 17.6×, compound rate 15× |
| 5 | Minimal Grammar robust within scope | 97.66%–99.76% isolation rate |
| 6 | Title–core system is open and non-deterministic | 0 locked cores, 4 restricted pairs |
| 7 | Title adjacency is the primary positional rule | START→CORE lift 2.64× |
| 8 | CORE network has site-based community structure | Modularity 0.859, site-dominant communities |
| 9 | M305/M249/M220 are sentence-final particles | 95–98% sequence-final, SD 0.06–0.10 |
| 10 | All compound pairs are unique one-time transactions | Zero repeated CORE pairs in corpus |

---

## Methodological Correction

v1 pairing strength inflated by conditional denominator. 52 pairs overcounted
by >20pp. After correction: **0 locked cores** (was 1), 4 robust restricted pairs.

> *"The disappearance of all fully deterministic pairings after correction
> indicates that previously observed rigidity was an artefact of conditional
> sampling rather than an intrinsic property of the system."*

---

## Pipeline

| Phase | Script |
|---|---|
| 5+6 | `indus_analysis.py` — boundary test, compound audit |
| 7 | `phase7_master_lexicon.py` — positional variance lexicon |
| 8 | `phase8_access_keys.py` — access matrix + HHI |
| 9 | `phase9_deep_access_keys.py` — Fisher exact, corrected strength |
| Engine | `indus_mhm_engine.py` — MHM harmonic routing + discovery |

---

## Quick Start

```bash
pip install pandas numpy matplotlib seaborn openpyxl scipy networkx

cd code
cp ../data/*.csv .

python indus_analysis.py
python phase7_master_lexicon.py
python phase8_access_keys.py
python phase9_deep_access_keys.py
python indus_mhm_engine.py      # standalone — no data files needed
```

---

## Paper Structure

```
paper/
├── indus_minimal_grammar.md      ← Main paper: five-type taxonomy
├── core_core_review.md           ← CORE→CORE manual review (99 seals)
├── new_findings_mhm_engine.md    ← Gap analysis: M235, template, register
├── followup_discoveries.md       ← M235 profile, geometric cluster, taxonomy
└── three_experiments.md          ← Network · Dravidian test · Pair uniqueness
```

---

## Citation

```
Holdat LLC / WILL DA BEATZ HOLDAT (2025).
A Five-Type Structural Taxonomy of Indus Valley Inscriptions:
Computational Evidence from 1,670 Seal Sequences.
GitHub: [repository URL]
```

---

## License

MIT License. Analysis code © 2025 Holdat LLC.  
MHM engine © 2025 Holdat LLC.  
Data derived from publicly available Indus corpus (Mahadevan 1977).
