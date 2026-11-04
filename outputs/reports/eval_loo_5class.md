# BioVid Part B evaluation: 5-class, leave-one-out template, 175 features

LOSO over **86 subjects / 8426 trials**, unweighted classes, identical folds.

## Core results

| model | accuracy | macro-F1 | kappa (quadratic) | kappa (unweighted) | MAE | Spearman | within 1 level |
|---|---:|---:|---:|---:|---:|---:|---:|
| XGBoost | 0.5221 | 0.5192 | 0.5152 | 0.4026 | 0.8754 | 0.5149 | 0.7363 |
| HGB | 0.5176 | 0.5171 | 0.5086 | 0.3969 | 0.8781 | 0.5103 | 0.7387 |

## Subject-level bootstrap 95% CIs (2000 resamples)

| model | metric | point | 95% CI |
|---|---|---:|---|
| XGBoost | accuracy | 0.5221 | [0.4979, 0.5469] |
| XGBoost | macro_f1 | 0.5192 | [0.4964, 0.5418] |
| XGBoost | kappa_quadratic | 0.5152 | [0.4667, 0.5622] |
| XGBoost | kappa_unweighted | 0.4026 | [0.3723, 0.4336] |
| XGBoost | mae | 0.8754 | [0.8153, 0.9335] |
| XGBoost | spearman | 0.5149 | [0.4679, 0.5614] |
| XGBoost | within_one_level | 0.7363 | [0.7169, 0.7559] |
| HGB | accuracy | 0.5176 | [0.4936, 0.5418] |
| HGB | macro_f1 | 0.5171 | [0.4944, 0.5398] |
| HGB | kappa_quadratic | 0.5086 | [0.4582, 0.5558] |
| HGB | kappa_unweighted | 0.3969 | [0.3669, 0.4273] |
| HGB | mae | 0.8781 | [0.8181, 0.9395] |
| HGB | spearman | 0.5103 | [0.4604, 0.5569] |
| HGB | within_one_level | 0.7387 | [0.7196, 0.7591] |

## Paired bootstrap: XGBoost - HGB

| metric | delta | 95% CI | p (two-sided) |
|---|---:|---|---:|
| accuracy | +0.0045 | [-0.0019, +0.0107] | 0.169 |
| macro_f1 | +0.0021 | [-0.0046, +0.0086] | 0.524 |
| kappa_quadratic | +0.0066 | [-0.0055, +0.0186] | 0.284 |
| kappa_unweighted | +0.0057 | [-0.0023, +0.0134] | 0.169 |
| mae | -0.0028 | [-0.0181, +0.0122] | 0.729 |
| spearman | +0.0046 | [-0.0077, +0.0172] | 0.468 |
| within_one_level | -0.0023 | [-0.0084, +0.0042] | 0.462 |

## Binary tasks derived from the multiclass probabilities

| task | model | n | accuracy | balanced acc | AUC | sensitivity | specificity |
|---|---|---:|---:|---:|---:|---:|---:|
| BL1_vs_any_pain | XGBoost | 8426 | 0.8168 | 0.5774 | 0.7999 | 0.9737 | 0.1811 |
| BL1_vs_PA1 | XGBoost | 3339 | 0.9323 | 0.9323 | 0.9804 | 0.9114 | 0.9532 |
| BL1_vs_PA2 | XGBoost | 3354 | 0.5975 | 0.5974 | 0.6410 | 0.6228 | 0.5719 |
| BL1_vs_PA3 | XGBoost | 3368 | 0.6758 | 0.6757 | 0.7526 | 0.6824 | 0.6691 |
| BL1_vs_PA4 | XGBoost | 3369 | 0.8047 | 0.8049 | 0.8924 | 0.7872 | 0.8225 |
| BL1_vs_any_pain | HGB | 8426 | 0.8178 | 0.5959 | 0.8008 | 0.9633 | 0.2284 |
| BL1_vs_PA1 | HGB | 3339 | 0.9305 | 0.9305 | 0.9807 | 0.9031 | 0.9580 |
| BL1_vs_PA2 | HGB | 3354 | 0.6011 | 0.6010 | 0.6425 | 0.6139 | 0.5881 |
| BL1_vs_PA3 | HGB | 3368 | 0.6734 | 0.6732 | 0.7468 | 0.6965 | 0.6499 |
| BL1_vs_PA4 | HGB | 3369 | 0.8044 | 0.8046 | 0.8905 | 0.7837 | 0.8255 |

## Per-class metrics

| model | class | support | precision | recall | F1 | AUC (one-vs-rest) |
|---|---|---:|---:|---:|---:|---:|
| XGBoost | BL1 | 1668 | 0.4464 | 0.4742 | 0.4599 | 0.7999 |
| XGBoost | PA1 | 1671 | 0.8929 | 0.8983 | 0.8956 | 0.9845 |
| XGBoost | PA2 | 1686 | 0.3390 | 0.2966 | 0.3164 | 0.7087 |
| XGBoost | PA3 | 1700 | 0.3327 | 0.3229 | 0.3278 | 0.7095 |
| XGBoost | PA4 | 1701 | 0.5725 | 0.6220 | 0.5962 | 0.8649 |
| HGB | BL1 | 1668 | 0.4583 | 0.4640 | 0.4611 | 0.8008 |
| HGB | PA1 | 1671 | 0.8951 | 0.8887 | 0.8919 | 0.9841 |
| HGB | PA2 | 1686 | 0.3412 | 0.3096 | 0.3246 | 0.7036 |
| HGB | PA3 | 1700 | 0.3206 | 0.3306 | 0.3255 | 0.6991 |
| HGB | PA4 | 1701 | 0.5671 | 0.5985 | 0.5824 | 0.8592 |

## Confusion matrices (rows = true)


**XGBoost**

| true \ pred | BL1 | PA1 | PA2 | PA3 | PA4 |
|---|---:|---:|---:|---:|---:|
| BL1 | 791 | 63 | 372 | 312 | 130 |
| PA1 | 73 | 1501 | 56 | 32 | 9 |
| PA2 | 491 | 55 | 500 | 413 | 227 |
| PA3 | 310 | 40 | 377 | 549 | 424 |
| PA4 | 107 | 22 | 170 | 344 | 1058 |

**HGB**

| true \ pred | BL1 | PA1 | PA2 | PA3 | PA4 |
|---|---:|---:|---:|---:|---:|
| BL1 | 774 | 54 | 368 | 343 | 129 |
| PA1 | 73 | 1485 | 65 | 40 | 8 |
| PA2 | 448 | 55 | 522 | 440 | 221 |
| PA3 | 288 | 42 | 389 | 562 | 419 |
| PA4 | 106 | 23 | 186 | 368 | 1018 |

All CIs resample subjects, not trials. The BL1-vs-any-pain accuracy uses a 0.5 threshold on 1 - P(BL1); pain trials are 80% of the sample, so AUC and balanced accuracy are the informative numbers.
