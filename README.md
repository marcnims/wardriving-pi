# Wardriving Pi

A Raspberry Pi 4B wardriving rig that boots straight into Kismet. Plug it in, drive, collect.

---

## Hardware

| Component | Details |
|-----------|---------|
| Raspberry Pi 4B | 4GB RAM running Raspberry Pi OS with GUI |
| Touchscreen | Attached display for live Kismet output — fully self-contained |
| Alfa AWUS036ACHM | Dual-band wireless adapter in monitor mode, 2.4GHz and 5GHz |
| GlobalSat BU-353S4 | USB GPS receiver — geo-tags every captured network automatically |

## Antennas

| Antenna | Gain | Notes |
|---------|------|-------|
| Stock | 3 dBi | Default omnidirectional, short range |
| High-Gain | 9 dBi | ~3x the range of stock |
| Directional Panel | 8/10 dBi | Focused beam for targeting a specific area |

---

## Setup

Kismet launches on boot via a systemd service with the Alfa adapter and GPS puck as capture sources. Power it on and it's already running — no keyboard, no setup needed.

See [`kismet.service`](kismet.service) for the systemd unit file.

Logs are stored locally and can be pulled off and opened in GPSPrune or Google Earth via the exported KML file.

---

## Build Notes

`make` kept crashing on the Pi during the Kismet build, so I cross-compiled on my workstation targeting ARM64 and transferred the binaries over manually. It worked — but afterwards I found out DragonOS comes with Kismet pre-installed. Lesson learned: research the ecosystem before spending hours building from scratch.
