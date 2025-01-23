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

| **Sensor Name**                               | **Unit** | **Location**        |
|-----------------------------------------------|----------|---------------------|
| Ambient Temperature Sensor                    | °C       | Weather Station     |
| Absolute Wind Direction Sensor                | °        | Weather Station     |
| Relative Wind Direction Sensor                | °        | Weather Station     |
| Wind Speed Sensor                             | m/s      | Weather Station     |
| Estimated Wind Speed Sensor                   | m/s      | Weather Station     |
| Pitch Angle Sensor                            | °        | Nacelle             |
| Hub Controller Temperature Sensor             | °C       | Hub                 |
| Top Nacelle Controller Temperature Sensor     | °C       | Nacelle             |
| Choke Coils Temperature Sensor (VCS Section)  | °C       | Nacelle             |
| VCP-Board Temperature Sensor                  | °C       | Nacelle             |
| VCS Cooling Water Temperature Sensor          | °C       | Nacelle             |
| Gearbox High-Speed Shaft Bearing Temperature Sensor | °C | Gearbox             |
| Gearbox Oil Temperature Sensor                | °C       | Gearbox             |
| Generator Drive-End Bearing Temperature Sensor | °C      | Generator           |
| Generator Non-Drive-End Bearing Temperature Sensor | °C  | Generator           |
| Stator Winding Phase 1 Temperature Sensor    | °C       | Generator           |
| Stator Winding Phase 2 Temperature Sensor    | °C       | Generator           |
| Stator Winding Phase 3 Temperature Sensor    | °C       | Generator           |
| Generator RPM Sensor                          | rpm      | Generator           |
| Split Ring Chamber Temperature Sensor         | °C       | Nacelle             |
| Busbar Section Temperature Sensor             | °C       | Nacelle             |
| Grid Side Inverter IGBT Temperature Sensor    | °C       | Inverter            |
| Phase Displacement Sensor                     | °        | Electrical          |
| Phase 1 Current Sensor                        | A        | Electrical          |
| Phase 2 Current Sensor                        | A        | Electrical          |
| Phase 3 Current Sensor                        | A        | Electrical          |
| Phase 1 Voltage Sensor                        | V        | Electrical          |
| Phase 2 Voltage Sensor                        | V        | Electrical          |
| Phase 3 Voltage Sensor                        | V        | Electrical          |
| Grid Frequency Sensor                         | Hz       | Grid                |
| Grid Capacitive Reactive Power Sensor        | kVAr     | Grid                |
| Grid Inductive Reactive Power Sensor         | kVAr     | Grid                |
| Grid Active Power Sensor                     | kW       | Grid                |
| Grid Power Sensor                             | kW       | Grid                |
| Grid Reactive Power Sensor                   | kVAr     | Grid                |
| Hydraulic Group Oil Temperature Sensor        | °C       | Hydraulic System    |
| Nacelle Direction Sensor                      | °        | Nacelle             |
| Nacelle Temperature Sensor                    | °C       | Nacelle             |
| Active Power Sensor (Generator Disconnected)  | Wh       | Generator           |
| Active Power Sensor (Delta Connection)        | Wh       | Generator           |
| Active Power Sensor (Star Connection)         | Wh       | Generator           |
| Reactive Power Sensor (Generator Disconnected)| VArh     | Generator           |
| Reactive Power Sensor (Delta Connection)      | VArh     | Generator           |
| Reactive Power Sensor (Star Connection)       | VArh     | Generator           |
| Total Active Power Sensor                     | Wh       | Generator           |
| Total Reactive Power Sensor                   | VArh     | Generator           |
| Rotor RPM Sensor                              | rpm      | Rotor               |
| Nose Cone Temperature Sensor                  | °C       | Rotor               |



