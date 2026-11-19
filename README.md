<p align="center"><img src="docs/logo.png" width="160" alt="KHPAL GPS logo"></p>

# KHPAL GPS

KHPAL GPS is an Xposed/LSPosed (Vector) module for Android. Pick a spot on the map and the module delivers it to the apps you select, with natural live variation.

Developer: **MK_MANDOKHAIL**  ·  Version **1.0.3**  ·  Package `com.khpalgps.zb`

## Features
- Map picker (free OpenStreetMap / Esri / OpenTopoMap tiles in the *foss* build, Google Maps in the *full* build) with zoom + / − buttons
- **The location provider follows Android**: the injected location keeps the provider Android really used (gps, network, fused), never forced to GPS. An app that asks for GPS while GPS has no fix is served by the network provider
- Settings in a clear order, each with a short description in its pop-up: Network accuracy, GPS accuracy, Fused accuracy, Horizontal accuracy, Vertical accuracy, Altitude, MSL altitude, Speed, Bearing, Bearing accuracy, Position jitter, Position drift, Randomize location, Randomize location interval, Smart provider learning system
- Network, GPS and Fused accuracy, each with a "randomize ±" range and an optional **systematic accuracy drift** (the accuracy rises and falls gradually instead of jumping). Each can follow the learned behaviour with the **SPLS learned behaviour deployment** toggle
- Horizontal accuracy and vertical accuracy, each with a value and a "randomize ±" range. **Network Accuracy sync** makes horizontal accuracy exactly equal to the network accuracy. Vertical accuracy is never reported higher than the provider accuracy
- Altitude and MSL altitude (with accuracy), speed in m/s (a network location always reports 0)
- **Bearing** (*Auto from movement* or *Fixed*) and **Bearing accuracy**, each with a "randomize ±" range, and **Position jitter** and **Position drift**. Each can be linked to SPLS
- Optional random position inside a radius, with a custom interval and a randomize-interval (hours / minutes / seconds)
- **Smart Provider Learning System (SPLS)**: records in the background how the network, GPS and fused providers really behave, shows the record counts, imports and exports the records as CSV (15 columns, including bearing, bearing accuracy, jitter and drift; older 11-column files still import) and can delete them to learn another location. Each provider is shown as a collapsible table of 12 accuracy ranges with the required samples. When every provider has at least 500 records and the compulsory ranges are filled, the **Network-Linked** settings (vertical accuracy, altitude, MSL, speed) and the settings linked to SPLS follow the learned behaviour. SPLS recording and mocking never run at the same time, with clear guidance when one blocks the other
- **SPLS recording**: the **Enable SPLS recording** switch is in Smart provider learning system. Before a recording starts, a checklist waits until Network, GPS and Fused all have a tick (with hints and a Cancel button). Each provider has its own Pause / Resume and Stop buttons, and its own editable maximum number of records (no limit unless you set one). Only that provider stops at its maximum
- **SPLS locations**: each recording belongs to a named SPLS location: without an area limit, around where you are now, or around an area picked on the map (radius from 1.5 m to 10,000 m). The SPLS Locations list in the menu lets you rename, change the radius, pause, stop or delete a record. A new area cannot overlap a saved area, and a clear warning is shown. While recording, walking into another saved area moves the recording to that area. A recording without an area limit is never stopped or moved by other areas
- **SPLS Diagnostic Logger** in the menu: on-device diagnostics that do not store coordinates and do not change SPLS behaviour, with an export button
- Favorites, search, joystick, dark theme

## Use responsibly
Intended for app developers, testers and privacy-minded users. Respect local laws and the rules of the apps you use.

## Credits and licence
KHPAL GPS is a **modified and updated version** for location mocking. It has been developed to meet the modern requirements of location mocking. It is inspired from GPS Setter by [@jqssun](https://github.com/jqssun/android-gps-setter), which itself is based on GPS Setter by [@Android1500](https://github.com/Android1500/GPS-Setter). Licensed under the **GNU General Public License v3.0** (see `LICENSE`). The original copyright and licence notices are kept in `NOTICE`, as the GPL requires.
