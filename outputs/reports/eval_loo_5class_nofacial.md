# BioVid Part B evaluation: 5-class, leave-one-out template, no facial EMG

LOSO over **86 subjects / 8426 trials**, unweighted classes, identical folds.

## Core results

| model | accuracy | macro-F1 | kappa (quadratic) | kappa (unweighted) | MAE | Spearman | within 1 level |
|---|---:|---:|---:|---:|---:|---:|---:|
| XGBoost | 0.3271 | 0.3200 | 0.3918 | 0.1588 | 1.1581 | 0.3954 | 0.6844 |
| HGB | 0.3202 | 0.3154 | 0.3778 | 0.1501 | 1.1703 | 0.3818 | 0.6810 |

## Subject-level bootstrap 95% CIs (2000 resamples)

| model | metric | point | 95% CI |
|---|---|---:|---|
| XGBoost | accuracy | 0.3271 | [0.3050, 0.3504] |
| XGBoost | macro_f1 | 0.3200 | [0.2989, 0.3416] |
| XGBoost | kappa_quadratic | 0.3918 | [0.3329, 0.4498] |
| XGBoost | kappa_unweighted | 0.1588 | [0.1311, 0.1879] |
| XGBoost | mae | 1.1581 | [1.0876, 1.2283] |
| XGBoost | spearman | 0.3954 | [0.3360, 0.4530] |
| XGBoost | within_one_level | 0.6844 | [0.6576, 0.7121] |
| HGB | accuracy | 0.3202 | [0.2981, 0.3429] |
| HGB | macro_f1 | 0.3154 | [0.2938, 0.3370] |
| HGB | kappa_quadratic | 0.3778 | [0.3190, 0.4368] |
| HGB | kappa_unweighted | 0.1501 | [0.1226, 0.1785] |
| HGB | mae | 1.1703 | [1.0991, 1.2399] |
| HGB | spearman | 0.3818 | [0.3229, 0.4412] |
| HGB | within_one_level | 0.6810 | [0.6553, 0.7080] |

## Paired bootstrap: XGBoost - HGB

| metric | delta | 95% CI | p (two-sided) |
|---|---:|---|---:|
| accuracy | +0.0067 | [-0.0005, +0.0148] | 0.062 |
| macro_f1 | +0.0045 | [-0.0029, +0.0126] | 0.258 |
| kappa_quadratic | +0.0139 | [+0.0001, +0.0282] | 0.049 |
| kappa_unweighted | +0.0084 | [-0.0006, +0.0185] | 0.065 |
| mae | -0.0120 | [-0.0294, +0.0039] | 0.158 |
| spearman | +0.0135 | [-0.0002, +0.0278] | 0.056 |
| within_one_level | +0.0034 | [-0.0040, +0.0105] | 0.335 |

## Binary tasks derived from the multiclass probabilities

| task | model | n | accuracy | balanced acc | AUC | sensitivity | specificity |
|---|---|---:|---:|---:|---:|---:|---:|
| BL1_vs_any_pain | XGBoost | 8426 | 0.8090 | 0.5357 | 0.6975 | 0.9882 | 0.0833 |
| BL1_vs_PA1 | XGBoost | 3339 | 0.5642 | 0.5642 | 0.5914 | 0.5793 | 0.5492 |
| BL1_vs_PA2 | XGBoost | 3354 | 0.5844 | 0.5842 | 0.6311 | 0.6103 | 0.5582 |
| BL1_vs_PA3 | XGBoost | 3368 | 0.6529 | 0.6526 | 0.7272 | 0.6818 | 0.6235 |
| BL1_vs_PA4 | XGBoost | 3369 | 0.7717 | 0.7718 | 0.8582 | 0.7678 | 0.7758 |
| BL1_vs_any_pain | HGB | 8426 | 0.8049 | 0.5402 | 0.6947 | 0.9784 | 0.1019 |
| BL1_vs_PA1 | HGB | 3339 | 0.5508 | 0.5508 | 0.5794 | 0.5595 | 0.5420 |
| BL1_vs_PA2 | HGB | 3354 | 0.5844 | 0.5843 | 0.6243 | 0.6050 | 0.5635 |
| BL1_vs_PA3 | HGB | 3368 | 0.6594 | 0.6592 | 0.7270 | 0.6847 | 0.6337 |
| BL1_vs_PA4 | HGB | 3369 | 0.7622 | 0.7623 | 0.8560 | 0.7607 | 0.7638 |

## Per-class metrics

| model | class | support | precision | recall | F1 | AUC (one-vs-rest) |
|---|---|---:|---:|---:|---:|---:|
| XGBoost | BL1 | 1668 | 0.3612 | 0.3657 | 0.3634 | 0.6975 |
| XGBoost | PA1 | 1671 | 0.2707 | 0.2705 | 0.2706 | 0.6305 |
| XGBoost | PA2 | 1686 | 0.2167 | 0.1679 | 0.1892 | 0.5668 |
| XGBoost | PA3 | 1700 | 0.2656 | 0.2682 | 0.2669 | 0.6096 |
| XGBoost | PA4 | 1701 | 0.4672 | 0.5614 | 0.5100 | 0.7994 |
| HGB | BL1 | 1668 | 0.3522 | 0.3507 | 0.3515 | 0.6947 |
| HGB | PA1 | 1671 | 0.2460 | 0.2400 | 0.2430 | 0.6137 |
| HGB | PA2 | 1686 | 0.2336 | 0.1922 | 0.2109 | 0.5577 |
| HGB | PA3 | 1700 | 0.2650 | 0.2800 | 0.2723 | 0.6064 |
| HGB | PA4 | 1701 | 0.4672 | 0.5362 | 0.4993 | 0.7930 |

## Confusion matrices (rows = true)


**XGBoost**

| true \ pred | BL1 | PA1 | PA2 | PA3 | PA4 |
|---|---:|---:|---:|---:|---:|
| BL1 | 610 | 385 | 241 | 251 | 181 |
| PA1 | 409 | 452 | 326 | 267 | 217 |
| PA2 | 328 | 411 | 283 | 395 | 269 |
| PA3 | 230 | 277 | 315 | 456 | 422 |
| PA4 | 112 | 145 | 141 | 348 | 955 |

**HGB**

| true \ pred | BL1 | PA1 | PA2 | PA3 | PA4 |
|---|---:|---:|---:|---:|---:|
| BL1 | 585 | 392 | 262 | 257 | 172 |
| PA1 | 417 | 401 | 344 | 299 | 210 |
| PA2 | 314 | 396 | 324 | 412 | 240 |
| PA3 | 227 | 270 | 309 | 476 | 418 |
| PA4 | 118 | 171 | 148 | 352 | 912 |

All CIs resample subjects, not trials. The BL1-vs-any-pain accuracy uses a 0.5 threshold on 1 - P(BL1); pain trials are 80% of the sample, so AUC and balanced accuracy are the informative numbers.
