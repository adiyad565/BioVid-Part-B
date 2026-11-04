# BioVid Part B evaluation: 4-class, PA1 excluded, no facial EMG

LOSO over **86 subjects / 6755 trials**, unweighted classes, identical folds.

## Core results

| model | accuracy | macro-F1 | kappa (quadratic) | kappa (unweighted) | MAE | Spearman | within 1 level |
|---|---:|---:|---:|---:|---:|---:|---:|
| XGBoost | 0.4084 | 0.4044 | 0.4271 | 0.2112 | 0.8520 | 0.4294 | 0.7871 |
| HGB | 0.4040 | 0.4016 | 0.4098 | 0.2053 | 0.8616 | 0.4119 | 0.7853 |

## Subject-level bootstrap 95% CIs (2000 resamples)

| model | metric | point | 95% CI |
|---|---|---:|---|
| XGBoost | accuracy | 0.4084 | [0.3790, 0.4390] |
| XGBoost | macro_f1 | 0.4044 | [0.3765, 0.4327] |
| XGBoost | kappa_quadratic | 0.4271 | [0.3638, 0.4862] |
| XGBoost | kappa_unweighted | 0.2112 | [0.1720, 0.2518] |
| XGBoost | mae | 0.8520 | [0.7918, 0.9126] |
| XGBoost | spearman | 0.4294 | [0.3667, 0.4885] |
| XGBoost | within_one_level | 0.7871 | [0.7630, 0.8111] |
| HGB | accuracy | 0.4040 | [0.3762, 0.4323] |
| HGB | macro_f1 | 0.4016 | [0.3746, 0.4288] |
| HGB | kappa_quadratic | 0.4098 | [0.3489, 0.4688] |
| HGB | kappa_unweighted | 0.2053 | [0.1681, 0.2429] |
| HGB | mae | 0.8616 | [0.8028, 0.9199] |
| HGB | spearman | 0.4119 | [0.3513, 0.4706] |
| HGB | within_one_level | 0.7853 | [0.7617, 0.8096] |

## Paired bootstrap: XGBoost - HGB

| metric | delta | 95% CI | p (two-sided) |
|---|---:|---|---:|
| accuracy | +0.0046 | [-0.0064, +0.0150] | 0.374 |
| macro_f1 | +0.0030 | [-0.0081, +0.0133] | 0.563 |
| kappa_quadratic | +0.0173 | [+0.0010, +0.0331] | 0.035 |
| kappa_unweighted | +0.0061 | [-0.0085, +0.0201] | 0.379 |
| mae | -0.0098 | [-0.0273, +0.0086] | 0.292 |
| spearman | +0.0176 | [+0.0016, +0.0333] | 0.029 |
| within_one_level | +0.0018 | [-0.0071, +0.0105] | 0.661 |

## Binary tasks derived from the multiclass probabilities

| task | model | n | accuracy | balanced acc | AUC | sensitivity | specificity |
|---|---|---:|---:|---:|---:|---:|---:|
| BL1_vs_any_pain | XGBoost | 6755 | 0.7779 | 0.5882 | 0.7386 | 0.9630 | 0.2134 |
| BL1_vs_PA2 | XGBoost | 3354 | 0.5909 | 0.5907 | 0.6358 | 0.6263 | 0.5552 |
| BL1_vs_PA3 | XGBoost | 3368 | 0.6600 | 0.6596 | 0.7245 | 0.7047 | 0.6145 |
| BL1_vs_PA4 | XGBoost | 3369 | 0.7664 | 0.7664 | 0.8607 | 0.7643 | 0.7686 |
| BL1_vs_any_pain | HGB | 6755 | 0.7720 | 0.5914 | 0.7341 | 0.9483 | 0.2344 |
| BL1_vs_PA2 | HGB | 3354 | 0.5927 | 0.5926 | 0.6321 | 0.6234 | 0.5618 |
| BL1_vs_PA3 | HGB | 3368 | 0.6496 | 0.6492 | 0.7190 | 0.6918 | 0.6067 |
| BL1_vs_PA4 | HGB | 3369 | 0.7619 | 0.7619 | 0.8526 | 0.7631 | 0.7608 |

## Per-class metrics

| model | class | support | precision | recall | F1 | AUC (one-vs-rest) |
|---|---|---:|---:|---:|---:|---:|
| XGBoost | BL1 | 1668 | 0.4540 | 0.4586 | 0.4563 | 0.7386 |
| XGBoost | PA2 | 1686 | 0.3296 | 0.2983 | 0.3132 | 0.6155 |
| XGBoost | PA3 | 1700 | 0.3031 | 0.2906 | 0.2967 | 0.5877 |
| XGBoost | PA4 | 1701 | 0.5209 | 0.5861 | 0.5516 | 0.7928 |
| HGB | BL1 | 1668 | 0.4454 | 0.4400 | 0.4427 | 0.7341 |
| HGB | PA2 | 1686 | 0.3227 | 0.2989 | 0.3103 | 0.6034 |
| HGB | PA3 | 1700 | 0.3099 | 0.3088 | 0.3094 | 0.5840 |
| HGB | PA4 | 1701 | 0.5219 | 0.5679 | 0.5439 | 0.7818 |

## Confusion matrices (rows = true)


**XGBoost**

| true \ pred | BL1 | PA2 | PA3 | PA4 |
|---|---:|---:|---:|---:|
| BL1 | 765 | 403 | 311 | 189 |
| PA2 | 456 | 503 | 453 | 274 |
| PA3 | 332 | 420 | 494 | 454 |
| PA4 | 132 | 200 | 372 | 997 |

**HGB**

| true \ pred | BL1 | PA2 | PA3 | PA4 |
|---|---:|---:|---:|---:|
| BL1 | 734 | 427 | 317 | 190 |
| PA2 | 441 | 504 | 471 | 270 |
| PA3 | 319 | 431 | 525 | 425 |
| PA4 | 154 | 200 | 381 | 966 |

All CIs resample subjects, not trials. The BL1-vs-any-pain accuracy uses a 0.5 threshold on 1 - P(BL1); pain trials are 80% of the sample, so AUC and balanced accuracy are the informative numbers.
