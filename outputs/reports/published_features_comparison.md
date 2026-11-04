# Our features vs the published Gruss et al. (2015) features

84 subjects present in both sources, 8226 trials retained by our quality filter; identical LOSO folds, within-subject z-score and models for both feature sets. Deltas are ours minus published, with 95% CIs from 2000 paired subject-level bootstrap resamples.

| task | features (ours / published) | model | ours accuracy [95% CI] | published accuracy [95% CI] | delta | 95% CI | p | AUC ours / published |
|---|---|---|---|---|---:|---|---:|---|
| 5-class, facial EMG without facial similarity | 169 / 147 | XGBoost | 0.3549 [0.333, 0.379] | 0.3906 [0.369, 0.413] | -0.0357 | [-0.051, -0.019] | 0.000 | 0.684 / 0.714 |
| 5-class, facial EMG without facial similarity | 169 / 147 | HGB | 0.3530 [0.331, 0.377] | 0.3848 [0.365, 0.406] | -0.0317 | [-0.046, -0.017] | 0.000 | 0.678 / 0.707 |
| 5-class, facial EMG without facial similarity | 169 / 147 | LogReg | 0.3364 [0.315, 0.358] | 0.3762 [0.358, 0.395] | -0.0399 | [-0.056, -0.024] | 0.000 | 0.662 / 0.698 |
| 5-class, facial EMG without facial similarity | 169 / 147 | SVM-RBF | 0.3369 [0.315, 0.359] | 0.3823 [0.363, 0.402] | -0.0455 | [-0.059, -0.032] | 0.000 | 0.657 / 0.684 |
| 4-class (BL1, PA2-PA4), all features | 175 / 159 | XGBoost | 0.4323 [0.406, 0.462] | 0.5333 [0.511, 0.556] | -0.1010 | [-0.120, -0.081] | 0.000 | 0.712 / 0.792 |
| 4-class (BL1, PA2-PA4), all features | 175 / 159 | HGB | 0.4379 [0.411, 0.467] | 0.5295 [0.508, 0.551] | -0.0916 | [-0.110, -0.073] | 0.000 | 0.709 / 0.788 |
| 4-class (BL1, PA2-PA4), all features | 175 / 159 | LogReg | 0.4156 [0.392, 0.442] | 0.5155 [0.494, 0.536] | -0.0999 | [-0.119, -0.080] | 0.000 | 0.685 / 0.775 |
| 4-class (BL1, PA2-PA4), all features | 175 / 159 | SVM-RBF | 0.4167 [0.391, 0.446] | 0.5222 [0.501, 0.543] | -0.1055 | [-0.123, -0.086] | 0.000 | 0.684 / 0.763 |
| BL1 vs PA1, facial EMG without facial similarity | 169 / 147 | XGBoost | 0.5428 [0.521, 0.565] | 0.7039 [0.678, 0.730] | -0.1611 | [-0.191, -0.130] | 0.000 | 0.573 / 0.790 |
| BL1 vs PA1, facial EMG without facial similarity | 169 / 147 | HGB | 0.5646 [0.543, 0.587] | 0.7057 [0.680, 0.730] | -0.1411 | [-0.175, -0.109] | 0.000 | 0.586 / 0.789 |
| BL1 vs PA1, facial EMG without facial similarity | 169 / 147 | LogReg | 0.5526 [0.530, 0.575] | 0.7128 [0.688, 0.737] | -0.1602 | [-0.189, -0.130] | 0.000 | 0.573 / 0.785 |
| BL1 vs PA1, facial EMG without facial similarity | 169 / 147 | SVM-RBF | 0.5545 [0.534, 0.576] | 0.6941 [0.672, 0.715] | -0.1396 | [-0.166, -0.112] | 0.000 | 0.586 / 0.761 |
| BL1 vs PA2, facial EMG without facial similarity | 169 / 147 | XGBoost | 0.5880 [0.560, 0.617] | 0.7071 [0.679, 0.734] | -0.1191 | [-0.153, -0.084] | 0.000 | 0.629 / 0.801 |
| BL1 vs PA2, facial EMG without facial similarity | 169 / 147 | HGB | 0.5776 [0.549, 0.608] | 0.7138 [0.685, 0.741] | -0.1362 | [-0.172, -0.100] | 0.000 | 0.616 / 0.801 |
| BL1 vs PA2, facial EMG without facial similarity | 169 / 147 | LogReg | 0.5834 [0.556, 0.613] | 0.7101 [0.683, 0.736] | -0.1268 | [-0.161, -0.090] | 0.000 | 0.614 / 0.792 |
| BL1 vs PA2, facial EMG without facial similarity | 169 / 147 | SVM-RBF | 0.5773 [0.552, 0.604] | 0.6891 [0.665, 0.713] | -0.1118 | [-0.140, -0.082] | 0.000 | 0.616 / 0.763 |
| BL1 vs PA3, facial EMG without facial similarity | 169 / 147 | XGBoost | 0.6685 [0.634, 0.703] | 0.7789 [0.755, 0.804] | -0.1104 | [-0.140, -0.078] | 0.000 | 0.747 / 0.861 |
| BL1 vs PA3, facial EMG without facial similarity | 169 / 147 | HGB | 0.6685 [0.633, 0.705] | 0.7734 [0.749, 0.799] | -0.1049 | [-0.137, -0.072] | 0.000 | 0.750 / 0.859 |
| BL1 vs PA3, facial EMG without facial similarity | 169 / 147 | LogReg | 0.6575 [0.624, 0.691] | 0.7616 [0.737, 0.787] | -0.1040 | [-0.135, -0.072] | 0.000 | 0.719 / 0.842 |
| BL1 vs PA3, facial EMG without facial similarity | 169 / 147 | SVM-RBF | 0.6645 [0.630, 0.700] | 0.7512 [0.725, 0.778] | -0.0867 | [-0.113, -0.060] | 0.000 | 0.734 / 0.831 |
| BL1 vs PA4, facial EMG without facial similarity | 169 / 147 | XGBoost | 0.7996 [0.764, 0.835] | 0.8577 [0.833, 0.883] | -0.0581 | [-0.079, -0.037] | 0.000 | 0.897 / 0.934 |
| BL1 vs PA4, facial EMG without facial similarity | 169 / 147 | HGB | 0.8069 [0.773, 0.841] | 0.8580 [0.832, 0.883] | -0.0511 | [-0.074, -0.030] | 0.000 | 0.896 / 0.933 |
| BL1 vs PA4, facial EMG without facial similarity | 169 / 147 | LogReg | 0.7881 [0.755, 0.821] | 0.8361 [0.809, 0.864] | -0.0480 | [-0.071, -0.025] | 0.000 | 0.871 / 0.919 |
| BL1 vs PA4, facial EMG without facial similarity | 169 / 147 | SVM-RBF | 0.7948 [0.763, 0.828] | 0.8419 [0.815, 0.870] | -0.0471 | [-0.067, -0.027] | 0.000 | 0.884 / 0.919 |
| 5-class, no facial EMG | 113 / 81 | XGBoost | 0.3262 [0.303, 0.351] | 0.3640 [0.345, 0.384] | -0.0378 | [-0.054, -0.021] | 0.000 | 0.659 / 0.689 |
| 5-class, no facial EMG | 113 / 81 | HGB | 0.3225 [0.302, 0.345] | 0.3585 [0.341, 0.377] | -0.0360 | [-0.050, -0.021] | 0.000 | 0.652 / 0.679 |
| 5-class, no facial EMG | 113 / 81 | LogReg | 0.3151 [0.294, 0.337] | 0.3564 [0.339, 0.377] | -0.0413 | [-0.058, -0.024] | 0.000 | 0.634 / 0.673 |
| 5-class, no facial EMG | 113 / 81 | SVM-RBF | 0.3129 [0.290, 0.336] | 0.3527 [0.333, 0.372] | -0.0398 | [-0.055, -0.023] | 0.000 | 0.631 / 0.656 |
| 4-class (BL1, PA2-PA4), no facial EMG | 113 / 81 | XGBoost | 0.4033 [0.376, 0.434] | 0.4494 [0.430, 0.470] | -0.0461 | [-0.067, -0.025] | 0.000 | 0.683 / 0.720 |
| 4-class (BL1, PA2-PA4), no facial EMG | 113 / 81 | HGB | 0.4002 [0.373, 0.429] | 0.4458 [0.425, 0.467] | -0.0456 | [-0.066, -0.025] | 0.000 | 0.676 / 0.717 |
| 4-class (BL1, PA2-PA4), no facial EMG | 113 / 81 | LogReg | 0.3861 [0.361, 0.412] | 0.4314 [0.411, 0.453] | -0.0453 | [-0.067, -0.023] | 0.000 | 0.653 / 0.700 |
| 4-class (BL1, PA2-PA4), no facial EMG | 113 / 81 | SVM-RBF | 0.3912 [0.365, 0.419] | 0.4355 [0.413, 0.458] | -0.0443 | [-0.063, -0.023] | 0.000 | 0.655 / 0.689 |
| BL1 vs PA1, no facial EMG | 113 / 81 | XGBoost | 0.5489 [0.528, 0.570] | 0.7002 [0.675, 0.724] | -0.1513 | [-0.180, -0.121] | 0.000 | 0.567 / 0.784 |
| BL1 vs PA1, no facial EMG | 113 / 81 | HGB | 0.5569 [0.537, 0.577] | 0.6993 [0.674, 0.723] | -0.1424 | [-0.173, -0.111] | 0.000 | 0.580 / 0.784 |
| BL1 vs PA1, no facial EMG | 113 / 81 | LogReg | 0.5489 [0.526, 0.571] | 0.7110 [0.685, 0.736] | -0.1620 | [-0.190, -0.131] | 0.000 | 0.573 / 0.789 |
| BL1 vs PA1, no facial EMG | 113 / 81 | SVM-RBF | 0.5477 [0.528, 0.567] | 0.6984 [0.673, 0.722] | -0.1507 | [-0.177, -0.123] | 0.000 | 0.562 / 0.764 |
| BL1 vs PA2, no facial EMG | 113 / 81 | XGBoost | 0.5907 [0.564, 0.620] | 0.7156 [0.689, 0.741] | -0.1249 | [-0.157, -0.091] | 0.000 | 0.625 / 0.803 |
| BL1 vs PA2, no facial EMG | 113 / 81 | HGB | 0.5892 [0.562, 0.618] | 0.7169 [0.690, 0.743] | -0.1277 | [-0.160, -0.094] | 0.000 | 0.619 / 0.797 |
| BL1 vs PA2, no facial EMG | 113 / 81 | LogReg | 0.5803 [0.554, 0.610] | 0.7117 [0.684, 0.738] | -0.1313 | [-0.167, -0.092] | 0.000 | 0.612 / 0.795 |
| BL1 vs PA2, no facial EMG | 113 / 81 | SVM-RBF | 0.5773 [0.553, 0.604] | 0.7062 [0.684, 0.728] | -0.1289 | [-0.159, -0.098] | 0.000 | 0.619 / 0.776 |
| BL1 vs PA3, no facial EMG | 113 / 81 | XGBoost | 0.6460 [0.612, 0.681] | 0.7570 [0.732, 0.784] | -0.1110 | [-0.145, -0.076] | 0.000 | 0.714 / 0.845 |
| BL1 vs PA3, no facial EMG | 113 / 81 | HGB | 0.6457 [0.610, 0.681] | 0.7533 [0.729, 0.781] | -0.1077 | [-0.141, -0.073] | 0.000 | 0.711 / 0.843 |
| BL1 vs PA3, no facial EMG | 113 / 81 | LogReg | 0.6387 [0.604, 0.675] | 0.7518 [0.724, 0.781] | -0.1131 | [-0.148, -0.075] | 0.000 | 0.695 / 0.832 |
| BL1 vs PA3, no facial EMG | 113 / 81 | SVM-RBF | 0.6399 [0.603, 0.677] | 0.7384 [0.712, 0.765] | -0.0985 | [-0.131, -0.064] | 0.000 | 0.706 / 0.823 |
| BL1 vs PA4, no facial EMG | 113 / 81 | XGBoost | 0.7516 [0.712, 0.790] | 0.8197 [0.795, 0.845] | -0.0681 | [-0.097, -0.041] | 0.000 | 0.851 / 0.910 |
| BL1 vs PA4, no facial EMG | 113 / 81 | HGB | 0.7565 [0.717, 0.794] | 0.8148 [0.791, 0.840] | -0.0584 | [-0.089, -0.030] | 0.000 | 0.850 / 0.907 |
| BL1 vs PA4, no facial EMG | 113 / 81 | LogReg | 0.7458 [0.709, 0.783] | 0.8085 [0.781, 0.835] | -0.0626 | [-0.091, -0.033] | 0.000 | 0.824 / 0.890 |
| BL1 vs PA4, no facial EMG | 113 / 81 | SVM-RBF | 0.7476 [0.709, 0.785] | 0.8027 [0.775, 0.830] | -0.0550 | [-0.081, -0.028] | 0.000 | 0.840 / 0.887 |
| 5-class, no facial EMG, no similarity features | 102 / 69 | XGBoost | 0.3220 [0.300, 0.347] | 0.2887 [0.268, 0.310] | +0.0333 | [+0.020, +0.048] | 0.000 | 0.658 / 0.618 |
| 5-class, no facial EMG, no similarity features | 102 / 69 | HGB | 0.3191 [0.296, 0.343] | 0.2853 [0.264, 0.307] | +0.0338 | [+0.020, +0.048] | 0.000 | 0.651 / 0.607 |
| 5-class, no facial EMG, no similarity features | 102 / 69 | LogReg | 0.3100 [0.289, 0.331] | 0.2886 [0.269, 0.308] | +0.0214 | [+0.009, +0.034] | 0.000 | 0.633 / 0.606 |
| 5-class, no facial EMG, no similarity features | 102 / 69 | SVM-RBF | 0.3072 [0.284, 0.330] | 0.2785 [0.257, 0.299] | +0.0287 | [+0.015, +0.043] | 0.000 | 0.630 / 0.592 |
| 4-class (BL1, PA2-PA4), no facial EMG, no similarity features | 102 / 69 | XGBoost | 0.4042 [0.376, 0.434] | 0.3548 [0.329, 0.381] | +0.0494 | [+0.033, +0.066] | 0.000 | 0.679 / 0.635 |
| 4-class (BL1, PA2-PA4), no facial EMG, no similarity features | 102 / 69 | HGB | 0.4050 [0.378, 0.434] | 0.3553 [0.331, 0.381] | +0.0497 | [+0.032, +0.068] | 0.000 | 0.676 / 0.633 |
| 4-class (BL1, PA2-PA4), no facial EMG, no similarity features | 102 / 69 | LogReg | 0.3806 [0.356, 0.406] | 0.3554 [0.331, 0.381] | +0.0252 | [+0.009, +0.041] | 0.001 | 0.650 / 0.617 |
| 4-class (BL1, PA2-PA4), no facial EMG, no similarity features | 102 / 69 | SVM-RBF | 0.3865 [0.361, 0.412] | 0.3480 [0.322, 0.374] | +0.0385 | [+0.019, +0.056] | 0.000 | 0.651 / 0.611 |
| BL1 vs PA1, no facial EMG, no similarity features | 102 / 69 | XGBoost | 0.5336 [0.510, 0.557] | 0.5198 [0.501, 0.539] | +0.0138 | [-0.012, +0.039] | 0.289 | 0.550 / 0.530 |
| BL1 vs PA1, no facial EMG, no similarity features | 102 / 69 | HGB | 0.5437 [0.520, 0.568] | 0.5216 [0.501, 0.544] | +0.0221 | [-0.005, +0.048] | 0.103 | 0.559 / 0.539 |
| BL1 vs PA1, no facial EMG, no similarity features | 102 / 69 | LogReg | 0.5545 [0.532, 0.576] | 0.5379 [0.519, 0.557] | +0.0166 | [-0.006, +0.039] | 0.156 | 0.573 / 0.549 |
| BL1 vs PA1, no facial EMG, no similarity features | 102 / 69 | SVM-RBF | 0.5336 [0.513, 0.555] | 0.5397 [0.523, 0.556] | -0.0061 | [-0.028, +0.018] | 0.557 | 0.560 / 0.554 |
| BL1 vs PA2, no facial EMG, no similarity features | 102 / 69 | XGBoost | 0.5874 [0.561, 0.614] | 0.5480 [0.526, 0.573] | +0.0394 | [+0.017, +0.063] | 0.001 | 0.622 / 0.571 |
| BL1 vs PA2, no facial EMG, no similarity features | 102 / 69 | HGB | 0.5855 [0.560, 0.614] | 0.5577 [0.536, 0.582] | +0.0278 | [+0.007, +0.049] | 0.015 | 0.615 / 0.572 |
| BL1 vs PA2, no facial EMG, no similarity features | 102 / 69 | LogReg | 0.5773 [0.550, 0.605] | 0.5443 [0.520, 0.571] | +0.0330 | [+0.012, +0.054] | 0.005 | 0.606 / 0.560 |
| BL1 vs PA2, no facial EMG, no similarity features | 102 / 69 | SVM-RBF | 0.5773 [0.553, 0.604] | 0.5425 [0.521, 0.566] | +0.0348 | [+0.016, +0.054] | 0.000 | 0.615 / 0.555 |
| BL1 vs PA3, no facial EMG, no similarity features | 102 / 69 | XGBoost | 0.6509 [0.616, 0.686] | 0.6122 [0.583, 0.644] | +0.0386 | [+0.015, +0.062] | 0.001 | 0.713 / 0.656 |
| BL1 vs PA3, no facial EMG, no similarity features | 102 / 69 | HGB | 0.6302 [0.595, 0.667] | 0.5988 [0.568, 0.633] | +0.0313 | [+0.005, +0.058] | 0.015 | 0.700 / 0.647 |
| BL1 vs PA3, no facial EMG, no similarity features | 102 / 69 | LogReg | 0.6253 [0.591, 0.661] | 0.5979 [0.566, 0.631] | +0.0274 | [+0.004, +0.052] | 0.030 | 0.684 / 0.630 |
| BL1 vs PA3, no facial EMG, no similarity features | 102 / 69 | SVM-RBF | 0.6372 [0.601, 0.674] | 0.5988 [0.569, 0.630] | +0.0383 | [+0.014, +0.063] | 0.004 | 0.701 / 0.647 |
| BL1 vs PA4, no facial EMG, no similarity features | 102 / 69 | XGBoost | 0.7516 [0.713, 0.789] | 0.7078 [0.667, 0.746] | +0.0438 | [+0.017, +0.072] | 0.002 | 0.845 / 0.790 |
| BL1 vs PA4, no facial EMG, no similarity features | 102 / 69 | HGB | 0.7476 [0.710, 0.784] | 0.7072 [0.669, 0.745] | +0.0404 | [+0.012, +0.069] | 0.004 | 0.840 / 0.796 |
| BL1 vs PA4, no facial EMG, no similarity features | 102 / 69 | LogReg | 0.7385 [0.703, 0.775] | 0.6969 [0.659, 0.733] | +0.0417 | [+0.020, +0.064] | 0.001 | 0.816 / 0.761 |
| BL1 vs PA4, no facial EMG, no similarity features | 102 / 69 | SVM-RBF | 0.7449 [0.709, 0.780] | 0.6838 [0.646, 0.721] | +0.0611 | [+0.037, +0.085] | 0.000 | 0.831 / 0.761 |

## Protocol: random 75/25 trial split vs LOSO

Gruss et al. (2015) reported 79.29% (BL1 vs PA1), 84.94% (BL1 vs PA3) and 90.94% (BL1 vs PA4) with an RBF-SVM, a random 75/25 split and forward feature selection. The same split protocol (5 repeats, no feature selection):

| task | features | model | random_split_acc | random_split_sd | loso_acc | published_acc | split_minus_loso |
|---|---|---|---|---|---|---|---|
| 5class | ours | xgb | 0.3544 | 0.0072 | 0.3549 | nan | -0.0005 |
| 5class | ours | hgb | 0.3492 | 0.0082 | 0.3530 | nan | -0.0038 |
| 5class | ours | logreg | 0.3368 | 0.0140 | 0.3364 | nan | 0.0004 |
| 5class | ours | svm | 0.3324 | 0.0077 | 0.3369 | nan | -0.0044 |
| 5class | plos | xgb | 0.3921 | 0.0064 | 0.3906 | nan | 0.0015 |
| 5class | plos | hgb | 0.3905 | 0.0111 | 0.3848 | nan | 0.0057 |
| 5class | plos | logreg | 0.3809 | 0.0069 | 0.3762 | nan | 0.0047 |
| 5class | plos | svm | 0.3890 | 0.0108 | 0.3823 | nan | 0.0067 |
| bl1_vs_pa1 | ours | xgb | 0.5077 | 0.0141 | 0.5428 | 0.7929 | -0.0351 |
| bl1_vs_pa1 | ours | hgb | 0.5301 | 0.0162 | 0.5646 | 0.7929 | -0.0345 |
| bl1_vs_pa1 | ours | logreg | 0.5274 | 0.0192 | 0.5526 | 0.7929 | -0.0253 |
| bl1_vs_pa1 | ours | svm | 0.4979 | 0.0139 | 0.5545 | 0.7929 | -0.0566 |
| bl1_vs_pa1 | plos | xgb | 0.7004 | 0.0136 | 0.7039 | 0.7929 | -0.0035 |
| bl1_vs_pa1 | plos | hgb | 0.6979 | 0.0179 | 0.7057 | 0.7929 | -0.0078 |
| bl1_vs_pa1 | plos | logreg | 0.7156 | 0.0125 | 0.7128 | 0.7929 | 0.0028 |
| bl1_vs_pa1 | plos | svm | 0.6790 | 0.0176 | 0.6941 | 0.7929 | -0.0151 |
| bl1_vs_pa3 | ours | xgb | 0.6925 | 0.0160 | 0.6685 | 0.8494 | 0.0240 |
| bl1_vs_pa3 | ours | hgb | 0.6932 | 0.0164 | 0.6685 | 0.8494 | 0.0247 |
| bl1_vs_pa3 | ours | logreg | 0.6815 | 0.0158 | 0.6575 | 0.8494 | 0.0240 |
| bl1_vs_pa3 | ours | svm | 0.6912 | 0.0075 | 0.6645 | 0.8494 | 0.0267 |
| bl1_vs_pa3 | plos | xgb | 0.7791 | 0.0048 | 0.7789 | 0.8494 | 0.0002 |
| bl1_vs_pa3 | plos | hgb | 0.7810 | 0.0085 | 0.7734 | 0.8494 | 0.0076 |
| bl1_vs_pa3 | plos | logreg | 0.7740 | 0.0228 | 0.7616 | 0.8494 | 0.0124 |
| bl1_vs_pa3 | plos | svm | 0.7635 | 0.0148 | 0.7512 | 0.8494 | 0.0123 |
| bl1_vs_pa4 | ours | xgb | 0.8104 | 0.0150 | 0.7996 | 0.9094 | 0.0108 |
| bl1_vs_pa4 | ours | hgb | 0.8122 | 0.0119 | 0.8069 | 0.9094 | 0.0052 |
| bl1_vs_pa4 | ours | logreg | 0.7993 | 0.0048 | 0.7881 | 0.9094 | 0.0112 |
| bl1_vs_pa4 | ours | svm | 0.8102 | 0.0109 | 0.7948 | 0.9094 | 0.0154 |
| bl1_vs_pa4 | plos | xgb | 0.8593 | 0.0048 | 0.8577 | 0.9094 | 0.0016 |
| bl1_vs_pa4 | plos | hgb | 0.8566 | 0.0061 | 0.8580 | 0.9094 | -0.0014 |
| bl1_vs_pa4 | plos | logreg | 0.8435 | 0.0022 | 0.8361 | 0.9094 | 0.0074 |
| bl1_vs_pa4 | plos | svm | 0.8408 | 0.0094 | 0.8419 | 0.9094 | -0.0011 |
| bl1_vs_pa4_nofacial | ours | xgb | 0.7633 | 0.0084 | 0.7516 | nan | 0.0117 |
| bl1_vs_pa4_nofacial | ours | hgb | 0.7599 | 0.0146 | 0.7565 | nan | 0.0034 |
| bl1_vs_pa4_nofacial | ours | logreg | 0.7468 | 0.0101 | 0.7458 | nan | 0.0010 |
| bl1_vs_pa4_nofacial | ours | svm | 0.7587 | 0.0118 | 0.7476 | nan | 0.0110 |
| bl1_vs_pa4_nofacial | plos | xgb | 0.8141 | 0.0091 | 0.8197 | nan | -0.0056 |
| bl1_vs_pa4_nofacial | plos | hgb | 0.8160 | 0.0151 | 0.8148 | nan | 0.0012 |
| bl1_vs_pa4_nofacial | plos | logreg | 0.8100 | 0.0053 | 0.8085 | nan | 0.0015 |
| bl1_vs_pa4_nofacial | plos | svm | 0.8012 | 0.0081 | 0.8027 | nan | -0.0015 |
| bl1_vs_pa4_nofacial_nosim | ours | xgb | 0.7594 | 0.0114 | 0.7516 | nan | 0.0078 |
| bl1_vs_pa4_nofacial_nosim | ours | hgb | 0.7548 | 0.0081 | 0.7476 | nan | 0.0072 |
| bl1_vs_pa4_nofacial_nosim | ours | logreg | 0.7409 | 0.0079 | 0.7385 | nan | 0.0024 |
| bl1_vs_pa4_nofacial_nosim | ours | svm | 0.7473 | 0.0048 | 0.7449 | nan | 0.0024 |
| bl1_vs_pa4_nofacial_nosim | plos | xgb | 0.7164 | 0.0135 | 0.7078 | nan | 0.0086 |
| bl1_vs_pa4_nofacial_nosim | plos | hgb | 0.7111 | 0.0124 | 0.7072 | nan | 0.0039 |
| bl1_vs_pa4_nofacial_nosim | plos | logreg | 0.6989 | 0.0103 | 0.6969 | nan | 0.0020 |
| bl1_vs_pa4_nofacial_nosim | plos | svm | 0.6855 | 0.0168 | 0.6838 | nan | 0.0017 |

## Audit of the published table

| channel | published_non_similarity_features | published_pa1_rows_identical_to_a_bl1_row | published_pa1_rows | twin_pairs | twin_r_ours_rms | twin_r_published_rms |
|---|---|---|---|---|---|---|
| corrugator | 33 | 14 | 1680 | 1616 | 1.000 | 0.308 |
| zygomaticus | 33 | 16 | 1680 | 1616 | 1.000 | 0.212 |
| trapezius | 33 | 0 | 1680 | 1616 | 0.424 | 0.324 |

| feature_set | feature | auc_pa1_vs_bl1 | separation |
|---|---|---|---|
| ours (leave-one-out template) | emg_corrugator_sim_corr | 0.936 | 0.872 |
| ours (leave-one-out template) | emg_corrugator_sim_coh_mean | 0.744 | 0.488 |
| ours (leave-one-out template) | emg_corrugator_sim_mi | 0.778 | 0.556 |
| ours (leave-one-out template) | emg_zygomaticus_sim_corr | 0.883 | 0.766 |
| ours (leave-one-out template) | emg_zygomaticus_sim_coh_mean | 0.649 | 0.297 |
| ours (leave-one-out template) | emg_zygomaticus_sim_mi | 0.697 | 0.394 |
| published | plos_emg_zygomaticus_Sim-cohe_F_median | 0.517 | 0.034 |
| published | plos_emg_zygomaticus_Sim-cohe_mean | 0.437 | 0.126 |
| published | plos_emg_zygomaticus_Sim-cohe_pond_mean | 0.513 | 0.027 |
| published | plos_emg_zygomaticus_Sim-cohe_areapond | 0.437 | 0.127 |
| published | plos_emg_zygomaticus_Sim-corr | 0.332 | 0.336 |
| published | plos_emg_zygomaticus_Sim-MutInfo | 0.512 | 0.024 |
| published | plos_emg_corrugator_Sim-cohe_F_median | 0.498 | 0.003 |
| published | plos_emg_corrugator_Sim-cohe_mean | 0.379 | 0.242 |
| published | plos_emg_corrugator_Sim-cohe_pond_mean | 0.504 | 0.007 |
| published | plos_emg_corrugator_Sim-cohe_areapond | 0.379 | 0.241 |
| published | plos_emg_corrugator_Sim-corr | 0.229 | 0.542 |
| published | plos_emg_corrugator_Sim-MutInfo | 0.524 | 0.048 |

## Link between published rows and released trials

| ours | published | r_bl1 | r_pain | r_shifted_by_one_trial |
|---|---|---|---|---|
| ecg_rr_mean_s | plos_ecg_meanRR | 0.914 | 0.896 | 0.164 |
| gsr_raw_mean | plos_gsr_A-MAV | 0.804 | 0.794 | 0.361 |
| emg_trapezius_rms | plos_emg_trapezius_A-RMS | 0.802 | 0.887 | 0.220 |
| emg_corrugator_rms | plos_emg_corrugator_A-RMS | 0.341 | 0.957 | 0.322 |
| emg_zygomaticus_rms | plos_emg_zygomaticus_A-RMS | 0.222 | 0.967 | 0.227 |