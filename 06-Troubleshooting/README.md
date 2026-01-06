# Troubleshooting

This section helps you diagnose and resolve common issues with BrewOS.

## Contents

- [Common Issues](Common-Issues.md) - Frequently encountered problems and solutions
- [Error Codes](Error-Codes.md) - Error code reference and meanings
- [Diagnostics](Diagnostics.md) - Using diagnostic tools and logs
- [Getting Help](Getting-Help.md) - Community resources and support

## Quick Troubleshooting

### Machine Won't Turn On
- Check power connection
- Verify control board power
- Check for errors in logs
- Review [Common Issues](Common-Issues.md)

### No Temperature Readings
- Check sensor wiring
- Verify sensor types match configuration
- Review [Diagnostics](Diagnostics.md)
- Check [Error Codes](Error-Codes.md)

### Communication Issues
- Check UART wiring (Pico ↔ ESP32)
- Verify baud rate (921600)
- Check connection status
- Review [Common Issues](Common-Issues.md)

### WiFi Problems
- Check WiFi credentials
- Verify 2.4GHz network (ESP32 doesn't support 5GHz)
- Check signal strength
- Review [Common Issues](Common-Issues.md)

## Diagnostic Tools

- **Web Interface Logs** - Settings → Logs
- **Serial Output** - Connect via USB serial
- **Diagnostics Page** - System diagnostics
- **Error Codes** - See [Error Codes](Error-Codes.md)

## Getting Help

If you can't resolve an issue:
- Check [Common Issues](Common-Issues.md)
- Review [Error Codes](Error-Codes.md)
- Use [Diagnostics](Diagnostics.md) tools
- See [Getting Help](Getting-Help.md) for community support

---

**Next:** [Common Issues](Common-Issues.md) or [Error Codes](Error-Codes.md)

