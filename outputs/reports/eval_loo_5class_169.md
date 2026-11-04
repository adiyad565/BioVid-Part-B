# BioVid Part B evaluation: 5-class, leave-one-out template, 169 features (no facial similarity)

LOSO over **86 subjects / 8426 trials**, unweighted classes, identical folds.

## Core results

| model | accuracy | macro-F1 | kappa (quadratic) | kappa (unweighted) | MAE | Spearman | within 1 level |
|---|---:|---:|---:|---:|---:|---:|---:|
| XGBoost | 0.3604 | 0.3541 | 0.4513 | 0.2004 | 1.0701 | 0.4584 | 0.7091 |
| HGB | 0.3509 | 0.3465 | 0.4307 | 0.1885 | 1.0910 | 0.4377 | 0.7010 |

## Subject-level bootstrap 95% CIs (2000 resamples)

| model | metric | point | 95% CI |
|---|---|---:|---|
| XGBoost | accuracy | 0.3604 | [0.3357, 0.3849] |
| XGBoost | macro_f1 | 0.3541 | [0.3307, 0.3773] |
| XGBoost | kappa_quadratic | 0.4513 | [0.3928, 0.5074] |
| XGBoost | kappa_unweighted | 0.2004 | [0.1695, 0.2309] |
| XGBoost | mae | 1.0701 | [0.9998, 1.1403] |
| XGBoost | spearman | 0.4584 | [0.3999, 0.5137] |
| XGBoost | within_one_level | 0.7091 | [0.6836, 0.7356] |
| HGB | accuracy | 0.3509 | [0.3269, 0.3759] |
| HGB | macro_f1 | 0.3465 | [0.3234, 0.3701] |
| HGB | kappa_quadratic | 0.4307 | [0.3729, 0.4851] |
| HGB | kappa_unweighted | 0.1885 | [0.1584, 0.2198] |
| HGB | mae | 1.0910 | [1.0231, 1.1606] |
| HGB | spearman | 0.4377 | [0.3806, 0.4917] |
| HGB | within_one_level | 0.7010 | [0.6755, 0.7276] |

## Paired bootstrap: XGBoost - HGB

| metric | delta | 95% CI | p (two-sided) |
|---|---:|---|---:|
| accuracy | +0.0094 | [+0.0014, +0.0173] | 0.020 |
| macro_f1 | +0.0075 | [-0.0005, +0.0156] | 0.072 |
| kappa_quadratic | +0.0207 | [+0.0087, +0.0329] | 0.002 |
| kappa_unweighted | +0.0118 | [+0.0018, +0.0217] | 0.020 |
| mae | -0.0209 | [-0.0380, -0.0032] | 0.014 |
| spearman | +0.0206 | [+0.0090, +0.0327] | 0.001 |
| within_one_level | +0.0081 | [-0.0002, +0.0162] | 0.058 |

## Binary tasks derived from the multiclass probabilities

| task | model | n | accuracy | balanced acc | AUC | sensitivity | specificity |
|---|---|---:|---:|---:|---:|---:|---:|
| BL1_vs_any_pain | XGBoost | 8426 | 0.8096 | 0.5381 | 0.7199 | 0.9876 | 0.0887 |
| BL1_vs_PA1 | XGBoost | 3339 | 0.5843 | 0.5843 | 0.6144 | 0.5895 | 0.5791 |
| BL1_vs_PA2 | XGBoost | 3354 | 0.5972 | 0.5970 | 0.6417 | 0.6251 | 0.5689 |
| BL1_vs_PA3 | XGBoost | 3368 | 0.6838 | 0.6835 | 0.7574 | 0.7094 | 0.6577 |
| BL1_vs_PA4 | XGBoost | 3369 | 0.8091 | 0.8093 | 0.8930 | 0.7895 | 0.8291 |
| BL1_vs_any_pain | HGB | 8426 | 0.8103 | 0.5463 | 0.7179 | 0.9834 | 0.1091 |
| BL1_vs_PA1 | HGB | 3339 | 0.5714 | 0.5714 | 0.6037 | 0.5835 | 0.5594 |
| BL1_vs_PA2 | HGB | 3354 | 0.5921 | 0.5920 | 0.6398 | 0.6192 | 0.5647 |
| BL1_vs_PA3 | HGB | 3368 | 0.6802 | 0.6800 | 0.7514 | 0.7076 | 0.6523 |
| BL1_vs_PA4 | HGB | 3369 | 0.7991 | 0.7992 | 0.8865 | 0.7795 | 0.8189 |

## Per-class metrics

| model | class | support | precision | recall | F1 | AUC (one-vs-rest) |
|---|---|---:|---:|---:|---:|---:|
| XGBoost | BL1 | 1668 | 0.3855 | 0.3783 | 0.3818 | 0.7199 |
| XGBoost | PA1 | 1671 | 0.2997 | 0.2867 | 0.2931 | 0.6583 |
| XGBoost | PA2 | 1686 | 0.2377 | 0.1916 | 0.2122 | 0.5915 |
| XGBoost | PA3 | 1700 | 0.2977 | 0.3265 | 0.3114 | 0.6440 |
| XGBoost | PA4 | 1701 | 0.5330 | 0.6167 | 0.5718 | 0.8342 |
| HGB | BL1 | 1668 | 0.3823 | 0.3543 | 0.3678 | 0.7179 |
| HGB | PA1 | 1671 | 0.2845 | 0.2729 | 0.2786 | 0.6406 |
| HGB | PA2 | 1686 | 0.2402 | 0.2064 | 0.2220 | 0.5856 |
| HGB | PA3 | 1700 | 0.2894 | 0.3253 | 0.3063 | 0.6357 |
| HGB | PA4 | 1701 | 0.5263 | 0.5932 | 0.5578 | 0.8254 |

## Confusion matrices (rows = true)


**XGBoost**

| true \ pred | BL1 | PA1 | PA2 | PA3 | PA4 |
|---|---:|---:|---:|---:|---:|
| BL1 | 631 | 359 | 278 | 273 | 127 |
| PA1 | 383 | 479 | 343 | 308 | 158 |
| PA2 | 323 | 424 | 323 | 391 | 225 |
| PA3 | 219 | 225 | 292 | 555 | 409 |
| PA4 | 81 | 111 | 123 | 337 | 1049 |

**HGB**

| true \ pred | BL1 | PA1 | PA2 | PA3 | PA4 |
|---|---:|---:|---:|---:|---:|
| BL1 | 591 | 371 | 294 | 288 | 124 |
| PA1 | 364 | 456 | 352 | 327 | 172 |
| PA2 | 299 | 418 | 348 | 396 | 225 |
| PA3 | 209 | 236 | 315 | 553 | 387 |
| PA4 | 83 | 122 | 140 | 347 | 1009 |

All CIs resample subjects, not trials. The BL1-vs-any-pain accuracy uses a 0.5 threshold on 1 - P(BL1); pain trials are 80% of the sample, so AUC and balanced accuracy are the informative numbers.
