# Power Metering

BrewOS supports power monitoring with the PZEM-004T power meter module for tracking energy consumption. This feature allows you to understand how much energy your espresso machine uses, identify high-consumption periods, and optimize your usage patterns to save money.

## Overview

Power metering provides comprehensive energy monitoring:

- **Real-time power** - Current power consumption in watts (updated every second)
- **Energy tracking** - Daily and total energy usage in kilowatt-hours (kWh)
- **Voltage monitoring** - Line voltage reading to detect power issues
- **Current monitoring** - Current draw in amperes to understand electrical load
- **Cost tracking** - Estimate energy costs based on your electricity rate
- **Power factor** - Measure electrical efficiency
- **Historical data** - Track energy usage over time

## Why Power Metering Matters

**Understanding Your Machine's Energy Use:**

- Espresso machines are significant energy consumers (1500-4000W heaters)
- Knowing actual consumption helps you understand operating costs
- Identifies opportunities for energy savings
- Helps optimize schedules and eco mode usage

**Real-World Impact:**

- A machine left on 12 hours/day can cost $300-600/year in electricity
- Eco mode can reduce this by 50-70%
- Scheduling can reduce idle time and save energy
- Power metering provides data to make informed decisions

**Optimization Opportunities:**

- See which heating strategies use more power
- Understand eco mode savings in real-time
- Identify if schedules are working effectively
- Track cost impact of usage changes

## Hardware Setup

### PZEM-004T Module

The PZEM-004T is a Modbus-based power meter that provides accurate energy measurements:

**Technical Specifications:**

- **Voltage range**: 80-260V AC (works worldwide)
- **Current range**: 0-100A (with appropriate current transformer)
- **Communication**: Modbus RTU over TTL/RS485 serial
- **Accuracy**: ±1% voltage, ±2% current (highly accurate)
- **Update rate**: 1 reading per second
- **Power calculation**: Real power (W), apparent power (VA), power factor

**How It Works:**

- The PZEM-004T uses a current transformer (CT) to measure current without direct connection
- Voltage is measured directly across the line
- Power is calculated as: Power (W) = Voltage (V) × Current (A) × Power Factor
- Energy is accumulated over time: Energy (kWh) = Power (W) × Time (hours) / 1000

**What It Measures:**

- **Voltage (V)**: Line voltage (typically 110V, 120V, 220V, or 240V depending on region)
- **Current (A)**: Current draw through the CT
- **Power (W)**: Real power consumption (what you pay for)
- **Energy (kWh)**: Total energy consumed (accumulated over time)
- **Frequency (Hz)**: AC frequency (50Hz or 60Hz)
- **Power Factor**: Electrical efficiency (0.0 to 1.0, higher is better)

### Current Transformer (CT) Options

The PZEM-004T requires a current transformer to measure current. Different CT options are available:

**PZEM-004T with Built-in CT (100A):**

- **Range**: 0-100A
- **Best for**: Most home espresso machines (typically 10-20A)
- **Installation**: Clamp around live wire
- **Non-invasive**: No need to break the circuit

**PZEM-004T with External CT:**

- **Lower range CTs**: Available for 5A, 10A, 20A, 30A (more accurate at lower currents)
- **Higher range CTs**: Available for 200A, 300A (for commercial machines)
- **Accuracy**: Smaller range CTs are more accurate for low-current applications
- **Selection**: Choose CT based on your machine's maximum current draw

**CT Selection Guide:**

- **5-10A CT**: Single boiler machines, low-power setups
- **20-30A CT**: Most dual boiler home machines (recommended)
- **50-100A CT**: High-power commercial machines or whole-house monitoring

### Wiring

**1. Power Connections:**

- **Line (L)**: Connect to live/hot wire of your machine's power supply
- **Neutral (N)**: Connect to neutral wire
- **Ground**: Connect to ground (for safety)
- **CT Installation**: Clamp CT around the live wire (only one wire, not both)
- **Direction matters**: CT has arrow indicating current flow direction
- **Isolation**: PZEM provides electrical isolation (safe)

**2. Communication Connections:**

- **UART Connection**: Connect to ESP32 UART1
  - **TX (PZEM) → RX (ESP32 GPIO7)**: Data from PZEM to ESP32
  - **RX (PZEM) → TX (ESP32 GPIO6)**: Data from ESP32 to PZEM
  - **GND**: Common ground between PZEM and ESP32
- **Voltage levels**: PZEM uses 5V TTL, ESP32 uses 3.3V (may need level shifter)
- **Baud rate**: 9600 baud (Modbus RTU standard)
- **RS485 option**: If using RS485 version, connect A/B lines to RS485 adapter

**3. Safety Considerations:**

- ⚠️ **MAINS VOLTAGE** - Exercise extreme caution
- **Qualified installer**: Only qualified electricians should install
- **Power off**: Always disconnect power before installation
- **Proper grounding**: Ensure proper grounding
- **Isolation**: PZEM provides isolation, but follow all safety guidelines
- **Code compliance**: Follow local electrical codes
- **Inspection**: Consider having installation inspected

**Installation Steps:**

1. **Power off** the machine and disconnect from mains
2. **Identify wires**: Locate live, neutral, and ground wires
3. **Install CT**: Clamp CT around live wire (arrow pointing toward machine)
4. **Connect PZEM**: Wire PZEM in parallel (doesn't break the circuit)
5. **Connect communication**: Wire to ESP32 UART1
6. **Verify connections**: Double-check all connections
7. **Power on**: Restore power and test
8. **Calibrate**: Calibrate if readings seem inaccurate

## Configuration

### Enable Power Metering

1. **In settings**:

   - Go to Settings → Power Meter
   - Enable "Power Metering"
   - Configure Modbus address (default: 1)
     - **Modbus address**: Each PZEM has an address (1-247)
     - **Default**: Address 1 (factory default)
     - **Multiple devices**: If using multiple PZEMs, each needs unique address
     - **Change address**: Can be changed via Modbus commands if needed
   - Save settings

2. **Verification**:
   - Check that readings appear in dashboard
   - Verify voltage reading matches your line voltage
   - Check that current reading is reasonable (0A when off, 5-20A when heating)
   - Power should be approximately voltage × current

### Calibration

**When Calibration is Needed:**

- Readings don't match known values
- Voltage reading is significantly off
- Current reading seems incorrect
- Power calculation seems wrong

**Voltage Calibration:**

- Compare PZEM voltage reading to known good voltmeter
- Adjust calibration factor if needed
- Typical accuracy: ±1% (usually doesn't need calibration)

**Current Calibration:**

- Compare to clamp meter reading
- Adjust calibration factor if needed
- CT accuracy: ±2% (usually accurate enough)
- **Important**: Ensure CT is properly installed (direction, single wire)

**Power Factor Adjustment:**

- Power factor affects real power calculation
- Typical for resistive loads (heaters): 0.95-1.0
- Lower power factor = less efficient
- Adjust if power readings seem low

**Calibration Process:**

1. Measure with known good meter (voltmeter, clamp meter)
2. Compare readings
3. Calculate calibration factor: `factor = actual_value / measured_value`
4. Apply factor in settings
5. Verify improved accuracy

### Display Options

**Dashboard Power Card:**

- **Show Power Card**: Display power consumption in dashboard
- **Real-time updates**: Updates every second
- **Visual indicators**: Color coding for power levels
- **Quick reference**: See power at a glance

**Daily Usage Tracking:**

- **Daily Usage**: Track energy consumed today (kWh)
- **Reset**: Resets at midnight (local time)
- **History**: View daily usage over time
- **Trends**: Identify high-usage days

**Cost Estimation:**

- **Electricity Rate**: Set your local rate ($/kWh)
- **Daily Cost**: Calculate cost for today
- **Monthly Estimate**: Project monthly cost
- **Annual Estimate**: Estimate yearly cost
- **Savings Tracking**: Compare costs with/without eco mode

**Statistics Integration:**

- Power data integrated with shot statistics
- See energy per shot
- Track energy efficiency
- Identify high-consumption periods

## Usage

### Dashboard Display

Power card shows:

- **Current Power** - Real-time consumption (W)
- **Daily Usage** - Energy used today (kWh)
- **Voltage** - Line voltage (V)
- **Current** - Current draw (A)

### Statistics

Power statistics include:

- **Daily energy** - kWh used today
- **Total energy** - Lifetime energy usage
- **Average power** - Average consumption
- **Peak power** - Maximum power draw

### Cost Tracking

Estimate energy costs:

- **Daily cost** - Cost for today
- **Monthly estimate** - Projected monthly cost
- **Rate configuration** - Set electricity rate

## Best Practices

### Installation

- **Proper CT sizing** - Use appropriate current transformer
- **Secure connections** - Ensure all connections are secure
- **Calibration** - Calibrate if readings seem inaccurate
- **Safety first** - Follow all safety guidelines

### Monitoring

- **Track usage** - Monitor daily energy usage
- **Identify patterns** - Find high-consumption periods
- **Optimize schedules** - Use data to optimize schedules
- **Cost awareness** - Understand energy costs

## Troubleshooting

### No Readings

- **Check wiring** - Verify all connections
- **Check Modbus** - Verify Modbus communication
- **Check address** - Verify Modbus address is correct
- **Check power** - Verify PZEM is powered

### Inaccurate Readings

- **Calibrate** - Use calibration settings
- **Check CT** - Verify current transformer is correct size
- **Check connections** - Loose connections cause issues
- **Review installation** - Verify proper installation

### Communication Errors

- **Check UART** - Verify UART connections
- **Check baud rate** - Verify Modbus baud rate
- **Check wiring** - Verify communication wiring
- **Review logs** - Check for Modbus errors

## Related Features

- [Statistics](Statistics.md) - Energy statistics
- [Eco Mode](Eco-Mode.md) - Energy saving
- [Scheduling](Scheduling.md) - Optimize schedules

---

**Next:** [OTA Updates](OTA-Updates.md)
