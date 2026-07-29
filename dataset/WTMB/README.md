# WTMB: Wind Turbine with Main-Bearing Fault

## Overview

WTMB is an anonymized industrial multivariate time series for main-bearing anomaly detection. It originates from a wind farm in the central-southern mountainous region of China containing 25 2-MW squirrel-cage and direct-drive wind turbines. The released training and test series come from two turbines: one normally operating turbine and one turbine with a main-bearing crack.

## Files

| File                    |            Rows | Columns | Description                                                               |
| ----------------------- | --------------: | ------: | ------------------------------------------------------------------------- |
| `train.csv`             |         659,875 |      34 | Reference training series from the normally operating turbine             |
| `test.csv`              |         153,800 |      34 | Evaluation series from the turbine associated with the main-bearing crack |
| `label.csv`             |         153,800 |       1 | Binary labels aligned with `test.csv`; `0=normal`, `1=anomaly`            |
| `anomaly_intervals.csv` |     4 intervals |       — | Exact contiguous positive-label intervals                                 |
| `failure_log.csv`       | 4 event records |       — | Anonymized signal-derived fault-event log                                 |
| `event_statistics.csv`  |        4 events |       — | Reproducible signal statistics for each labelled event                    |

The CSV header is not counted as a sample. Public interval boundaries are zero-based and inclusive.

## Sampling

* Sampling interval: **1 second (1 Hz)**, pending final confirmation against the original acquisition configuration.

* Test duration: 153,800 seconds (42 h 43 min 20 s).

* Positive samples: 107,834.

* Anomaly rate: 70.1131%.

## Ground-truth intervals

| Event    | Start index | End index | Samples | Relative start |  Relative end | Inclusive duration |
| -------- | ----------: | --------: | ------: | -------------: | ------------: | -----------------: |
| WTMB-A01 |      10,520 |   110,500 |  99,981 |     T+02:55:20 | T+1d 06:41:40 |        1d 03:46:21 |
| WTMB-A02 |     114,000 |   118,000 |   4,001 |  T+1d 07:40:00 | T+1d 08:46:40 |           01:06:41 |
| WTMB-A03 |     118,200 |   119,500 |   1,301 |  T+1d 08:50:00 | T+1d 09:11:40 |           00:21:41 |
| WTMB-A04 |     119,700 |   122,250 |   2,551 |  T+1d 09:15:00 | T+1d 09:57:30 |           00:42:31 |

These four rows are contiguous runs in the released `label.csv` and are documented as four signal-derived episodes associated with the same reported component-level diagnosis. They must not automatically be interpreted as four independent physical failures.

## Signal-derived event log

| Event    | Main reproducible evidence                                                          | Evidence-based interpretation               |
| -------- | ----------------------------------------------------------------------------------- | ------------------------------------------- |
| WTMB-A01 | Temperature variance +131.3%; current variance +250.5%; generator-side power -41.0% | Prolonged fault-associated operating regime |
| WTMB-A02 | Temperature variance +259.4%; current variance +444.8%; generator-side power -30.5% | Renewed/intensified abnormal episode        |
| WTMB-A03 | Temperature variance +207.9%; current variance +296.9%; generator-side power -33.3% | Short persistent abnormal episode           |
| WTMB-A04 | Temperature variance +249.1%; current variance +473.3%; generator-side power -67.8% | Late derating/output-loss episode           |

The X/Y vibration channels do not display a consistent variance increase across these periods. Consequently, the released signals support abnormal multivariate operating intervals associated with the reported main-bearing diagnosis, but they do not independently establish the existence or geometry of a bearing crack.


## Release-level preprocessing and data quality

* Turbine/farm identifiers and absolute timestamps were removed for confidentiality; chronological order was preserved.

* The released values remain in physical units and are not stored as z-scores or min-max-normalized values.

* `curr_var` and `temp_var` are derived dispersion variables included as channels.

* No missing cells occur in either `train.csv` or `test.csv`.

* Repeated rows are retained as time samples: 1,981 repeated rows occur in the training file and 30 in the test file when equality is evaluated over all 34 columns.

* The training header spells the final column `tetmp_var`, whereas the test header spells it `temp_var`. Rename `tetmp_var` to `temp_var` when loading to obtain a consistent schema.

Model-specific imputation, normalization, windowing, and threshold-selection procedures are not encoded in these CSV files and must be documented with the experiment.

## Variables

| Variable                                   | Unit     | Location        |
| ------------------------------------------ | -------- | --------------- |
| Hub Speed                                  | rpm      | Hub             |
| Hub Angle                                  | degree   | Hub             |
| Blade 1 Angle                              | degree   | Blade           |
| Blade 2 Angle                              | degree   | Blade           |
| Blade 3 Angle                              | degree   | Blade           |
| Pitch Motor 1 Current                      | A        | Nacelle         |
| Pitch Motor 2 Current                      | A        | Nacelle         |
| Pitch Motor 3 Current                      | A        | Nacelle         |
| Vibration Value in X Direction             | m/s^2    | Nacelle         |
| Vibration Value in Y Direction             | m/s^2    | Nacelle         |
| Hydraulic Brake Pressure                   | bar      | Nacelle         |
| Wind Speed (Nacelle Weather Station)       | m/s      | Weather station |
| Absolute Wind Direction                    | degree   | Weather station |
| Inverter Power on Generator Side           | kW       | Inverter        |
| Generator Operating Frequency              | Hz       | Generator       |
| Generator Current                          | A        | Generator       |
| Generator Torque                           | Nm       | Generator       |
| Ambient Temperature (Meteorological Tower) | degree C | Weather station |
| Hub Temperature                            | degree C | Hub             |
| Pitch Motor 1 Power Estimation             | kW       | Nacelle         |
| Pitch Motor 2 Power Estimation             | kW       | Nacelle         |
| Pitch Motor 3 Power Estimation             | kW       | Nacelle         |
| Current Turbine State Value                | —        | Control         |
| Blade 1 Battery Box Temperature            | degree C | Blade           |
| Blade 2 Battery Box Temperature            | degree C | Blade           |
| Blade 3 Battery Box Temperature            | degree C | Blade           |
| Blade 1 Pitch Motor Temperature            | degree C | Blade           |
| Blade 2 Pitch Motor Temperature            | degree C | Blade           |
| Blade 3 Pitch Motor Temperature            | degree C | Blade           |
| Blade 1 Inverter Box Temperature           | degree C | Blade           |
| Blade 2 Inverter Box Temperature           | degree C | Blade           |
| Blade 3 Inverter Box Temperature           | degree C | Blade           |
| Current Variance (`curr_var`)              | A        | Electrical      |
| Temperature Variance (`temp_var`)          | degree C | Electrical      |

## Interpretation

WTMB is a targeted fault-trajectory case. The 70.1131% test anomaly rate is not a natural prevalence estimate for a wind farm. For this split, a detector predicting every test sample as anomalous obtains precision 0.7011, recall 1.0000, and F1 0.8243. Report this baseline and threshold-free/ranking metrics when comparing detectors.

