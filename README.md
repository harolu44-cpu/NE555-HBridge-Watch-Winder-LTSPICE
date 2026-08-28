# NE555-HBridge-Watch-Winder-LTSPICE
Mostly analog watch winder controller using an NE555 timer, flip-flop, and H-bridge motor driver for timed bidirectional motor operation designed in LTSPICE.

Design Goals

The controller was designed to:
- Run the motor for approximately 5 minutes
- Keep the motor off for approximately 40 minutes
- Automatically repeat the timing cycle
- Alternate the intended motor direction between operating cycles
- Implement the control system primarily with discrete analog and digital circuitry
- Verify circuit behavior using LTspice transient simulation

The NE555 provides the periodic timing signal used to control when the output stage is enabled.

The timing network uses:
R1: 91 kΩ
R2: 750 kΩ
C1: 4700 µF
D1: 1N4148

The resistor and capacitor values were selected to create approximately:
5-minute active interval
40-minute inactive interval
The diode provides separate charging and discharging paths so that the active and inactive periods can be set to significantly different durations.

Direction Control

A CD4013 D flip-flop is used to maintain and alternate the direction state.

The output stage is modeled as a four-switch H-bridge.

The bridge receives two control states:
Forward
Reverse

The control logic combines the NE555 enable signal with the direction state so that the H-bridge is only driven during an active timing interval. Depending on the flip-flop state, the bridge applies opposite polarity across the modeled load.

This architecture allows bidirectional operation without manually reversing the motor connections.

Project Status
This project is currently a circuit design and LTspice simulation project. The circuit has not yet been physically constructed.
The simulation was used as a preliminary design and verification step before potential hardware implementation.
"I have recently finished my ESP32 PCB design in Altium and I will work on this one in the upcoming weeks between classes."
