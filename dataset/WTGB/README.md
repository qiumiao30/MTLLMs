# WTGB: Wind Turbine with Generator-Bearing Fault

## Overview

WTGB is an anonymized industrial multivariate SCADA time series describing a generator-bearing degradation/failure case. The released data capture abnormal temperature increases in the Drive-End and Non-Drive-End generator bearings, accompanied during fault development by generator winding-temperature imbalance, rotational-speed fluctuation, three-phase current imbalance, and reduced power output.

## Files

| File                    |            Rows | Columns | Description                                                    |
| ----------------------- | --------------: | ------: | -------------------------------------------------------------- |
| `train.csv`             |         108,976 |      46 | Reference training series                                      |
| `test.csv`              |         111,144 |      46 | Evaluation series                                              |
| `label.csv`             |         111,144 |       1 | Binary labels aligned with `test.csv`; `0=normal`, `1=anomaly` |

The CSV header is not counted as a sample. Public interval boundaries are zero-based and inclusive.

## Sampling

* Sampling interval: **10 minutes**.

* Test duration: 1,111,440 minutes (771 d 20 h).

* Positive samples: 6,520.

* Anomaly rate: 5.8663%.

## Ground-truth intervals

| Event    | Start index | End index | Samples | Relative start | Relative end | Inclusive duration |
| -------- | ----------: | --------: | ------: | -------------: | -----------: | -----------------: |
| WTGB-A01 |      52,436 |    54,447 |   2,012 |   T+364d 03:20 | T+378d 02:30 |          13d 23:20 |
| WTGB-A02 |     106,349 |   110,856 |   4,508 |   T+738d 12:50 | T+769d 20:00 |          31d 07:20 |

These rows are the complete set of contiguous positive runs in the released `label.csv` and are documented as two signal-derived episodes associated with the reported generator-bearing diagnosis. They are not claimed to be two independently maintenance-confirmed physical failures.

## Signal-derived event log

| Event    | Main reproducible evidence                                                                                                                                                                              | Evidence-based interpretation                      |
| -------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------- |
| WTGB-A01 | Drive-End mean 128.1 °C; Non-Drive-End mean 108.3 °C; bearing temperatures exceed 80 °C for 88.0%/76.6% of the interval; stator-temperature spread +1255.7%; operational current imbalance +230.4%      | Acute overheating and electrical-propagation stage |
| WTGB-A02 | Drive-End mean 92.4 °C; Non-Drive-End mean 100.0 °C; stator-temperature spread +1053.2%; operational current imbalance +91.7%; rpm -26.7%; grid power -39.6%; near-zero power for 53.9% of the interval | Progressed fault with derating/shutdown            |

These component-specific thermal changes and downstream electrical/operational effects provide strong signal-level evidence for generator-bearing failure. The exact damage mode and maintenance action still require an inspection, work-order, or component-replacement record if such evidence can be released.


## Release-level preprocessing and data quality

* Turbine/farm identifiers and absolute timestamps were removed for confidentiality; chronological order was preserved.

* The released values remain in physical units and are not stored as z-scores or min-max-normalized values.

* Repeated rows are retained as time samples. The training file contains 46,437 rows that repeat a complete 46-channel value vector seen elsewhere; these can represent different 10-minute timestamps, including stopped or stable operation, and should not be deduplicated solely by value.

* Missing values remain in the public release:

  * training indices `12090`, `12091`, `41524`, `74629`, `74630`, and `104063`;

  * test indices `54051`, `110618`, and `110619`;

  * at each listed index, both `Temperature in generator bearing 1 (Non-Drive End)` and `Actual phase displacement` are missing.

* Any imputation must be fitted without test-label information. The experiment should state the actual method used (for example, training-only median imputation, forward filling within a split, or interpolation) rather than leaving it implicit.

## Variables

| Standardized name            | Description                                          | Unit     |
| ---------------------------- | ---------------------------------------------------- | -------- |
| `ambient_temp`               | Ambient temperature                                  | degree C |
| `wind_abs_dir`               | Wind absolute direction                              | degree   |
| `wind_rel_dir`               | Wind relative direction                              | degree   |
| `wind_speed`                 | Wind speed                                           | m/s      |
| `est_wind_speed`             | Estimated wind speed                                 | m/s      |
| `pitch_angle`                | Pitch angle                                          | degree   |
| `hub_ctrl_temp`              | Hub-controller temperature                           | degree C |
| `top_nacelle_ctrl_temp`      | Top-nacelle controller temperature                   | degree C |
| `vcs_choke_coil_temp`        | VCS choke-coil temperature                           | degree C |
| `vcp_board_temp`             | VCP-board temperature                                | degree C |
| `vcs_cooling_water_temp`     | VCS cooling-water temperature                        | degree C |
| `gearbox_hss_bearing_temp`   | Gearbox high-speed-shaft bearing temperature         | degree C |
| `gearbox_oil_temp`           | Gearbox oil temperature                              | degree C |
| `gen_bearing2_temp`          | Generator bearing 2 temperature (Drive End)          | degree C |
| `gen_bearing1_temp`          | Generator bearing 1 temperature (Non-Drive End)      | degree C |
| `gen_stator_winding_temp_p1` | Generator stator winding temperature, phase 1        | degree C |
| `gen_stator_winding_temp_p2` | Generator stator winding temperature, phase 2        | degree C |
| `gen_stator_winding_temp_p3` | Generator stator winding temperature, phase 3        | degree C |
| `gen_rpm`                    | Generator rotational speed                           | rpm      |
| `split_ring_chamber_temp`    | Slip-ring chamber temperature                        | degree C |
| `busbar_section_temp`        | Busbar-section temperature                           | degree C |
| `igbt_grid_inverter_temp`    | Grid-side inverter IGBT-driver temperature           | degree C |
| `actual_phase_displacement`  | Actual phase displacement                            | degree   |
| `avg_current_p1`             | Average phase-1 current                              | A        |
| `avg_current_p2`             | Average phase-2 current                              | A        |
| `avg_current_p3`             | Average phase-3 current                              | A        |
| `grid_freq`                  | Grid frequency                                       | Hz       |
| `grid_cap_reactive_power`    | Grid capacitive reactive power                       | kVAR     |
| `grid_ind_reactive_power`    | Grid inductive reactive power                        | kVAR     |
| `grid_active_power`          | Grid active power                                    | kW       |
| `grid_power`                 | Grid power                                           | kW       |
| `grid_reactive_power`        | Grid reactive power                                  | kVAR     |
| `avg_voltage_p1`             | Average phase-1 voltage                              | V        |
| `avg_voltage_p2`             | Average phase-2 voltage                              | V        |
| `avg_voltage_p3`             | Average phase-3 voltage                              | V        |
| `igbt_rotor_inv_temp_p1`     | Rotor-side inverter IGBT-driver temperature, phase 1 | degree C |
| `igbt_rotor_inv_temp_p2`     | Rotor-side inverter IGBT-driver temperature, phase 2 | degree C |
| `igbt_rotor_inv_temp_p3`     | Rotor-side inverter IGBT-driver temperature, phase 3 | degree C |
| `hv_transformer_temp_L1`     | HV-transformer temperature, L1                       | degree C |
| `hv_transformer_temp_L2`     | HV-transformer temperature, L2                       | degree C |
| `hv_transformer_temp_L3`     | HV-transformer temperature, L3                       | degree C |
| `hydraulic_oil_temp`         | Hydraulic-group oil temperature                      | degree C |
| `nacelle_dir`                | Nacelle direction                                    | degree   |
| `nacelle_temp`               | Nacelle temperature                                  | degree C |
| `rotor_rpm`                  | Rotor rotational speed                               | rpm      |
| `nose_cone_temp`             | Nose-cone temperature                                | degree C |

## Fault manifestations

Across the documented failure case, the principal bearing temperatures increase by approximately 60–90 degree C and show periodic fluctuations. Generator stator winding temperatures become imbalanced with increases of approximately 40 degree C. Speed fluctuations can reach approximately 45% of the base speed, three-phase current fluctuations approximately 35%, and power output can decrease by up to approximately 60%. These signal manifestations describe the case and should not replace the independent maintenance evidence used to establish the ground truth.

