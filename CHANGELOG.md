# Changelog – Metric Cycling (App: Metric)

All notable changes to this project are documented in this file.
Format follows [Keep a Changelog](https://keepachangelog.com/en/1.1.0/) and [Semantic Versioning](https://semver.org/spec/v2.0.0.html) (`MAJOR.MINOR.PATCH` + monotonically increasing macOS `CFBundleVersion` build).

## [Unreleased]

## Version 1.2.2 (Build 5) – 2026-11-14

### Changed
- **Unified Sidebar Workout Cards:** Intervals.icu scheduled events in `HomeView` now use the same bordered card layout, `14pt`/`12pt` typography, duration-first metadata (`docDuration` fallback to `movingTime`), leading icon (`calendar`), and context menu actions (including **Save to Custom Workouts**) as Custom Workouts.
- **Summary Transition & End-Screen Polish:** `AppModel.endRide()` switches to `SummaryView` immediately before writing the optional TCX export, preserves summaries for naturally completed workouts shorter than 10 seconds, scales the `WorkoutProfileView` bars in Summary by each step's recorded live intensity (`stepBiasFactors`), and keeps the summary header timestamp single-line while truncating long workout titles cleanly.

## Version 1.2.1 (Build 4) – 2026-11-14

### Changed
- **Clean Release Binaries:** Strip Mach-O debug symbols (`strip -S -x`) before ad-hoc code signing so local filesystem build paths are never embedded in distributed `Metric.app`, `Metric.dmg`, or `Metric.zip` artifacts.
- **Single-Source Versioning & Update Handling:** Unified version and build synchronization via `VERSION` (`SemVer 2.0.0 + Build`) into `Info.plist` and `AppVersion`, and added SemVer/pre-release-aware update comparison in `AppModel`.

## Version 1.2.0 (Build 3) – 2026-11-14

### Highlights
- **Automatic In-App Update Checks:** Metric now checks `Lassegra/metric` on GitHub Releases once on launch (quietly ignoring offline errors and skipped versions), adds a subtle sidebar update pill, an **Updates** section in Settings (`Automatic update check` + **Check Now …**), **Metric → Check for Updates …**, and an in-app **Update** sheet linking straight to `Metric.dmg`.
- **Live Workout Intensity ("Bias"):** Adjust target power live during a ride from `50%` to `150%` in `±5%` steps using the compact top-bar control (`− 100% +`), keyboard shortcuts (`↑` / `↓`, `0` to reset), the `Workout` menu, or compatible handlebar remotes. Updates FTMS ERG targets immediately, rescales the profile chart/zone colors/Up Next target, and scores post-ride `Power Hit Rate` accurately against the biased targets.
- **Redesigned Handlebar Remote Defaults:** Mapped `+` / `−` to **Intensity +5% / −5%**, `B` to **Reset intensity (100%)**, `A` to **Pause / Resume** (and Home screen Start), `←` / `→` to steps, `↑` / `↓` to `±5 s`, and `Y` to **Sound on/off** (all mappings remain customizable in Settings).
- **Live Preview in Workout Editor:** Upgraded the **Add / Edit Workout** sheet into a split-pane editor with real-time `Duration`, `IF`, `TSS`, and `Avg Target` metrics, live power profile chart, line-referenced parser notices, scrollable interval list, and an empty-state quick syntax guide.

## Version 1.1.0 (Build 2) – 2026-11-14

### Highlights
- **Power & Cadence Focused Training View (`RideView`):** Prioritizes live Power and Cadence telemetry and scales cards, countdowns, and the full-workout profile dynamically across different window sizes and aspect ratios to minimize unused whitespace.
- **Reliable TCX Export (`Download TCX` & `Save As …`):** Added a 1-click **Download TCX** action that saves `.tcx` files directly to `Downloads`, fixed the native macOS **Save As …** sheet dialog by registering `.tcx` (`local.metriccycling.tcx`) via `UTImportedTypeDeclarations` in `Info.plist`, and added inline export error reporting.
- **Copy Confirmation Feedback:** Workout **Copy** controls now show immediate visual confirmation (`Copied`) with animation so it is clear when the workout text is copied to the clipboard.
- **Reset All Settings:** Added a destructive **Reset All Settings** section (**Reset All …** → **Reset Everything** confirmation) in Settings that restores FTP, accent color, preferences, Intervals.icu Keychain API key, custom workouts, and paired Bluetooth devices/remotes back to defaults.
- **Styled Drag-to-Applications `Metric.dmg` Installer:** Built an Apple-style Finder DMG installer (`660×380 pt` Retina background with volume icon, titanium label capsules, and Gatekeeper first-launch note) and updated installation docs to prefer `Metric.dmg` over `Metric.zip`.

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
