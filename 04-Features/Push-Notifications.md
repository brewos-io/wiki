# Push Notifications

BrewOS supports web push notifications to alert you when your machine needs attention, even when you're away.

## Overview

Push notifications provide:
- **Remote alerts** - Receive notifications anywhere
- **Browser-based** - Works in modern browsers
- **Multiple types** - Various notification types
- **Configurable** - Choose which notifications to receive

## Setup

### Prerequisites

- **Modern browser** - Chrome, Firefox, Edge, Safari (latest)
- **HTTPS or localhost** - Required for push notifications
- **Cloud access** - For remote notifications (optional)

### Enable Notifications

1. **Subscribe**:
   - Go to Settings → Push Notifications
   - Click "Subscribe" or "Enable Notifications"
   - Grant browser permissions when prompted

2. **Configure**:
   - Select notification types
   - Choose which alerts to receive
   - Save settings

### Browser Permissions

When you subscribe:
- **Browser prompt** - Browser asks for permission
- **Grant permission** - Click "Allow" to enable
- **Deny** - Click "Block" to disable (can change later)

## Notification Types

### Machine Ready

Alert when machine reaches temperature:
- **Trigger**: Machine reaches READY state
- **Use case**: Know when machine is ready for first shot
- **Configurable**: Enable/disable in settings

### Low Water

Alert when water tank is low:
- **Trigger**: Water level drops below threshold
- **Use case**: Prevent dry heating
- **Important**: Critical safety notification

### Error Alerts

Alert when errors occur:
- **Trigger**: Machine enters error/fault state
- **Use case**: Immediate notification of problems
- **Important**: Critical for machine safety

### Maintenance

Cleaning and maintenance reminders:
- **Trigger**: Shot counter reaches threshold
- **Use case**: Remind to clean machine
- **Configurable**: Set shot count threshold

### Custom Notifications

Additional notification types may be available:
- **Shot complete** - When shot finishes
- **Schedule triggered** - When schedule activates
- **Eco mode** - When entering/exiting eco mode

## Configuration

### Settings

Configure in Settings → Push Notifications:

- **Enabled** - Enable/disable all notifications
- **Notification Types** - Select which types to receive
- **Test Notification** - Send test notification

### Browser Settings

Manage in browser:
- **Chrome/Edge**: Settings → Site Settings → Notifications
- **Firefox**: Preferences → Privacy & Security → Permissions
- **Safari**: Preferences → Websites → Notifications

## Usage

### Receiving Notifications

When notification is triggered:
- **Browser notification** - Appears as system notification
- **Sound** - Browser plays notification sound
- **Action** - Click notification to open interface
- **Dismiss** - Dismiss if not needed

### Notification Actions

Some notifications support actions:
- **Open interface** - Click to open web interface
- **Dismiss** - Dismiss notification
- **Settings** - Go to notification settings

## Best Practices

### Notification Selection

- **Important only** - Enable only important notifications
- **Avoid spam** - Don't enable too many types
- **Test first** - Test notifications before relying on them
- **Review regularly** - Adjust based on usage

### Browser Management

- **Keep browser open** - Notifications work when browser is open
- **Background tabs** - Works in background tabs
- **PWA** - Install as PWA for better experience
- **Multiple devices** - Subscribe on multiple devices

## Troubleshooting

### Notifications Not Appearing

- **Check permissions** - Verify browser permissions granted
- **Check subscription** - Verify notifications are subscribed
- **Check browser** - Some browsers have limitations
- **Check HTTPS** - Requires HTTPS or localhost
- **Try different browser** - Test with different browser

### Not Receiving Notifications

- **Check enabled** - Verify notifications are enabled
- **Check types** - Verify notification types are selected
- **Check browser** - Browser must be running
- **Check connection** - Requires internet connection (for cloud)
- **Review logs** - Check for notification errors

### Too Many Notifications

- **Disable types** - Disable unnecessary notification types
- **Adjust thresholds** - Change notification thresholds
- **Review settings** - Review and adjust notification settings

## Related Features

- [Cloud Access](Cloud-Access.md) - Remote access
- [Scheduling](Scheduling.md) - Automated schedules
- [Statistics](Statistics.md) - Shot tracking

---

**Next:** [Power Metering](Power-Metering.md) or [OTA Updates](OTA-Updates.md)

