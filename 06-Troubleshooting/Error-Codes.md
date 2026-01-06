# Error Codes

Reference guide for BrewOS error codes and their meanings.

## Overview

BrewOS uses error codes to indicate specific problems. Error codes are displayed in:
- Web interface logs
- Serial output
- Diagnostic pages
- Error notifications

## Error Code Format

Error codes typically follow format: `ERR_XXX` or numeric codes.

## Common Error Codes

### Communication Errors

**ERR_COMM_TIMEOUT**
- **Meaning**: Communication timeout between Pico and ESP32
- **Causes**: UART wiring issue, baud rate mismatch, power issue
- **Solutions**: Check UART wiring, verify baud rate, check power

**ERR_COMM_CRC**
- **Meaning**: CRC checksum error in communication
- **Causes**: Electrical interference, wiring issue, baud rate
- **Solutions**: Check wiring, verify baud rate, check for interference

**ERR_COMM_DISCONNECTED**
- **Meaning**: Pico disconnected from ESP32
- **Causes**: UART wiring, power issue, firmware issue
- **Solutions**: Check UART wiring, verify power, check firmware

### Sensor Errors

**ERR_SENSOR_READ_FAIL**
- **Meaning**: Failed to read sensor
- **Causes**: Sensor wiring, sensor failure, ADC issue
- **Solutions**: Check sensor wiring, test sensor, check ADC

**ERR_SENSOR_OUT_OF_RANGE**
- **Meaning**: Sensor reading out of valid range
- **Causes**: Sensor failure, wiring issue, incorrect sensor type
- **Solutions**: Check sensor, verify wiring, check sensor type

**ERR_TEMP_SENSOR_FAIL**
- **Meaning**: Temperature sensor failure
- **Causes**: Sensor failure, wiring issue, thermal contact
- **Solutions**: Check sensor, verify wiring, check installation

### Safety Errors

**ERR_OVERTEMP**
- **Meaning**: Over-temperature detected
- **Causes**: SSR stuck on, sensor failure, PID issue
- **Solutions**: Check SSR, verify sensor, check PID, safety shutdown

**ERR_WATER_LOW**
- **Meaning**: Low water level detected
- **Causes**: Empty water tank, level sensor issue
- **Solutions**: Fill water tank, check level sensor

**ERR_WATCHDOG**
- **Meaning**: Watchdog timer expired
- **Causes**: System hang, firmware issue, hardware problem
- **Solutions**: Power cycle, check firmware, review logs

### System Errors

**ERR_FLASH_WRITE**
- **Meaning**: Flash write failed
- **Causes**: Flash full, flash corruption, filesystem issue
- **Solutions**: Check flash space, reformat filesystem, check logs

**ERR_FILESYSTEM**
- **Meaning**: Filesystem error
- **Causes**: Filesystem corruption, flash issue
- **Solutions**: Reformat filesystem, check flash, restore defaults

**ERR_MEMORY**
- **Meaning**: Memory allocation failed
- **Causes**: Memory leak, insufficient memory
- **Solutions**: Restart system, check for memory leaks

## Error Severity

### Critical Errors
- Require immediate attention
- Machine enters safe state
- May require power cycle
- Examples: ERR_OVERTEMP, ERR_WATCHDOG

### Warning Errors
- Indicate potential issues
- Machine continues operation
- Should be investigated
- Examples: ERR_SENSOR_READ_FAIL, ERR_COMM_TIMEOUT

### Informational
- Status information
- No action required
- For monitoring
- Examples: Connection status, state changes

## Error Handling

### Automatic Handling

- **Safe state**: Machine enters safe state on critical errors
- **Retry**: Some errors trigger automatic retry
- **Logging**: All errors are logged
- **Notification**: Critical errors trigger notifications

### Manual Handling

- **Review logs**: Check error logs for details
- **Diagnostics**: Use diagnostic tools
- **Reset**: Power cycle if needed
- **Support**: Contact support if issue persists

## Troubleshooting Errors

### Steps

1. **Identify error code**: Note exact error code
2. **Check meaning**: Refer to this guide
3. **Review logs**: Check detailed error logs
4. **Check diagnostics**: Use diagnostic tools
5. **Apply solutions**: Try recommended solutions
6. **Document**: Note what worked

### Getting Help

If error persists:
- Document error code and context
- Review [Common Issues](Common-Issues.md)
- Use [Diagnostics](Diagnostics.md) tools
- See [Getting Help](Getting-Help.md)

## Related Documentation

- [Common Issues](Common-Issues.md) - Common problems
- [Diagnostics](Diagnostics.md) - Diagnostic tools
- [Getting Help](Getting-Help.md) - Support resources

---

**Next:** [Diagnostics](Diagnostics.md) or [Getting Help](Getting-Help.md)

