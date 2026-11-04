# BioVid Part B — biosignal-only pain intensity classification

A fully reproducible, leave-one-subject-out (LOSO) pipeline for pain intensity recognition from the
filtered biosignals of the **BioVid Heat Pain Database, Part B** (EDA/GSR, ECG and three EMG channels;
no video, no metadata). Everything lives in one notebook, `biovid_partB_pipeline.ipynb`, which runs
from raw CSV files to evaluation reports, figures and a results summary for writing up.

Reference work: Gruss et al. (2015), *Pain Intensity Recognition Rates via Biopotential Feature Patterns
with Support Vector Machines*, PLoS ONE 10(10): e0140330. Their published feature table can optionally be
evaluated under the same protocol (Step 9).

## Headline findings

LOSO accuracy, 86 subjects, 95% subject-bootstrap CIs. Chance is 0.20 for five classes and 0.25 for four.

| Task | Features | XGBoost | HGB | LogReg | SVM-RBF |
|---|---:|---|---|---|---|
| 5-class (BL1, PA1–PA4), no facial similarity | 169 | **0.360** [0.336, 0.385] | 0.351 | 0.337 | 0.340 |
| 4-class (BL1, PA2–PA4) | 175 | **0.440** [0.413, 0.468] | 0.435 | 0.420 | 0.421 |
| 5-class, no facial EMG | 113 | **0.327** [0.305, 0.350] | 0.320 | 0.317 | 0.316 |
| 4-class, no facial EMG | 113 | **0.408** [0.379, 0.439] | 0.404 | 0.389 | 0.393 |

BL1 vs PA4 AUC from the 5-class model is 0.89. The full metric set is in `outputs/reports/summary.md`.

1. **The released Part B facial EMG of BL1 is a copy of PA1.** For 99% of PA1 trials the corrugator and
   zygomaticus arrays are byte-identical to a BL1 trial of the same subject. Compared with the features Gruss et al.
   computed from the original recordings, the released PA1 facial signals are genuine (r > 0.9), while the released BL1
   facial signals are not (r 0.22–0.34). Any baseline-similarity feature on those channels becomes a PA1 detector, and any
   facial feature describes PA1 faces in the BL1 class. The no-facial runs avoid both problems.
2. **A BL1 trial must not contribute to its own baseline template.** With the full BL1 mean as template, 5-class
   accuracy is 0.66; with a leave-one-out template it is 0.52; without the leaking facial similarity it is 0.36.
3. **XGBoost beats logistic regression and an RBF-SVM** on the same folds and features. The paired accuracy gain is
   +0.010 to +0.023, significant in 3 of 4 main runs, and it holds against the best regularisation of each baseline.
   HGB lies between them.
4. **Against the published feature set** (84 shared subjects, identical trials, folds and models), the published
   features win while their similarity features are included. Those features show the same self-inclusion
   signature as our full-template features. With similarity features removed from both sets, our features are
   significantly better in 5 of 6 tasks and not different in the sixth.

## Pipeline

| Step | What it does | Output folder |
|---|---|---|
| 1 | Index and audit every `*_bio.csv` (NaN, dead channels, row count, sampling rate); exclude corrupt or flat trials; cache the signals per subject as a `(n_trials, 5, 2816)` float32 array | `outputs/features/` |
| 2 | 232 features per trial: 61 EDA (tonic/phasic, SCR peaks, spectral), 51 ECG (morphology, spectral, R-peak HRV), 40 per EMG channel (amplitude, spectral, bursting). Baseline-similarity features are computed with a full and a leave-one-out BL1 template | `outputs/features/` |
| 3 | Feature hygiene: drop constants, greedy de-duplication at \|r\| > 0.95 on within-subject z-scores (232 → 175) | `outputs/features/` |
| 4 | LOSO (86 folds) with XGBoost and HistGradientBoosting on identical folds, six configurations (see notebook) | `outputs/models/` |
| 5 | Evaluation: accuracy, macro-F1, kappa, MAE, Spearman, binary sub-tasks, subject-level bootstrap CIs, paired model comparison | `outputs/reports/` |
| 6 | Facial-EMG duplication audit (hash matching, twin-pair behaviour, source-file check) | `outputs/reports/` |
| 7 | Figures | `outputs/figures/` |
| 8 | Linear baselines (logistic regression, RBF-SVM, small C grid) on the same folds | `outputs/models/` |
| 9 | Optional: the published Gruss et al. (2015) features linked to the released trials, audited, and run under the same protocol in three variants; random-split protocol check | `outputs/features/`, `outputs/models/`, `outputs/reports/` |
| 10 | Paired subject-level bootstrap comparisons: boosted vs baselines, our vs published features | `outputs/reports/`, `outputs/figures/` |
| 11 | `summary.md`: every number needed for a paper (data, features, models, integrity findings, results, comparisons, limitations, versions) | `outputs/reports/` |

Models are not tuned on Part B: XGBoost uses a fixed shallow configuration (depth 3, 300 trees,
learning rate 0.07), HGB is capacity-matched, and the baselines use library defaults. Normalisation is a
within-subject z-score fitted on the subject's own unlabelled trials.

## Setup

Requirements: Python 3.10–3.12 (tested with 3.11), CPU only, about 1.5 GB of free disk for outputs.

```bash
git clone <this repository>
cd <repository>
python -m venv .venv
# Windows: .venv\Scripts\activate      Linux/macOS: source .venv/bin/activate
pip install -r requirements.txt
cp .env.example .env                   # then edit .env
```

### Dataset

Request the BioVid Heat Pain Database from the University of Ulm (it is not redistributed here).
From Part B you need the **filtered biosignals** folder, which contains one sub-folder per subject:

```
<BIOVID_PARTB_DIR>/
  071309_w_21/
    071309_w_21-BL1-081_bio.csv
    071309_w_21-PA1-001_bio.csv
    ...
  071614_m_20/
  ...
```

Each CSV is tab-separated with the columns `time, gsr, ecg, emg_trapezius, emg_corrugator, emg_zygomaticus`.

For Step 9 you also need the feature table that ships with the database as
`PartB_PLOS_ONE_2015_biofeatures/Table_Step2_159Features-85Subs-5Levels-z.xlsx`.

### Configuration (`.env`)

| Variable | Required | Meaning |
|---|---|---|
| `BIOVID_PARTB_DIR` | yes | Folder that holds the subject sub-folders (use forward slashes on every OS) |
| `BIOVID_OUTPUT_DIR` | no | Where outputs are written; default `./outputs` |
| `BIOVID_N_JOBS` | no | Parallel workers for file reading, feature extraction, XGBoost and the baselines; default `-1` (all cores) |
| `BIOVID_PLOS_FEATURES` | no | Path to the published Gruss et al. (2015) feature table; when empty, Step 9 is skipped |

No other edits are needed; the notebook contains no machine-specific paths.

## Run

From the repository folder (so that `.env` is found):

```bash
jupyter nbconvert --to notebook --execute --inplace --ExecutePreprocessor.timeout=-1 biovid_partB_pipeline.ipynb
```

or open the notebook in JupyterLab / VS Code and run all cells.

Runtime on a 20-core CPU: reading, caching and feature extraction take a few minutes. The six LOSO configurations of
Step 4 take 3–20 minutes each, the baselines of Step 8 about 12 minutes, and Step 9 adds about an hour.
The whole notebook takes about two hours.

The notebook always recomputes everything; delete `outputs/` first if you want a guaranteed clean run.

## Outputs

```
outputs/
  features/   index_biosignals_partB.parquet       audit of all 8,600 trials, with exclusion flags
              cache/<subject>.npy, meta.parquet    cached clean signals and their metadata
              features_raw_partB.parquet           232 features + 24 leave-one-out similarity columns
              features_model_partB.parquet         175 model features, full BL1 template
              features_model_partB_loo.parquet     175 model features, leave-one-out BL1 template
              features_plos_matched.parquet        published features linked to our retained trials (Step 9)
              feature_dedupe_log.parquet, *_manifest.json
  models/     loso_predictions_<run>.parquet       per-trial predictions and class probabilities (XGBoost, HGB)
              loso_predictions_<run>__baselines.parquet   the same for logistic regression and SVM
              loso_folds_<run>.parquet, xgb_gain_<run>.parquet, loso_<run>_manifest.json
  reports/    summary.md, summary.csv, summary.json     everything for the paper; one row per run and model
              eval_<run>.{md,json}, per_subject_<run>.parquet   full evaluation of the main runs
              model_comparison.{md,json}           boosted vs baselines, paired bootstrap
              published_features_comparison.{md,json}, published_features_audit.json, protocol_random_split.json
              pa1_duplication.{md,json}, pa1_twin_pairs.parquet, template_correction.json
  figures/    fig01–fig07 (confusion matrices, per-subject accuracy, feature importance, correction history,
              model comparison, our vs published features)
```

`outputs/features/` and `outputs/models/` are git-ignored because of their size; reports and figures are kept.

## Reproducibility notes

- All seeds are fixed (42); folds are defined by subject, not by sample order.
- Trials are retained only if every channel has `std > 1e-8` and no NaN. This removes 174 of 8,600 trials
  (2.0%); every subject keeps at least 71 trials.
- Within-subject z-scoring uses all of a subject's trials, including the held-out fold (labels are not used).
  This is standard in affect recognition but is a mild optimistic bias relative to training-fold-only scaling.
- Part B is not an external validation of Part A: 84 of the 86 subjects also appear in Part A.
- Results are deterministic given the dataset. XGBoost's multithreaded histogram method can produce
  last-digit differences across CPU architectures.
