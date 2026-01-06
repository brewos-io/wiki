# System Requirements

Before installing BrewOS, ensure your espresso machine and hardware meet these requirements.

## Machine Compatibility

BrewOS supports three main machine architectures:

### ✅ Dual Boiler
- Separate brew and steam boilers
- Independent temperature control
- Examples: ECM Synchronika, Profitec Pro 700, Lelit Bianca

### ✅ Single Boiler
- One boiler for both brewing and steaming
- Temperature surfing required
- Examples: ECM Barista, Profitec Pro 300, Rancilio Silvia

### ✅ Heat Exchanger (HX)
- Steam boiler with heat exchanger for brew water
- Simultaneous brew and steam capability
- Examples: ECM Mechanika, Profitec Pro 500, E61 HX machines

## Validated Machines

The following machines have been fully tested and confirmed working:

| Brand | Model | Boiler Type | Notes |
|-------|-------|-------------|-------|
| ECM | **Synchronika** | Dual Boiler | **Reference machine** - Primary development platform |

## Expected Compatible Machines

These machines use the same PID controller and GICAR board as the Synchronika and should work with minimal or no modification:

### ECM (Same Platform)
- Barista (Single Boiler)
- Technika (Heat Exchanger)
- Technika Profi (Heat Exchanger)
- Mechanika (Heat Exchanger)
- Mechanika Profi (Heat Exchanger)
- Mechanika V Slim (Heat Exchanger)
- Controvento (Dual Boiler)

### Profitec (Same Platform)
- Pro 300 (Single Boiler)
- Pro 500 (Heat Exchanger)
- Pro 700 (Dual Boiler)

> **Note:** ECM and Profitec share the same parent company and use identical electronics.

## Other Compatible Machines

Many other E61 group head machines may be compatible but require custom wiring configuration. See the [Compatibility List](../05-Machine-Specific/Compatibility-List.md) for a complete list.

## Hardware Requirements

### Required Components

1. **BrewOS Control Board**
   - Raspberry Pi Pico 2 (RP2350) based
   - Replaces factory PID controller
   - Includes all necessary relays and drivers

2. **ESP32-S3 Display Module** (Optional but recommended)
   - Provides WiFi connectivity
   - Web server for local access
   - Optional on-machine display

3. **Sensors**
   - NTC thermistors for boiler temperature (typically 100K or 50K)
   - K-type thermocouple for group head (M4 thread)
   - Pressure transducer (0-16 bar, 1/8" BSP)
   - Water level sensors

4. **Power Supply**
   - 100-240V AC, 50/60Hz input
   - 5V DC (3A) and 3.3V DC (500mA) outputs
   - Included in control board

### Optional Components

- **Power Meter** (PZEM-004T) - For energy monitoring
- **Bluetooth Scale** - For brew by weight feature
- **Home Assistant** - For smart home integration

## Electrical Requirements

### Input Power
- **Voltage**: 100-240V AC
- **Frequency**: 50/60Hz
- **Current**: Depends on machine (typically 10-20A)

### Outputs
- **Relay outputs**: 3× relays (lamp, pump, solenoid)
- **SSR triggers**: 2× for heater control (external SSRs required)
- **Isolation**: 3000V AC (reinforced)

## Physical Requirements

### Control Board
- **Size**: 80mm × 80mm (target)
- **Mounting**: Replaces factory GICAR board
- **Connectors**: Bottom edge mounting (prevents water ingress)

### ESP32 Display Module
- **Size**: Varies by display size (typically 2.1" or 2.8")
- **Mounting**: Front panel or external enclosure
- **Connections**: UART to control board, power

## Prerequisites

### Skills Required
- **Basic electronics knowledge** - Understanding of wiring and safety
- **Soldering** - For sensor installation (if not pre-wired)
- **Firmware flashing** - Using USB or web interface
- **Network configuration** - WiFi setup

### Tools Needed
- Soldering iron (if custom wiring)
- Multimeter (for testing)
- USB cable (for firmware flashing)
- Computer or smartphone (for initial setup)

### Safety Requirements

⚠️ **CRITICAL: MAINS VOLTAGE WORK**

This project involves 100-240V AC mains electricity. Improper handling can result in death or serious injury.

**Only qualified individuals should work on mains circuits.**

- Always disconnect power before making changes
- Use isolation transformers during development
- Never work alone on energized equipment
- Follow all local electrical codes and regulations

## Software Requirements

### For Firmware Flashing
- **Computer**: Windows, macOS, or Linux
- **USB cable**: For connecting to Pico and ESP32
- **Web browser**: For accessing the web interface

### For Web Interface
- **Modern web browser**: Chrome, Firefox, Safari, or Edge (latest versions)
- **WiFi connection**: For local network access
- **Optional**: Cloud account for remote access

## Network Requirements

### Local Network
- **WiFi**: 2.4GHz or 5GHz (ESP32 supports 2.4GHz)
- **Router**: Standard home router
- **IP address**: DHCP or static (configurable)

### Cloud Access (Optional)
- **Internet connection**: Required for remote access
- **Google account**: For authentication (if using cloud service)

## Checking Your Machine

Before purchasing or installing BrewOS:

1. **Verify machine type** - Dual boiler, single boiler, or heat exchanger?
2. **Check compatibility** - See [Compatibility List](../05-Machine-Specific/Compatibility-List.md)
3. **Review wiring** - Ensure standard E61 group head and sensors
4. **Assess skills** - Confirm you can safely work with mains voltage

## Next Steps

Once you've verified your machine is compatible:

- **Quick Start**: Follow the [Quick Start Guide](Quick-Start-Guide.md)
- **Full Installation**: Proceed to [Installation & Setup](../02-Installation-Setup/)
- **Machine-Specific**: See [Machine-Specific Guides](../05-Machine-Specific/) for your machine type

---

**Next:** [Quick Start Guide](Quick-Start-Guide.md) or [Installation & Setup](../02-Installation-Setup/)

