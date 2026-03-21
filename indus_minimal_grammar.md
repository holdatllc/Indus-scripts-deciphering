# A Constraint-Based Structural Analysis of Indus Inscriptions Using Corrected Co-occurrence Metrics

**Author:** Holdat LLC Research Division  
**Date:** March 2025  
**Repository:** indus_valley_repo  
**Status:** Preprint — not peer reviewed

---

## Abstract

This study presents a structural analysis of the Indus inscriptional corpus (N = 1,670 sequences) using co-occurrence statistics, positional variance, and contextual motif mapping. Initial results suggested the presence of deterministic identity–title pairings; however, a methodological correction to the pairing strength denominator — expanding from title-conditioned occurrences to all occurrences of each CORE symbol — eliminated all fully locked associations.

The corrected model reveals a predominantly open combinatorial system: 155 CORE symbols exhibit generalist behavior, 59 show restricted (non-exclusive) associations, and no symbol demonstrates deterministic pairing. Despite this, four identity–title pairs remain statistically robust, exhibiting high lift and significant Fisher test results, indicating localized but non-deterministic constraints.

In contrast to weak co-occurrence structure, strong non-uniformity is observed in iconographic motif associations, suggesting that contextual domains exert the primary structural constraint on symbol usage. Positional variance further supports a flexible, slot-based system without rigid sequencing rules.

These findings indicate that the Indus script encodes information through a sparse, context-driven constraint system rather than fixed symbolic dependencies, providing a statistically grounded framework for future analysis without invoking phonetic or semantic interpretation.

---

## 1. Introduction

The Indus Valley Civilization (c. 2600–1900 BCE) produced approximately 4,000 inscribed objects bearing an undeciphered script. The brevity of most inscriptions — typically 5 signs or fewer — has long frustrated decipherment. Yet this brevity encodes structural information: an administrative system recording ownership, title, or authority would produce predictable co-occurrence patterns between its sign classes.

Prior computational work (Rao et al. 2009; Sproat 2010) debated whether the script's entropy profile is consistent with language. The present work does not address that question. Instead we ask: given the role-tag structure of the inscriptions, what can be said about the combinatorial rules governing which title signs appear with which identity signs?

Two hypotheses were tested:

**Open System Hypothesis (OSH):** Title signs are broadly reusable. Any title can appear with any identity. No systematic exclusivity exists.

**Constrained System Hypothesis (CSH):** Specific identities require specific titles. The system exhibits statistically significant non-random pairings above what chance predicts.

The corrected data supports a nuanced intermediate position: the system is predominantly open, with rare but statistically robust localised constraints embedded within it.

---

## 2. Data

### 2.1 Corpus

1,670 seal sequences drawn from the Mahadevan (1977) concordance, annotated with four role tags:

| Tag | Linguistic role |
|---|---|
| START | Classifier or title prefix |
| CORE | Core identity nucleus |
| LINK | Relational / genitive bridge |
| END | Case marker or terminal suffix |

Sign M125 — appearing in 127 of 1,670 seals — was identified as a clause-boundary operator and injected as BOUNDARY during sequence splitting.

---

## 3. Methods

### 3.1 Phase 5: Boundary Operator Validation

For each internal M125 occurrence, we split at that position and tested whether both resulting sub-sequences match the Minimal Clause Grammar `(START)*(REL)*(CORE)*(REL)*(END)*`. Validity: **75%** (36/48 internal occurrences), significantly above chance.

### 3.2 Phase 6: Compound Subject Audit

Each sequence was split at M125 walls and tested for the pattern `CORE (REL)+ CORE` within each isolated clause. Result: **4 matches in 1,670 seals (0.24%)**. One clause encodes at most one CORE identity — the Minimal Grammar is confirmed.

### 3.3 Phase 7: Positional Variance Lexicon

For each CORE symbol, mean relative position and positional variance were computed across all seals. Symbols with variance < 0.05 were classified Fixed-Pattern; others Mobile-Pattern.

### 3.4 Phase 9: Corrected Co-occurrence Analysis

For each of 580 START–CORE pairs, we computed lift, Fisher exact p-value, and pairing strength with the corrected denominator (see Section 3.5).

---

## 4. Correction of Conditional Pairing Strength Estimation

### 4.1 The v1 Error

Initial Phase 9 analysis computed pairing strength as:

$$P_{\text{v1}} = \frac{n_{\text{both}}}{n_{\text{core with any title}}}$$

This formulation conditioned on the presence of titles, excluding occurrences where a CORE symbol appeared without any associated title. This introduced a systematic inflation bias, particularly for low-frequency symbols.

### 4.2 The Corrected Formulation

The corrected formulation uses:

$$P_{\text{v2}} = \frac{n_{\text{both}}}{n_{\text{core total}}}$$

where $n_{\text{core total}}$ includes **all** occurrences of the CORE symbol, regardless of title presence.

### 4.3 Impact of Correction

| Metric | v1 (incorrect) | v2 (corrected) |
|---|---|---|
| LOCKED cores | 1 | **0** |
| RESTRICTED cores | 81 | **59** |
| OPEN cores | 99 | **155** |
| Robust pairs (all 4 gates) | 5 | **4** |

A total of 52 CORE–title pairs were reduced by more than 20 percentage points. The most extreme case (M222←M001) decreased from 100% to 20%. The previously identified deterministic pair M396←M014 decreased from 100% to 66.7%, reclassifying it as restricted rather than locked.

This correction demonstrates that no fully deterministic pairing relationships exist in the corpus when absence cases are properly included.

> *"The disappearance of all fully deterministic pairings after correction indicates that previously observed rigidity was an artefact of conditional sampling rather than an intrinsic property of the system."*

---

## 5. Results

### 5.1 Minimal Grammar (Phase 6)

| Metric | Value |
|---|---|
| Total seals | 1,670 |
| Compound subject matches | 4 (0.24%) |
| Isolation rate | **99.76%** |
| Verdict | Minimal Grammar confirmed |

The Minimal Grammar holds across 99.76% of the corpus. The 4 exceptions (seal_239, seal_609, seal_1354, seal_1500) each involve the M235 sign as a relational marker, suggesting M235 may function as a secondary relational operator.

### 5.2 Fixed-Pattern Grammar (Phase 7)

| Class | Count | % |
|---|---|---|
| Fixed-Pattern (variance < 0.05) | 18 | 90% |
| Mobile-Pattern | 2 | 10% |

90% of CORE symbols occupy a stable mid-sequence position, consistent with a proper-name or office-title register.

### 5.3 Corrected Co-occurrence Structure (Phase 9)

**Top CORE–Title Associations (Corrected Analysis)**

| Rank | Pair | True Strength (%) | Lift | Fisher p-value | Classification |
|---|---|---|---|---|---|
| 1 | M396 ← M014 | 66.7 | 65.49× | 0.0003 | Restricted |
| 2 | M164 ← M060 | 66.7 | 55.67× | 0.0004 | Restricted |
| 3 | M224 ← M008 | 66.7 | 50.61× | 0.0005 | Restricted |
| 4 | M280 ← M080 | 50.0 | 43.95× | 0.0007 | Restricted |

No CORE–title pairing reaches 100% under the corrected denominator, confirming the absence of deterministic relationships.

**System-level classification:**

| Core class | Count | Description |
|---|---|---|
| LOCKED (ts ≥ 80%, n ≥ 2) | **0** | No deterministic pairings |
| RESTRICTED (ts ≥ 50%, n ≥ 2) | 59 | Preferred but non-exclusive |
| OPEN (spread, n ≥ 2) | 155 | Generalist — multiple titles |
| SINGLETON (n = 1 only) | 57 | Insufficient data |

**Title exclusivity:**

| Title class | Count |
|---|---|
| EXCLUSIVE (HHI > 0.80) | 0 |
| PREFERENTIAL (HHI 0.40–0.80) | 1 (M054) |
| GENERALIST (HHI < 0.40) | 76 |

### 5.4 Iconographic Motif Associations

The CORE × motif co-occurrence matrix shows strong non-uniformity inconsistent with random pairing. Several CORE symbols appear preferentially on specific animal-motif seals (unicorn, zebu bull, rhinoceros), supporting a departmental model of Indus administration in which specific identity tokens are associated with specific commodity or institutional categories. Motif association is the strongest structural signal in the dataset — stronger than title co-occurrence.

---

## 6. Discussion

### 6.1 The System Is Predominantly Open

76 of 77 title symbols are generalist, spread across many CORE identities. Zero titles meet strict exclusivity criteria. The Indus administrative system allowed broad reuse of title signs across many identity contexts, consistent with known ancient administrative systems in which commodity markers similarly appear across many agent identifiers.

### 6.2 Localised Constraints Are Real but Non-Deterministic

The four robust pairs identified in Section 5.3 are not noise. They represent genuine structural constraints: specific identities that appear more often than chance with specific titles across multiple independent seal impressions. These localised constraints likely represent institutionalised roles, named offices, or fixed administrative dyads — but they are not exclusive locks.

### 6.3 Heavy-Tailed Distribution

The co-occurrence structure follows a heavy-tailed distribution: most pairs are weak or random-level; a small number are extremely strong. This is the signature of bureaucratic tagging systems (Zipf 1935), social network administrative records, and archives where most transactions are routine and a few are highly institutionalised. This structure is incompatible with purely random sign placement and incompatible with a fully constrained system.

### 6.4 What This Does Not Prove

The present analysis does not establish: phonetic values of signs, whether the script encodes spoken language, the social identity of individuals named by CORE signs, or the temporal scope of the identified constraints. These limitations are inherent to corpus-only computational analysis without a bilingual key.

---

## 7. The Five Publishable Claims

**Claim 1: The Minimal Grammar is real and robust.**  
One clause encodes at most one core identity in 99.76% of 1,670 seal sequences.

**Claim 2: M125 is a syntactic boundary operator.**  
75% clause-split validity, significantly above chance. First computational validation of the boundary-operator hypothesis.

**Claim 3: CORE signs occupy a fixed grammatical slot.**  
90% Fixed-Pattern rate (variance < 0.05). CORE signs are not free-floating; they operate under a slot grammar.

**Claim 4: The title–core system is a sparse, open combinatorial network with rare localised constraints.**  
Fisher exact testing of 580 pairs identifies 4 robust associations (p < 0.001) within a predominantly generalist structure (76/77 titles). No deterministic pairings after denominator correction.

**Claim 5: CORE symbols show systematic non-uniform association with animal iconography.**  
Motif co-occurrence is the strongest structural signal in the dataset, supporting a departmental model of Indus administration.

---

## 8. Conclusions

The Indus script is not a randomly organised sign system — but it is not a globally constrained one. It is a sparse, flexible administrative record system in which most title signs are reusable across many identity contexts, and rare but statistically robust local constraints encode specific institutionalised relationships.

> **The Indus inscriptions exhibit a sparse, constraint-based co-occurrence structure with rare statistically significant identity–title pairings embedded within a largely open combinatorial system.**

---

## Figure Captions

**Figure 1.** Core Identity vs. Animal Iconography (raw co-occurrence counts).

**Figure 2.** Contextual Motif Preference (row-normalised). Each cell shows the proportion of a CORE sign's appearances on seals bearing that motif.

**Figure 3.** Administrative Logic: Core–Title Substitution Matrix. Co-occurrence counts for top-15 symbols by frequency.

**Figure 4.** Access Key Co-occurrence (raw counts, Phase 8 hand-picked matrix).

**Figure 5.** Access-Key Lift Matrix (observed / expected). Corrected denominator. High-lift cells with low n should be interpreted cautiously.

**Figure 6.** Fisher Exact Significance Map (−log₁₀ p). Values above 1.3 correspond to p < 0.05. Most high-lift cells do not pass this threshold, confirming sparse-constraint interpretation.

**Figure 7.** True Pairing Strength — Corrected Denominator. Each cell = % of all seals containing the CORE that also contain the START title.

**Figure 8.** Title Exclusivity (HHI). 76/77 titles are generalist. Zero meet exclusivity threshold.

**Figure 9.** Before vs After Correction — CORE Classification. The transition from title-conditioned to full-occurrence normalisation eliminates all falsely inferred deterministic pairings and reveals a predominantly open system.  
*Caption:* Impact of denominator correction on CORE classification. LOCKED disappears entirely; OPEN expands from 99 to 155.

---

## References

Mahadevan, I. (1977). *The Indus Script: Texts, Concordance and Tables.* Archaeological Survey of India.

Parpola, A. (1994). *Deciphering the Indus Script.* Cambridge University Press.

Rao, R. P. N. et al. (2009). Entropic evidence for linguistic structure in the Indus script. *Science*, 324(5931), 1165.

Sproat, R. (2010). Ancient symbols, computational linguistics, and the reviewing practices of the general science journals. *Computational Linguistics*, 36(3), 585–594.

Wells, B. (1999). *An Introduction to Indus Writing.* Early Sites Research Society.

Zipf, G. K. (1935). *The Psycho-Biology of Language.* Houghton Mifflin.

---

*All results reproducible by running scripts in order as described in HOWTO.md.*
