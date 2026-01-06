# Hardware Architecture

BrewOS uses a dual-microcontroller architecture that separates connectivity and user interface from real-time machine control. This design provides better performance, reliability, and user experience compared to single-controller solutions.

## Overview

BrewOS consists of two main hardware components:

- **Raspberry Pi Pico RP2350** - Internal control board handling all real-time machine operations
- **ESP32-S3 Display Module** - External module with screen, located on top of the machine for connectivity and user interface

These two microcontrollers communicate via high-speed UART, allowing each to focus on its specialized role.

## Why Separate ESP and Pico?

The separation of ESP32-S3 and Raspberry Pi Pico provides several key advantages:

### Specialized Roles

**Raspberry Pi Pico RP2350:**
- **Real-time control** - Handles critical timing-sensitive operations
- **PID loops** - Precise temperature control with sub-millisecond response
- **Safety systems** - Hardware watchdog and fail-safe mechanisms
- **Sensor reading** - High-frequency sensor sampling
- **Machine control** - Direct control of pumps, valves, and heaters

**ESP32-S3:**
- **Connectivity** - WiFi, MQTT, and cloud communication
- **User interface** - Web server and display rendering
- **Network protocols** - HTTP, WebSocket, MQTT handling
- **Bluetooth** - BLE support for local configuration

### Performance Benefits

- **No interference** - Network operations don't interrupt critical control loops
- **Independent operation** - Each microcontroller runs at optimal speed for its tasks
- **Better responsiveness** - UI updates don't affect machine control timing
- **Reliability** - Network issues don't impact safety-critical systems

### Development Benefits

- **Modular design** - Each component can be developed and updated independently
- **Easier debugging** - Issues isolated to specific components
- **Flexible updates** - OTA updates for ESP32 don't require reflashing control board
- **Future-proof** - Easy to upgrade or replace individual components

## ESP32-S3 Display Module

### External Location

The ESP32-S3 module is designed to be **external** and mounted **on top of the machine** for several important reasons:

#### Better WiFi Signal

- **Line of sight** - Elevated position provides better signal propagation
- **Reduced interference** - Away from metal chassis and electrical noise
- **Antenna placement** - Optimal antenna positioning for maximum range
- **Reliable connectivity** - Consistent WiFi connection even in challenging environments

#### User Experience

- **Easy access** - Display visible without opening machine
- **Convenient interaction** - Physical controls accessible during use
- **Status visibility** - Real-time information always visible
- **Professional appearance** - Clean, modern interface on machine top

#### Practical Benefits

- **Easy installation** - No need to route display cables through machine internals
- **Simple maintenance** - Module can be accessed without opening machine
- **Upgrade path** - Easy to replace or upgrade display module
- **Cable management** - Single cable connection to control board

### Display Screen

The ESP32-S3 module uses the **UEDX48480021-MD80E** display for several practical reasons:

#### Cost and Availability

- **Affordable** - Low-cost display solution keeps overall system cost down
- **Widely available** - Common display module, easy to source
- **Supply chain** - Readily available from multiple suppliers
- **Community support** - Popular display with good community resources

#### Technical Specifications

- **480x800 resolution** - Clear, readable display for UI elements
- **Touch support** - Capacitive touch for user interaction
- **Good visibility** - Bright display suitable for kitchen environments
- **Reliable** - Proven display technology with good reliability

#### Design Considerations

- **Size** - Appropriate size for machine-top mounting
- **Interface** - Compatible with ESP32-S3 display interfaces
- **Power** - Efficient power consumption suitable for embedded use
- **Durability** - Suitable for kitchen environment use

## System Communication

### UART Communication

The ESP32-S3 and Pico communicate via high-speed UART:

- **Baud rate** - 921600 baud for fast data transfer
- **Protocol** - Custom binary protocol optimized for real-time data
- **Bidirectional** - Full duplex communication
- **Reliable** - Error detection and retry mechanisms

### Data Flow

**Pico → ESP32:**
- Machine status (temperature, pressure, state)
- Sensor readings
- Error conditions
- Safety status

**ESP32 → Pico:**
- User commands (power on/off, temperature setpoints)
- Configuration changes
- Brew commands
- Settings updates

## Physical Layout

### Control Board (Pico RP2350)

**Location:** Inside machine, replacing factory controller

**Responsibilities:**
- All machine control functions
- Safety systems
- Sensor interfaces
- Power management

**Connections:**
- Mains power input
- Heater SSRs
- Relays (pump, solenoid, lamp)
- Sensors (temperature, pressure, level)
- ESP32 module (via J15 connector)

### ESP32-S3 Module

**Location:** External, on top of machine

**Responsibilities:**
- WiFi connectivity
- Web server
- Display rendering
- User input handling

**Connections:**
- Control board (via J15 connector)
- Display (integrated)
- WiFi antenna (integrated)
- Power (from control board)

## Benefits of This Architecture

### Reliability

- **Isolation** - Network issues don't affect machine control
- **Redundancy** - Each system can operate independently
- **Safety** - Critical systems isolated from network stack
- **Stability** - Specialized firmware for each role

### Performance

- **Real-time guarantees** - Pico ensures timing-critical operations
- **Responsive UI** - ESP32 dedicated to user interface
- **Fast communication** - High-speed UART for low latency
- **Efficient resource use** - Each microcontroller optimized for its role

### User Experience

- **Always accessible** - Display always visible and accessible
- **Reliable connectivity** - Better WiFi signal for consistent connection
- **Modern interface** - Full-featured web interface and local display
- **Remote access** - Cloud connectivity for remote monitoring

### Maintainability

- **Modular updates** - Update components independently
- **Easy troubleshooting** - Issues isolated to specific components
- **Future-proof** - Easy to upgrade individual components
- **Community support** - Standard components with good documentation

## Related Documentation

- [What is BrewOS?](What-is-BrewOS.md) - System overview
- [System Requirements](System-Requirements.md) - Hardware requirements
- [Hardware Installation](../02-Installation-Setup/Hardware-Installation.md) - Installation guide
- [WiFi Connectivity](../04-Features/WiFi-Connectivity.md) - WiFi setup and configuration

---

**Next:** [System Requirements](System-Requirements.md) or [What is BrewOS?](What-is-BrewOS.md)


