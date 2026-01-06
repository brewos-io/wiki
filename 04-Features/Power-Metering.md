# Power Metering

BrewOS supports power monitoring with the PZEM-004T power meter module for tracking energy consumption.

## Overview

Power metering provides:
- **Real-time power** - Current power consumption
- **Energy tracking** - Daily and total energy usage
- **Voltage monitoring** - Line voltage reading
- **Cost tracking** - Estimate energy costs

## Hardware Setup

### PZEM-004T Module

The PZEM-004T is a Modbus-based power meter:
- **Voltage range**: 80-260V AC
- **Current range**: 0-100A (with appropriate CT)
- **Communication**: Modbus RTU over TTL/RS485
- **Accuracy**: ±1% voltage, ±2% current

### Wiring

1. **Power connections**:
   - Connect PZEM to mains (L, N)
   - Connect current transformer (CT) around live wire
   - Ensure proper isolation

2. **Communication**:
   - Connect to ESP32 UART1 (GPIO6/7)
   - Use TTL or RS485 adapter if needed
   - Connect GND for common ground

3. **Safety**:
   - ⚠️ **MAINS VOLTAGE** - Exercise extreme caution
   - Only qualified individuals should install
   - Follow all safety guidelines

## Configuration

### Enable Power Metering

1. **In settings**:
   - Go to Settings → Power Meter
   - Enable "Power Metering"
   - Configure Modbus address (default: 1)
   - Save settings

2. **Calibration** (if needed):
   - Voltage calibration
   - Current calibration
   - Power factor adjustment

### Display Options

- **Show Power Card** - Display power in dashboard
- **Daily Usage** - Track daily consumption
- **Cost Estimation** - Calculate energy costs

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

