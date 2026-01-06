# Hardware Installation

This guide covers the physical installation of the BrewOS control board, sensors, and wiring. **This work involves mains voltage and should only be performed by qualified individuals.**

> **⚠️ Disclaimer:** BrewOS is provided "as is" without warranty. Use at your own risk. You assume full responsibility for any use, modification, or installation. See the [full disclaimer](../../README.md#-disclaimer) for important information.

## ⚠️ Safety Warning

```
⚠️  WARNING: MAINS VOLTAGE

This installation involves 100-240V AC mains electricity.
Improper handling can result in death or serious injury.

• Only qualified individuals should work on mains circuits
• Always disconnect power before making any changes
• Use isolation transformers during development
• Never work alone on energized equipment
• Follow all local electrical codes and regulations
```

## Prerequisites

Before starting:

- ✅ Machine is unplugged and power is disconnected
- ✅ All required components are available
- ✅ You have basic electronics knowledge
- ✅ You understand the risks involved

## Required Components

- BrewOS control board (Pico-based)
- ESP32-S3 display module (optional but recommended)
- NTC thermistors (boiler temperature sensors)
- K-type thermocouple (group head sensor)
- Pressure transducer (0-16 bar)
- Water level sensors
- Wiring and connectors
- External SSRs for heater control (if not included)

## Installation Steps

### Step 1: Remove Factory Controller

1. **Disconnect power** - Unplug machine from wall outlet
2. **Remove access panel** - Access the control board compartment
3. **Document wiring** - Take photos of existing wiring before disconnecting
4. **Disconnect factory board** - Remove all connections from factory GICAR board
5. **Remove board** - Unmount and remove the factory control board

### Step 2: Install Control Board

1. **Mount control board** - Install in same location as factory board
2. **Secure mounting** - Ensure board is firmly mounted
3. **Check orientation** - Verify connectors are accessible
4. **Verify clearance** - Ensure adequate clearance for wiring

### Step 3: Install Sensors

#### Boiler Temperature Sensors (NTC Thermistors)

1. **Locate sensor ports** - Find M4 threaded ports on boilers
2. **Install sensors** - Thread NTC thermistors into ports
3. **Apply thermal paste** - Ensure good thermal contact
4. **Wire to control board** - Connect to appropriate terminals

**Typical locations:**
- Brew boiler: Side or top of brew boiler
- Steam boiler: Side or top of steam boiler

#### Group Head Thermocouple

1. **Locate port** - Find M4 threaded port on group head
2. **Install thermocouple** - Thread K-type thermocouple into port
3. **Wire to control board** - Connect to thermocouple input

#### Pressure Transducer

1. **Locate port** - Find 1/8" BSP port on group head or brew path
2. **Install transducer** - Thread pressure transducer into port
3. **Wire to control board** - Connect to analog input

#### Water Level Sensors

1. **Install level probe** - Mount in steam boiler (for dual boiler/HX)
2. **Install tank sensor** - Mount in water reservoir
3. **Wire to control board** - Connect to digital inputs

### Step 4: Wire Control Board

#### Power Input

1. **Mains input** (J1):
   - L (Live) → Control board L terminal
   - N (Neutral) → Control board N terminal
   - PE (Ground) → Control board PE terminal

2. **Verify isolation** - Check 6mm creepage/clearance between HV and LV sections

#### Relay Outputs

1. **Indicator lamp** (J2):
   - Connect lamp to J2-NO terminal
   - Common to fused live bus

2. **Pump** (J3):
   - Connect pump to J3-NO terminal
   - Common to fused live bus

3. **Solenoid** (J4):
   - Connect solenoid to J4-NO terminal
   - Common to fused live bus

#### SSR Triggers

1. **Brew heater SSR** (SSR1):
   - Connect SSR trigger to control board SSR1 output
   - External SSR handles heater power (does NOT flow through PCB)

2. **Steam heater SSR** (SSR2):
   - Connect SSR trigger to control board SSR2 output
   - External SSR handles heater power (does NOT flow through PCB)

**Important:** Heater power does NOT flow through the control board. External SSRs connect directly to mains.

#### Sensor Connections

1. **Temperature sensors** - Connect to J26 unified terminal:
   - Brew NTC → T1 terminal
   - Steam NTC → T2 terminal
   - Group thermocouple → Thermocouple input

2. **Pressure transducer** - Connect to PSG terminal

3. **Digital inputs** - Connect to J26:
   - Water switch → S1
   - Tank level → S2
   - Brew handle → S3
   - Steam level → S4

### Step 5: Install ESP32 Display Module

1. **Mount ESP32 module** - Install in front panel or external enclosure
2. **Connect to J15** - Wire ESP32 to control board J15 connector:
   - 5V → Pin 1
   - GND → Pin 2
   - TX → Pin 4 (ESP32 TX to Pico RX)
   - RX → Pin 3 (ESP32 RX to Pico TX)
   - RUN → Pin 5 (optional, for reset control)
   - WEIGHT_STOP → Pin 7 (for brew-by-weight)

3. **Verify connections** - Check all wiring before powering on

### Step 6: Verify Installation

Before powering on:

1. **Visual inspection**:
   - All connections secure
   - No loose wires
   - Proper clearance maintained
   - No damaged components

2. **Continuity check** (with power OFF):
   - Verify sensor connections
   - Check relay outputs
   - Verify SSR triggers

3. **Insulation check**:
   - Verify HV/LV isolation
   - Check for shorts
   - Verify ground connections

## Wiring Diagrams

### J26 Unified Terminal (18-pin)

```
┌───┬───┬───┬───┬───┬───┬───┬───┬───┬───┬───┬───┬───┬───┬───┬───┬───┬───┐
│ 1 │ 2 │ 3 │ 4 │ 5 │ 6 │ 7 │ 8 │ 9 │10 │11 │12 │13 │14 │15 │16 │17 │18 │
│S1 │GND│S2 │GND│S3 │S4 │GND│T1 │GND│T2 │GND│5V │GND│PSG│5V │SR-│5V │SR-│
└───┴───┴───┴───┴───┴───┴───┴───┴───┴───┴───┴───┴───┴───┴───┴───┴───┴───┘
 │       │       │   │       │       │       └─Press─┘ └SSR1─┘ └SSR2─┘
 Water   Tank   Lvl Brew    Brew    Steam
 Switch  Level  Prb Handle  NTC     NTC
```

### J15 ESP32 Connector (8-pin)

| Pin | Signal | Description |
|-----|--------|-------------|
| 1 | 5V | Power supply for ESP32 |
| 2 | GND | Common ground |
| 3 | TX | Pico TX → ESP32 RX |
| 4 | RX | ESP32 TX → Pico RX |
| 5 | RUN | Reset control (optional) |
| 6 | SPARE1 | Future use |
| 7 | WEIGHT_STOP | Brew-by-weight signal |
| 8 | SPARE2 | Future use |

## Machine-Specific Considerations

### Dual Boiler Machines
- Two independent boilers
- Separate temperature sensors for each
- Independent SSR triggers

### Single Boiler Machines
- One boiler for both brewing and steaming
- Single temperature sensor
- Single SSR trigger

### Heat Exchanger Machines
- Steam boiler with HX for brew water
- Steam boiler sensor required
- Group head sensor recommended

See [Machine-Specific Guides](../05-Machine-Specific/) for detailed configuration.

## Safety Checklist

Before first power-on:

- ✅ Power disconnected
- ✅ All connections verified
- ✅ No shorts detected
- ✅ Ground connections verified
- ✅ HV/LV isolation confirmed
- ✅ Fuses installed correctly
- ✅ Sensors properly installed
- ✅ Wiring secured and protected

## Next Steps

After hardware installation:

1. **Do NOT power on yet** - Complete firmware flashing first
2. **Proceed to**: [Firmware Flashing](Firmware-Flashing.md)
3. **Then**: [Initial Setup](Initial-Setup.md)

## Troubleshooting

If you encounter issues:

- Check [Troubleshooting Installation](Troubleshooting-Installation.md)
- Verify all connections
- Review wiring diagrams
- Check sensor types match configuration

---

**Next:** [Firmware Flashing](Firmware-Flashing.md)

