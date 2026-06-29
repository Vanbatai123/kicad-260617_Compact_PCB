Project Details
$10.00 – 30.00 USD

 Bidding ends in 6 days, 22 hours
I have a complete electronic schematic and need a PCB layout based on it. The project was prepared in Fusion Electronics, but the PCB may also be designed in Eagle PCB.

The PCB should be as small as reasonably possible, maximum 60 × 50 mm. A 4-layer PCB is preferred.

The board includes, among others:

* ESP32-S3-WROOM-1-N8R8,
* BQ25887 2S Li-Ion/Li-Po charger,
* TUSB320LAI USB-C CC controller,
* S-82B2 2S battery protection IC,
* AP63203 3.3 V buck converter,
* TC4427 MOSFET gate driver,
* CSD17573Q5B power MOSFETs,
* TPS3823 watchdog,
* two USB-C connectors,
* 2S battery connector,
* heater connectors,
* NTC connectors,
* nRF24L01 and VTX / Eachine TX805 headers.

The PCB must follow good engineering practice, manufacturer layout recommendations, DFM rules, EMI/EMC rules and proper thermal design.

Main requirements:

* PCB size: as small as possible, max. 60 × 50 mm,
* FR4, 1.6 mm thickness,
* 4 copper layers,
* ENIG finish,
* black solder mask, white silkscreen,
* minimum signal trace width: 0.25 mm,
* minimum power trace width: 0.5 mm,
* high-current VBAT/heater paths: minimum 1.0 mm, preferably copper pours,
* minimum clearance: 0.2 mm,
* minimum via: 0.3 mm drill / 0.6 mm pad,
* all connectors must have clear pin descriptions,
* J1 USB-C must be marked as CHG,
* J2 USB-C must be marked as SVC,
* all footprints must match the real selected parts.

Preferred 4-layer stackup:

* L1 TOP: components, short signals, USB, SPI, I2C, ADC, local power pours,
* L2 INNER 1: solid uninterrupted GND plane,
* L3 INNER 2: power planes/pours such as V_BAT_PROT, 3V3, VBUS_FUSED,
* L4 BOTTOM: auxiliary signals, test points, GND pour where possible.

L2 GND must not be split under ESP32, USB lines, RF area, switching converters, BQ25887, AP63203 or ADC/NTC traces.

Component placement:

* Place both USB-C connectors on one PCB edge.
* Place TUSB320, USB-C protection and BQ25887 close to the charging USB-C connector.
* Place BMS IC, shunt and battery protection MOSFETs close to the battery connector.
* Place heater MOSFETs and TC4427 close to the heater connectors.
* Place ESP32-S3-WROOM at the PCB edge with the antenna facing outside the board.
* Place nRF24 and VTX headers close to ESP32 but outside the ESP32 antenna keep-out area.
* Keep ADC/NTC dividers away from inductors, SW nodes, MOSFETs and heater current paths.

ESP32 antenna requirements:

* The ESP32 antenna must be placed at the PCB edge, preferably extending outside the PCB outline.
* If not possible, keep at least 15 mm antenna keep-out.
* No copper, traces, vias, polygons or components are allowed in the antenna keep-out area on any layer.
* Provide a solid GND plane under the logic part of the ESP32.
* Add sufficient GND stitching vias.
* Add local 100 nF and 10–22 µF decoupling capacitors close to ESP32 power pins.
* EN, BOOT and programming signals must be accessible for testing.

USB-C service port J2:

* USB D+ and D− must be routed as a 90 Ω differential pair.
* Match D+ and D− lengths.
* Route over continuous GND.
* Avoid vias if possible.
* Do not route USB near inductors, SW nodes, MOSFETs, heater paths, gate traces or RF antennas.
* Place USB ESD protection close to the connector.
* Place 22 Ω series resistors close to ESP32.
* CC1 and CC2 must have 5.1 kΩ Rd resistors to GND.
* J2 VBUS must not power the system unless explicitly shown in the schematic.

USB-C charging port J1:

* J1 is used for charging the 2S battery pack.
* TUSB320 must be placed close to J1.
* CC lines must be short and routed away from noise.
* TUSB320 is not a USB-PD controller, so do not assume higher PD voltages.
* The design should allow firmware to set the BQ25887 input current limit based on Type-C current detection.
* Default charging state should be safe for weaker USB sources.
* Place ESD/TVS and fuse/polyfuse close to J1.

BQ25887 charger layout:

* Place BQ25887 close to J1 and the battery power path.
* Place PMID, SNS, VBUS and BAT capacitors directly near the IC pins.
* Place the inductor close to SW pins.
* Keep the SW node short and small.
* Do not route USB, ADC, I2C, SPI or RF traces under the inductor or SW node.
* Connect the thermal pad to GND with multiple thermal vias.
* Route MID and TS as sensitive analog signals away from power paths.
* Ensure proper heat dissipation for the balancing/CBSET resistor.
* Route I2C short, with pull-ups to 3.3 V.

AP63203 3.3 V buck converter:

* Place close to V_BAT_PROT.
* Input capacitor must be directly at VIN/GND.
* BST capacitor must be directly between BST and SW.
* Inductor must be close to SW.
* Output capacitors must be close to the inductor and IC.
* Keep SW node small.
* Do not route USB, ADC, NTC, CC or RF traces under the converter.
* Route 3.3 V as a wide trace or copper pour.

BMS and battery protection:

* Battery connector, S-82B2, shunt and MOSFETs must form a compact block.
* Main battery current path must be short and wide.
* The shunt must be routed using Kelvin sensing.
* Sense traces must come directly from the shunt pads, not from nearby copper pours.
* High-current paths should be copper pours on multiple layers when possible.
* Use multiple vias for layer transitions.

Heater power path:

* Heater MOSFETs must be close to heater connectors.
* TC4427 must be close to the MOSFETs, not close to ESP32.
* Gate traces must be short.
* Gate resistors and gate pull-down resistors must be placed directly near MOSFET gates.
* Add local 100 nF + 1 µF decoupling for TC4427.
* Heater current paths must be wide copper pours.
* Avoid bottlenecks.
* MOSFETs must have large copper areas for heat dissipation.
* Add footprints for optional RC snubber or TVS if needed.

ADC / NTC / voltage sensing:

* Route analog signals away from inductors, SW nodes, MOSFETs, gate traces and heater paths.
* Place ADC filter capacitors close to ESP32 ADC pins.
* Route ADC traces over solid GND.
* Keep voltage divider sensing points accurate.
* Do not connect analog divider grounds to noisy high-current return points.

SPI, I2C and RF headers:

* SPI to nRF24 and VTX should be short and routed over solid GND.
* Avoid vias if possible.
* Add optional 22–100 Ω series resistor footprints on longer SPI lines.
* I2C to BQ25887 and TUSB320 must be routed away from switching nodes.
* nRF24 supply should have local 100 nF + 10 µF, with optional space for 47–100 µF.
* VTX supply must match the real module requirements. If +5 V is used, a real +5 V source must exist on the PCB.

Mechanical requirements:

* USB-C connectors must be placed on a PCB edge with correct mechanical pads.
* Battery and heater connectors must be placed so wires do not pass over the ESP32 antenna.
* High-current connectors must be connected with wide copper pours.
* Avoid thin thermal reliefs on high-current pads.
* Check connector orientation in 3D view.
* Check all courtyards and mechanical collisions.

EMI and thermal requirements:

* Minimize switching current loops.
* Minimize SW node copper area.
* Do not route sensitive traces under inductors.
* Use GND stitching vias around converters, USB area, PCB edges and power sections.
* Use large copper areas and thermal vias for BQ25887, AP63203, MOSFETs, shunt and balancing resistor.
* High-current paths should use pours on several layers connected by multiple vias.

Required test points:

GND, 3V3, V_BAT_PROT, VBUS_FUSED, BAT+, BATT_MID, RESET/EN, BOOT, WDI, SDA, SCL, USB2_VBUS_DET, MOSFET gates, heater outputs, ADC_BAT, ADC_MID, NTC1, NTC2.

Required output files:

* source schematic file,
* source PCB file,
* Gerber files,
* drill files,
* BOM,
* Pick & Place / CPL,
* DRC report,
* ERC report,
* 3D render top and bottom,
* stackup information,
* USB impedance settings,
* confirmation of high-current trace widths,
* confirmation of ESP32 antenna keep-out,
* confirmation that footprints match real parts.

Acceptance criteria:

* PCB is as small as possible and does not exceed 60 × 50 mm,
* DRC has 0 errors,
* ERC has 0 errors or exceptions are clearly explained,
* USB D+/D− impedance is 90 Ω ±10%,
* ESP32 antenna keep-out is respected,
* L2 is a solid GND plane,
* VBAT and heater paths have no narrow bottlenecks,
* BQ25887 and AP63203 follow manufacturer layout recommendations,
* shunt is Kelvin-routed,
* MOSFETs have proper thermal copper areas,
* connectors are correctly placed and described,
* Gerbers import correctly into the PCB manufacturer viewer.

Autorouting should not be used as the main routing method. USB, power, RF, ADC and heater sections must be routed manually.