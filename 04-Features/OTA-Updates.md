# OTA Updates

BrewOS supports Over-The-Air (OTA) firmware updates, allowing you to update firmware wirelessly without physical access to the device.

## Overview

OTA updates provide:
- **Wireless updates** - Update firmware without USB
- **Convenient** - No need to open machine
- **Safe** - Automatic rollback on failure
- **Both firmwares** - Update Pico and ESP32

## Prerequisites

- **WiFi connection** - Machine must be on WiFi network
- **Internet access** - For downloading updates (if using cloud)
- **Stable connection** - Reliable WiFi connection required

## Updating ESP32 Firmware

### Via Web Interface

1. **Access interface**:
   - Go to Settings → Firmware Update
   - Or navigate to firmware update page

2. **Select firmware**:
   - Choose firmware file (`.bin` for ESP32)
   - Or use built-in update checker

3. **Upload and flash**:
   - Click "Upload"
   - Wait for upload to complete
   - Firmware flashes automatically
   - ESP32 reboots when complete

### Update Process

1. **Upload firmware** - Firmware uploaded to ESP32
2. **Verification** - Firmware verified (checksum)
3. **Flash** - Firmware written to flash
4. **Reboot** - ESP32 reboots with new firmware
5. **Verification** - System verifies new firmware

## Updating Pico Firmware

### Via Web Interface (OTA)

1. **Access interface**:
   - Go to Settings → Firmware Update
   - Select Pico firmware update

2. **Select firmware**:
   - Choose `.uf2` file for your machine type
   - `brewos_dual_boiler.uf2`
   - `brewos_single_boiler.uf2`
   - `brewos_heat_exchanger.uf2`

3. **Upload and flash**:
   - Click "Upload"
   - Wait for upload to complete
   - Click "Flash Pico"
   - Pico reboots when complete

### Update Process

1. **Upload firmware** - Firmware uploaded to ESP32
2. **Serial bootloader** - Pico enters bootloader mode
3. **Stream firmware** - ESP32 streams firmware to Pico
4. **Flash** - Pico writes firmware to flash
5. **Reboot** - Pico reboots with new firmware

## Automatic Updates

### Update Notifications

- **Version check** - System checks for updates
- **Notification** - Notifies when update available
- **Manual update** - User initiates update

### Update Channels

- **Stable** - Production releases
- **Beta** - Pre-release testing
- **Development** - Latest development builds

## Safety Features

### Automatic Rollback

If update fails:
- **Detection** - System detects failed update
- **Rollback** - Automatically reverts to previous firmware
- **Notification** - Alerts user of rollback
- **Stability** - Machine remains functional

### Verification

- **Checksum** - Firmware verified before flashing
- **Compatibility** - Machine type verified
- **Size check** - Firmware size verified

## Best Practices

### Before Updating

- **Backup settings** - Document important settings
- **Stable connection** - Ensure reliable WiFi
- **Don't interrupt** - Don't power off during update
- **Read release notes** - Understand what's new

### During Update

- **Wait patiently** - Updates take several minutes
- **Don't interrupt** - Don't close browser or power off
- **Monitor progress** - Watch update progress
- **Don't use machine** - Avoid using during update

### After Update

- **Verify version** - Check firmware version
- **Test functions** - Verify machine works correctly
- **Check settings** - Verify settings are intact
- **Review changes** - Read release notes

## Troubleshooting

### Update Fails

- **Check connection** - Verify stable WiFi
- **Try again** - Retry update
- **Check firmware** - Verify firmware file is correct
- **Manual update** - Try USB update method

### Update Stuck

- **Wait longer** - Updates can take time
- **Check progress** - Monitor update progress
- **Don't interrupt** - Don't power off or close browser
- **If stuck** - May need to power cycle and retry

### Version Not Updating

- **Check file** - Verify firmware file is correct version
- **Clear cache** - Clear browser cache
- **Try different file** - Download fresh firmware
- **Manual verification** - Check version after update

### Rollback Occurred

- **Check logs** - Review update logs
- **Try again** - Retry update
- **Check compatibility** - Verify firmware is compatible
- **Contact support** - If issue persists

## Related Features

- [Firmware Flashing](../02-Installation-Setup/Firmware-Flashing.md) - Manual update method
- [System Settings](../03-User-Manual/Settings-Overview.md) - System configuration

---

**Next:** [Machine-Specific Guides](../05-Machine-Specific/) or [Troubleshooting](../06-Troubleshooting/)

