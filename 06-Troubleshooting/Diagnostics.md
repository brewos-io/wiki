# Diagnostics

Using diagnostic tools and logs to troubleshoot BrewOS issues.

## Diagnostic Tools

### Web Interface Diagnostics

Access via Settings → Diagnostics or Logs:

1. **System Status**:
   - Overall system health
   - Connection status
   - Error indicators

2. **Sensor Readings**:
   - All sensor values
   - Real-time updates
   - Historical data

3. **Connection Status**:
   - Pico connection status
   - ESP32 connection status
   - WiFi status

4. **Error Log**:
   - Recent errors
   - Error codes
   - Timestamps

### Serial Output

Connect via USB serial for detailed logs:

**ESP32:**
```bash
# Using PlatformIO
pio device monitor

# Or using screen
screen /dev/tty.usbserial-* 115200
```

**Pico:**
```bash
# Using screen
screen /dev/tty.usbmodem* 115200
```

### Log Files

Logs are stored in:
- **Web interface**: Settings → Logs
- **Serial output**: Real-time via USB
- **Filesystem**: Stored on ESP32 flash (if enabled)

## Diagnostic Information

### System Information

- **Firmware versions**: Pico and ESP32 versions
- **Machine type**: Configured machine type
- **Uptime**: System uptime
- **Build date**: Firmware build information

### Connection Status

- **Pico**: Connected/disconnected status
- **ESP32**: WiFi connection status
- **MQTT**: MQTT broker connection (if enabled)
- **Cloud**: Cloud service connection (if enabled)

### Sensor Readings

All sensor values displayed:
- **Temperatures**: Brew, steam, group head
- **Pressure**: Brew pressure
- **Water level**: Tank and boiler levels
- **Power**: Current power, voltage (if meter installed)

### Error Log

Recent errors with:
- **Error code**: Specific error code
- **Timestamp**: When error occurred
- **Context**: Additional error information
- **Severity**: Error severity level

## Using Diagnostics

### Routine Monitoring

- **Check system status** regularly
- **Monitor sensor readings** for anomalies
- **Review error log** for issues
- **Verify connections** are stable

### Troubleshooting

1. **Identify issue**: Note symptoms
2. **Check diagnostics**: Review diagnostic information
3. **Review logs**: Check error logs
4. **Check sensors**: Verify sensor readings
5. **Test connections**: Verify all connections

### Performance Analysis

- **Monitor temperatures**: Check stability
- **Review pressure**: Verify pressure profiles
- **Check power**: Monitor energy usage
- **Analyze trends**: Look for patterns

## Best Practices

### Regular Checks

- **Daily**: Quick status check
- **Weekly**: Review error logs
- **Monthly**: Full diagnostic review
- **As needed**: When issues occur

### Documentation

- **Note issues**: Document problems
- **Track changes**: Note configuration changes
- **Keep logs**: Save important log entries
- **Record solutions**: Note what worked

### Preventive Maintenance

- **Monitor trends**: Watch for gradual changes
- **Check connections**: Verify wiring regularly
- **Review errors**: Address errors promptly
- **Update firmware**: Keep firmware current

## Advanced Diagnostics

### Serial Debugging

For advanced troubleshooting:
- **Enable debug mode**: If available
- **Verbose logging**: More detailed logs
- **Protocol analysis**: Monitor communication
- **Performance metrics**: Detailed performance data

### Network Diagnostics

For network issues:
- **Ping test**: Test connectivity
- **Signal strength**: Check WiFi signal
- **Network scan**: Check available networks
- **Connection test**: Test MQTT/cloud connections

## Related Documentation

- [Common Issues](Common-Issues.md) - Common problems
- [Error Codes](Error-Codes.md) - Error reference
- [Getting Help](Getting-Help.md) - Support resources

---

**Next:** [Getting Help](Getting-Help.md)

