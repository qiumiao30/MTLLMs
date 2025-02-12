
# WTMB

The WTMB dataset originates from a wind farm in the central-southern mountainous region of China, consisting of 25 units of 2MW squirrel-cage and direct-drive wind turbines. The dataset includes two turbines: one in normal operation and the other with a cracked main bearing, which are used to form the training and testing sets. The dataset comprises 34 variables that are used to analyze the performance differences between the turbines in normal operation and under fault conditions. By analyzing these variables, the WTMB dataset helps researchers gain deeper insights into the impact of main bearing cracks on wind turbine operation, offering significant practical value.

| **Sensor Name**                               | **Unit** | **Location**        |
|-----------------------------------------------|----------|---------------------|
| Hub Speed                                     | rpm      | Hub                 |
| Hub Angle                                     | °        | Hub                 |
| Blade 1 Angle                                 | °        | Blade               |
| Blade 2 Angle                                 | °        | Blade               |
| Blade 3 Angle                                 | °        | Blade               |
| Pitch Motor 1 Current                         | A        | Nacelle             |
| Pitch Motor 2 Current                         | A        | Nacelle             |
| Pitch Motor 3 Current                         | A        | Nacelle             |
| Vibration Value in X Direction                | m/s²     | Nacelle             |
| Vibration Value in Y Direction                | m/s²     | Nacelle             |
| Hydraulic Brake Pressure                       | bar      | Nacelle             |
| Wind Speed (Nacelle Weather Station)           | m/s      | Weather Station     |
| Absolute Wind Direction                       | °        | Weather Station     |
| Inverter Power on Generator Side              | kW       | Inverter            |
| Generator Operating Frequency                 | Hz       | Generator           |
| Generator Current                             | A        | Generator           |
| Generator Torque                              | Nm       | Generator           |
| Ambient Temperature (Meteorological Tower)    | °C       | Weather Station     |
| Hub Temperature                               | °C       | Hub                 |
| Pitch Motor 1 Power Estimation                | kW       | Nacelle             |
| Pitch Motor 2 Power Estimation                | kW       | Nacelle             |
| Pitch Motor 3 Power Estimation                | kW       | Nacelle             |
| Current Turbine State Value                   | -        | Control             |
| Blade 1 Battery Box Temperature               | °C       | Blade               |
| Blade 2 Battery Box Temperature               | °C       | Blade               |
| Blade 3 Battery Box Temperature               | °C       | Blade               |
| Blade 1 Pitch Motor Temperature               | °C       | Blade               |
| Blade 2 Pitch Motor Temperature               | °C       | Blade               |
| Blade 3 Pitch Motor Temperature               | °C       | Blade               |
| Blade 1 Inverter Box Temperature              | °C       | Blade               |
| Blade 2 Inverter Box Temperature              | °C       | Blade               |
| Blade 3 Inverter Box Temperature              | °C       | Blade               |
| Current Variance (curr\_var)                  | A        | Electrical          |
| Temperature Variance (temp\_var)              | °C       | Electrical          |


# WTGB

In this dataset, which was collected at 10-minute intervals with anonymized timestamps, we observed a typical case of bearing failure. The fault primarily manifested as abnormal bearing temperature rises, particularly at the Drive End and Non-Drive End bearings, where temperatures increased significantly by 60-90 degrees Celsius with notable periodic fluctuations. As the fault progressed, the generator's stator three-phase winding temperatures showed imbalances, with temperature rises of approximately 40 degrees. Simultaneously, significant operational abnormalities emerged: speed fluctuations reached 45\% of the base speed with sudden speed variations; three-phase currents displayed marked imbalances with fluctuations of up to 35\%; ultimately leading to a substantial decrease in unit power output, with maximum reductions reaching 60\%. These fault characteristics exhibited typical nonlinear development trends in the 10-minute resolution data, indicating that the bearing failure had begun to affect the overall operational status of the generating unit.

# Standardized Variable Names

| Variable Name                         | Description                                      | Unit       | Location               |
|----------------------------------------|--------------------------------------------------|------------|------------------------|
| `ambient_temp`                         | Ambient temperature                              | °C         | Weather station       |
| `wind_abs_dir`                         | Wind absolute direction                          | °          | Weather station       |
| `wind_rel_dir`                         | Wind relative direction                          | °          | Weather station       |
| `wind_speed`                           | Wind speed                                      | m/s        | Weather station       |
| `est_wind_speed`                       | Estimated wind speed                            | m/s        | Weather station       |
| `pitch_angle`                          | Pitch angle                                     | °          | Blade control system  |
| `hub_ctrl_temp`                        | Temperature in the hub controller               | °C         | Hub                   |
| `top_nacelle_ctrl_temp`                | Temperature in the top nacelle controller       | °C         | Nacelle               |
| `vcs_choke_coil_temp`                  | Temperature in the choke coils on the VCS-section | °C         | VCS section           |
| `vcp_board_temp`                       | Temperature on the VCP-board                    | °C         | VCS section           |
| `vcs_cooling_water_temp`               | Temperature in the VCS cooling water            | °C         | VCS cooling system    |
| `gearbox_hss_bearing_temp`             | Temperature in gearbox bearing on high-speed shaft | °C         | Gearbox               |
| `gearbox_oil_temp`                     | Temperature of oil in gearbox                   | °C         | Gearbox               |
| `gen_bearing2_temp`                    | Temperature in generator bearing 2 (Drive End)  | °C         | Generator             |
| `gen_bearing1_temp`                    | Temperature in generator bearing 1 (Non-Drive End) | °C      | Generator             |
| `gen_stator_winding_temp_p1`           | Temperature inside generator stator windings phase 1 | °C     | Generator             |
| `gen_stator_winding_temp_p2`           | Temperature inside generator stator windings phase 2 | °C     | Generator             |
| `gen_stator_winding_temp_p3`           | Temperature inside generator stator windings phase 3 | °C     | Generator             |
| `gen_rpm`                              | Generator RPM in latest period                  | rpm        | Generator             |
| `split_ring_chamber_temp`              | Temperature in the split ring chamber           | °C         | Slip ring chamber     |
| `busbar_section_temp`                  | Temperature in the busbar section               | °C         | Electrical system     |
| `igbt_grid_inverter_temp`              | Temperature measured by the IGBT driver on the grid-side inverter | °C | Inverter system      |
| `actual_phase_displacement`            | Actual phase displacement                       | °          | Electrical system     |
| `avg_current_p1`                       | Averaged current in phase 1                     | A          | Electrical system     |
| `avg_current_p2`                       | Averaged current in phase 2                     | A          | Electrical system     |
| `avg_current_p3`                       | Averaged current in phase 3                     | A          | Electrical system     |
| `grid_freq`                            | Grid frequency                                  | Hz         | Electrical grid       |
| `grid_cap_reactive_power`              | Possible grid capacitive reactive power         | kVAR       | Electrical grid       |
| `grid_ind_reactive_power`              | Possible grid inductive reactive power         | kVAR       | Electrical grid       |
| `grid_active_power`                    | Possible grid active power                      | kW         | Electrical grid       |
| `grid_power`                           | Grid power                                     | kW         | Electrical grid       |
| `grid_reactive_power`                   | Grid reactive power                            | kVAR       | Electrical grid       |
| `avg_voltage_p1`                       | Averaged voltage in phase 1                     | V          | Electrical system     |
| `avg_voltage_p2`                       | Averaged voltage in phase 2                     | V          | Electrical system     |
| `avg_voltage_p3`                       | Averaged voltage in phase 3                     | V          | Electrical system     |
| `igbt_rotor_inv_temp_p1`               | Temperature measured by the IGBT driver on the rotor-side inverter phase 1 | °C | Inverter system      |
| `igbt_rotor_inv_temp_p2`               | Temperature measured by the IGBT driver on the rotor-side inverter phase 2 | °C | Inverter system      |
| `igbt_rotor_inv_temp_p3`               | Temperature measured by the IGBT driver on the rotor-side inverter phase 3 | °C | Inverter system      |
| `hv_transformer_temp_L1`               | Temperature in HV transformer phase L1          | °C         | High-voltage transformer |
| `hv_transformer_temp_L2`               | Temperature in HV transformer phase L2          | °C         | High-voltage transformer |
| `hv_transformer_temp_L3`               | Temperature in HV transformer phase L3          | °C         | High-voltage transformer |
| `hydraulic_oil_temp`                   | Temperature of oil in the hydraulic group       | °C         | Hydraulic system      |
| `nacelle_dir`                          | Nacelle direction                              | °          | Nacelle               |
| `nacelle_temp`                         | Nacelle temperature                            | °C         | Nacelle               |
| `rotor_rpm`                            | Rotor RPM                                      | rpm        | Rotor                 |
| `nose_cone_temp`                       | Temperature in the nose cone                   | °C         | Nose cone             |




