AV LED Module Development

Overview

This repository contains the design and documentation for a compact, lightweight LED module for Unmanned Aerial Vehicles (UAVs), developed by MobileTechSpecialists UAV Division. The module uses a single XL-2835WWC-02 LED (LCSC: C2843875) powered by one or two 18650 3.7V button-top lithium-ion batteries, with a simple resistor-based current-limiting circuit for reliability and minimal weight. The design includes battery protection, an on/off switch, and optional USB-C charging, making it suitable for UAV navigation, visibility, or signaling applications.

Features





High-Brightness LED: XL-2835WWC-02 (~3.3V, 150mA, ~1W) for strong illumination.



Power Source: Single or dual 18650 batteries (3.7V, ~2600mAh each, parallel for increased capacity).



Safety: Battery protection circuit (overcharge, over-discharge, short-circuit) and polyfuse.



Compact Design: Optimized for UAV payload constraints (~30x50mm PCB, ~20–30g).



Optional Charging: USB-C charging via TP4056 module for field maintenance.

Prerequisites





Software: EasyEDA account (easyeda.com) for schematic and PCB design.



Hardware: Access to JLCPCB for PCB fabrication and LCSC.com for components.



Tools: Soldering iron, multimeter, USB-C cable (for optional charging).

Schematic Design

The schematic is designed in EasyEDA with the following connections:





Battery (18650): Connects to a protection circuit module (PCM).



PCM (C511607): Protects battery; outputs to SPDT switch.



SPDT Switch (C319441): Controls power to the circuit.



Polyfuse (C70374): Provides short-circuit protection.



Resistor (3.3Ω, C211107): Limits LED current to ~150mA.



LED (XL-2835WWC-02): Connected to resistor and ground.



Capacitor (22µF, C216593): Stabilizes power input.



Optional TP4056 (C2681626) + USB-C (C393947): For battery charging.

Steps to Replicate in EasyEDA





Create Project:





Open EasyEDA, start a new schematic: File > New > Schematic.



Add Components:





Use LCSC library to import components (search by part numbers in BOM).



Place Battery, PCM (as 4-pin block), Switch, Polyfuse, Resistor, LED, Capacitor, and optional TP4056/USB-C.



Wire Connections:





Battery: BAT+ to PCM B+, BAT- to PCM B-.



PCM: P+ to Switch, P- to GND.



Switch: Output to Polyfuse input.



Polyfuse: Output to Resistor and Capacitor positive.



Resistor: Output to LED anode.



LED: Cathode to GND.



Capacitor: Across Polyfuse output and GND.



TP4056 (optional): IN+ to USB-C positive, IN- to GND, OUT+ to BAT+, OUT- to BAT-.



Verify:





Run Design Rule Check (DRC) to ensure no errors.



Assign designators (e.g., R1, D1) via Design Manager.



Export:





Save schematic and export BOM (Design > BOM Export).



Convert to PCB for layout (minimize to ~30x50mm).

Bill of Materials (BOM)

See the simplified BOM below for essential components. All parts are sourced from LCSC.com and compatible with JLCPCB SMT assembly.

PCB Fabrication





Convert to PCB: In EasyEDA, click “Convert to PCB.”



Layout:





Place components compactly, prioritizing LED near the edge for light output.



Use 20–30 mil traces for battery and LED paths.



Add thermal vias under LED (0.3mm diameter).



Order: Export Gerber files and BOM, order via JLCPCB (~$50 for 10 boards with SMT).

Assembly and Testing





Assemble:





Solder components (or use JLCPCB SMT assembly).



Attach a small heatsink (C524987) to the LED if needed.



Test:





Verify PCM functionality (4.25V cutoff, 2.5V discharge limit) with a multimeter.



Confirm LED current (~150mA) and voltage (~3.3V across LED).



Run a 10-hour ground test to validate battery life (~17 hours for 2600mAh at 150mA).



UAV Integration:





Ensure module weight (~20–30g) and power draw (~0.5W) suit UAV specifications.



Secure battery holder and PCB to avoid vibration damage.

Safety Notes





Battery Safety: Use only button-top 18650 batteries with PCM to prevent overcharge/discharge.



Thermal Management: Monitor LED temperature; ensure <70°C during operation.



UAV Compliance: Verify compliance with regulations (e.g., FAA Part 107 for U.S. operations).

Contributing

Contributions are welcome! Submit pull requests for schematic improvements, PCB layout optimizations, or additional features (e.g., PWM dimming). Contact MobileTechSpecialists UAV Division for collaboration.

License

Proprietary - MobileTechSpecialists UAV Division. Contact support@mobiletechspecialists.com for usage permissions.

MobileTechSpecialists UAV Division
Precision Engineering for Aerial Innovation
