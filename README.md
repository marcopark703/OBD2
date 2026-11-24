# Universal OBD-II Dashboard PWA — v1.1.0

## Release contents
- Responsive PWA with a dedicated narrow-screen layout for Galaxy Fold cover displays.
- Speed uses a dominant full-width panel; RPM moves to a separate row on narrow screens.
- Enlarged coolant, oil-temperature and boost gauges, plus battery and engine-load cards.
- Near-black / charcoal / red theme based on the user's Photoshop mockup.
- Generic BLE device chooser, common BLE GATT profile probing and standard OBD-II PID polling.
- Full-screen request, optional Screen Wake Lock, connection log and offline app-shell cache.

## Deploy and install
1. Extract this ZIP.
2. Upload the contents to an HTTPS static host such as GitHub Pages or Cloudflare Pages.
3. Open the HTTPS URL in an Android browser supporting Web Bluetooth.
4. Choose Install / Add to Home Screen in the browser menu.
5. Open the installed PWA, press CONNECT OBD-II, and select the BLE adapter.

## Known limitations
- This is a first field-test release, not a universally validated product.
- Web Bluetooth requires a supported browser and secure HTTPS origin.
- Bluetooth Classic SPP and Wi-Fi adapters are not supported by this browser-only PWA.
- BLE adapters use different GATT layouts. Several common profiles are probed, but all adapters are not guaranteed.
- ELM-compatible commands and standard PID support vary by adapter and vehicle ECU.
- Oil temperature (PID 0x5C) is displayed only if supported by the ECU.
- Boost is calculated from MAP minus BARO; both values must be supported.
- Vehicle-specific enhanced PIDs are not implemented in v1.1.0.
- Refresh rate depends on adapter throughput, ECU response and sequential polling.
- Validate readings while parked. Do not troubleshoot or operate the dashboard while driving.

## v1.1.0 test changes
- Speedometer: large analog needle dial plus bold digital speed readout.
- RPM: large digital value with a segmented tachometer scale.
- Speed needle is interpolated for smoother movement while the numeric reading remains current.
- Standard oil-temperature PID 0x5C is checked once per connection; unsupported values show N/A instead of repeatedly polling.
