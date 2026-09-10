# ADB and Android emulators

SmartMacroAI uses Android Debug Bridge for emulator automation.
Supported operations include target discovery, display-size reading, capture, tap, swipe, key events, and text input.

## Readiness

The selected target must appear in `adb devices` with the state `device`.
These states are not ready:

- `offline`
- `unauthorized`
- missing serial

Wait for Android to finish booting before starting a workflow.

## Coordinates

ADB coordinates use the Android logical display returned by `wm size`.
They are not Windows desktop coordinates and are not the outer emulator-window size.
Normalized Click and Drag steps are recalculated against the current Android display.
Pixel positions and image/OCR regions may require adjustment after a resolution or orientation change.

## Connection types

Emulators may expose ADB through a local TCP port or a vendor-managed connection.
A physical device may use USB or wireless debugging.
Ports, authorization, and capture behavior vary between vendors.

## Capture fallback

Some emulator renderers may not return usable frames through `adb screencap`.
SmartMacroAI can use a host-window capture fallback when it can map the selected ADB serial to the correct emulator window.
Compatibility remains dependent on the emulator renderer.

## Text input

ADB text input is most reliable for ASCII characters.
Unicode input may require an emulator-specific clipboard method.

## Troubleshooting

1. Confirm the expected serial in `adb devices`.
2. Verify that its state is `device`.
3. Confirm the reported `wm size` and orientation.
4. Test capture before testing input actions.
5. Re-select the target after restarting the emulator.

[Back to English README](../README.md) · [Về README tiếng Việt](../README.vi.md)
