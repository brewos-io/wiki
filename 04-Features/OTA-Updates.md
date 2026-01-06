# OTA Updates

BrewOS supports Over-The-Air (OTA) firmware updates, allowing you to update firmware wirelessly without physical access to the device.

## Overview

OTA updates provide:

- **Wireless updates** - Update firmware without USB
- **Convenient** - No need to open machine
- **Automatic download** - Both firmwares download from GitHub releases automatically
- **Combined update** - Updates both Pico and ESP32 in a single operation
- **No manual uploads** - Everything is handled automatically

## Prerequisites

- **WiFi connection** - Machine must be connected to WiFi
- **Internet access** - Required for downloading firmware from GitHub releases
- **Stable connection** - Reliable WiFi connection required during update
- **Device powered on** - Both Pico and ESP32 must be powered and connected

## Updating Firmware

BrewOS uses a **combined OTA update** that automatically updates both the Pico (machine controller) and ESP32 (network controller) in a single operation. Both firmwares are downloaded from GitHub releases automatically - no manual file uploads are required.

### Via Web Interface

1. **Access interface**:

   - Go to Settings → System Settings → Firmware Update
   - The system automatically checks for available updates

2. **Select update channel**:

   - **Stable** - Production releases (recommended)
   - **Beta** - Pre-release versions for testing
   - **Dev** - Latest development builds (dev mode only)

3. **Check for updates**:

   - Click "Check" to refresh available versions
   - Available updates are shown with version numbers and release dates

4. **Install update**:
   - Click "Install" on the desired version
   - Confirm the update in the dialog
   - The system automatically downloads and installs both firmwares

### Combined Update Process

The OTA update process automatically handles both firmwares in sequence:

#### Step 1: Update Pico (Machine Controller)

1. **Download** - ESP32 downloads Pico firmware from GitHub releases (automatically selects correct file for your machine type)
2. **Bootloader entry** - ESP32 sends command to Pico to enter serial bootloader mode
3. **Bootloader ACK** - Pico confirms bootloader is ready
4. **Stream firmware** - ESP32 streams firmware data to Pico via UART
5. **Flash** - Pico writes firmware to flash memory
6. **Reboot** - Pico resets and boots with new firmware
7. **Verification** - ESP32 verifies Pico is running the new version

#### Step 2: Update ESP32 (Network Controller)

1. **Download** - ESP32 downloads its own firmware from GitHub releases
2. **Flash** - Firmware is written to flash memory
3. **Reboot** - ESP32 automatically reboots with new firmware
4. **Verification** - System verifies new firmware on boot

**Note:** Both firmwares are downloaded automatically from GitHub releases. The system automatically selects the correct Pico firmware file based on your machine type (dual boiler, single boiler, or heat exchanger). No manual file uploads or selections are required.

## Update Channels

BrewOS supports three update channels:

### Stable Channel

- **Recommended for most users**
- Production releases that have been tested
- Most stable and reliable versions
- Tagged releases (e.g., `v1.0.0`)

### Beta Channel

- Pre-release versions for testing
- Includes new features before stable release
- May contain bugs or incomplete features
- Tagged as pre-releases on GitHub

### Dev Channel

- Latest builds from main branch
- For developers and advanced users
- May be unstable or contain breaking changes
- Only available when dev mode is enabled
- Tagged as `dev-latest` on GitHub

You can switch between channels in the firmware update settings. The system will show available updates for your selected channel.

## Update Notifications

The system can notify you when updates are available:

- **Automatic checking** - System periodically checks GitHub for new releases
- **In-app notifications** - Notification appears when updates are available
- **Manual check** - Click "Check" button to manually check for updates
- **Manual installation** - All updates require user confirmation to install

**Note:** Updates are not installed automatically. You must manually initiate each update.

## Safety Features

### Verification

- **Size check** - Firmware size is verified before flashing
- **Download verification** - ESP32 verifies complete download before flashing
- **Flash verification** - ESP32 OTA library verifies successful flash

### Error Handling

- **Connection errors** - Automatic retry on network failures
- **Download errors** - Clear error messages if download fails
- **Flash errors** - Update is aborted if flash fails
- **Progress tracking** - Real-time progress updates during download and flash

### Update States

The system provides real-time feedback during updates:

- **Download** - Downloading firmware from GitHub
- **Flash** - Writing firmware to flash memory
- **Complete** - Update finished successfully
- **Error** - Update failed with error message

## Best Practices

### Before Updating

- **Check release notes** - Read what's new in the update
- **Stable connection** - Ensure reliable WiFi connection
- **Don't interrupt** - Don't power off or close browser during update
- **Backup settings** - Document important settings (settings are preserved, but good practice)

### During Update

- **Wait patiently** - Updates can take several minutes
- **Don't interrupt** - Don't close browser, power off, or disconnect WiFi
- **Monitor progress** - Watch the update overlay for progress
- **Don't use machine** - Avoid using the machine during update

### After Update

- **Verify version** - Check firmware version in System Settings
- **Test functions** - Verify machine works correctly
- **Check settings** - Verify settings are intact
- **Review changes** - Read release notes for new features

## Troubleshooting

### Update Fails to Start

- **Check connection** - Verify stable WiFi and internet connection
- **Check device status** - Ensure device is online and connected
- **Try again** - Retry the update
- **Check logs** - Review system logs for error messages

### Download Fails (ESP32)

- **Internet connection** - Verify device has internet access
- **GitHub access** - Check if GitHub releases are accessible
- **Retry** - The system automatically retries on network errors
- **Check version** - Verify the selected version exists on GitHub
- **Wait and retry** - GitHub may be temporarily unavailable

### Pico Update Fails During Combined OTA

- **Machine type detection** - Ensure device is powered on and connected (ESP32 needs to know machine type)
- **Download failure** - Check internet connection and GitHub accessibility
- **Bootloader entry** - Pico may fail to enter bootloader mode
- **UART connection** - Verify ESP32-Pico UART connection is working
- **Storage space** - ESP32 may not have enough free space for temporary firmware file
- **Retry** - Try the update again

### Update Stuck or Slow

- **Wait longer** - Downloads can take several minutes depending on connection
- **Check progress** - Monitor the update overlay for progress
- **Don't interrupt** - Don't power off, close browser, or disconnect WiFi
- **Network speed** - Slow internet will make downloads take longer
- **If truly stuck** - Wait 5-10 minutes, then check device status

### Device Disconnects During Update

- **Normal behavior** - Device may reboot during update (this is expected)
- **Wait for reconnect** - Device will reconnect automatically after reboot
- **Check overlay** - Update overlay will show reconnection status
- **Don't refresh** - The overlay persists across page refreshes
- **If stuck offline** - Wait 5 minutes, then check if device is back online

### Version Not Updating

- **Check current version** - Verify what version is actually installed
- **Refresh page** - Clear browser cache and refresh
- **Check channel** - Ensure you're checking the correct update channel
- **Manual verification** - Check version in System Settings after update completes

### Combined Update Fails Partway Through

- **Pico update succeeded, ESP32 failed** - Device will restart and may be in inconsistent state
- **Check versions** - Verify which firmware was updated successfully
- **Retry update** - Try the update again (system will skip already-updated firmware if possible)
- **Check logs** - Review system logs for specific error messages
- **Manual recovery** - As last resort, use USB update method for the failed component

### Update Error Messages

Common error messages and solutions:

- **"Not enough storage space"** - ESP32 doesn't have enough free space for temporary firmware files
- **"Download failed"** - Check internet connection and GitHub accessibility
- **"Connection stalled"** - Network issue during download, wait and retry
- **"Timeout"** - Download took too long, check connection speed
- **"Write failed"** - Flash memory error, retry update
- **"Device not ready"** - Machine type not detected, ensure device is powered on and connected
- **"Device not responding"** - Pico failed to enter bootloader mode, check UART connection
- **"Update failed - restarting"** - One component failed, device will restart and may need retry

## Related Features

- [Firmware Flashing](../02-Installation-Setup/Firmware-Flashing.md) - Manual update method
- [System Settings](../03-User-Manual/Settings-Overview.md) - System configuration

---

**Next:** [Machine-Specific Guides](../05-Machine-Specific/) or [Troubleshooting](../06-Troubleshooting/)
