# Professional development formats and assessment self-efficacy among lower-secondary teachers

**An analysis of TALIS 2024 data | Netherlands**

*Fatima Mashood | May 2026*

---

## Research Question

**Which professional development formats are associated with higher self-reported self-efficacy in using assessment strategies, among lower-secondary teachers in the Netherlands?**

Assessment self-efficacy, a teacher's confidence in their ability to use a variety of assessment strategies, is considered a meaningful indicator of instructional quality. PD is one of the primary levers schools and systems use to build that capacity, yet whether format (independent of content) is associated with assessment confidence remains an open research question. This analysis uses TALIS 2024 survey data to examine that question for Dutch lower-secondary teachers.

---

## Data Source

**OECD Teaching and Learning International Survey (TALIS) 2024**
- International teacher-level file: `ttgintt4`
- Publicly available at: [webfs.oecd.org/talis](https://webfs.oecd.org/talis/index.html)
- **Sample used:** Netherlands lower-secondary teachers (ISCED 2): `CNTRY = "NLD"` and `IDCNTPOP = "NLD2"` (`IDPOP = 2`), **n = 1,271 teachers** across 630 variables (1,179 with a valid outcome). The 1,305 Dutch primary (ISCED 1, `NLD1`) teachers in the file are excluded.
- **File provenance:** analysed files as downloaded, SHA-256 `ttgintt4.sav` = `44cedc0dd3a05c4ffedf7b62390a08cdedcae6165d82d54a2e5ddb9f6e7878ff`; `ttgintt4.csv` = `d6cc0b101783fb5f80ee24b28c19b4bca4f7dea109b7307f2efecd10ca4e0b10`. The `.sav` file's internal creation timestamp is 5 November 2025, and the local copies date from May 2026 (`.sav`) and June 2026 (`.csv`, the "NoESE" export). The OECD release/version label was not recorded at download; the SPSS and CSV files give identical Netherlands counts.

### Key Variables

| Role | Code | Description | Scale |
| --- | --- | --- | --- |
| Outcome | `TT4G27J` | Self-efficacy: "Use a variety of assessment strategies" | 1–4 (Not at all → A lot) |
| Predictor | `TT4G20A` | PD: Courses / workshops / seminars (no valid NLD responses) | 1/2/3=Yes (in person / online / both), 4=No |
| Predictor | `TT4G20B` | PD: Education conferences | same |
| Predictor | `TT4G20C` | PD: Formal qualification programme | same |
| Predictor | `TT4G20D` | PD: Visits to other schools | same |
| Predictor | `TT4G20E` | PD: Visits to business premises | same |
| Predictor | `TT4G20F` | PD: Lesson observation & reflection | same |
| Predictor | `TT4G20G` | PD: Coaching / mentoring | same |
| Predictor | `TT4G20H` | PD: Teacher networks | same |
| Predictor | `TT4G20I` | PD: Self-initiated learning | same |
| Not analysed | `TT4G21M` | PD covered: Analysis and use of student assessments: flagged for future work | 1=Yes, 2=No |

Yes (codes 1–3) is pooled against No (code 4) for each format.

---

## Methods

1. **Data loading & filtering**- Chunked CSV reading to filter to NLD2 rows from the ~278k-row international file.
2. **Data quality checks**: Column coverage, missing data rates, sampling weight presence (`TCHWGT`), and unique respondent ID verification.
3. **Sentinel recode**: TALIS uses numeric sentinel codes (8, 9, 96–99, 996–999) for missing responses; these are replaced with `NaN` on a clean copy of the data, preserving the original.
4. **Variable labelling**: SPSS metadata extracted via `pyreadstat` to map cryptic column names to full question text.
5. **Descriptive analysis**: PD participation rates per format; outcome distribution including mean and SD.
6. **Comparative analysis**: Mann-Whitney U tests comparing assessment self-efficacy (`TT4G27J`) between teachers who did and did not participate in each format. Effect size reported as rank-biserial correlation (*r* = 2U / (n_yes × n_no) − 1; positive = Yes group scores higher). Comparisons run only where both groups had *n* ≥ 30. The main tests are unweighted; a weighted sensitivity check (mean differences with `TCHWGT` and BRR replicate weights) is also reported.

---

## Key Findings

### Descriptive

All figures are unweighted and use valid responses only.

**Outcome: assessment self-efficacy (`TT4G27J`).** n = 1,179 of 1,271 (92.8%); mean = 2.96, SD = 0.73, median = 3. Self-efficacy is **fairly high**.

| Response | n | % |
| --- | --- | --- |
| 1 – Not at all | 31 | 2.6 |
| 2 – To some extent | 247 | 20.9 |
| 3 – Quite a bit | 642 | 54.5 |
| 4 – A lot | 259 | 22.0 |
| **Total** | **1,179** | **100.0** |

**Predictors: PD format participation.**

| Format | n valid | % valid | % participated |
| --- | --- | --- | --- |
| Lesson observation & reflection | 1,217 | 95.8 | 69.0 |
| Self-initiated learning | 1,216 | 95.7 | 53.8 |
| Education conferences | 1,217 | 95.8 | 42.6 |
| Teacher networks | 1,213 | 95.4 | 40.7 |
| Coaching / mentoring | 1,214 | 95.5 | 35.9 |
| Visits to other schools | 1,214 | 95.5 | 23.8 |
| Visits to business premises | 1,215 | 95.6 | 20.3 |
| Formal qualification programme | 1,209 | 95.1 | 19.5 |
| Courses / workshops / seminars | 0 | 0.0 | n/a |

### Comparative

Eight formats had at least 30 teachers in both groups (courses/workshops has no valid NLD responses). **Three show small, statistically significant positive associations** with assessment self-efficacy: education conferences, teacher networks and self-initiated learning (all p < .001, *r* ≈ 0.12–0.14).

| Format | n (Yes) | Mean (Yes) | n (No) | Mean (No) | p-value | Effect (*r*) | Diff, 95% CI |
| --- | --- | --- | --- | --- | --- | --- | --- |
| Education conferences | 497 | 3.06 | 672 | 2.89 | < .001 | +0.12 | +0.17 [0.09, 0.26] |
| Formal qualification programme | 222 | 2.89 | 939 | 2.97 | .103 | −0.06 | −0.08 [−0.19, 0.03] |
| Visits to other schools | 276 | 3.04 | 889 | 2.93 | .053 | +0.07 | +0.11 [0.01, 0.20] |
| Visits to business premises | 238 | 3.03 | 929 | 2.94 | .106 | +0.06 | +0.09 [−0.00, 0.19] |
| Lesson observation & reflection | 802 | 2.98 | 367 | 2.91 | .170 | +0.05 | +0.07 [−0.02, 0.16] |
| Coaching / mentoring | 421 | 2.99 | 744 | 2.94 | .249 | +0.04 | +0.05 [−0.03, 0.14] |
| Teacher networks | 475 | 3.07 | 691 | 2.88 | < .001 | +0.14 | +0.19 [0.11, 0.28] |
| Self-initiated learning | 629 | 3.04 | 539 | 2.86 | < .001 | +0.13 | +0.18 [0.10, 0.27] |

A design-based sensitivity check (weighted mean differences using `TCHWGT` with BRR replicate weights, in the notebook) confirms the pattern: the same three formats are significant (weighted differences +0.20, +0.22, +0.20; all p < .001) and no other format is (smallest p = .076). These are associations, not evidence that any format raises self-efficacy. The three significant results also pass a Bonferroni threshold for eight tests (.05 / 8 ≈ .006).

**Joint model (sensitivity).** Entering all eight formats together in one OLS model (school-clustered standard errors, 84 schools, unweighted, n = 1,135 complete cases) leaves the same three formats positive and significant at .05: conferences *b* = +0.126 (95% CI 0.035 to 0.216), teacher networks +0.142 (0.067 to 0.217), self-initiated learning +0.121 (0.034 to 0.207). Against a Bonferroni threshold of .05 / 8 = .00625, networks and self-initiated learning pass and conferences narrowly misses (*p* = .0064). An ordered logit gives the same three positive associations (odds ratios 1.42, 1.47, 1.38). In that model formal qualification turns weakly negative (OR = 0.74, *p* = .042), but it is not significant in the OLS model (*p* = .061) or the one-at-a-time test (*p* = .103), so treat it as unstable. No teacher or school covariates are included. Details are in the notebook (Step C4) and `brief.md`. Comparisons are complete-case, and the CI column above is a Welch *t* interval for the unweighted difference.


---

## Limitations

- **Survey design**: The main tests and plotted intervals are unweighted and ignore school clustering. A weighted sensitivity check (`TCHWGT`, BRR replicate weights) supports the same conclusions, but it is a simple mean-difference check without covariates, so results should still be read as sample-level associations.
- **Sample and non-response**: Lower-secondary (ISCED 2, `IDPOP = 2`) teachers only; Dutch primary teachers in the file are excluded. The OECD's Netherlands country note (OECD, 2025) flags the Dutch estimates because the sample did not meet TALIS participation-rate standards, with a higher risk of non-response bias, so results should be interpreted with caution.
- **Self-report bias**: Both predictor and outcome are self-reported; self-efficacy scores may reflect personality disposition rather than genuine competence.
- **Cross-sectional design**: Causality cannot be inferred; teachers with higher baseline self-efficacy may self-select into more PD.
- **Multiple comparisons**: Eight tests, no formal adjustment (in the one-at-a-time tests the three significant results pass a Bonferroni threshold of .05 / 8 = .00625; in the joint model conferences narrowly misses it); formats are analysed one at a time with no covariates, and participation in different formats is likely correlated.
- **Format, not content**: The analysis does not capture PD duration, quality, or content (e.g., `TT4G21M`).
- **Missing item**: `TT4G20A` (courses/workshops) has no valid NLD responses.

---

## Implications

Teachers who attended education conferences, took part in teacher networks or engaged in self-initiated learning report somewhat higher assessment confidence in this sample, and the differences are small. The design cannot show whether the formats build confidence or whether more confident teachers choose them. Next steps:

- **Weighted, design-based analysis**: `TCHWGT` with BRR replicate weights (`TRWGT1–100`).
- **PD content**: `TT4G21M` (whether PD specifically covered assessment analysis) is a more theoretically proximate predictor.
- **Multilevel modelling**: Teachers are nested within schools; model formats jointly with teacher covariates.

---

## Get the data and run it

The TALIS 2024 microdata are not redistributed here (size and OECD terms). To reproduce:

1. Download the TALIS 2024 teacher data from the [OECD TALIS 2024 data page](https://webfs.oecd.org/talis/index.html): the teacher questionnaire file `ttgintt4` in both **CSV** and **SPSS (.sav)** form.
2. Put both files anywhere under `./datasets/` (the notebook searches sub-folders), or point `TALIS_DATA_DIR` at the folder that holds them.
3. Install and run:

```bash
pip install -r requirements.txt
jupyter nbconvert --to notebook --execute talis2024.ipynb --inplace
```

The first code cell lists which files it found and stops with a clear message if either is missing. A full run takes under a minute. The CSV is used for the data, the `.sav` only for variable labels. The checksums of the files used for the reported results are in the file-provenance section above.

```
talis-2024-pd-formats-assessment-self-efficacy/
├── talis2024.ipynb          # Analysis notebook (outputs included)
├── talis_labels.txt         # Variable labels (TALIS 2024 teacher file)
├── requirements.txt
├── README.md
├── brief.md
├── fig1_descriptive.png
├── fig2_comparison.png
└── datasets/                # you add this (git-ignored)
```

---

**Reference:** OECD. (2025, 7 October). *Results from TALIS 2024 – Country notes: Netherlands.* OECD Publishing. https://www.oecd.org/en/publications/results-from-talis-2024-country-notes_e127f9e2-en/netherlands_db6bd540-en.html

*Analysis by Fatima Mashood | Data: TALIS 2024, OECD | Country: Netherlands (NLD)*
