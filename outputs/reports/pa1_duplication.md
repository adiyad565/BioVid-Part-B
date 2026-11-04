# PA1 facial-EMG duplication audit

Retained trials: **8426** across **86** subjects.

| channel | subjects BL1 set == PA1 set | PA1 fully matched | pooled PA1 matched | min PA1 match | order-aligned exact |
|---|---:|---:|---:|---:|---:|
| `emg_corrugator` | 72 / 86 | 75 / 86 | 1656 / 1671 (99.1%) | 0.750 | 72 / 74 |
| `emg_zygomaticus` | 72 / 86 | 75 / 86 | 1656 / 1671 (99.1%) | 0.750 | 72 / 74 |

## Twin pairs (1656), leave-one-out 5-class model

| model | both twins correct | same label | P(PA1) higher for the PA1 twin |
|---|---:|---:|---:|
| XGBoost | 0.4251 | 0.0851 | 0.9946 |
| HGB | 0.4112 | 0.0809 | 0.9921 |

## Source-file check

`071309_w_21-BL1-081` vs `071309_w_21-PA1-001`:

| channel | byte-identical |
|---|---|
| `gsr` | no |
| `ecg` | no |
| `emg_trapezius` | no |
| `emg_corrugator` | yes |
| `emg_zygomaticus` | yes |

Byte-identical facial signals across two experimental conditions cannot be physiological. With a leave-one-out template a PA1 trial still finds its BL1 twin inside the template while the BL1 trial cannot find itself, so the facial similarity features become a PA1 detector. They carry no BL1-vs-PA1 information. Which class holds the original recording is established in Step 9 (`published_features_audit.json`).
