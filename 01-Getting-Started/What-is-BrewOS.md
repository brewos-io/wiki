# What is BrewOS?

BrewOS is an open-source control system designed to replace factory controllers in espresso machines. It provides enhanced temperature control, real-time monitoring, and modern features while maintaining safety as the top priority.

## Overview

BrewOS transforms your espresso machine into a smart, connected device. Whether you have a dual boiler, single boiler, or heat exchanger machine, BrewOS provides precise control and monitoring capabilities that rival or exceed commercial-grade systems.

## Key Benefits

### 🎯 Precise Temperature Control
- **Sub-degree stability** - PID control maintains temperature within 0.1°C
- **Independent boiler control** - Separate brew and steam boiler management
- **Group head monitoring** - Real-time temperature tracking at the group head

### 📱 Modern Connectivity
- **WiFi enabled** - Monitor and control from any device
- **Progressive Web App** - Install on phone, tablet, or computer
- **Cloud access** - Control your machine from anywhere
- **Home Assistant integration** - Native MQTT support with auto-discovery

### 🛡️ Safety First
- **Hardware watchdog** - Automatic shutdown on system failure
- **Water level protection** - Prevents dry heating
- **Over-temperature protection** - Automatic shutdown at 165°C
- **Fail-safe design** - Multiple safety layers protect your machine

### 📊 Data & Insights
- **Shot statistics** - Track every shot with temperature and pressure data
- **Power monitoring** - Monitor energy consumption (with optional power meter)
- **Temperature graphs** - Real-time and historical temperature visualization
- **Brew counter** - Automatic cleaning reminders

### 🔄 Convenience Features
- **OTA updates** - Update firmware wirelessly
- **Scheduling** - Auto-on/off schedules for daily routines
- **Eco mode** - Energy-saving idle mode
- **Brew by weight** - Integrated scale support for precision brewing

## System Architecture

BrewOS uses a multi-layer architecture:

| Layer | Components | Purpose |
|-------|------------|---------|
| **Cloud** | Google OAuth, Node.js, SQLite | Remote access via WebSocket relay |
| **ESP32-S3** | WiFi, Web Server, MQTT, BLE, LVGL | Connectivity & UI hub |
| **Pico RP2350** | PID, Boiler, Pump, Valve control | Real-time machine control |
| **Hardware** | SSRs, Sensors, Valves | Physical machine interface |

### How It Works

1. **Pico RP2350** - Handles all real-time machine control (PID loops, safety systems, sensor reading)
2. **ESP32-S3** - Manages connectivity (WiFi, web server, MQTT) and provides the user interface
3. **Communication** - High-speed UART (921600 baud) connects the two microcontrollers
4. **Web Interface** - Accessible via local network or cloud service

## Supported Machines

BrewOS supports three main machine architectures:

- **Dual Boiler** - Separate brew and steam boilers (e.g., ECM Synchronika, Profitec Pro 700)
- **Single Boiler** - One boiler for both brewing and steaming (e.g., ECM Barista, Profitec Pro 300)
- **Heat Exchanger** - Steam boiler with heat exchanger for brew water (e.g., ECM Mechanika, Profitec Pro 500)

See [Compatibility List](../05-Machine-Specific/Compatibility-List.md) for a complete list of supported machines.

## What You Get

### Hardware
- Custom control board (replaces factory PID controller)
- ESP32-S3 display module (optional, for on-machine display)
- All necessary sensors and wiring

### Software
- Real-time firmware for machine control
- Web-based user interface (Progressive Web App)
- Cloud service for remote access (optional)
- Home Assistant integration

### Features
- Precise PID temperature control
- Shot timer with statistics
- Pre-infusion support
- Brew by weight (with compatible scales)
- Scheduling and automation
- Energy monitoring
- Push notifications
- And much more!

## Who Is BrewOS For?

BrewOS is perfect for:
- **Espresso enthusiasts** who want better control and monitoring
- **Home baristas** looking to upgrade their machine's capabilities
- **DIY enthusiasts** comfortable with electronics and firmware
- **Home automation users** who want to integrate their machine into smart home systems

## Getting Started

Ready to get started? Here's what you need to do:

1. **Check compatibility** - See [System Requirements](System-Requirements.md)
2. **Install hardware** - Follow [Hardware Installation](../02-Installation-Setup/Hardware-Installation.md)
3. **Flash firmware** - See [Firmware Flashing](../02-Installation-Setup/Firmware-Flashing.md)
4. **Configure** - Complete [Initial Setup](../02-Installation-Setup/Initial-Setup.md)

## Learn More

- [System Requirements](System-Requirements.md) - Check if your machine is compatible
- [Quick Start Guide](Quick-Start-Guide.md) - Fast-track setup
- [Features](../04-Features/) - Detailed feature documentation
- [Installation & Setup](../02-Installation-Setup/) - Complete installation guide

---

**Next:** [System Requirements](System-Requirements.md)

