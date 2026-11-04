# BioVid Part B evaluation: 4-class, PA1 excluded, 175 features

LOSO over **86 subjects / 6755 trials**, unweighted classes, identical folds.

## Core results

| model | accuracy | macro-F1 | kappa (quadratic) | kappa (unweighted) | MAE | Spearman | within 1 level |
|---|---:|---:|---:|---:|---:|---:|---:|
| XGBoost | 0.4401 | 0.4368 | 0.4867 | 0.2534 | 0.7825 | 0.4907 | 0.8144 |
| HGB | 0.4346 | 0.4320 | 0.4848 | 0.2461 | 0.7873 | 0.4874 | 0.8136 |

## Subject-level bootstrap 95% CIs (2000 resamples)

| model | metric | point | 95% CI |
|---|---|---:|---|
| XGBoost | accuracy | 0.4401 | [0.4133, 0.4677] |
| XGBoost | macro_f1 | 0.4368 | [0.4113, 0.4626] |
| XGBoost | kappa_quadratic | 0.4867 | [0.4274, 0.5437] |
| XGBoost | kappa_unweighted | 0.2534 | [0.2176, 0.2901] |
| XGBoost | mae | 0.7825 | [0.7265, 0.8389] |
| XGBoost | spearman | 0.4907 | [0.4317, 0.5471] |
| XGBoost | within_one_level | 0.8144 | [0.7914, 0.8373] |
| HGB | accuracy | 0.4346 | [0.4058, 0.4638] |
| HGB | macro_f1 | 0.4320 | [0.4041, 0.4600] |
| HGB | kappa_quadratic | 0.4848 | [0.4271, 0.5401] |
| HGB | kappa_unweighted | 0.2461 | [0.2077, 0.2850] |
| HGB | mae | 0.7873 | [0.7301, 0.8451] |
| HGB | spearman | 0.4874 | [0.4305, 0.5425] |
| HGB | within_one_level | 0.8136 | [0.7906, 0.8367] |

## Paired bootstrap: XGBoost - HGB

| metric | delta | 95% CI | p (two-sided) |
|---|---:|---|---:|
| accuracy | +0.0055 | [-0.0043, +0.0154] | 0.270 |
| macro_f1 | +0.0047 | [-0.0048, +0.0146] | 0.339 |
| kappa_quadratic | +0.0020 | [-0.0110, +0.0150] | 0.768 |
| kappa_unweighted | +0.0073 | [-0.0057, +0.0205] | 0.281 |
| mae | -0.0048 | [-0.0193, +0.0086] | 0.510 |
| spearman | +0.0033 | [-0.0096, +0.0164] | 0.615 |
| within_one_level | +0.0008 | [-0.0059, +0.0074] | 0.796 |

## Binary tasks derived from the multiclass probabilities

| task | model | n | accuracy | balanced acc | AUC | sensitivity | specificity |
|---|---|---:|---:|---:|---:|---:|---:|
| BL1_vs_any_pain | XGBoost | 6755 | 0.7787 | 0.5948 | 0.7571 | 0.9581 | 0.2314 |
| BL1_vs_PA2 | XGBoost | 3354 | 0.5942 | 0.5940 | 0.6354 | 0.6311 | 0.5570 |
| BL1_vs_PA3 | XGBoost | 3368 | 0.6835 | 0.6832 | 0.7523 | 0.7182 | 0.6481 |
| BL1_vs_PA4 | XGBoost | 3369 | 0.8053 | 0.8054 | 0.8930 | 0.7972 | 0.8135 |
| BL1_vs_any_pain | HGB | 6755 | 0.7723 | 0.6000 | 0.7543 | 0.9404 | 0.2596 |
| BL1_vs_PA2 | HGB | 3354 | 0.5868 | 0.5866 | 0.6276 | 0.6115 | 0.5618 |
| BL1_vs_PA3 | HGB | 3368 | 0.6698 | 0.6696 | 0.7436 | 0.6976 | 0.6415 |
| BL1_vs_PA4 | HGB | 3369 | 0.8085 | 0.8086 | 0.8921 | 0.8013 | 0.8159 |

## Per-class metrics

| model | class | support | precision | recall | F1 | AUC (one-vs-rest) |
|---|---|---:|---:|---:|---:|---:|
| XGBoost | BL1 | 1668 | 0.4747 | 0.4670 | 0.4708 | 0.7571 |
| XGBoost | PA2 | 1686 | 0.3506 | 0.3084 | 0.3282 | 0.6428 |
| XGBoost | PA3 | 1700 | 0.3411 | 0.3529 | 0.3469 | 0.6323 |
| XGBoost | PA4 | 1701 | 0.5737 | 0.6314 | 0.6012 | 0.8272 |
| HGB | BL1 | 1668 | 0.4679 | 0.4628 | 0.4653 | 0.7543 |
| HGB | PA2 | 1686 | 0.3346 | 0.3072 | 0.3203 | 0.6318 |
| HGB | PA3 | 1700 | 0.3447 | 0.3500 | 0.3473 | 0.6229 |
| HGB | PA4 | 1701 | 0.5740 | 0.6179 | 0.5951 | 0.8249 |

## Confusion matrices (rows = true)


**XGBoost**

| true \ pred | BL1 | PA2 | PA3 | PA4 |
|---|---:|---:|---:|---:|
| BL1 | 779 | 409 | 338 | 142 |
| PA2 | 476 | 520 | 460 | 230 |
| PA3 | 278 | 396 | 600 | 426 |
| PA4 | 108 | 158 | 361 | 1074 |

**HGB**

| true \ pred | BL1 | PA2 | PA3 | PA4 |
|---|---:|---:|---:|---:|
| BL1 | 772 | 442 | 324 | 130 |
| PA2 | 487 | 518 | 446 | 235 |
| PA3 | 281 | 409 | 595 | 415 |
| PA4 | 110 | 179 | 361 | 1051 |

All CIs resample subjects, not trials. The BL1-vs-any-pain accuracy uses a 0.5 threshold on 1 - P(BL1); pain trials are 80% of the sample, so AUC and balanced accuracy are the informative numbers.
