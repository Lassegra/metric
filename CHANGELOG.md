# Changelog – Metric Cycling (App: Metric)

## Version 1.0.0 (Build 1) – 2026-11-13

First public release for macOS 14+ (Universal Binary for Apple Silicon & Intel, distributed directly via GitHub Releases as `Metric.zip` and `Metric.dmg`).

### Highlights
- **Project & App Naming:** Published as **Metric Cycling** (`MetricCycling`, Bundle ID `local.metriccycling`), while the end-user macOS app (`Metric.zip` → `Metric.app`), window title, menu bar, UI copy, and TCX exports (`Metric_*.tcx`) consistently display **Metric**.
- **High-Contrast Cockpit & Projector Display:** Legible, scaled layout showing active step, Coggan zone, target vs. actual power and cadence accuracy feedback, step countdown, next-step preview, and full-workout profile canvas.
- **Offline Custom Workouts:** Create and edit workouts in compact text syntax, choose from 4 built-in templates, import `.txt` files or clipboard text, duplicate, and pin custom workouts to the top.
- **Optional Intervals.icu Integration:** Personal API key secured strictly in the macOS Keychain (`kSecAttrAccessibleWhenUnlockedThisDeviceOnly`), performing strictly read-only HTTPS GET calls (no redirects, no cookies) for scheduled workouts (today + 6 days) and cycling FTP.
- **Bluetooth LE Telemetry & Optional FTMS ERG Control:** Connects to Smart Trainers (`0x2AD2` FTMS Indoor Bike Data + `0x2A63` Cycling Power) and Heart Rate Straps (`0x2A37`) with automatic reconnect; optional sequential FTMS ERG Control (`0x2AD9`) handles start, pause (`0x08 0x02`), 0-rpm spin-up resume, target coalescing, and `0x05` permission retry.
- **Compatible Bluetooth Handlebar Remotes:** Configurable button mapping, single-trigger press decoding, and collapsible raw packet diagnostics.
- **Account-Free Synchronized Starts (`Sync :00`):** One-click workout copy/share paired with system-clock whole-minute synchronized start (`−1 min`, `+1 min`, `Start Now`).
- **Summary & TCX Export:** Post-ride analytics (Duration, Avg Power, NP, IF, TSS, Avg/Max HR, Avg Cadence, cadence/power target accuracy, time in zones, and target-vs-actual chart), optional automatic export to `Downloads`, and manual `Export TCX …` save dialog.
- **Demo Mode & Native Window Integration:** Realistic simulated telemetry (`1×`–`20×` playback speed) and clean macOS titlebar clearance with full-height sidebar framing and full-screen support.
